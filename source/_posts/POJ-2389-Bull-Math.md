﻿title: POJ 2389 Bull Math
date: 2014-08-06 15:03:00
tags: [ACM, POJ, Java, 高精度计算]
categories: Exercise
toc: true
---
# 题目
源地址：http://poj.org/problem?id=2389

# 理解
没什么好说的，java大数模板水之。

<!-- more -->

# 代码
```
import java.math.BigDecimal;
import java.util.Scanner;
public class Main{
	public static void main(String[] args){
		Scanner in=new Scanner (System.in);
		while(in.hasNext()){
			BigDecimal a=in.nextBigDecimal();
			BigDecimal b=in.nextBigDecimal();
			System.out.println(a.multiply(b));
		}
	}
}
```
	
# 更新日志
- 2014年08月06日 已AC。