微信公众帐号管理平台 操作手册
================

######Http接口文档
* 调用方法

```
    /**
     * url String GET请求的地址
     * params Map  请求参数
     */
    ${http.getUrl(url,params)}
    
```

```
    /**
     * url String POST请求的地址
     * params Map  请求参数
     */
    ${http.postUrl(url,params)}
    
```
```
    /**
     * GET请求
     * ctx Object 会话上下文对象 直接内置变量 ctx
     * apiName String HTTP接口标识
     * params Map  请求参数
     */
    ${http.get(ctx,apiName,params)}
    
```
```
    /**
     * POST请求
     * ctx Object 会话上下文对象 直接内置变量 ctx
     * apiName String HTTP接口标识
     * params Map  请求参数
     */
    ${http.post(ctx,apiName,params)}
    
```

* 返回格式说明
    http.getUrl和http.postUrl 不会对返回格式进行处理,直接放回文本内容
    http.get和http.post请求 会对放回值进行预处理
    如果放回值不可以解析成json,则直接返回文本内容
    json格式如下
    {
        "type":plaintext|text|news,
        "content":"string",
        "items":[
            {
                "title":"title",
                "desc":"desc",
                "picture":"pucture url",
                "url":"article url",
            }
        ]
    }
    如果type是plaintext则直接返回文本内容给模板引擎,如果是text类型,则告诉微信引擎返回content的文本内容,忽略模板其他部分
    如果是news则微信引擎处理输出items的图文内容
    

