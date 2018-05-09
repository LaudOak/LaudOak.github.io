---
layout: post
title: Excel VLOOKUP Function
category: 其他
---

## 举个栗子🌰

VLOOKUP是Excel里的一个查找和引用函数；作用是当你给定一个想要在表格里查找的值，函数查找这个值所在的行，再根据你给定要取这行哪列的数据给出这个数据。

例如下面这个表格：

| 姓名 | 性别 | 年龄 |
| --- | --- | --- |
| 张三 | 男 | 18 |
| 李四 | 男 | 19 |
| 王五 | 女 | 20 |

如果你已经知道李四这个姓名，想知道李四的年龄，可以通过VLOOKUP这个函数；已知的查找条件（查找的值）是`李四`，你要查找的列是年龄那一列（第3列），使用函数查找时函数先找到李四在第2行，再取这行数据的第3列得到年龄是19；

## VLOOKUP函数的定义

```
=VLOOKUP（lookup_value,table_array,col_index_num,range_lookup）
```
函数有4个入参：
1，lookup_value 要查找的值：相当于上面的`李四`；
2，table_array 要在其中查找值的区域：从哪里找，相当于上面的例子中的整个表；
3，col_index_num 区域中包含返回值的列号：相当于上面的年龄那列（第3列）；
4，range_lookup 精确匹配或近似匹配 – 指定为 0/FALSE 或 1/TRUE：一般使用精确匹配（FALSE），模糊匹配会导致数据不准确；


## 实际应用

SheetA：
![屏幕快照 2018-04-21 下午10.20.41.png](https://i.loli.net/2018/04/21/5adb48e1635b3.png)

SheetB：
![屏幕快照 2018-04-21 下午10.23.01.png](https://i.loli.net/2018/04/21/5adb497f6ef99.png)

A部门维护这员工信息，知道员工工号和姓名，对应SheetA；B部门知道员工工号和工资，对应SheetB；我们需要把员工工资从B表根据工号对应填写到A表里面，当数据量很小的时候我们可以在A表取一个工号到B表找到工号对应的工资再填写到A表，但当数据成百上千上万的时候手工超找效率很低；这个时候可以用VLOOKUP函数实现：

##### 1，在工具条里：公式Tab>插入函数>公式生成器>VLOOKUP>插入函数：

[![20180421224019.png](https://i.loli.net/2018/04/21/5adb4d8534bc9.png)](https://i.loli.net/2018/04/21/5adb4d8534bc9.png)

##### 2，在公式生成器里写参数，点击完成：

[![20180421224822.png](https://i.loli.net/2018/04/21/5adb4f5593510.png)](https://i.loli.net/2018/04/21/5adb4f5593510.png)

```
lookup_value=A2 //A2是第2行A列，也就是工号A001，这里不写A001因为后面可以批量自动填充完成剩下所有工资的查找

table_array=SheetB!$A2:$B6 //SheetB表的第2行A列到第6行B列的所有数据，$表示绝对引用

col_index_num=2 //SheetB表的工资列（第2列）

range_lookup=false //精确查找
```

##### 3，点击完成后可以看到SheetA表A001的工资变成了123，然后是批量自动填充，查找并填充剩下工号的工资列：

[![20180421225701.png](https://i.loli.net/2018/04/21/5adb5153ca07b.png)](https://i.loli.net/2018/04/21/5adb5153ca07b.png)


## 参考
VLOOKUP函数：
[https://support.office.com/zh-cn/article/vlookup-%E5%87%BD%E6%95%B0-0bbc8083-26fe-4963-8ab8-93a18ad188a1](https://support.office.com/zh-cn/article/vlookup-%E5%87%BD%E6%95%B0-0bbc8083-26fe-4963-8ab8-93a18ad188a1)

Excel的批量自动填充：
[https://support.office.com/zh-cn/article/%E5%9C%A8%E5%B7%A5%E4%BD%9C%E8%A1%A8%E5%8D%95%E5%85%83%E6%A0%BC%E4%B8%AD%E8%87%AA%E5%8A%A8%E5%A1%AB%E5%85%85%E6%95%B0%E6%8D%AE-74e31bdd-d993-45da-aa82-35a236c5b5db](https://support.office.com/zh-cn/article/%E5%9C%A8%E5%B7%A5%E4%BD%9C%E8%A1%A8%E5%8D%95%E5%85%83%E6%A0%BC%E4%B8%AD%E8%87%AA%E5%8A%A8%E5%A1%AB%E5%85%85%E6%95%B0%E6%8D%AE-74e31bdd-d993-45da-aa82-35a236c5b5db)

