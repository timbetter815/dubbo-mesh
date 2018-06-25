# Dubbo-Mesh是什么？
Dubbo的RPC通信和服务治理能力一直限定在Java语言生态，因此提供多语言支持是建设Dubbo生态的一个重要方向。

[中间件性能优化挑战详细](https://tianchi.aliyun.com/markets/tianchi/aliware2018contest)


# Dubbo-Mesh运行步骤
### 启动基础镜像环境：
* 1、下载安装docker到开发机器
    * 根据官方文档安装docker.[mac为例](https://docs.docker.com/docker-for-mac/)
    * 安装docker完毕，使用docker --version检查
    * 使用docker创建本项目Dockerfile镜像。进入到dubbo-mesh目录，执行：docker build -t my-dubbo-mesh .
    * 创建完毕my-dubbo-mesh镜像，使用docker images查询镜像是否创建成功。
    * 启动my-dubbo-mesh镜像：docker run -it mydubbo /bin/bash
    PS：启动my-dubbo-mesh镜像出错，请使用docker run -it --entrypoint="" my-dubbo-mesh /bin/bash，进入检查启动脚本 
    
### docker运行图：
![](https://raw.githubusercontent.com/tantexian/dubbo-mesh/dev/static/imgs/docker-run.png)   
 
     
         