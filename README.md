# Dubbo-Mesh是什么？
Dubbo的RPC通信和服务治理能力一直限定在Java语言生态，因此提供多语言支持是建设Dubbo生态的一个重要方向。

[中间件性能优化挑战详细](https://tianchi.aliyun.com/markets/tianchi/aliware2018contest)


# Dubbo-Mesh运行步骤
### 启动基础镜像环境：
* 方法1、使用docker-compose来编排容器集群环境
    * 根据官方文档安装docker.[mac为例](https://docs.docker.com/docker-for-mac/)
    * 安装docker完毕，使用docker --version检查
    * 安装docker-composo(pip install docker-compose)
    * 编写docker-compose.yml编排文件
    * 运行编排文件：docker-compose up
### docker-compose运行图：
![](https://raw.githubusercontent.com/tantexian/dubbo-mesh/dev/static/imgs/docker-compose-run-1.png)
![](https://raw.githubusercontent.com/tantexian/dubbo-mesh/dev/static/imgs/docker-compose-run-2.png)
![](https://raw.githubusercontent.com/tantexian/dubbo-mesh/dev/static/imgs/docker-compose-run-3.png)


* 方法2、下载安装docker到开发机器(建议使用方法1)
    * 根据官方文档安装docker.[mac为例](https://docs.docker.com/docker-for-mac/)
    * 安装docker完毕，使用docker --version检查
    * 使用docker创建本项目Dockerfile镜像。进入到dubbo-mesh目录，执行：docker build -t my-dubbo-mesh .
    * 创建完毕my-dubbo-mesh镜像，使用docker images查询镜像是否创建成功。
    * 
    ```
    docker run -it --name=etcd --hostname=etcd registry.cn-hangzhou.aliyuncs.com/aliware2018/alpine-etcd /bin/bash
    ```
    * 启动其他容器(其中下述命令中的172.17.0.2，为etcd容器的ip地址[docker inspect etcd 查看容器ip地址])
        ```
        docker run -it --name my-dubbo-mesh --hostname=my-dubbo-mesh --add-host=etcd:172.17.0.2 my-dubbo-mesh consumer
        docker run -it --name my-dubbo-mesh --hostname=my-dubbo-mesh --add-host=etcd:172.17.0.2 my-dubbo-mesh provider-small
        docker run -it --name my-dubbo-mesh --hostname=my-dubbo-mesh --add-host=etcd:172.17.0.2 my-dubbo-mesh provider-medium
        docker run -it --name my-dubbo-mesh --hostname=my-dubbo-mesh --add-host=etcd:172.17.0.2 my-dubbo-mesh provider-large
        ```
    PS：启动my-dubbo-mesh镜像出错，请使用docker run -it --entrypoint="" my-dubbo-mesh /bin/bash，进入检查启动脚本

### docker运行图：
![](https://raw.githubusercontent.com/tantexian/dubbo-mesh/dev/static/imgs/docker-run.png)


# docker附加命令
* 删除所有容器：
```
docker rm `docker ps -qa`
```
* 删除所有镜像:
```
docker rmi `docker images -q`
```
