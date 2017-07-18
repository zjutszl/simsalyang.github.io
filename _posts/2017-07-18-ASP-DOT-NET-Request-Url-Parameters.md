---
layout: post
title: ASP.NET获取当前url各参数
date: 2017-07-18
categories: blog
tags: [ASP.NET,C#]
description: asp.net获取当前url中的各种参数，文章内容转载自http://congcong.blog.51cto.com/3840971/856701

---

假设当前页完整地址是：[http://www.test.com/aaa/bbb.aspx?id=5&name=kelli](http://www.test.com/aaa/bbb.aspx?id=5&name=kelli)

- "http://"是协议名
- "[www.test.com](http://www.test.com/)"是域名
- "aaa"是虚拟目录名
- "bbb.aspx"是页面名（文件名）
- "id=5&name=kelli"是参数

【1】获取 完整url （协议名+域名+虚拟目录名+文件名+参数）

string url=Request.Url.ToString();

url= [http://www.test.com/aaa/bbb.aspx?id=5&name=kelli](http://www.test.com/aaa/bbb.aspx?id=5&name=kelli)

【2】获取 虚拟目录名+页面名+参数：

string url=Request.RawUrl;

(或 string url=Request.Url.PathAndQuery;)

url= /aaa/bbb.aspx?id=5&name=kelli

【3】获取 虚拟目录名+页面名：

string url=HttpContext.Current.Request.Url.AbsolutePath;

(或 string url= HttpContext.Current.Request.Path;)

url= aaa/bbb.aspx

【4】获取 域名：

string url=HttpContext.Current.Request.Url.Host;

url= [www.test.com](http://www.test.com/)

【5】获取 参数：

string url= HttpContext.Current.Request.Url.Query;

url= ?id=5&name=kelli

 （的确有效，感谢原创作者。）

Request.QueryString["id"]和Request.QueryString["name"]访问各参数

Request.UrlReferrer可以获取客户端上次请求的url的有关信息， 这样我们就可以通过这个属性返回到“上一页”。

同样地，Request.UrlReferrer.Query可以获取客户端上次请求的url的有关参数部分