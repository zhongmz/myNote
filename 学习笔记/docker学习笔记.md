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

  

