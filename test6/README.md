#  基于GitHub的实验管理平台的分析与设计

| 姓名 |     学号     |       班级        |
| :--: | :----------: | :---------------: |
| 刘爽 | 201510414209 | 2015-软件工程二班 |

##  1.概述

- 基于GitHub的实验管理平台的作用是在线管理实验成绩的Web应用系统。学生和老师的实验内容均存放在GitHUB 页面上。
- 学生的功能主要有：一是设置自己的GitHub用户名，二是查询自己的实验成绩。学生的GitHub用户名是公开的，但成绩不公开。
- 老师的功能主要有：一是批改每个学生的成绩，二是查看每个学生的成绩。
- 老师和学生都能通过本系统的链接方便地跳转到学生的每个GitHUB实验目录，以便批改实验或者查看实验情况。
- 实验成绩按数字分数计算，每项实验的满分为100分，最低为0分。
- 系统自动计算每个学生的所有实验的平均分。

## 2.系统总体结构

![](images/系统总体结构.png)

## 3.用例图设计   [源码](src/usercase.puml)

![](images/用例图.png)

## 4.类图设计  [源码](src/class.puml) 

![](images/类图.png)



## 5.数据库设计

**详见[数据库设计](数据库设计.md)**

## 6.用例及界面详细设计

[**“登录”用例**](./用例/登录.md)，[界面](https://sh5-ang-liu.github.io/is_analysis/test6/ui/登录.html)

[**“登出”用例**](./用例/登出.md)，[界面](https://sh5-ang-liu.github.io/is_analysis/test6/ui/index.html)

[**“学生列表”用例**](./用例/学生列表.md)，[界面](https://sh5-ang-liu.github.io/is_analysis/test6/ui/学生表.html)

[**“选择课程”用例**](./用例/选择课程.md)，[界面](https://sh5-ang-liu.github.io/is_analysis/test6/ui/选课.html)

[**“查看成绩“用例**](./用例/查看成绩.md)，[界面](https://sh5-ang-liu.github.io/is_analysis/test6/ui/查看成绩.html)

[**“修改成绩“用例**](./用例/修改成绩.md)，[界面](https://sh5-ang-liu.github.io/is_analysis/test6/ui/评定成绩.html)

[**“查看用户信息“用例**](./用例/查看用户信息.md)，[界面](https://sh5-ang-liu.github.io/is_analysis/test6/ui/查看用户信息.html)

[**“修改用户信息“用例**](./用例/修改用户信息.md)，[界面](https://sh5-ang-liu.github.io/is_analysis/test6/ui/修改用户信息.html)

[**“修改密码“用例**](./用例/修改密码.md)，[界面](https://sh5-ang-liu.github.io/is_analysis/test6/ui/修改密码.html)

