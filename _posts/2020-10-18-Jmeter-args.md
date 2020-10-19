---
layout: post
title: Jmeter传参
categories: [Jmeter]
description: Jmeter传参
keywords: Jmeter
---

# Jmeter学习

![image-20201018144724517](https://i.loli.net/2020/10/18/sPNQSdEiWyzFO42.png)

## Jmeter参数化

### 接口间参数传递

1. 正则表达式提取器

   ![Pw7dWemV6DXULR3](https://i.loli.net/2020/10/18/Pw7dWemV6DXULR3.png)

   ![wNnEzm5lrdYktIZ](https://i.loli.net/2020/10/18/wNnEzm5lrdYktIZ.png)
 
2. json 提取器

   ![IPYaFGH9kot7Nx1](https://i.loli.net/2020/10/18/IPYaFGH9kot7Nx1.png)

   ![c3qSPVZMIiFWe5h](https://i.loli.net/2020/10/18/c3qSPVZMIiFWe5h.png)

### 跨线程组传参

> 通过后置处理器 BeanShell PostProcessor 或函数助手_setPerproty 将参数设置成全局参数

1. ![krEjzAhClcPb4Jm](https://i.loli.net/2020/10/18/krEjzAhClcPb4Jm.png)
2. ![GAaf6mE3PbOinwx](https://i.loli.net/2020/10/18/GAaf6mE3PbOinwx.png)
   * 将生成的函数再粘贴到BeanShell取样器

## Jmeter报告生成

![AFqBvcfdYarHuw2](https://i.loli.net/2020/10/18/AFqBvcfdYarHuw2.png)

> jmeter -n -t [jmx file] -l [results file] -e -o [Path to web report folder]
>
> jmx file脚本文件的绝对路径 result file输出文件，以.jtl结尾 最后的是测试报告的绝对路径

* -n是指非GUI模式执行Jmeter
* -t是指脚本文件的路径
* -l生成结果的保存文件
* -e测试结束后生成测试报告
* -o测试报告的路径

![sytQLrH49UxKpzm](https://i.loli.net/2020/10/18/sytQLrH49UxKpzm.png)

## CSV Data Set Config

![Seix5cTCYLkjPhl](https://i.loli.net/2020/10/18/Seix5cTCYLkjPhl.png)

## 接口测试测试用例

![caRjTMzBkvuowYA](https://i.loli.net/2020/10/18/caRjTMzBkvuowYA.png)

