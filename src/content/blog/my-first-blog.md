---
title: "Day.js日期时间的常计算"
excerpt: "Ornare cum cursus laoreet sagittis nunc fusce posuere per euismod dis vehicula a, semper fames lacus maecenas dictumst pulvinar neque enim non potenti. Torquent hac sociosqu eleifend potenti."
publishDate: "2024-07-05T11:39:36.050Z"
image: "../../assets/blog/blog3.avif"
category: "lifestyle"
author: "mario-sanchez"
tags: [design, architecture, interior]
---

# Day.js日期时间的常计算

## 1、介绍

**Day.js**：Day.js是一个极简的JavaScript库，可以为现代浏览器解析、验证、操作和显示日期和时间。主要为操作时间日期的库。

## 2、场景使用

1. 计算周几、当月第一天
2. 计算xx天前/后的日期
3. 将时间戳转换为日期(YYYY-MM-DD)
4. 计算月天数
5. 获取两个日期的时间差

## 3、使用例子

1. 获取当天、月、年

```TypeScript
dayjs().format(YYYY-MM-DD)   // 2024-05-23
dayjs().format(YYYY-MM)      // 2024-05
dayjs().format(YYYY)         // 2024
```

2. 获取当月第一天

```TypeScript
dayjs().startOf('month').format('YYYY-MM-DD') // 2024-05-01
```

3. 获取本周第一天

```TypeScript
dayjs().day()                                                     // 4（获取当天星期几）
dayjs().subtract(dayjs().day() - 1, "day").format("YYYY-MM-DD");  // 2024-05-20（周一）
dayjs().startOf('week').format('YYYY-MM-DD')                      // 2024-05-19（周日）
```

4. 获取当前日期时间

```TypeScript
dayjs().endOf().format('YYYY-MM-DD HH:mm:ss')  // 2024-05-23 17:20:12
```

5. n天前/后的日期

```TypeScript
dayjs().add(n, 'day').format('YYYY-MM-DD')  // 做加法
dayjs().subtract(n, 'day').format('YYYY-MM-DD')  // 做减法
```

6. 获取本月天数

```TypeScript
dayjs().daysInMonth()  // 31
dayjs('2024-06').daysInMonth() // 30
```

7. 计算两个日期之间相差的时间

```TypeScript
// 相差: 年 参数--year
dayjs('2022-02-01').diff('2012-01-01','year') // 10（年）
dayjs('2022-02-01').diff('2012-01-01','month') // 121（月）
dayjs('2022-02-01').diff('2012-01-01','day') // 3684（天）
dayjs('2022-02-01').diff('2012-01-01','hour') // 88416（时）
dayjs('2022-02-01').diff('2012-01-01','minute') // 5304960（分）
dayjs('2022-02-01').diff('2012-01-01','second') // 318297600（秒）
```