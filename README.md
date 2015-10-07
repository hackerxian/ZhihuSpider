# ZhihuSpider

本来想用nodejs对知乎进行模拟登陆，抓取信息

通过request post发送用户名和密码的方式，可以进行登陆，但是需要输入验证码，用程序来识别感觉太麻烦。

最后想到用cookie的方式来解决就很简单了。

打开Chrome控制台，查看知乎首页的请求，就能看到Cookie，试了几下还真的可以。

最后简单封装了一下，懒得发版本

```
'use strict';

var co = require('co');
var getContent = require('./index');

co(function* () {
  let Cookie = 'your cookie here';
  let url = 'http://www.zhihu.com/';
  let content = yield getContent(url, Cookie);
  console.log(content)
}).catch(onerror);

function onerror(err) {
  console.error(err.stack);
}
```
