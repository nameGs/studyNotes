# Java复习

## Java基础

## Java进阶


### 多线程

* 进程：在一个时间段上可以运行多个程序，并且程序需要进行资源的抢占。同一个时间段上会有多个程序并发执行，同一个时间点上只有一个进程执行。
* 线程：进程基础上划分更小的程序单元，线程是进程基础上创建并使用的，所以线程依赖于进程的支持。但是线程的启动速度比进程速度快很多。
* Java是多线程的编程语言，Java在进行并发处理问题的时候可以更加高效。
* 使用多线程： 
  * 阻塞。当系统发生阻塞现象，可以考虑使用多线程。
  * 依赖，当两个业务没有依赖关系并且他们容易阻塞时可以使用多线程。

#### 上下文切换

* ==时间片==是CPU分配给各个线程的时间，时间片非常短。
* CPU通过时间片分配算法来循环执行任务，切换前会保存上一个任务的执行状态，==任务从保存到再加载的过程就是一次上下文切换==。
* 上下文切换会增加程序的开销导致速度变慢。
* 解决上下文切换的方法有：
  * 无锁并发编程；多线程竞争锁时会引起上下文切换；
  * CAS算法：使用算法而不需要加锁；
  * 使用最少线程：避免创建不必要的线程； 
  * 协程：在单线程中实现多任务的调度。

#### 多线程实现

* 继承Thread类实现多线程，覆写Thread中的run()方法。多线程中执行方法都应该在run()方法中定义。

  * run()方法不能直接被调用。

  ```java
  class Text extends Thread{
      private String message;
      Text(String message){
          this.message = message;
      }
      @Override
      public void run() {
          for(int i = 0;i < 10 ;i ++){
              System.out.println(message);
          }
      }
  }
  public class Text01{
      public static void main(String[] args) {
          new Text("Hello World ! Let's study").start();
          new Text("Hello World ! Let's play").start();
          new Text("Hello World ! Let's watch TV").start();
      }
  }
  ```

  * 每个线程类都只允许启动一次，如果重复启动则会抛出异常IllegalThreadStateException。
  * Thread类中的start0()方法使用JNI技术将线程适用于不同的操作系统中。
  * start()方法执行步骤：
    1. 通过JVM告诉系统创建Thread；
    2. 操作系统开辟内存并使用Windows SDK中的createThread()函数拆功能键Thread线程；
    3. 操作系统对Thread进行调度，以确定执行时机；
    4. Thread再操作系统中被创建完成。
  * 执行start()方法顺序并不代表执行run()方法顺序。
  * run()方法和start()方法的区别
    * run()方法：立即执行run()方法，不启动新线程；
    * start()方法：执行run()方法时机不确定，启动新的线程。

* 实现Runnable接口实现多线程

  * Runnable使用函数式编程。

  ```java
  class Text implements Runnable{
      private String message;
      Text(String message){
          this.message = message;
      }
      @Override
      public void run() {
          for(int i = 0;i < 10;i ++){
              System.out.println(message);
          }
      }
  }
  public class Text01{
      public static void main(String[] args) {
          Thread thread1 = new Thread(new Text("A"));
          Thread thread2 = new Thread(new Text("B"));
          Thread thread3 = new Thread(new Text("C"));
          thread1.start();
          thread2.start();
          thread3.start();
      }
  }
  ```

* 对比Runnable和Thread两种实现：

  * Thread单继承具有局限性；Runnable是接口，间接实现多继承更加方便。
  * Thread类是Runnable的实现类，继承Thread类实际上还是覆写Runnable的run方法。
  * 多线程启动必须得用Thread类的start()方法。
  * Runnable缺点是执行完毕后无法获得返回值。

* Callable实现多线程

  * Callable中只有个call方法，该方法可以获得泛型的返回值。

  ```java
  //Callable实现多线程
  public class Main {
  	public static void main(String[] args) throws Exception {
          FutureTask<String> thread1 = new FutureTask<>(new Example());
          Thread thread = new Thread(thread1);
          thread.start();
          System.out.println(thread1.get());
      }
  }
  class Example implements Callable {
      @Override
      public Object call() throws Exception {
          for (int i = 0;i < 5;i ++){
              System.out.println("线程执行 : "+i);
          }
          return "线程执行完毕";
      }
  }
  ```

* Runnable和Callable的区别：

  * Runnable比Callable更早。
  * Runnable没有返回值，Callable有返回值。

