# 实验5：图书管理系统数据库设计与界面设计

|  姓名  |      学号      |     班级      |
| :--: | :----------: | :---------: |
|  刘爽  | 201510414209 | 2015-软件工程二班 |

## 1.数据库表设计



### 1.1. Book表
|     字段      |      类型       | 主键，外键 | 可以为空 | 默认值  |  约束  | 说明                 |
| :---------: | :-----------: | :---: | :--: | :--: | :--: | :----------------- |
|    ISBN     | varchar2(14)  |  主键   |  否   |      |      | 书本印刷的ISBN,且每本书都不一样 |
|  book_name  | varchar2(60)  |       |  否   |      |      |                    |
|   author    | varchar2(50)  |       |  是   |      |      |                    |
|  publisher  | varchar2(100) |       |  是   |      |      |                    |
|    price    |    double     |       |  否   | 0.0  |      |                    |
| public_date |     date      |       |  否   |      |      | 出版日期               |
|  total_Num  |      int      |       |  否   |  0   |      | 即该图书库存的总量          |
|  rest_Num   |      int      |       |  否   |  0   |      | 目前可借的图书量           |
|  is_borrow  |      int      |       |  否   |  0   |      | 是否可借               |

### 1.2. Reader表
|      字段       |      类型      | 主键，外键 | 可以为空 |   默认值    |  约束  | 说明                 |
| :-----------: | :----------: | :---: | :--: | :------: | :--: | :----------------- |
|    user_ID    | varchar2(32) |  主键   |  否   |          |      | 用户ID创建的时候自增        |
|     ISBN      | varchar2(14) |  外键   |  否   |          |      | 书本印刷的ISBN,且每本书都不一样 |
|   user_name   | varchar2(32) |       |  否   |          |      |                    |
|    gender     |     int      |       |      |          |  否   |                    |
|   password    | varchar2(32) |       |  否   | '123456' |      | 密码采用32位MD5加密       |
|    college    | varchar2(50) |       |  是   |          |      | 该读者所在学院            |
| borror_number |     int      |       |  是   |    0     |      | 已借数量               |


### 1.3. Administrator表
|    字段     |      类型      | 主键，外键 | 可以为空 |   默认值    |  约束  | 说明           |
| :-------: | :----------: | :---: | :--: | :------: | :--: | :----------- |
|  user_ID  | varchar2(32) |  主键   |  否   |          |      |              |
| user_name | varchar2(32) |       |  否   |  '管理员'   |      |              |
|  gender   |     int      |       |      |          |  否   |              |
| password  | varchar2(32) |       |  否   | '123456' |      | 密码采用32位MD5加密 |


### 1.4. LendRecord表
|         字段          |      类型      | 主键，外键 | 可以为空 | 默认值  |      约束       | 说明                 |
| :-----------------: | :----------: | :---: | :--: | :--: | :-----------: | :----------------- |
| lendrecord_recordID | varchar2(32) |  主键   |  否   |      |               | 借书编号               |
|       user_ID       | varchar2(32) |  外键   |  否   |      | reader.userID |                    |
|        ISBN         | varchar2(14) |  外键   |  否   |      |   Book.ISBN   |                    |
|     borrow_date     |   datetime   |       |  否   |      |               | 借阅时间               |
|      is_renew       |   tinyint    |       |  否   |  0   |      0-1      | 是否续借图书，1为已续借，0为未续借 |
|     return_date     |   datetime   |       |  否   |      |               | 归还时间，若为空代表未归还      |

### 1.5. Forfeit表
|      字段       |      类型      | 主键，外键 | 可以为空 | 默认值  |  约束  | 说明            |
| :-----------: | :----------: | :---: | :--: | :--: | :--: | :------------ |
|  forfeit_id   |     int      |  主键   |  否   |      |      | 逾期缴费ID自增      |
|    user_ID    | varchar2(32) |       |  否   |      |      | 读者编号          |
|    book_id    | varchar2(32) |       |  否   |      |      | 书籍名称          |
|   book_name   | varchar2(10) |       |  否   |      |      | 书籍名称          |
|  borrow_date  |   datetime   |       |  否   |      |      | 借阅时间          |
|  return_date  |   datetime   |       |  否   |      |      | 归还时间，若为空代表未归还 |
| forfeit_money |    double    |       |  否   | 0.0  |      | 逾期金额          |



