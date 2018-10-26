# Docker-TensorFlow-with-Web_GPU

这是一个包含python/tensorflow/flask/opencv等库的基于NVIDIA运行环境的docker镜像。



## 开始

- 直接拉取镜像

> 国内可能会出现速度很慢的情况，可以使用阿里云的docker镜像源加速，参考[使用阿里云Docker镜像仓库](https://yq.aliyun.com/ziliao/283741)

```bash
$ sudo docker pull kevinleeex/tensorflow-with-web_gpu
```



- 从Dockerfile构建

```bash
$ git clone https://github.com/kevinleeex/Docker-Tensorflow-with-Web_GPU.git
$ cd ./Docker-Tensorflow-with-Web_GPU
$ sudo docker build -t kevinleeex/tensorflow-with-web_gpu:latest .
```



## Docker 常用操作

- 从当前目录的Dockerfile创建镜像

  ```bash
  $ sudo docker build -t kevinleeex/tensorflow-with-web_gpu:latest .
  ```

  - 参数

    - -t 表示Tag

- 使用容器运行镜像

  ```bash
  $ sudo docker run --runtime=nvidia  -v /abs_path/to/host:/abs_path/to/container -it -p 5000:5000 kevinleeex/tensorflow-with-web_gpu /bin/bash
  ```

  - 参数
    - -d 后台运行容器并返回容器ID

    - -i 以交互模式运行容器，通常与 -t 同时使用 

    - -t 为容器重新分配一个伪输入终端，通常与 -i 同时使用

    - -p 表示端口映射

    - --runtime 表示运行环境(eg: nvidia)

    - -d 和--rm 同时使用 表示容器在退出的时候移除或者后台退出时移除

    - -v 挂载目录/abs_path/to/host:/abs_path/to/container



- 列出容器

  ```bash
  $ sudo docker ps -a
  ```

  - 参数

    - -a 表示全部



- 删除容器

  ```bash
  $ sudo docker rm <container_id>
  ```

- 启动容器

  ```bash
  $ sudo docker start -a <container_id>
  ```

  - 参数

    - -a 表示attach连接

- 在镜像和主机之间复制文件(夹)

   ```bash
   $ sudo docker cp src/. <container_id>:/dst
   $ sudo docker cp <container_id>:/src/. dst
   ```

- 更新容器镜像

  > 在容器里更新后，使用```exit``` 退出容器

  ```bash
  $ sudo docker commit -m="[*]updated" -a="Kevin T. Lee" <containner_id> kevinleeex/tensorflow-with-web_gpu:v2
  ```

  - 参数
    - -m 表示提交的消息
    - -a 表示作者信息




- 列出镜像

   ```bash
   $ sudo docker images
   ```

- 删除镜像

   > 先删除容器再删除镜像

   ```bash
   $ sudo docker rmi <image_id>
   ```



## 声明

© 2018 | Kevin T. Lee all rights reserved. 本项目采用[MIT](./LICENSE)协议。