#### Thread类中方法详解

* `Thread.currentThread();`该方法可返回**代码段**正在被哪个线程调用。
* `this`表示的是继承Thread或实现Runnable的类，与上边相区别。
* `isAlive();`该方法用于判断当前线程是否存活，测试线程是否处于活动状态。
  * 活动状态：线程处于==启动且尚未终止==的状态。
  * 如果线程处于==正在运行或准备开始运行==的状态，就可以认为线程是存活的。
* `sleep(long millis);`在指定的时间（毫秒）内让this.currentThread()返回的线程休眠。
* `sleep(long millis,int nanos);`在指定的时间（毫秒+纳秒）内让this.currentThread()返回的线程休眠，受到系统计时器和调度程序的精度和准确性的影响。
* `StackTraceElement[] getStackTrace();`返回一个表示该线程堆栈跟踪元素数组（追踪执行过的方法等）。
  * 如果该线程未启动或已终止：返回一个零长度的数组。
  * 如果返回不是零长度，则第一个就是堆栈顶，表示该数组中最新的方法调用。
* `static void dumpStack();`将当前线程的堆栈跟踪消息输出至标准错误流。
* `static Map<Thread,StackTraceElement[]> getAllStackTrace();` 返回所有活动线程的堆栈跟踪的一个映射，映射键是线程，值是StackTraceElement数组，该数组表示相应的Thread的堆栈转储。
* `getId();`获得线程的唯一标识。
* `public static boolean holdsLock(Object obj);`当currentThread在指定的对象上保持锁定时，返回true。

#### 继承Thread类和实现Runnable接口内部流程分析

* 继承Thread类在运行start()方法后JVM调用Thread.java的run()方法，源码：

  ```java
  @Override
  public void run(){
      //target就是创建Thread对象时放入的Runnable对象，
      if(target != null){
          target.run();
      }
  }
  ```

  target在init()方法中复制初始化，init()方法在Thread中的构造方法中调用。

#### 线程运行状态

* 执行完start()方法后线程进入准备就绪状态。
* 进行资源分配。
* 完成。

#### 线程命名

* 多线程运行是不确定得状态，因此取名是很重要的概念。

* 命名：

  * 构造方法命名。

  * 通过普通方法：

    ```java
    public final void setName(String name);   //设置名字
    public final String getName();			  //修改名字
    ```

* 获取当前线程得方法：currentThread();

* 当开发者为线程设置名字后会使用设置得名字，如果没有设置名字则使用默认的名字。

* 主方法也是一个线程，每当使用java命令执行程序的时候就表示启动了一个JVM的进程，一台电脑上可以同时启动多个JVM进程，每个JVM进程都会有自己的线程。将耗时复杂的工作交给子线程操作，使得主线程和子线程并发进行。主线程负责处理整体又称，子线程负责处理耗时项目。


#### 线程的休眠

* 暂缓线程的进行叫做线程的休眠。

  ```java
  //第一个可以设置毫秒参数
  public static native void sleep(long millis) throws InterruptedException;
  //第二个更精确，可以设置毫秒和纳秒
  public static void sleep(long millis, int nanos)
      throws InterruptedException;
  ```

  在休眠过程中可能会产生中断异常(InterruptedException)，中断异常必须处理。休眠时间到立马继续执行代码。

  ```java
  public class Text01 {
  	public static void main (String[] args) throws Exception{
  			new Thread(()-> {
  			for(int i = 0;i < 5;i ++) {
  				System.out.println(i+1);
  				try {
  					Thread.sleep(1000);
  				} catch (InterruptedException e) {
  					e.printStackTrace();
  				}
  			}
  		}).start();
  	}
  }
  ```

#### 线程的中断

* 线程中断的方法：
  * 使用==interrupt做退出标志，并合理利用异常==使线程正常退出。
  * ~~使用stop()方法强行终止线程~~，缺点有：
    * 容易造成业务处理的不确定性；
    * 暴力停止线程造成清理工作不能完成或数据添加不完整，抛出ThreadDeath异常。
    * 对锁定对象进行“解锁”，会导致数据得不到同步处理，进而出现数据不一致的情况。
  * 使用interrupt做退出标记，~~并使用return方法~~，缺点：
    * return前需要搭配一个写入日志的代码，代码显得臃肿。

