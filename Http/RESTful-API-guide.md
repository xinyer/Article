## URI
1. 不要用大写
2. 单词间使用分割线‘-’，不要使用下划线‘_’
3. 不使用动词，资源要使用名词复数形式，如：users、rooms、tickets，而且所用名词往往与数据库的表名对应
```
https://api.example.com/v1/zoos
https://api.example.com/v1/animals
https://api.example.com/v1/employees
```
4. 在URI体现资源而非动作
比如比如 /user/1/update ，其中update就是一个动作，正确的做法应该是 使用PUT动作 URI为 /user/1

5. 层级 >= 三层，则使用'?'带参数
```
users/1/address/2/citys (bad) /citys?users=1&address=2; (good)
```

# HTTP动词
* GET（SELECT）
从服务器取出资源（一项或多项）

* POST（CREATE）
在服务器新建一个资源

* PUT（UPDATE）
在服务器更新资源（客户端提供改变后的完整资源）

* PATCH（UPDATE）
在服务器更新资源（客户端提供改变的属性）

* DELETE（DELETE）
从服务器删除资源

* HEAD
获取资源的元数据

* OPTIONS
获取信息，关于资源的哪些属性是客户端可以改变的

例子
```
GET /zoos：列出所有动物园
POST /zoos：新建一个动物园
GET /zoos/ID：获取某个指定动物园的信息
PUT /zoos/ID：更新某个指定动物园的信息（提供该动物园的全部信息）
PATCH /zoos/ID：更新某个指定动物园的信息（提供该动物园的部分信息）
DELETE /zoos/ID：删除某个动物园
GET /zoos/ID/animals：列出某个指定动物园的所有动物
DELETE /zoos/ID/animals/ID：删除某个指定动物园的指定动物
```

# 复杂查询
* 尽量不要使用多个单词拼接的方式，如果不可避免使用‘_’下划线

```
?limit=10：指定返回记录的数量
?offset=10：指定返回记录的开始位置。
?page=2&count=100：指定第几页，以及每页的记录数。
?sortby=name&order=asc：指定返回结果按照哪个属性排序，以及排序顺序。
?animal_type_id=1：指定筛选条件
```

# Request
1. GET 非id的参数使用'?'方式传输
```
/users/1?state=closed
```

2. POST PATCH PUT DELETE 非id的参数使用body传输，并且应该encode

3. 分页
```
?limit=10&offset=10

limit：返回记录数量
offset：返回记录的开始位置
```

4. 单参数多字段
使用, 分隔，如
```
/users/1?fields=name,age,city
```

5. 鉴权相关的参数放在Header

6. 查询条件的参数不应该放到Header

# Response
1. 在接收的返回时间数据时只使用UTC格式. 查阅ISO8601时间格式, 例如:
```
"finished_at": "2012-01-01T12:00:00Z"
```

2. 使用json格式返回数据
```
{
    "success":true,
    "data":{"id":1,"name":"xiaotuan"},
}
```

3. 各HTTP方法成功处理后的数据格式
| respionse  | 格式         |
| ---------- | ----        |
| GET        | 单个对象、集合|
| POST       | 新增成功的对象|
|PUT/PATCH   | 更新成功的对象|
|DELETE      | 空|


4. 分页查询返回


```
{
    "paging":{"limit":10,"offset":0,"total":729},
    "data":[{},{},{}...]
}

```


# 安全性与幂等性

# 版本控制
在URI中加入版本
 如 api.meow.com/v1/users


# 状态码
## 成功
> Code          Method                              Description
200              ALL                                     请求成功并返回实体资源
201              POST /PUT/PATCH          创建资源成功
201              ALL					 表示一个请求已经进入后台排队（异步任务） 
202		     DELETE				  删除数据成功


## 客户端错误
> Code          Method          Description
400              ALL                 用户发出的请求有错误，服务器没有进行新建或修改数据的操作，该操作是幂等的
401              ALL                 表示用户没有权限（令牌、用户名、密码错误）
403              ALL                 表示用户得到授权（与401错误相对），但是访问是被禁止的
404              ALL                 用户发出的请求针对的是不存在的记录，服务器没有进行操作，该操作是幂等的
406 		     GET		     用户请求的格式不可得（比如用户请求JSON格式，但是只有XML格式）
410 		     GET		     用户请求的资源被永久删除，且不会再得到的
422              ALL                 一般是必要字段缺失或参数格式化问题

### 服务器错误
> Code          Method          Description
500              ALL                 服务器未知错误

完整状态码列表 参考 [HTTP Status Codes](http://www.restapitutorial.com/httpstatuscodes.html)

### URI失效
* 随着系统发展，总有一些API失效或者迁移，对失效的API，返回404 not found 或 410 gone；对迁移的API，返回 301 重定向

# API文档
## 导航
* 分两级标题显示，一级标题标明属于哪个模块，二级标题标明具体功能
```
以Github Api为例

-Overview
--| Media Types
--| OAuth Authorizations API
--| API Previews

-Activity
--| Events
--| Feeds

-Gists
--| Comments

```
 

## 格式
* 包含以下内容
标题、描述、URL、参数、response格式

比如:
---
### List email addresses for a user
List email for the specified user.

`GET /users/:username/emails`

#### Parameters
:username  用户名

#### Response
```
Status: 200 OK

[
  {
    "email": "octocat@github.com",
    "verified": true,
    "primary": true,
    "visibility": "public"
  }
]
```

## API文档生成工具
* apidoc  [链接](https://github.com/caixw/apidoc)
* 具体文档 [链接](http://apidoc.tools/)

#meow