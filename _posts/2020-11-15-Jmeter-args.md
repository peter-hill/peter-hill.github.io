---
layout: post
title: Jmeter实战
categories: [Jmeter]
description: Jmeter实战
keywords: Jmeter
---

# Jmeter实战三四五章学习记录

![image-20201018144724517](https://i.loli.net/2020/10/18/sPNQSdEiWyzFO42.png)

![ApPEQ6x49tXYlTG](https://i.loli.net/2020/11/16/ApPEQ6x49tXYlTG.png)

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
>
> jmeter -g [result] -o [Path to web report folder]

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

## 访问地址参数化

> 为了应对写脚本时的地址与执行时的服务器地址参数不一致，将地址参数化后，如果地址有变动时直接改参数就好了

![截屏2020-11-10 上午11.03.39](https://i.loli.net/2020/11/10/SjRs64E8QXyB5Zt.png)

## HTTP请求默认值

> 一个项目的地址是不变的，每个请求都写一遍，会加大工作量，HTTP请求默认值就可以将重复的内容分离出来

![ArlRTohb6FOzJiw](https://i.loli.net/2020/11/11/ArlRTohb6FOzJiw.png)

## 断言

> 通过匹配响应字段来验证服务器是否成功响应

![zEMnm74ivgkCxoQ](https://i.loli.net/2020/11/11/zEMnm74ivgkCxoQ.png)

- 图中的忽略状态勾选了表示如果第一个响应失败，第二次成功还是可以判定为该次事物成功的

- **模式匹配规则**

  ![XhPeU9CTcMpNJj4](https://i.loli.net/2020/11/11/XhPeU9CTcMpNJj4.png)

  ## Jmeter事务

  > 性能测试关注的是TPS，事务控制器就可以将多个请求统计成一个事务

  ### 事务控制器

  ![c3I82owPEROfQy4](https://i.loli.net/2020/11/15/c3I82owPEROfQy4.png)

  - Generate parent sample:勾选后事务控制器作为子采样器的父采样器，否则作为额外采样器加在子采样器后面
  - include duration of timer and per-most processors in generated sample:是否包含定时器、预处理和后期处理延迟的时间

  ## Jmeter集合点

  > 用于性能测试时模拟大量用户在同一时间发送请求，Jmeter的集合点是通过定时器完成的

  ### 同步定时器

  <img src="https://i.loli.net/2020/11/15/Yg5LmG3Zjr4wSCy.png" alt="image-20201115180951246"/>

  * 参数1为要同步的数量

  - 参数2为超时时间，若在这个时间内没有加载到对应的并发数，就发送请求
  - 超时时间设置：超时时间 > 请求集合数量 * 1000 / (线程数 / 线程加载时间)

## Jmeter元件运行顺序

> 类似于二叉树的中序遍历

### Jmeter执行顺序逻辑

1. 配置元件
2. 前置处理器
3. 定时器
4. 取样器
5. 后置处理器
6. 断言
7. 监听器

![1739Y6gco852ENX](https://i.loli.net/2020/11/15/1739Y6gco852ENX.png)

### 上图中的执行顺序如下

1. 线程组
2. 简单控制器
3. HTTP cookie管理器
4. 执行前置处理器用户参数
5. 执行定时器
6. 执行取样器1
7. 执行后置处理器
8. 执行断言
9. HTTP cookie管理器
10. 执行前置处理器用户参数
11. 执行定时器
12. 执行取样器2
13. 执行后置处理器
14. 执行断言
15. 执行取样器3
16. 执行查看结果树

## 场景设计

> 用于模拟用户真实操作的工作单元，Jmeter主要通过线程组来完成

## 场景设置

> 通过线程组创建线程池

![EB6YPkTOel9cJzw](https://i.loli.net/2020/11/16/EB6YPkTOel9cJzw.png)





