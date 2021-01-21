OhMyDash支持通过HTTP REST-API的方式来读取数据。

#### API服务器
OhMydash要求REST-API服务器返回的数据格式必须为JSON. OhMyDash提供了通用JsonPath的方式来映射API的数据格式到OhMyDash的数据格式。
对于不能通过JsonPath映射的REST-API服务器，我们需要建议您在服务器端做适配层，进行数据格式的转化。

#### 创建
在数据源列表页面，点击+按钮进入数据源创建向导,选择REST-API数据源，点击进入下一步，REST-API数据源设置页面,输入数据源名称，API服务器的URL。Swagger API Doc URL是可选的。

![Create REST-API](rest-api.jpg)

API服务器的URL的格式为http(s)://server-host:server-port. 如果所有的URL都是以api/v1开始，你也可以写为http(s)://server-ip:server-port/api/v1，点击下一步，一个REST-API数据源就创建好了。

#### 查询
REST-API使用JSON格式的查询文本，格式为
```json
{
    "method": "",
    "url": "",
    "headers": {
    "http-header-name": "http-header-value"
    },
    "body": {
    
    },
    "columns": [
      {
        "name": "<your colomn name1>",
        "jsonPath": "",
        "defaultValue": ""
      },
      {
        "name": "<your colomn name2>",
        "jsonPath": "",
        "defaultValue": ""
      }
    ]
}
```

- method
  可选参数。默认值为"get",你还可以使用post.其他http method则不支持。
- url
  必填参数。相对API服务器的URL地址。例如在创建数据源步骤中设置的服务器的URL为http://localhost:8080/api/v1 该查询请求的地址为http://localhost:8080/api/v1/types，则此处的url应为types.
- headers
  可选参数。你可以设置多个http header, 例如指定Content-Type, Accept-Type等，
- body
  可选参数。发送的http body的内容。一般method为post时需要。
- columns
  必填参数。该参数定义如何映射数据到OhMyDash的数据格式。


#### 示例

假定您的某个REST-API通过 http://your-api-server/getbooks 接口，返回如下格式的JSON:

```json
{
  "store": {
    "book": [
      {
        "category": "reference",
        "author": "Nigel Rees",
        "title": "Sayings of the Century",
        "price": 8.95
      },
      {
        "category": "fiction",
        "author": "Evelyn Waugh",
        "title": "Sword of Honour",
        "price": 12.99
      },
      {
        "category": "fiction",
        "author": "Moby Dick",
        "title": "Moby Dick",
        "isbn": "0-553-21311-3",
        "price": 8.99
      },
      {
        "category": "fiction",
        "author": "J. R. R. Tolkien",
        "title": "The Lord of the Rings",
        "isbn": "0-395-19395-8",
        "price": 22.99
      }
    ],
    "bicycle": {
      "color": "red",
      "price": 19.95
    }
  },
  "expensive": 10
}
```
您想获得如下的数据表

|Title|Author |Price |Category |
|:-----|:----- |-----:|:-------- |
|Sayings of the Century   |Nigel Rees      |  8.95   |  reference|
|Evelyn Waugh   |Evelyn Waugh      |  12.99   |  fiction|
|Moby Dick   |Moby Dick  |  22.99   |  fiction|
|The Lord of the Rings   |J. R. R. Tolkien      |  19.95   |  fiction|

您首先可以创建一个Base URL为 http://your-api-server/ 的REST-API 数据源，并在新建的图表中引用它。

然后，您只需定义如下的查询参数，就可以获得如上图所示的查询结果。

```json
  {
     "method": "get",
     "url": "getbooks",
     "columns": [
       {
          "name": "Title",
          "jsonPath": "$.store.book[*].title",
          "defaultValue": ""
       },
       {
          "name": "Author",
          "jsonPath": "$.store.book[*].author",
          "defaultValue": ""
       },
       {
          "name": "Price",
          "jsonPath": "$.store.book[*].price",
          "defaultValue": "0"
       },
       {
          "name": "Category",
          "jsonPath": "$.store.book[*].category",
          "defaultValue": ""
       }
     ]
  }
```