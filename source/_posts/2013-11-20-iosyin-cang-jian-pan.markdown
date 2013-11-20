---
layout: post
title: "ios隐藏键盘"
date: 2013-11-20 20:51
comments: true
categories: oc片段
keywords: oc
description: 
---
点击UIViewController的任意地方，就可以dismiss keyboard,最简单的办法就是在VC中override以下方法：

```objc
-(void)touchesBegan:(NSSet *)touches withEvent:(UIEvent *)event{
	[self.view endEditing:YES];
}
```