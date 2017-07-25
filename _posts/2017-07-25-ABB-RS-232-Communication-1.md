---
layout: post
title: ABB机器人串口通讯1
date: 2017-07-25
categories: blog
tags: [ABB机器人,串口通讯]
description: 
---



因业务需要使机器人与计算机进行串口通讯，于是开始尝试实现该功能。经过尝试，将一点经验分享出来，供大家参考。

硬件需求：要实现机器人与计算机的串口通讯，在机器人控制器内必须安装 DSQC1003 通讯板。因为现在的计算机尤其是笔记本电脑，一般都没有串行接口，因此需要配备 USB 转 RS232 转接线，及 自制RS232 转换线（接线方法与一般接法相同，2 、3 脚位置对调，5 脚相连即可）

示教器配置：接好线之后，需要在示教器上进行配置，与 配置 DSQC652 I/O 板在控制面板的 I/O System主题中 DeviceNet Device 中添加不同，串口配置需在 Communication 主题中的 Serial Port 中添加，默认端口号为 COM1,设置好“波特率（Baudrate）”、“校验位（Parity）”、“数据位（Number of Bits）”、“停止位（Number of Stop Bits）”。

编写程序：自行根据需要编写接收、发送数据程序，具体写法，可参考论坛 @bianshaoyun 的帖子 http://bbs.gongkong.com/d/201701/703644_1.shtml，下载程序例子研究即可。我也在学习中。






