---
title: ajax跨域问题
date: 2016-12-26 15:16:56
tags:[ajax]
---

## 想要解决跨域问题，首先要知道为什么会出现跨域问题？
##### 由于JS同源策略的影响，因此js只能访问同域名下的文档。

域不一样的即为跨域，包括（协议，域名，端口号)。

#### Ajax解决跨域的两种方式：
#### 1、只需要在服务端填上响应头： /* IE10以下不支持*/


header("Access-Control-Allow-Origin:*");       /* 星号表示所有的域都可以接受，*/

header("Access-Control-Allow-Methods:GET,POST");

#### 2、jsonp

	$.ajax({
		type:"get",
		url:"http://localhost:3000/showAll",/*url写异域的请求地址*/
		dataType:"jsonp",  /*加上datatype*/
		jsonpCallback:"cb",  /*设置一个回调函数，名字随便取，和下面的函数里的名字相同就行*/
		success:function(){
			  。。。
			}
		});


著作权归作者所有，转载请联系作者获得授权，并标注“github作者”。