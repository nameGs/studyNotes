# Vue

## 下载Nodejs

官网：http://nodejs.cn/

### CentOS 7



### Windows10

![image-20210116220024536](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210116220024536.png)

1. 选择64位.mis安装包，点击下载。

2. 根据提示信息进行安装

3. 创建node_global和node_cache文件夹，

   用户变量设置：将用户变量中 PATH 的值改成： ~~本地路径~~\node_global，没有PATH，可以直接添加。

   系统变量设置：添加变量 NODE_PATH 值为：~~下载node路径~~\node_modules

4. 进入CMD需改配置：

   ```shell
   #node_global用于保存下载的文件
   npm config set prefix "本地路径\node_global"
   #node_cache用于保存node缓存
   npm config set cache "本地路径\node_cache"
   ```

5. 验证下载

   ```shell
   node -v 
   npm -v
   ```

6. 加速下载

   原npm下载速度过慢，可以通过设置镜像仓库和使用`cnpm`来达到提速的效果

   1. 设置淘宝镜像

      ```shell
      #设置淘宝镜像
      npm config set registry https://registry.npm.taobao.org
      ```

      测试

      ```shell
      npm config get registry
      ```

      成功信息

      ![image-20210116221337916](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210116221337916.png)

   2. 使用`cnpm`

      ```shell
      npm install -g cnpm --registry=https://registry.npm.taobao.org
      ```

      然后便可以使用`cnpm`代替`npm`

## 下载Vue-CLI

### CentOS

### Windows10

1. 打开CMD，输入

   ```shell
   #-g表示下载到全局目录，即node_global
   #下载vue-cli
   npm install vue-cli -g
   #下载vue-router
   npm install vue-router -g
   ```

2. 完成后输入`vue -V`验证下载



### Vue打包

打包执行命令`npm run build`，然后在项目目录下会生成一个dist文件，文件内是编译后的html项目。

#### 问题1：打包后的项目读取不到静态资源

由于路径配置问题，导致打包后文件默认读取静态资源的路径和实际上不符，因此需要配置打包后读取的路径

```js
module.exports = {
    //配置打包读取静态文件路径
    publicPath: process.env.NODE_ENV === 'production'? './': '/',
    devServer: {
        disableHostCheck: false,
        host: "localhost",
        port: 8008,
        https: false,
        hotOnly: false,
        proxy: null
    },
};
```

PS：由于Vue-CLI3之后移除了conf文件，因此需要在和src同级目录下创建`vue.conf.js`文件，将配置写在该文件中

#### 问题2：打包后的项目想存放在指定的路径下

如果使用nginx做代理，则需要把编译后的文件放在nginx下的html文件中

```js

```

