# API Check List

- [ ] Basic: 使用RESTful API设计规范
- [ ] Basic: 接入swagger API 自动文档

- [ ] 协议: 使用HTTPS，沒有使用请提案

- [ ] 域名: 使用专用的子域名/通过 URL 标记加以区别

      https: //api.example.com
    
      或
    
      https: //www.example.com/api/

- [ ] 版本控制: 在 URL 中使用整型版本号

      https: //api.example.com/v{n}/

- [ ] API路径: 网址中不能有动词，只能有名词，而且所用的名词通常与数据库的表格名对应，API中的名词也应该使用复数

      https://api.example.com/v1/products 
      https://api.example.com/v1/users 
      https://api.example.com/v1/shops

- [ ] HTTP 请求方式: 相似API统一

      GET(SELECT): 从服务器取出资源(一项或多项)
      POST(CREATE): 在服务器新建一个资源
      PUT(UPDATE): 在服务器更新资源(客户端提供改变后的完整资源)
      DELETE(DELETE): 从服务器删除资源
      
      例子:  
      GET /products: 列出所有商品
      POST /product: 新建一个商品
      GET /products/ID: 获取某个指定商品的信息
      PUT /products/ID: 更新某个指定商品的信息
      DELETE /products/ID: 删除某个商品
      GET /products/ID/suppliers: 列出某个指定商品的所有供应商
      GET /products/ID/suppliers/ID: 获取某个指定商品的指定供应商信息

- [ ] 数据过滤: 提供了通过参数对返回结果的数量、顺序、范围进行控制的设计

      一些常见的参数: 
      
      ?limit=10: 指定返回记录的数量
      ?offset=10: 指定返回记录的开始位置
      ?page=2&per_page=100: 指定第几页，以及每页的记录数
      ?sortby=name&order=asc: 指定返回结果按照哪个属性排序，以及排序顺序
      ?producy_type=1: 指定筛选条件
            
- [ ] 参数传递: 方式统一
  - [ ] RESTful 风格的地址栏参数
  
        /api/v1/product/122，其中 122 为产品编号
        
  - [ ] GET 方式的查询字串地址栏参数
        
        /api/v1/product?id=122
  
  - [ ] POST 方式的 body 数据
  
  - [ ] OAuth方面: cookie/request header
  
- [x] Response: 格式正确

       {
          status: 0, // 表示接口的执行的状态，“status=0”表示成功，“status<0”表示异常
          data: {}||[],  // 返回的业务数据
          code: 1000, // 与返回结果相关的业务代码，例如: 用户注册时，返回 1001，表示用户填写的昵称不可用
          msg: ʼʼ // 接口调用结果的提示信息，特别是当 status 不等于 0 时，需要描述异常的现象或者原因
       }

- [x] Response: data包含字段满足前端展示需要
- [x] Response: data没有无用字段
- [x] Response: 字段没有拼写错误，统一为驼峰或者下划线，下划线的前端应使用humps转换为camelizeKeys使用
- [ ] Response: 返回正确使用状态码

      200 OK - [GET]
      201 CREATED - [POST/PUT/PATCH]: 用户新建或修改数据成功
      202 Accepted - [*]: 表示一个请求已经进入后台排队（异步任务）
      204 NO CONTENT - [DELETE]: 用户删除数据成功
      ---
      400 INVALID REQUEST - [POST/PUT/PATCH]: 用户发出的请求有错误，服务器没有进行新建或修改数据的操作，该操作是幂等的
      401 Unauthorized - [*]: 表示用户没有权限（令牌、用户名、密码错误）
      403 Forbidden - [*] 表示用户得到授权（与401错误相对），但是访问是被禁止的
      404 NOT FOUND - [*]: 用户发出的请求针对的是不存在的记录，服务器没有进行操作，该操作是幂等的
      406 Not Acceptable - [GET]: 用户请求的格式不可得（比如用户请求JSON格式，但是只有XML格式）
      410 Gone -[GET]: 用户请求的资源被永久删除，且不会再得到的
      422 Unprocesable entity - [POST/PUT/PATCH] 当创建一个对象时，发生一个验证错误
      ---
      500 INTERNAL SERVER ERROR - [*]: 服务器发生错误，用户将无法判断发出的请求是否成功

- [x] 安全: 必须有安全措施

  - [ ] API 服务使用前置“过滤器”对请求的合法性进行验证
  - [ ] 基于令牌(access_token)的鉴权

- [x] 核心业务逻辑的判断应该由API决策后返回结果,前端不能处理

- [x] 一个 API 只为一个业务功能服务

      比如，“用户信息更新 API” 只应该被用来更新用户信息。

- [x] 确认提示信息是前端负责，还是 API 负责
    

## References

MonstarLab Chengdu API Standard

http://www.ruanyifeng.com/blog/2014/05/restful_api.html

https://codeplanet.io/principles-good-restful-api-design/

https://bourgeois.me/rest/

https://developer.github.com/v3/media/#request-specific-version