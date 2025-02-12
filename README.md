# XtERVGDemo
本项目为飞流边缘AI视频网关盒子所部署的相关源程序代码，它适用于应急、安防、无人机巡检等场景下的视频AI识别与实时传输的需求。具备超强的抗弱网特性，完美解决了此类视频远程传输中的卡顿、延迟、花屏等问题,实现了AI标注视频流的超低延迟远程实时播放。为实现智能体的协同提供了一个强有力的通信引擎。本方案是基于RDK X3架构实现的。各位开发者可以基于此引擎开发适用于自己应用场景的实时AI视频应用。
# 简介
## 功能介绍
边缘智能网关盒子主要解决各类（安防、应急、无人机等）视频远程传输时遇到的卡顿、延迟、花屏，以及缺乏智能等问题。该网关集成了高实时高可靠的自研通讯中间件，实现了 70+%丢包率下的可靠视频传输效果，远程传输时延迟仅为 0.2 秒，远超传统实时视频传输方式（如 RTMP、RTSP、WebRTC 等）。并且结合 RDK X3 卓越的 AI 分析能力实现了远程超低延迟的实时 AI 标注视频流的流畅展示。
## 应用架构
 ![1](./image/1.png)
 RDK X3 盒子的主要作用是从局域网中提取视频流，并利用其强大的 AI 分析能力对视频流进行实时标注。随后，借助自主研发的高实时、高可靠通讯中间件，将标注信息及视频流传输至云端。
 ## 特色功能介绍
 **1.远程观看实时视频**
 
 边缘智能网关盒子具备高可靠、低延迟的特性，抗丢包能力可达到 70%以上，延迟仅为0.2 秒。
 
 **2.AI 标注结构化**
 
 AI 标注结构化使得远程观看可以实时调整标注内容，以及可以对标志信息进行二次挖掘。
 
# 支持平台
| 平台         | 操作系统                             | 
|--------------|--------------------------------------| 
| RDK X3       | Ubuntu 20、Ubuntu 22                |
# 准备工作
## 硬件准备工作
 1.RDK X3 已烧录好 Ubuntu 20.04/Ubuntu 22.04 系统镜像。
 
 2.摄像头为 H264 编码格式，且具备 RTMP/RTSP/FLV 任意一种取流方式。
 
 3.RDK X3 与摄像头在同一网段。

 4.RDK X3 可以访问公网（互联网）。
 
## 软件 准备工作
 1.前往[息通开发平台](https://open.zhilianxi.com/front/#/login)注册账号，创建应用获取 APP 鉴权信息；
 
 2.提交设备号。
# 试用体验
## 下载 SDK 及 DEMO。
**1.配置 DNS 服务。**

请参考 https://developer.d-robotics.cc/rdk_doc/System_configuration/network_blueteeth#dns%E6%9C%8D%E5%8A%A1，完成 DNS 相关配置。

**2.安装及运行。**
```bash
# 解压下载的安装包（下载的安装包名称为随机生成，此处以xt举例，请根据实际情况进行调整）
unzip xt.zip

# 进入项目目录
cd xt

# 修改安装文件的执行权限
chmod +x setup.sh

# 以root身份运行
sudo ./setup.sh

# 安装完成后，检查monitor进程是否存在。（若不存在，请一分钟后再次查看）
ps -ef | grep -v grep | grep bin/monitor

# monitor日志所在目录
cd /usr/local/xt/logs
```

## 配置通道信息。
1.登录[飞流可靠安防视频平台](https://monitor.zhilianxi.com/videoMonitorPlatform/index.html#/login)，账号密码同息通五洲开发者平台登录账号密码一致。

 ![三1](./image/三1.png)

2.进入系统后点击 顶部导航栏 中的"设备管理"。

 ![三2](./image/三2.png)
 
3.点击网关下的“通道管理”进入通道管理的页面。

![三3](./image/三3.png)

4.点击添加通道。

![三4](./image/三4.png)

**通道：为网关中继的一条视频流。**
    
5.根据提示信息填写相应内容并确认。

![三5](./image/三5.png)

在本对话框内填写本通道的接入视频流信息（支持 RTSP、RTMP、FLV 三种接入方式）。
注：本 DEMO 暂不支持接入国标平台。
## 检查通道视频及观看试用。
1.检查通道视频（在RDK X3盒子上运行）
```bash
# 检查xftp进程是否存在（若不存在，请一分钟后再次查看）
ps -ef | grep -v grep | grep bin/xftp

# xftp日志所在目录
cd /usr/local/xt/logs
```
2.查看通道视频
（1） 在飞流可靠安防视频平台，点击顶部导航栏中的“视频中心”。

 ![四2 (1)](./image/四1.png)
 
（2） 在“视频中心”的“实时视频”部分点击网关，选择先前添加的通道进行查看。

![四2](./image/四2.png)

（3） 系统目前支持“可靠模式”与“普通模式”两种观看模式。

![四3](./image/四3.png)

边缘AI视频标注仅能使用可靠模式进行体验，请下载插件。插件安装请参考飞流视频播放器插件使用说明。

（4） 观看效果。

![四4]([.image/四4.gif](https://github.com/steven-j-on-ai/XtERVGDemo/image)

**注：应用可用流量有限，请合理规划使用。**
![动图描述](.image/2.gif)
https://github.com/steven-j-on-ai/XtERVGDemo/image/四4.gif/路径/动图文件名.gif