* 判断线程是否是停止状态
  * `public static boolean interrupted();`测试currentThread()是否已经中断，测试完后清楚interrupt状态。
  * `public boolean isInterrupted;`测试this关键字所在类的对象是否已经中断，不对线程状态做出改变。
  
* 中断线程，判断线程是否是停止状态，如果是则可以使用==抛出异常==停止下边代码的执行。

  ```java
  public class Main {
  	public static void main(String[] args) throws Exception {
          MyThread my = new MyThread();
          my.start();
          Thread.sleep(2000);
          my.interrupt();
  	}
  }
  class MyThread extends Thread{
      @Override
      public void run() {
          try{
              for(int i = 0;i < 500000;i ++){
                  if (this.isInterrupted()){
                      throw new InterruptedException();
                  }
                  System.out.println(i);
              }
          }catch (InterruptedException e){
              System.out.println("我死了!");
          }
      }
  }
  ```

  * 产生异常同样可以释放锁。

* 将sleep()方法和interrupt()方法连用也会抛出InterruptException异常。

#### 暂停线程

* ~~suspend()方法搭配resume()方法~~可以不销毁而仅仅暂停线程，缺点是：
  * 产生死锁。
  * 数据不完整。
* ==使用wait()方法和notify()方法或notifyAll()方法==

#### 线程的强制执行

* 满足于某些条件之后，某个线程对象可以独占资源，一直到该线程的程序执行结束。获取到某个线程后可以通过Thread中的join方法使某个线程独占。

  ```java
  public class Text01 {
  	public static void main (String[] args) throws Exception{
  		Thread mainThread = Thread.currentThread();
  		Thread thread1 = new Thread(()-> {
  			for(int i = 0;i < 5; i++) {
  				System.out.println("小线程 : 我抢得资源次数 : " + i);
  				if(i == 3) {
  					System.out.println("大线程 : WDNMD敢跟我抢资源?");
  	  			try {
  						mainThread.join();
  					} catch (InterruptedException e) {
  						e.printStackTrace();
  					}
  				}
  			}
  		},"小线程");
  		thread1.start();
  		for(int x = 0;x < 10;x ++) {
  			System.out.println("大线程 : 我抢得资源次数 : " + x);
  		}
  	}
  }
  ```

#### 线程的礼让

* 线程的礼让：线程让出资源让别的线程先执行。线程的礼让可以通过Thread中的`yieId()`方法实现。调用`yieId()`方法进行线程礼让时，每次只会礼让一次。

  ```java
  public class Text01 {
  	public static void main (String[] args) throws Exception{
  		Thread mainThread = Thread.currentThread();
  		Thread thread1 = new Thread(()-> {
  			for(int i = 0;i < 5; i++) {
  				System.out.println("小线程 : 我抢得资源次数 : " + i);
  				if(i >= 0) {
  					System.out.println("小线程 : 大哥你先");
  					Thread.yield();
  				}
  			}
  		},"小线程");
  		thread1.start();
  		for(int x = 0;x < 10;x ++) {
  			System.out.println("大线程 : 我抢得资源次数 : " + x);
  		}
  	}
  }
  ```

#### 线程的优先级

* 理论上来说线程的优先级越高越容易抢占资源。Thread中针对优先级有如下操作：
  * 设置优先级：`public final void setPriority(int newPriority);`
  * 获取优先级：`public final int getPriority();`
