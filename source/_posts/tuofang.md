---
title: Dragthe
date: 2016-11-15 20:13:07
tags:[javascript,html5 Drag,drop]
---


##	 拖放
##### 拖放是一种常见的特性，即抓取对象以后拖到另一个位置

##  Examples

##	  dragenter


	开始拖动
	
##  dragover	

	拖动中

##	  dragleave	

	拖动放开
	
##	  drop	

	拖动完成

##		Basis

	把图片拖到这里试试		（这里就不做演示了）

	
##  css代码
	#target_box{
  			max-width : 100%;
  			width: 300px;
  			height: 100px;
  			border: 1px solid red;
  			display: flex;
  			justify-content: center;
  			align-items: center;
  			font-size: 18px; transition: all 0.5s;
		}
	#target_box.droping{
  			color: red;
  			font-weight: blod;
  			font-size: 30px;
		}

	#show-drop img{
 			 max-width : 100%;
 			 display: block;
		}
##		html代码

	
	<div id="target_box">把图片拖到这里试试</div>
	<div id="show-drop" title="将拖动的图片在这里显示出来"></div>
	
	
##  	js代码

	function addEventListener(dom,event,callback){
    if(typeof dom == "string"){
      document.querySelector(dom).addEventListener(event,callback);
    }else{
      dom.addEventListener(event,callback);
    	}
	}
	//开始拖动
	addEventListener(document,"dragenter",function(e){
 		 e.preventDefault();
		 document.querySelector("#target_box").setAttribute("class","droping");
	});

	//拖动中
	addEventListener(document,"dragover",function(e){
 		 e.preventDefault();
	});

	//拖放完成
	addEventListener(document,"drop",function(e){
 		 e.preventDefault();
	});
	//拖放离开
	addEventListener(document,"dragleave",function(e){
 		 e.preventDefault();
 	 document.querySelector("#target_box").setAttribute("class","");
	});
	//监听是否拖放当元素上后离开的
		addEventListener("#target_box",'drop',function(e){
 		 e.preventDefault();//移除原有浏览器监听效果
 		 var dataTransfer = e.dataTransfer;//获取文件对象
  		 var files = dataTransfer.files[0];
  	//获取文件后缀
 	 var match = files.name ? files.name.match(/\.([a-zA-Z]+)$/) || [] : false;
  	 var suffix = match ? match[1] : "";
 	//如果后缀不是图片
  	if(!suffix || ["jpg","jpeg","png","gif"].indexOf(suffix.toLocaleLowerCase()) < 0){
    	return alert("你拖动的不是图片");
  	}
  	//读取文件的 base64 值
  		var filereader = new FileReader();
  		addEventListener(filereader,'load',function(ee){
    //获取 base64 编码
    var base64 = ee.target.result;
    var img = document.createElement("img");
    img.src = base64;
    //将图片添加到页面中
    document.querySelector("#show-drop").appendChild(img);
  	});
  	filereader.readAsDataURL(files);
	});	

##  base64图片

	如果需要实现图片上传，可以将转行后的 base64 上传到服务器，服务器将 base64 生成为图片
	
	
####  这里如果希望大家能帮到大家的地方	
	
	