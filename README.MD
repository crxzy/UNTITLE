# UNTITLE [![Version][version-badge]](LICENSE.md)


## Requirements

- Fiddler v5.0
- Editor

## Download

[FILE](https://raw.githubusercontent.com/crxzy/UNTITLE/master/CustomRules.js)

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
static var targetUrl = '/g89anniver2019/custom/login'; 
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

```bash
    static var targetUrl = '/g89anniver2019/custom/login';    
    
    static function OnBeforeTargetUrlResponse(oSession :Session, resp: Object) {
        // TODO:
        // 修改 resp['xxx'] = xxx 增加或修改响应内容    
        //resp['cur_game_data']['score'] = 151;
        resp['cur_game_data']['score'] = 100;
		resp['cur_game_data']['nick'] = 'ZhaoYan Chen';
    }

    static function OnBeforeTargetUrlRequest(oSession :Session, req: Object) {
        // TODO:
        // 只支持GET METHOD
        // 修改 req['xxx'] = xxx 增加或修改请求参数    
        //req['test'] = 'fffffffff';
        req['roleid'] = 28576629;
    }
```


![DEMO][examples-link]


## 用处

适用于营销活动的抽奖、时光机、兑换、进度条等

[version-badge]:   https://img.shields.io/badge/version-v0.1-brightgreen
[examples-link]:   https://raw.githubusercontent.com/crxzy/InfinityHook/master/demo.gif

