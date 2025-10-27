---
title: magisk教程
description: 这是一个副标题
slug: magisk
date: 2025-04-26
draft: true
image: 4.png
categories:
    - 教程
---
# **1 安卓设备root快速指南**
* 在开始前确定你的设备已经解锁[**bootloader（bl锁）**](https://miuiver.com/how-to-unlock-xiaomi-phone/)
* 因手机品牌，安卓系统版本不一，本指南不一定100%有效，在遇到问题时请自行搜索
* 请注意！root可能会将你的手机变成[**黑砖**](https://jingyan.baidu.com/article/0a52e3f402d400bf62ed7234.html),**售后不保修**,**无法使用各种app**,**游戏封号**等问题,**你需要自行承担风险**！


### **1.1 使用第三方rec卡刷（推荐方法）**
1. 下载你机型对应的[第三方recovery（第三方rec）](https://miuiver.com/third-party-recovery/),比如：[TWRP](https://twrp.me/Devices/),[橙狐rec](https://orangefox.download/zh-CN)等
2. 把magisk.apk复制到手机，你能找到的目录
3. 将下载的recovery刷入手机
    1. 下载[fastboot工具（platform-tools）](https://developer.android.google.cn/tools/releases/platform-tools?hl=zh-cn)
    2. 将手机重启至[fastboot模式](https://baike.baidu.com/item/fastboot/3228436 "fastboot模式")（关机后按住音量下和电源键）
    3. 使用USB线将电脑连接至手机
    4. 打开cmd，刷入recovery
    * 在这里分为两种情况
      1. 有recovery分区（[A-Only机型](https://source.android.com/docs/core/ota/nonab?hl=zh-cn "A-Only机型")）
        * 直接将下载的recovery刷入手机
	    * 重启至recovery
            ```
            fastboot flash recovery 镜像名称
            fastboot reboot recovery
            ```       
      2. 无recovery分区（[AB/VAB机型](https://source.android.com/docs/core/ota/ab?hl=zh-cn "AB/VAB机型")）
	    * 首先临时启动recovery镜像
            ```
            fastboot boot 镜像名称
            ```
        * 手机进入recovery后选择高级，点击一键安装TWRP
4. 在recovery点击<安装>,点击magisk.apk,滑动滑条
5. 安装完毕