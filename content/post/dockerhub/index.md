---
title: 如何使用DockerHub镜像加速器
description: 本文主要演示如何配置dockerhub镜像加速，以解决镜像拉取超时等问题
slug: docker
date: 2025-05-30
lastmod: 2025-10-28
image: page.png
categories:
    - 教程
---
## 选择DockerHub镜像加速地址

本站提供的镜像加速器地址

```
https://docker.chabing.top
```

> ​**提示**​：本站提供的镜像加速器是免费服务，稳定性远不如商业服务。对于生产环境，建议使用阿里云或腾讯云等提供的专属加速地址或自行搭建。
> 
> **免责声明**：用户在使用本站提供的镜像加速器时，因遵守法律法规，不得用于任何非法目的，否则后果自负。

其他镜像加速地址

| DockerHub镜像仓库|镜像加速器地址|
|---| --- |
|[毫秒镜像](https://1ms.run)|https://docker.1ms.run|
|[DaoCloud 镜像站](https://github.com/DaoCloud/public-image-mirror)|https://docker.m.daocloud.io|
|[1panel](https://1panel.cn/docs/user_manual/containers/setting/#1)|https://docker.1panel.live|
|[阿里云](https://cr.console.aliyun.com/)（需登录，系统分配）|https://<your_code>.mirror.aliyuncs.com|

## 使用DockerHub镜像加速地址

选好你的镜像加速地址后有两种使用方式：

### 长期使用（修改配置文件）

#### Linux配置

``` bash
sudo mkdir -p /etc/docker
sudo tee /etc/docker/daemon.json <<EOF
{
  "registry-mirrors": [
    "https://docker.chabing.top"
  ]
}
EOF
sudo systemctl daemon-reload
sudo systemctl restart docker
```

#### MAC配置

1. 打开 Docker Desktop
2. 点击顶部菜单栏 Docker 图标 → Preferences
3. 选择 Docker Engine 标签
4. 在配置文件中添加：

``` json
{
  "registry-mirrors": ["https://docker.chabing.top"]
}
```

#### Windows配置

1. 右键点击系统托盘中的 Docker 图标
2. 选择 Change settings
3. 导航到 Docker Engine 选项卡
4. 在 JSON 配置中倒数第二行添加：
   ``` json
   "registry-mirrors": ["https://docker.chabing.top"]
   ```

> 以上配置中的https://docker.chabing.top可以修改为任意镜像加速器地址
>
> PS：建议配置多个镜像加速器地址，以防止单个服务出现故障

### 临时使用（单次拉取镜像）

直接在镜像名前添加 `docker.chabing.top/`

示例：

``` bash
docker pull linuxserver/firefox                    #加速前拉取镜像
docker pull docker.chabing.top/linuxserver/firefox #加速后拉取镜像
```