* 优先级分为三类:
  1. 最高优先级：`public final static int MAN_PRIORITY = 10;`
  2. 中等优先级：`public final static int NORM_PRIORITY = 5;`
  3. 最小优先级：``public final static int MIN_PRIORITY = 1;`
* 优先级具有继承性。比如A启动B，则B的优先级和A一样。
* 当线程的优先级很大时，谁先执行完和代码的调用顺序无关。
* 优先级并不是绝对，它具有随机性。

#### synchronized关键字 (同步锁)

* 同步会造成程序整体性能下降，而异步才会提高程序性能。

* **synchronized同步方法**

  * 同步方法锁住的是当前对象，加在静态方法上是类锁。
  * 同步就是指多个操作在**同一时间段内**只能有一个线程进行，其他线程需等待其结束才可以执行。
  * 可以使用`synchronized`关键字来实现，利用此方法可以定义同步方法或同步代码块。
  * synchronized可以对任意对象及方法加锁，而加锁的这段代码称为**互斥区**或**临界区**。
  * 一个线程调用有synchronized关键字修饰的对象或代码块*以下简称同步方法*时，首先判断这个对象或代码块是否被上锁，如果有锁就说明有其他线程正在调用，则必须等其他线程调用结束。
  * 执行流程：如果一个线程想执行同步方法中的内容时,首先尝试申请锁，如果申请到则执行，如果申请不到则会反复申请，并且和其他线程争夺锁，直到申请成功。
  * 多个线程执行同一业务对象中的不同同步方法时，是按顺序同步的方式执行。
  * sychronized具有==重入锁==的功能，在使用sychronized时，当一个线程得到一个对象锁后，再次请求此对象锁时是可以得到该对象锁的。在synchronized方法/块的内部调用本类的其他synchronized方法/块时，是永远可以得到锁的。
  * ==可重入锁==：指的是自己可以再次获取自己的内部锁。
  * 锁重入也支持父子类继承的环境。子类可以通过锁重入调用父类的同步方法。
  * 子类重写父类的方法同样需要加上synchronized关键字实现同步。
  * synchronized关键字再字节码指令中的原理：
    * 在方法上加synchronized关键字实现同步的原因是使用flag标记ACC_SYNCHRONIZED，调用方法时先检查是否有这个标记，如果有则执行线程先持有同步锁，然后执行，执行完后释放锁。
    * 使用synchronized代码块，则使用monitorenter和monitorexit指令进行同步处理。

  同步方法进行处理：

  ```java
  synchronized public void method(){
      //方法体
  }
  ```

  ```java
  public class Text01 {
  	public static void main (String[] args) throws Exception{
  		Cinema cinema = new Cinema();
  		new Thread(cinema,"王乃华").start();
  		new Thread(cinema,"蛋蛋").start();
  		new Thread(cinema,"小黑").start();
  	}
  }
  class Cinema implements Runnable{
  	private int ticket = 10;
  	public synchronized void sell() {
  		try {
  			Thread.sleep(1000);
  			System.out.println(Thread.currentThread().getName()+"买票了，ticket:"+ticket--);
  		} catch (InterruptedException e) {
  			System.out.println("WDNMD电影院关门了。");
  		}
  	}
  	@Override
  	public void run() {
  		sell();
  	}
  }
  ```

* **synchronized关键字同步代码块**
  
  * 同步代码块将==任意对象==作为锁。

#### volatile关键字

* volatile关键字主要是在属性定义上使用的，表示此属性为直接数据操作，而不进行副本的拷贝处理。

* 正常数据操作流程：

  * 读取属性的值并拷贝出一个副本；
  * 操作副本获取结果的值；
  * 将结果赋给属性。

  volatile关键字直接省略拷贝副本，而是直接操作内存。

#### 脏读

* 发生原因是读取实例变量时，此值已经被其他线程更改过。
* 脏读前一定会出现不同线程一起去写实例变量的情况。
* 使用synchronized关键字可以避免脏读。

#### 死锁

* 产生的主要原因：彼此都在互相等待对方先让出资源。
* 死锁是开发中出现的一种不确定状态，如果代码处理不当则会不定期出现死锁。
* 避免死锁的方法：
  *  避免一个线程同时获取多个锁。
  * 避免一个线程在锁内同时占用多个资源，尽量保证每个锁只占用一个资源。
  * 尝试使用定向锁，使用lock.tryLock(timeout)来替代使用内部锁机制。
  * 对于数据库锁，加锁和解锁必须在一个数据库连接里，否则会解锁失败。

#### 停止线程

* ==禁止使用Thread中的停止多线程方法stop()，销毁多线程方法destory()，挂起线程suspend()，恢复挂起resume()。这些方法可能导致线程的死锁。==
* 判断线程是否是停止的：
  * `public static boolean interrupted();`测试当前线程是否中断。
  * `public boolean this.isInterrupted();`测试this关键字所在类的对象是否已经中断。

#### 守护线程(Daemon线程)

* java中有两种线程，一种叫用户线程，另一种叫守护线程。
* 守护线程时一种特殊的线程，如果进程中没有用户线程，则守护线程自动销毁。典型的守护线程时垃圾回收线程。它存在的目的就是为用户线程的运行提供便利。
* main线程属于用户线程，调用setDaemon()方法的就是守护线程，该方法要放到start()方法执行前调用，否则会抛出`IllegalThreadStateException`异常。
