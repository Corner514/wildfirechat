# 敏感词
野火IM内置有敏感词过滤功能，对文本消息的内容进行过滤。为了不影响性能，请保持敏感词在1000个以内。

## 添加敏感词
#### 地址
```
http://domain/admin/sensitive/add
```
#### body
| 参数 | 类型 | 必需 | 描述 |
| ------ | ------ | --- | ------ |
| words | list<string> | 是 | 敏感词数组 |

#### 响应
N/A

#### 示例
```
curl -X POST -H "nonce:14723" -H "timestamp":"1539698981861" -H "sign":"9e9f98672f466a81e6dd61570689528cf38e6418" -H "Content-Type:application/json" -d "{\"words\":[\"a\",\"b\",\"c\"]}" http://localhost/admin/sensitive/add

{
  "code":0,
  "msg":"success"
}
```

## 删除敏感词
#### 地址
```
http://domain/admin/sensitive/del
```
#### body
| 参数 | 类型 | 必需 | 描述 |
| ------ | ------ | --- | ------ |
| words | list<string> | 是 | 敏感词数组 |

#### 响应
N/A

#### 示例
```
curl -X POST -H "nonce:14723" -H "timestamp":"1539698981861" -H "sign":"9e9f98672f466a81e6dd61570689528cf38e6418" -H "Content-Type:application/json" -d "{\"words\":[\"a\",\"b\",\"c\"]}" http://localhost/admin/sensitive/del

{
  "code":0,
  "msg":"success"
}
```

## 获取敏感词列表
#### 地址
```
http://domain/admin/sensitive/query
```
#### body
| 参数 | 类型 | 必需 | 描述 |
| ------ | ------ | --- | ------ |
| words | list<string> | 是 | 敏感词数组 |

#### 响应
N/A

#### 示例
```
curl -X POST -H "nonce:14723" -H "timestamp":"1539698981861" -H "sign":"9e9f98672f466a81e6dd61570689528cf38e6418" -H "Content-Type:application/json"  http://localhost/admin/sensitive/query

{
  "code":0,
  "msg":"success"
  "result": {
    "words":[\"a\",\"b\",\"c"]
  }
}
```

## 敏感词的高级处理方法
内置敏感词过滤功能只能对文本消息进行敏感词匹配。如果您有高级需求，比如对图片消息/语音消息或其它消息进行过滤。请使用消息[转发功能](../event_callback.md#接收消息回调)，把每一条消息都转发过去，异步处理，如果命中敏感词，再调用[撤回](./message_api.md#撤回消息)方法对消息进行撤回。
