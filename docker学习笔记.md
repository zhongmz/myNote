- 启动`docker `

- ```
   sudo systemctl start docker
  ```



- 













- 

  ```shell
  ~ systemctl start docker.service
  Job for docker.service failed. See 'systemctl status docker.service' and 'journalctl -xn' for details.
  ```

- ```dockerfile
  若配置了国内镜像，且镜像文件为/etc/docker/daemon.json 那么修改文件后缀为.conf
  ```

  



# 指令

## 查看所有容器container的状态

```shell
docker ps -a
```

## 运行容器

```shell
docker run  *******
```

```shell
docker run -itd --name homework-oracle -p 5000:1521/tcp images_name /bin/bash
```



## 进入容器

```shell
docker exec **************
```



## 删除容器

```
docker rm -f **************
```







# 一些错误

## 守护进程未打开

```shell
Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?
```

```shell
➜  ~ service docker start
Redirecting to /bin/systemctl start docker.service
```

- 打开docker





# datagrip + Docker + Oracle

## 安装docker 

- 菜鸟教程中有安装教程【找国内镜像即可】
- 不过值得一提的是，我用阿里云服务器然后用阿里的镜像很慢，但是用腾讯的镜像却快不少

## Oracle



### 获取镜像

- ```shell
  docker pull registry.cn-hangzhou.aliyuncs.com/helowin/oracle_11g
  ```

- 这里涉及到如何去获取一个镜像

- ```shell
  docker pull image_name
  ```

### 启动镜像【容器】

- ```shell'
  docker run [一些参数 比如 -i  -t  -d] image_name /bin/bash
  ```

- 在这里我们

- ```shell
  docker run -i -t -d -- name myoracle -p 5000:1521 registry.cn-hangzhou.aliyuncs.com/helowin/oracle_11g
  ```

- 但是注意启动容器并不代表进入容器【应该很好理解吧】

### 进入容器

- 就是能够在容器中使用其工具

- 在这里如何进入Oracle 容器呢

- ```shell
  docker exe -it myoracle bash
  ```

- 其中 exec 和**attach**是有区别的：attach退出容器的时候 容器会exit 但是exec退出容器的时候，容器会一直`up`

### 进入之后的操作

1. ```shell
   su root
   #开始输入密码，初始密码为helowin
   ```

2. 进入root状态的目的是

   - 修改配置文件和

   ```shell
   vi /etc/profile
   # 在文件末尾添加
   export ORACLE_HOME=/home/oracle/app/oracle/product/11.2.0/dbhome_2
   export ORACLE_SID=helowin
   export PATH=$ORACLE_HOME/bin:$PATH
   ```

   - 创建软连接

```shell
ln -s $ORACLE_HOME/bin/sqlplus /usr/bin
```

- 切换会oracle用户

- ```shell
  su oracle
  ```

- ```shell
  [oracle@66b9cbb16bc3 ~]$ sqlplus /nolog
  
  SQL*Plus: Release 11.2.0.1.0 Production on Mon Sep 28 15:42:56 2020
  
  Copyright (c) 1982, 2009, Oracle.  All rights reserved.
  
  SQL>
  ```

  - 说明进入了SQL中

- 连接

- ```shell
  conn / as sysdba
  ```

- ```shell
  alter user system identified by system;
  create user <username> identified by <password> ;
  grant connect,resource,dba to <username> ;
  ```

- 其中`<username>`和`password`可以自己取

## DataGrip

![image-20200928155424665](https://www.endacsd.cn/images/image-20200928155424665.png)

- 填写
  - `Host` 是你服务器的`ip`地址
  - `Port`是你映射后的`端口`，就是`5000`
  - `SID`是`helowin`
  - `username`是`myoracle`是我取的名字<username>

- Test Connection
  - 测试是否能连接

### 





























