---
title: test
date: 2016-11-15 17:06:23
tags:[CSS,实现简单的轮播图]
---
###    用css3实现一个简单的轮播图

大家如果不用插件，如果js还学得不好，实现一个轮播图，那么就试试我这个cs3实现的轮播图把！哈哈哈



#### 用css3实现一个简单的slider轮播图
    ```bash
	<!DOCTYPE html>
	<html>
	<head>
		<meta charset="utf-8"/>
		<title></title>
		<style type="text/css">
			.box{
				width: 456px;
				height: 256px;
				margin: auto;
				overflow: hidden;
			}
			.bigdiv{
				width: 2400px;
				animation:run 20s linear infinite;

			}
			img{
				width: 19%;
			}
			@keyframes run{
        	   0%{
          		margin-left: 0px;
            	}
               5%{
            	 margin-left: 0px;
          	   }
          	   20%{
            	 margin-left: -456px;
         	    }
           	  25%{
             	margin-left: -456px;
           	  }
              40%{
             	margin-left: -912px;
            	 }
              45%{
             	margin-left: -912px;
              }
             60%{
             	margin-left: -1368px;
             }
             65%{
             	margin-left: -1368px;
             }
             80%{
             	margin-left: -1834px;
             }
             85%{
             	margin-left: -1834px;
             }
             100%{
             	margin-left: -2280px;-
             }

		}

	</style>
	</head>
	<body>
   	 	<div class="box">
    	 	  <div class="bigdiv">
    	   	 	      <img src="放置图片路径" 	alt="">   // 这里没有放置图片  大家可以自己添加
    	   	     	  <img src="放置图片路径" 	alt="">   // 这里没有放置图片  大家可以自己添加
    	   	      	  <img src="放置图片路径"		alt="">   // 这里没有放置图片  大家可以自己添加
    	   	      	  <img src="放置图片路径" 	alt="">   // 这里没有放置图片  大家可以自己添加
    	   	    	  <img src="放置图片路径" 	alt="">   // 这里没有放置图片  大家可以自己添加
    	  	 </div>
   		 </div>

	</body>
	</html>
	```
	
这样一个轮播图就出来了   大家看完如果觉得不错  就收藏一下⭐️⭐️⭐️⭐️⭐️

