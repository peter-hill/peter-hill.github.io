---
layout: post
title: 功能测试小结
categories: [functional test]
description: 功能测试总结
keywords: functional test
topmost: false
---

# 功能测试小结

大概算算功能测试做了大概也有一年之久了，今天来小结一下吧

功能测试，从字面意思理解就是测试系统的功能是否能正常使用；放在工作中来理解就是验证当前做出来的功能是否与功能设计文档一致。

在日常工作中我们一般都是通过我们测试人员设计的测试用例来评估测试量，测试进度。

流程重要性的啥就不说了。

说一说平时的测试思路吧。

1. 首先，考虑功能的主流程，比如单据新增
2. 其次，考虑功能的取值，值集，下拉列表啥的
3. 然后，考虑非主要字段的保存前后比对，数据排序啥的
4. 最后，考虑功能前后的业务线的关联

我觉得业务线和状态流转应该单独依据业务线来进行测试

突然来感觉吃了个饭没感觉了 先写到这吧