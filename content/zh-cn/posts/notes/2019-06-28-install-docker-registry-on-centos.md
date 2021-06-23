---
layout: post
title:  "install docker registry on centos"
date:   2019-06-28 13:06:41 +0800
categories: linux
---

## centos搭建docker私有仓库


#### 安装docker

略过
```shell
# 重启docker
systemctl daemon-reload
systemctl restart docker
```

#### 拉取仓库镜像
```shell
docker pull registry 
```
#### 运行仓库
```shell
docker run -d -v /registry:/var/lib/registry -p 5000:5000 --restart=always --privileged=true --name registry registry:latest 
```

#### 示例:从官方仓库拉取hello-world
```shell
docker pull hello-world
```

#### 给hello-world镜像打个tag，表示新的版本
```shell
docker tag hello-world 127.0.0.1:5000/hello-world:latest 
```

#### 推送：将新的hello-world镜像上传到私有仓库
```shell
docker push 127.0.0.1:5000/hello-world:latest
```

#### 在私有仓库查看上传的镜像
```shell
ls /registry/docker/registry/v2/repositories
```

通过客户端查看镜像
```shell
curl http://127.0.0.1:5000/v2/_catalog
```

输出:
```json
{"repositories":["hello-world"]}
```