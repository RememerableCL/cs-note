---
tags:
  - "#程序语言/Golang/库/标准库/time"
  - "#时间处理"
  - "#待处理"
---



# 背景相关知识

1. [[时间格式-标准化]]

# time包概要

## 包-官方
[time package - time - Go Packages](https://pkg.go.dev/time#pkg-overview)
## 包-基本类型

Go 语言中的 time 包提供了处理时间和日期的函数和类型。它包括了以下几个基本组成部分：

1. 时间类型 Time：
	1. time.Time 是 Go 语言中表示时间的类型，它包含了年、月、日、时、分、秒、纳秒等时间信息，并支持各种时间操作和格式化。
	    
2. 时间间隔类型 Duration：
	1. time.Duration 是 Go 语言中表示时间间隔的类型，它表示两个时间点之间的时间差，可以用来进行时间计算和比较。
	    
3. 时区类型 Location：
	1. time.Location 是 Go 语言中表示时区的类型，它包含了时区的名称、偏移量等信息，并支持时区转换和比较。
	    
4. 时间格式化函数 Format：
	1. time.Format 函数可以将时间类型 Time 转换为指定格式的字符串，或者将字符串解析为时间类型 Time。
	    
	    
6. 定时器类型 Timer 和 Ticker：
	1. time 包还包括了定时器类型 Timer 和 Ticker，可以用来实现定时任务和周期性任务。
	    

以上是 time 包的基本组成部分，通过这些类型和函数，我们可以方便地进行时间和日期的处理和计算。需要注意的是，在使用 time 包时，应该注意时区和时间格式的问题，以避免出现意外的错误


## 包-基本操作

提供常见的时间相关操作函数：
*  Add、Sub、Round、Truncate 等，可以对时间类型 Time 进行加减、舍入、截断等操作。
*  时间相等比较
* 时间格式化、解析时间格式
* 定时器

## 包-基本使用

[13.Go语言标准库之time包 - Go语言中文网 - Golang中文社区 (studygolang.com)](https://studygolang.com/articles/26473)
[Time · Go语言中文文档 (topgoer.com)](https://www.topgoer.com/%E5%B8%B8%E7%94%A8%E6%A0%87%E5%87%86%E5%BA%93/time.html)

[Go语言time包：时间和日期 (biancheng.net)](https://c.biancheng.net/view/5392.html)

[Golang 时间操作大全 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/362936088)



