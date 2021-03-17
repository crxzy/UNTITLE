# 更方便的修改请求和返回 [![Version][version-badge]](LICENSE.md)


## Requirements

- Fiddler v5.0
- Editor

## Download

[CustomRules.js](https://raw.githubusercontent.com/crxzy/UNTITLE/master/CustomRules.js)

## 使用

- 复制 CustomRules.js 到 %userprofile%\Documents\Fiddler2\Scripts\ 并覆盖

- 编辑 CustomRules.js 查看顶部
```bash
    static var targetUrl = '';    
    
    static function OnBeforeTargetUrlRequest(oSession :Session, req: Object) {
        // TODO:
        // 只支持GET METHOD
        // 修改 req['xxx'] = xxx 增加或修改请求参数    

    }

    static function OnBeforeTargetUrlResponse(oSession :Session, resp: Object) {
        // TODO:
        // 修改 resp['xxx'] = xxx 增加或修改响应内容    
    }


```

- 修改 targetUrl 为需要拦截的url
```bash
static var targetUrl = '/custom/login'; 
```

- 在请求中添加或修改参数
```bash
    static function OnBeforeTargetUrlRequest(oSession :Session, req: Object) {
        // TODO:
        // 只支持GET METHOD
        // 修改 req['xxx'] = xxx 增加或修改请求参数    

        req['roleid'] = 28576629;
    }
```

- 在响应中篡改数据

```bash
    static function OnBeforeTargetUrlResponse(oSession :Session, resp: Object) {
        // TODO:
        // 修改 resp['xxx'] = xxx 增加或修改响应内容    
        resp['cur_game_data']['score'] = 151;
    }
```

## For example:
##### 修改进度条
- 对应查询人数接口
```
用户数量查询接口
/api/259_894_2019_11_08/query_apntnum?callback=xxx

调用方式
GET

输入参数
callback：选传，回调函数名

返回值
callback({
    "status": true/错误码,
    "msg": 错误原因 //仅当status不为true时返回
    "usernumber": int //当前用户数量
})
```
- 修改 CustomRules.js
```
static var targetUrl = '/api/259_894_2019_11_08/query_apntnum'; 
		
		
			
static function OnBeforeTargetUrlRequest(oSession :Session, req: Object) {
	// 只支持GET METHOD
	// 修改 req['xxx'] = xxx 增加或修改请求参数    
	// TODO:
	 
}
		
    
static function OnBeforeTargetUrlResponse(oSession :Session, resp: Object) {
	// 修改 resp['xxx'] = xxx 增加或修改响应内容    
	// TODO:
	
	resp['usernumber'] = 1500000;
}
```
![DEMO][progress]

[version-badge]:   https://img.shields.io/badge/version-v0.1-brightgreen
[progress]:   https://raw.githubusercontent.com/crxzy/UNTITLE/master/image/progress.gif

