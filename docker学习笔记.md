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



## 进入容器

```shell
docker exec **************
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