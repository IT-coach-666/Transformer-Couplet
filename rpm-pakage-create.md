### （1）安装 rpm 编译环境
```shell
yum install gcc rpm-build rpm-devel rpmlint make python bash coreutils diffutils  -y
```

安装完成 rpm-build 包后, 会自动生成在 ~/rpmbuild/ 目录, 目录下有以下文件夹(如果没有, 可手动创建):
```shell
mkdir ~/rpmbuild
cd ~/rpmbuild
mkdir BUILD RPMS SOURCES SPECS SRPMS
```

其中，各个目录的作用说明如下：
- SPECS 存放 spec 文件
- SOURCES   存放源码包和补丁等，rpmbuild会在这里寻找源码
- BUILD     工作车间，也是源码编译的路径，在这个目录下进行编译
- RPMS      存放编译好后的rpm包
- SRPMS     存放编译好后的srpm包

###（2）下载 httpd-2.4.27.tar.bz2
在 http://archive.apache.org/dist/httpd/ 中查找相应版本；
```shell
    wget http://183.207.33.43:9011/archive.apache.org/c3pr90ntc0td/dist/httpd/httpd-2.4.27.tar.bz2
```
在 http://archive.apache.org/dist/apr/ 中查找 apr 包的相应版本;
```shell
wget http://183.207.33.35:9011/archive.apache.org/c3pr90ntc0td/dist/apr/apr-1.6.2.tar.gz
wget http://183.207.33.35:9011/archive.apache.org/c3pr90ntc0td/dist/apr/apr-util-1.6.0.tar.gz
```


```shell
tar xf httpd-2.4.27.tar.bz2
tar xf apr-1.6.2.tar.gz
mv  apr-1.6.2  httpd-2.4.27/srclib/apr
tar xf apr-util-1.6.0.tar.gz
mv apr-util-1.6.0  httpd-2.4.27/srclib/apr-util
```

以下之所以解压并重新归档压缩, 是因为 httpd 依赖于 apr, 在 .spec 中指定这个过程比较麻烦, 所以我就直接这么做了
```shell
tar -jcvf  httpd-2.4.27.tar.bz2  httpd-2.4.27
mv httpd-2.4.27.tar.bz2 ~/rpmbuild/SOURCES
```
