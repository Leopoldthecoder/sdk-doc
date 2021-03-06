# 历史

> **info**
> 此历史包含的是对文档操作的历史，比如创建、重命名、内容修改和分享等。

## 获取历史列表

**接口**

`GET <SHIMO_API>/files/:guid/histories`

**参数说明**

| 参数      | 类型   | 必填 | 说明 |
| :------- | :----- | :-- | :-- |
| size | Number | N   | 返回的历史条数，默认 `10` |
| historyType | Number | N   | history type 类型 |
| order | String | N   | 排序方式，默认 `desc` |
| sort | String | N   | 排序字段，默认 `createdAt` |
| page | Number | N   | 查询的页码，默认 `0` |
| count | Number | N   | 跳过多少个记录，默认 `0`，`count: 30` 等同于 `page: 1, size: 30`。`count` 存在时 `page` 将被忽略。_**deprecated**_ |
| size | Number | N   | 返回多少结果，别名为 `pageSize`，默认 `30` |

**代码示例**

```js
const request = require('node-fetch')

fetch('<SHIMO_API>/files/JyRX1679PL86rbTk/histories', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <Access Token>'
  }
})
  .then(res => res.json())
  .then(body => console.log(body.data))
```

**返回示例**

```json
{
  "histories": [{
    "fileGuid": "JyRX1679PL86rbTk",
    "historyType": 1,
    "userId": "10676",
    "updatedAt": "2018-05-29T09:07:51.000Z",
    "createdAt": "2018-05-29T09:07:51.000Z",
    "id": 434594,
    "content": "{\"action\":\"create\"}"
  }],
  "isLastPage": false,
  "guid": "JyRX1679PL86rbTk",
  "users": { "1": "shimo" },
  "limit": null
}
```

## 获取历史

**接口**

`GET <SHIMO_API>/files/:guid/histories/:id`

**代码示例**

```js
const request = require('node-fetch')

fetch('<SHIMO_API>/files/JyRX1679PL86rbTk/histories/434594', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <Access Token>'
  }
})
  .then(res => res.json())
  .then(body => console.log(body.data))
```

**返回示例**

```json
{
  "fileGuid": "JyRX1679PL86rbTk",
  "historyType": 1,
  "userId": "10676",
  "updatedAt": "2018-05-29T09:07:51.000Z",
  "createdAt": "2018-05-29T09:07:51.000Z",
  "id": 434594,
  "content": "{\"action\":\"create\"}"
}
```

## 创建历史

**接口**

`POST <SHIMO_API>/files/:guid/histories`

**参数说明**

| 参数      | 类型   | 必填 | 说明 |
| :------- | :----- | :-- | :-- |
| content | String | Y   | 历史内容 |
| historyType | Number | Y   | 历史类型<br>`1`：和文档**信息**有关的改动，如创建、重命名、分享<br>`2`：和文档**内容**有关的改动，如内容更改 |

**代码示例**

```js
const request = require('node-fetch')

fetch('<SHIMO_API>/files/JyRX1679PL86rbTk/histories', {
  method: 'POST',
  headers: {
    'Authorization': 'Bearer <Access Token>'
  },
  body: JSON.stringify({
    thistoryTypeype: 1,
    content: '{\"action\":\"create\"}'
  })
})
  .then(res => res.json())
  .then(body => console.log(body.data))
```

**返回示例**

```json
{
  "fileGuid": "JyRX1679PL86rbTk",
  "historyType": 1,
  "userId": "10676",
  "updatedAt": "2018-05-29T09:07:51.000Z",
  "createdAt": "2018-05-29T09:07:51.000Z",
  "id": 434594,
  "content": "{\"action\":\"create\"}"
}
```

## 更新历史

**接口**

`PATCH <SHIMO_API>/files/:guid/histories/:id`

**参数说明**

| 参数      | 类型   | 必填 | 说明 |
| :------- | :----- | :-- | :-- |
| content | String | N   | 历史内容 |
| historyType | Number | N   | 历史类型<br>`1`：和文档**信息**有关的改动，如创建、重命名、分享<br>`2`：和文档**内容**有关的改动，如内容更改 |
| userId | Number | N   | 用户标识 |

**代码示例**

```js
const request = require('node-fetch')

fetch('<SHIMO_API>/files/JyRX1679PL86rbTk/histories/434594', {
  method: 'PATCH',
  headers: {
    'Authorization': 'Bearer <Access Token>'
  },
  body: JSON.stringify({
    content: '{\"action\":\"rename\",\"before\":\"无标题\",\"after\":\"无标题2\"}'
  })
})
  .then(res => res.json())
  .then(body => console.log(body.data))
```

**返回示例**

```json
{
  "fileGuid": "JyRX1679PL86rbTk",
  "historyType": 1,
  "userId": "10676",
  "updatedAt": "2018-05-29T09:07:51.000Z",
  "createdAt": "2018-05-29T09:07:51.000Z",
  "id": 434594,
  "content": "{\"action\":\"rename\",\"before\":\"无标题\",\"after\":\"无标题2\"}"
}
```

## 获取指定历史的文档名

**接口**

`GET <SHIMO_API>/files/:guid/histories/:id/title`

**代码示例**

```js
const request = require('node-fetch')

fetch('<SHIMO_API>/files/JyRX1679PL86rbTk/histories/434594', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <Access Token>'
  }
})
  .then(res => res.json())
  .then(body => console.log(body.data))
```

**返回示例**

```json
"无标题"
```
