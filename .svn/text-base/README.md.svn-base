/*
Title: micoUser
Description: 注册、登录、修改密码、邮箱等基础用户管理
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[isExist](#1)<br/>

[getSmsCode](#2)<br/>

[signUpOrlogInByPhone](#3)<br/>

[setPassword](#4)<br/>

[loginWithPhone](#5)<br/>

[resetPassword](#6)<br/>

[updatePassword](#7)<br/>

[updateEmail](#8)<br/>
</div>

#**概述**

micoUser模块封装了用户注册、登录、发送验证码、验证验证码、密码修改、邮箱修改等方法

#**isExist**<div id="1"></div>

判断此用户是否存在，如果已存在，不允许进行注册，如果用户不存在则不允许重置密码。

$mxuser.isExist(phone, callback(ret, err))

##phone

phone：

- 类型：字符串
- 默认值：无
- 描述：用户的手机号码

##callback(ret, err)

ret：

- 类型：int对象

内部字段：
 0 //操作成功返回用户名为phone用户的个数

err：

- 类型：JSON对象


##示例代码

```js
var phone = "131XXXX2211";
$mxuser.isExist(phone, function(ret, err) {
	alert("ret = " + ret);
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**getSmsCode**<div id="2"></div>

发送验证码给用户（每帐号前100条免费超出后0.1元/条）

$mxuser.getSmsCode(phone, callback(ret, err))

##phone

phone：

- 类型：字符串
- 默认值：无
- 描述：用户的手机号码

##callback(ret, err)
ret：

- 类型：int对象

内部字段：

 0 //返回0 操作成功

err：

- 类型：JSON对象


##示例代码

```js
var username = "131XXXX2211";
$mxuser.getSmsCode(username, function(ret) {
	//发送成功
	alert("ret = " + ret);
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**signUpOrlogInByPhone**<div id="3"></div>

验证发送给用户的验证码

$mxuser.signUpOrlogInByPhone(phone, identify, callback(ret, err))

##phone

phone：

- 类型：字符串
- 默认值：无
- 描述：用户的手机号码

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	"mobilePhoneNumber":"", // 手机号
	"mobilePhoneVerified":true, //验证成功
	"username":"", 	//用户名，默认为手机号
	"objectId":"", 	//唯一标识
	"createdAt":"2015-05-18T08:58:55.956Z", //创建日期
	"updatedAt":"2015-05-18T08:58:55.956Z"	//更新日期
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
	"mobilePhoneNumber":""		//操作失败的手机号
	"smsCode":""	//验证失败的验证码
}
```

##示例代码

```js
var phone = "131XXXX2211";
var identify = "194662";
$mxuser.signUpOrlogInByPhone(phone, identify, function(ret, err) {
	alert("ret = " + JSON.stringify(ret));
	alert("err = " + JSON.stringify(err));
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setPassword**<div id="4"></div>

设置用户初始密码完成注册

$mxuser.setPassword(phone, password, callback(ret, err))

##phone

phone：

- 类型：字符串
- 默认值：无
- 描述：用户的手机号码

##password

password：

- 类型：字符串
- 默认值：无
- 描述：用户的初始密码

##callback(ret, err)
ret：

- 类型：JSON对象

内部字段：
```js
{
	"login_id":"", //用户ID，及手机号
	"token":"", //用户的Token，以后控制设备验证用户都要用到
	"message":"注册成功!" //注册成功
}
```

err：

- 类型：JSON对象
- 
内部字段：
```js
{
	"code":403,	//错误代码
	"message":"Forbidden: user is existed!" //错误原因
}
```

##示例代码

```js
var phone = "131XXXX2211";
var password = "123456";
$mxuser.setPassword(phone, password, function(ret, err) {
	alert("ret = " + JSON.stringify(ret));
	alert("err = " + JSON.stringify(err));
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**loginWithPhone**<div id="5"></div>

通过用户名和密码登录

$mxuser.loginWithPhone(phone, password, callback(ret, err))

##phone

phone：

- 类型：字符串
- 默认值：无
- 描述：用户的手机号码

##password

password：

- 类型：字符串
- 默认值：无
- 描述：用户的密码

##callback(ret, err)
ret：

- 类型：JSON对象

内部字段：
```js
{
  "mobilePhoneNumber": "", //手机号
  "userToken": "",	//Token
  "username": "", 	//用户名
  "emailVerified": false,	//是否验证了邮箱
  "authData": null,
  "mobilePhoneVerified": true,
  "objectId": "",
  "createdAt": "2015-05-18T08:58:55.956Z",
  "updatedAt": "2015-05-18T09:52:52.660Z"
}
```

err：

- 类型：JSON对象
- 
- 内部字段：
```js
{
	"code":210, //错误代码
	"message":"The username and password mismatch." //错误原因
}
```


##示例代码

```js
var phone = "131XXXX2211";
var password = "123456";
$mxuser.loginWithPhone(phone, password, function(ret, err) {
	alert("ret = " + JSON.stringify(ret));
	alert("err = " + JSON.stringify(err));
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**resetPassword**<div id="6"></div>

重置用户密码，一般是在验证短信通过后执行

$mxuser.resetPassword(password, callback(ret, err))

##phone

password：

- 类型：字符串
- 默认值：无
- 描述：用户密码

##callback(ret, err)
ret：

- 类型：JSON对象

内部字段：
```js
{
  "mobilePhoneNumber": "", //手机号
  "userToken": "",	//Token
  "username": "", 	//用户名
  "emailVerified": false,	//是否验证了邮箱
  "authData": null,
  "mobilePhoneVerified": true,
  "objectId": "",
  "createdAt": "2015-05-18T08:58:55.956Z",
  "updatedAt": "2015-05-18T09:52:52.660Z"
}
```

err：

- 类型：JSON对象
- 
- - 内部字段：
```js
{
	"code":2, //错误代码
	"message":"" //错误原因
}
```


##示例代码

```js
var password = "123456";
$mxuser.resetPassword(password, function(ret, err) {
	alert("ret = " + JSON.stringify(ret));
	alert("err = " + JSON.stringify(err));
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**updatePassword**<div id="7"></div>

修改用户的密码，可以验证老密码是否正确

$mxuser.updatePassword(oldpsw, password, callback(ret, err))

##oldpsw

oldpsw：

- 类型：字符串
- 默认值：无
- 描述：用户的旧密码

##password

password：

- 类型：字符串
- 默认值：无
- 描述：用户的新密码

##callback(ret, err)
ret：

- 类型：JSON对象

内部字段：

```js
{
	"updatedAt":"2015-05-18T10:24:18.848Z",	//更新时间
	"objectId":""	//id
}
```

err：

- 类型：JSON对象
- 
- 内部字段：

```js
{
	"code":2, //错误代码
	"error":"" //错误原因
}
```


##示例代码

```js
var oldpsw = "123456";
var password = "123456";
$mxuser.updatePassword(oldpsw, password, function(ret, err) {
	alert("ret = " + JSON.stringify(ret));
	alert("err = " + JSON.stringify(err));
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**updateEmail**<div id="8"></div>

修改用户的邮箱

$mxuser.updateEmail(email,  callback(ret, err))

##email

email：

- 类型：字符串
- 默认值：无
- 描述：用户的邮箱

##callback(ret, err)
ret：

- 类型：JSON对象

内部字段：
```js
{
  	"mobilePhoneNumber": "", //手机号
  	"userToken": "",	//Token
  	"username": "", 	//用户名
  	"emailVerified": false,	//是否验证了邮箱
  	"authData": null,
  	"mobilePhoneVerified": true,
  	"objectId": "",
	"email":"222@qq.com",	//邮箱
	"objectId":"",
	"createdAt":"2015-05-18T08:58:55.956Z",
	"updatedAt":"2015-05-18T10:28:05.733Z"
}
```

err：

- 类型：JSON对象

- 内部字段：
```js
{
	"code":125,	//错误代码
	"message":"The email address was invalid." 	//错误原因
}
```

##示例代码

```js
var email = "222@qq.com";
$mxuser.updateEmail(email, function(ret, err) {
	alert("ret = " + JSON.stringify(ret));
	alert("err = " + JSON.stringify(err));
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

/*
Title: micoBind
Description: EasyLink配网连接和获取本地SSID，以及设备的配网和绑定
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[getSsid](#1)<br/>

[getDevip](#2)<br/>

[getDevid](#3)<br/>

[bindDevCloud](#4)
</div>

#**概述**

micoBind模块封装了获取当前SSID的方法，以及EasyLink配网和获取WIFI设备ip的方法

#**getSsid**<div id="1"></div>

当前手机是否连接上wifi，连接上则返回SSID,否则返回设备未联网。

getSsid(null, callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	ssid:""		//操作成功返回json数据
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:""    //错误描述
}
```

##示例代码

```js
var wifissid = api.require('wifiSsid');
wifissid.getSsid(null, function(ret, err) {
	if (ret.ssid) {
		api.alert({msg:ret.ssid});
	}else{
		api.alert({msg:err.msg});
    }
});
```

##补充说明

获取当前WIFI的SSID

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**getDevip**<div id="2"></div>

发送ssid和psw给WIFI设备，并等待返回设备的ip

getDevip({params}, callback(ret, err))

##params

wifi_ssid：

- 类型：字符串
- 默认值：无
- 描述：WIFI的SSID，不可为空

wifi_password：

- 类型：字符串
- 默认值：无
- 描述：WIFI的密码，不能为空

##callback(ret, err)
ret：

- 类型：JSON对象

内部字段：

```js
{
	devip:""	 //操作成功返回json数据
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:""    //错误描述
}
```
##示例代码

```js
var devipme = api.require('micoBind');
var ssid = "micp";
var psw = "888888";
devipme.getDevip({
	wifi_ssid : ssid,
	wifi_password : psw
}, function(ret, err) {
	if (ret.devip) {
		api.alert({msg:ret.devip});
    }else{
		api.alert({msg:'error'});
    }
});
```

##补充说明

发送ssid和psw，得到WIFI设备的ip

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**getDevid**<div id="3"></div>

设备会启动一个server，app调用此接口连接服务并获取设备的Deviceid

$mico.getDevid(dev_ip, dev_psw, dev_token, callback(ret, err))

##dev_ip

dev_ip：

- 类型：字符串
- 默认值：无
- 描述：getDevip得到的设备ip

##dev_psw
dev_psw：

- 类型：字符串
- 默认值：无
- 描述：设备的密码，必须为数字一般为4-6位

##dev_token
dev_token：

- 类型：字符串
- 默认值：无
- 描述：注册用的token，下面绑定设备的时候还会用到

##callback(ret, err)
ret：

- 类型：JSON对象

内部字段：

```js
{
	"device_id": "af2b33be/c8934645dd0a"	//设备的deviceid，唯一标识
}
```

err：

- 类型：JSON对象

内部字段：

```js
	网络通信的错误代码
```
##示例代码

```js
var dev_ip = "192.168.1.111";
var dev_psw = "1234";
var userToken = getUserInfo().get("userToken");
var dev_token = $.md5(dev_ip + userToken);
$mico.getDevid(dev_ip, dev_psw, dev_token, function(ret, err) {
	alert("devid = " + ret.device_id);
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**bindDevCloud**<div id="4"></div>

获取到deviceid后去云端与设备绑定

$mico.bindDevCloud(APP_ID, userToken, dev_token, callback(ret, err))

##APP_ID
APP_ID：

- 类型：字符串
- 默认值：无
- 描述：APP_ID:8323c298-adc2-40ae-bb9d-30098c4dc42f

##userToken
userToken：

- 类型：字符串
- 默认值：无
- 描述：用户注册时候得到的usertoken，可以通过以下方法获取
- getUserInfo().get("userToken");

##dev_token
dev_token：

- 类型：字符串
- 默认值：无
- 描述：注册用的token，获取方法如下：$.md5(dev_ip + userToken);


##callback(ret, err)
ret：

- 类型：JSON对象

内部字段：

```js
{
  "user-device-key": "3ed5a203-1219-4d29-b44f-b02517741d8e" //暂时未用到
}
```

err：

- 类型：JSON对象

内部字段：

```js
"error": 
{
    "code": 403,	//错误代码
    "message": "Forbidden: active_token is not found!"	//错误描述
}
```
##示例代码

```js
var APP_ID = "8323c298-adc2-40ae-bb9d-30098c4dc42f";
var userToken = getUserInfo().get("userToken");
var dev_token = $.md5(dev_ip + userToken);
$mico.bindDevCloud(APP_ID, userToken, dev_token, function(ret, err) {
});
```

##补充说明
无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


/*
Title: micoDev
Description: 设备配置绑定成功后，可以对设备进行基础操作，包含获取设备列表、获取能授权的设备，修改设备名称，授权设备给其他用户，删除用户
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[getDevList](#1)<br/>

[getAuthDev](#2)<br/>

[editDevName](#3)<br/>

[authDev](#4)<br/>

[deleteDev](#5)

</div>

#**概述**

micoDev用于对设备的管理

#**getDevList**<div id="1"></div>

获取名下能控制的所有设备

$mico.getDevList(userToken, callback(ret, err))

##userToken

userToken：

- 类型：字符串
- 默认值：无
- 描述：用户的usertoken

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
[
  {
    "id": "d64f517c/00504302fe01",	//devideID
    "serial": null,
    "bssid": "00504302fe01",
    "created": "2015-05-18 15:37:08",
    "alias": "good",	//设备名称
    "online": "1",	//是否在线
    "power_time": null,
    "ip": null,	//设备ip
    "ssid": null,	//设备ssid
    "online_time": "2015-05-18 15:37:09",
    "offline_time": null
  }
]
```

err：

- 类型：JSON对象

内部字段：

```js

```

##示例代码

```js
var userToken = "";
$mico.getDevList(userToken, function(ret, err) {

});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getAuthDev**<div id="2"></div>

获取名下能控制的所有设备

$mico.getAuthDev(userToken, callback(ret, err))

##userToken

userToken：

- 类型：字符串
- 默认值：无
- 描述：用户的usertoken

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
[
  {
    "id": "d64f517c/00504302fe01",	//devideID
    "serial": null,
    "bssid": "00504302fe01",
    "created": "2015-05-18 15:37:08",
    "alias": "good",	//设备名称
    "online": "1",	//是否在线
    "power_time": null,
    "ip": null,	//设备ip
    "ssid": null,	//设备ssid
    "online_time": "2015-05-18 15:37:09",
    "offline_time": null
  }
]
```

err：

- 类型：JSON对象

内部字段：

```js

```

##示例代码

```js
var userToken = "";
$mico.getAuthDev(userToken, function(ret, err) {

});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**editDevName**<div id="3"></div>

发送ssid和psw给WIFI设备，并等待返回设备的ip

$mico.editDevName(APP_ID, userToken, inputname, devid, callback(ret, err))

##APP_ID

APP_ID：

- 类型：字符串
- 默认值：无
- 描述：APPID

##userToken

userToken：

- 类型：字符串
- 默认值：无
- 描述：用户的userToken
- 
##inputname

inputname：

- 类型：字符串
- 默认值：无
- 描述：需要修改的名字
- 
##devid

devid：

- 类型：字符串
- 默认值：无
- 描述：设备的SSID

##callback(ret, err)
ret：

- 类型：JSON对象

内部字段：

```js
{
  "result": "success"
}
```

err：

- 类型：JSON对象

内部字段：

```js
"error": 
{
    "code": 401,	//错误代码
    "message": "Unauthorized"	//错误描述
}
```
##示例代码

```js
$mico.editDevName(APP_ID, userToken, inputname, devid, function(ret, err) {

});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**authDev**<div id="4"></div>

授权设备

$mico.authDev(APP_ID, userToken, phone, devid, callback(ret, err))

##APP_ID

APP_ID：

- 类型：字符串
- 默认值：无
- 描述：APPID

##userToken

userToken：

- 类型：字符串
- 默认值：无
- 描述：用户的userToken
- 
##phone

phone：

- 类型：字符串
- 默认值：无
- 描述：授权给此用户，phone是用户的用户名(此处为手机号)
- 
##devid

devid：

- 类型：字符串
- 默认值：无
- 描述：设备的SSID

##callback(ret, err)
ret：

- 类型：JSON对象

内部字段：

```js

```

err：

- 类型：JSON对象

内部字段：

```js
"error": 
{
    "code": 401,	//错误代码
    "message": "Unauthorized"	//错误原因
}
```
##示例代码

```js
$mico.autDev(APP_ID, userToken, phone, devid, function(ret, err) {

});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**deleteDev**<div id="5"></div>

删除名下能控制的设备

$mico.deleteDev(APP_ID, userToken, devid, callback(ret, err))

##APP_ID
APP_ID：

- 类型：字符串
- 默认值：无
- 描述：APP_ID:8323c298-adc2-40ae-bb9d-30098c4dc42f

##userToken
userToken：

- 类型：字符串
- 默认值：无
- 描述：用户注册时候得到的usertoken，可以通过以下方法获取
- getUserInfo().get("userToken");

##devid
devid：

- 类型：字符串
- 默认值：无
- 描述：设备的DeviceID

##callback(ret, err)
ret：

- 类型：JSON对象

内部字段：

```js
{
  "result": "success"
}
```

err：

- 类型：JSON对象

内部字段：

```js
"error": 
{
    "code": 403,	//错误代码
    "message": "Forbidden: active_token is not found!"	//错误描述
}
```
##示例代码

```js
$mico.deleteDev(APP_ID, userToken, devid, function(ret, err) {

});
```

##补充说明
无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

/*
Title: micoMqtt
Description: MQTT连接
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[startMqtt](#1)

[recvMqttMsg](#2)

[stopRecvMqttMsg](#3)

[publish](#4)

[stopMqtt](#5)
</div>

#**概述**

micoMqtt模块封装了标准的mqtt方法，可实现订阅，publish和停止订阅

#**startMqtt**<div id="1"></div>

打开MQTT，如果未连接成功，则自动重连直到连接上为止。

startMqtt({params}, callback(ret, err))

##params

host：

- 类型：字符串
- 默认值：无
- 描述：服务器地址，不可为空

username：

- 类型：字符串
- 默认值：无
- 描述：用户名，可为空

password：

- 类型：字符串
- 默认值：无
- 描述：用户密码，可为空


clientID：

- 类型：字符串
- 默认值：无
- 描述：客户端连接mqtt所用到的唯一ID，不可为空


topic：

- 类型：字符串
- 默认值：五
- 描述：订阅的主题，不可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:false		//是否成功，布尔类型
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:""    //错误描述
}
```

##示例代码

```js
var micoMqtt = api.require("micoMqtt");
var host = "http://api.easycc.io";
var username = "";
var password = "";
var clientID = "aca213caec5c";
var topic = "d64f517c/out/read/#";
micoMqtt.startMqtt({
	micoMqtt : micoMqtt,
	host : host,
	username : username,
	password : password,
	clientID : clientID,
	topic : topic
}, function(ret, err){
	if(ret.status){
		api.alert({msg:'start success'});
	}else{
		api.alert({msg:err.msg});
    }
});
```

##补充说明

打开MQTT连接

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**recvMqttMsg**<div id="2"></div>

接收消息

recvMqttMsg(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	subs:		 //消息内容，JSON对象
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:""    //错误描述
}
```

##示例代码

```js
var micoMqtt = api.require("micoMqtt");
micoMqtt.recvMqttMsg(function(ret, err) {
	if(ret){
		api.alert({msg:JSON.stringify(ret.subs)});
	}else{
		api.alert({msg:err.msg});
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**stopRecvMqttMsg**<div id="3"></div>

停止接收消息。

stopRecvMqttMsg()

##示例代码

```js
var micoMqtt = api.require("micoMqtt");
micoMqtt.stopRecvMqttMsg();
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**publish**<div id="4"></div>

向服务发送消息并获取回执

publish({params}, callback(ret, err))

##params

topic：

- 类型：字符串
- 默认值：无
- 描述：发布消息的主题，不可为空

command：

- 类型：字符串
- 默认值：无
- 描述：发布消息的指令，不能为空

##callback(ret, err)
ret：

- 类型：JSON对象

内部字段：

```js
{
	status:false		//是否成功，布尔类型
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:""    //错误描述
}
```
##示例代码

```js
var micoMqtt = api.require("micoMqtt");
var topic = "d64f517c/in/read/app1";
var command = "{}";
micoMqtt.publish({
	topic : topic,
	command : command
}, function(ret, err){
	if(ret.status){
		api.alert({msg:'publish success'});
    }else{
		api.alert({msg:err.msg});
    }
});
```

##补充说明

发送消息

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**stopMqtt**<div id="5"></div>

关闭MQTT连接

stopMqtt(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:false		//是否成功，布尔类型
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:""    //错误描述
}
```
##示例代码

```js
var micoMqtt = api.require("micoMqtt");
micoMqtt.stopMqtt(function(ret, err) {
	if(ret.status){
		api.alert({msg:'stop success'});
    }else{
		api.alert({msg:err.msg});
    }
});
```

##补充说明

关闭MQTT连接

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本