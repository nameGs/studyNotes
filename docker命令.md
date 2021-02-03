# Docker笔记

## 1.Docker

* Docker有两个版本 : Docker CE (Docker社区版，免费)，Docker EE(企业版，收费)。命令大体相同。

* docker底层使用go语言。
* Docker包括三个概念 : 
  1. 镜像(Image) : root文件系统，类似于操作系统。
  2. 容器(Container) : 镜像运行产生容器。容器可以被创建，启动，删除，停止等。==同一个镜像可以产生多个容器==。
  3. 仓库(Repository) : 仓库是看作是代码控制中心，用来保存镜像。

## 2.Docker的安装和配置

### 1.安装

```shell
#1.安装仓库
[root@GS gs]# yum install -y epel-release
#2.安装docker
[root@GS gs]#yum install -y docker-io
```

## 3.Docker命令

### Docker镜像操作（Docker运行产生镜像）（类似安装程序）

* 查看docker仓库文件

  ```shell
  docker search 查看的文件(如docker search mysql)
  ```

* 下载文件，默认标签是最新的(latest)

  ```shell
  docker pull 文件名:标签名(如：docker pull mysql:5.5)
  ```

* 查看镜像

  ```shell
  docker images
  ```

* 删除镜像

  ```shell
  docker rmi 镜像ID/名称(镜像ID通过docker images查看):tag
  ```

### Docker容器操作（Docker镜像运行产生容器）（类似exe文件）

* 可以把容器看作一个简易版的linux环境。

* Docker运行镜像命令

  ```shell
  docker run --name 自定义名字 -d(后台运行) 镜像名字:tag
  ```

* Docker查看运行中的容器，加上-a即可查看全部

  ```shell
  docker ps 
  ```

* 停止运行中的容器

  ```shell
  docker stop 容器ID（通过docker ps命令查看）
  ```
  
* Docker运行CentOS

  ```shell
  docker run -it CentOS IMAGEID
  ```

  * 可以与宿主交互。

* 退出容器

  ```shell
  exit 或者 
  ```


### Docker帮助命令

* 查看Docker信息

  ```shell
  docker info
  ```

* 查看Docker帮助信息

  ```shell
  docker (指令) --help
  ```

### Docker遇到问题

#### 服务无法起来：`Failed to start docker.service: Unit not found`

* 原因：曾经有过docker相关服务，并且没有卸载干净。

* 方法：

  ```
  docker update
  yum install docker
  yum start docker.service
  ```

  