### 1.6. ManageBookRecord表
|         字段         |      类型      | 主键，外键 | 可以为空 | 默认值  |          约束          | 说明                                       |
| :----------------: | :----------: | :---: | :--: | :--: | :------------------: | :--------------------------------------- |
| manageBookRecordID | varchar2(32) |  主键   |  否   |      |                      |                                          |
|      user_ID       | varchar2(32) |  外键   |  否   |      | Administrator.userID |                                          |
|        ISBN        | varchar2(14) |  外键   |  否   |      |      Book.ISBN       |                                          |
|     manageDate     |   datetime   |       |  否   |      |                      | 管理图书的时间                                  |
|       action       | varchar2(10) |       |  否   |      |                      | 管理图书的动作，add添加图书，delete为删除图书，update为更新图书信息 |
|     manegeNum      |     int      |       |  否   |      |                      | 管理图书的数量                                  |



### 1.7. BookReserve表
|         字段          |      类型      | 主键，外键 | 可以为空 | 默认值  |      约束       | 说明                    |
| :-----------------: | :----------: | :---: | :--: | :--: | :-----------: | :-------------------- |
| bookrecord_recordID | varchar2(32) |  主键   |  否   |      |               |                       |
|       userID        | varchar2(32) |  外键   |  否   |      | Reader.userID |                       |
|        ISBN         | varchar2(14) |  外键   |  否   |      |   Book.ISBN   |                       |
|      book_Date      |   datetime   |       |  否   |      |               | 预定图书的时间               |
|     active_Time     |     int      |       |  否   |  7   |               | 预定图书的有效期，单位为天         |
|      is_cannel      |     int      |       |  否   |  0   |      0-1      | 此预订是否取消，1表示已取消，0表示未取消 |

## 2 界面设计

### 2.1 查询API

*  功能：根据输入信息，查询图书信息
* 请求地址：http://localhost:8080/library/search/list
* 请求方法：GET
* 请求参数：

| 参数名称 |  必填  |       说明        |
| :--: | :--: | :-------------: |
| ISBN |  是   | 根据图书的ISBN编码查询图书 |

* 返回实例：

 ```
 {
        "code": 200,
        "data": {
           "ISBN": "3498-123",
            "bookName": "红楼梦",
            "author": "曹雪芹",
            "publisher": "人民文学出版社",
            "publishTime": 2011-9,
            "price": 59.70,
            "discription": "中国古典四大名著之首",
            "cnum": "20",
            "lnum":12,
         },
        "msg": "操作成功"
}
 ```
* 返回参数说明

| 参数名称 |   说明   |
| :--: | :----: |
| code | 请求响应状态 |
| data | 图书的信息  |
| msg  |  返回信息  |

### 2.修改图书API

* 功能：点击借阅，图书的可借数量减一
* 请求地址：http://localhost:8080/library/update/book
* 请求方法：POST
* 请求参数：

| 参数名称 |  必填  |   说明   |
| :--: | :--: | :----: |
| lnum |  是   | 可借数量减1 |

* 返回实例：

```
{
        "code": 200,
        "data": {
            "ISBN": "3498-123",
            "bookName": "红楼梦",
            "author": "曹雪芹",
            "publisher": "人民文学出版社",
            "publishTime": 2011-9,
            "price": 59.70,
            "discription": "中国古典四大名著之首",
            "cnum": "20",
            "lnum":12,
         },
        "msg": "操作成功"
}   
```
* 返回参数说明

| 参数名称 |   说明   |
| :--: | :----: |
| code | 请求响应状态 |
| data | 图书的信息  |
| msg  |  返回信息  |
