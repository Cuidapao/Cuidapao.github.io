---
title: gulp-入门教程
date: 2016-10-16 21:02:24
tags: [gulp,gulp入门教程详解]
---

# gulp入门教程详解
最近使用gulp自动化构建工具来开发网站，在此给大家分享一下使用gulp的一些使用教程。

## 一、 gulp安装
#### 1、安装nodejs
       1.1、说明：gulp是基于nodejs，理所当然需要安装nodejs

       1.2、安装：打开[<font style="blue">nodejs官网</font>](https://nodejs.org/en/)，点击硕大的绿色Download按钮，它会根据系统信息选择对应版本（.msi文件）。

#### 2、全局安装gulp
        2.1、说明：全局安装gulp目的是为了通过她执行gulp任务；

        2.2、安装：命令提示符执行npm install gulp -g；

        2.3、查看是否正确安装：命令提示符执行gulp -v，出现版本号即为正确安装。

#### 3、新建package.json文件
       3.1、说明：package.json是基于nodejs项目必不可少的配置文件，它是存放在项目根目录的普通json文件；

       3.2、执行命令提示符执行npm init进行手动安装

       3.3、安装完成后会在当前文件夹下看到如下package.json文件
       
![Mou icon](http://upload-images.jianshu.io/upload_images/3164024-76d2e9fa62a00632.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)       


#### package.json文件

       文件说明：

      "name":"test",//项目名称（必须）

      "version":"1.0.0",//项目版本（必须）

      "description":"This is for study gulp project !",//项目描述（必须）

      "devDependencies":{//项目依赖的插件

       3.4、查看package.json帮助文档，命令提示符执行npm help package.json

#### 4、安装本地gulp及其常用插件
      4.1、执行命令行npm install gulp 安装本地gulp

     4.2、安装gulp插件：以gulp—sass为例

     执行命令npm install gulp-sass即可安装gulp-sass插件，安装完成后即可在node_modules文件夹下查看到新安装的插件

#### 5、新建gulpfile.js文件（重要）
     5.1、说明：gulpfile.js是gulp项目的配置文件，是位于项目根目录的普通js文件（其实将gulpfile.js放入其他文件夹下亦可）

     5.2、gulpfile.js文件用法（以gulp-sass为例）

    	 5.2.1 导入工具包 require('node_modules里对应模块')

             var gulp=require('gulp')

             var less=require('gulp-less');

     	5.2.2 定义一个testLess任务（自定义任务名称）

	gulp.task('testLess',function(){

		gulp.src('src/less/index.less')     //该任务针对的文件

		.pipe(less())      //该任务调用的模块

		.pipe(gulp.dest('src/css'));     //将会在src/css下生成index.css

	});

	gulp.task("default",["watch"],function(){ //定义默认任务 并让gulp监视文件变化自动执行

	gulp.watch("sass/*.scss",["sass"]);       

	})
## 二、gulp常用插件

#### 1、gulp-uglify(JS压缩)

##### 安装：npm install --save-dev gulp-uglify

#### gulpfile.js代码如下：

	var gulp = require('gulp'),

	var rename= require('gulp-rename')

	var uglify= require("gulp-uglify");

	gulp.task('rename',function() {
	
		gulp.src('src/**/*.js')
		
		.pipe(uglify())//压缩
		
		.pipe(rename('index.min.js'))    
		
		.pipe(gulp.dest('build/js'));

	});

	gulp.task('default',['rename']);

	uglify= require("gulp-uglify");
	
#### 2、gulp-minify-html（html压缩）

#### 安装：npm install --save-dev gulp-minify-html

#### 代码如下：


	var gulp = require('gulp'),

	var minifyHtml= require("gulp-minify-html");

	gulp.task('minify-html',function() {
	
		gulp.src('src/**/*.html')//要压缩的html文件
		
		.pipe(minifyHtml())//压缩
		
		.pipe(gulp.dest('build'));

	});

	gulp.task('default',['minify-html']);

#### 3、 gulp-concat (js文件合并)
#### 安装：npm install --save-dev gulp-concat

#### 代码如下：


	var gulp = require('gulp'),

	concat= require("gulp-concat");

	gulp.task('concat',function() {
	
	 gulp.src('src/**/*.js')  //要合并的文件
	 
	 .pipe(concat('index.js'))  //合并匹配到的js文件并命名为 "index.js"
	 
	 .pipe(gulp.dest('build/js'));

	});

	gulp.task('default',['concat']);

#### 4、gulp-jada
#### 安装：npm install –save-dev  gulp-jada

#### Gulpfile.js代码如下：

	var gulp= require('gulp');

	var jade= require('gulp-jade');

	gulp.task("jade",function(){

	gulp.src("./jade/*.jade")
	
		.pipe(jade({
	
		pretty:true

	}))
	
		.pipe(gulp.dest("html/"))

	})
	
		gulp.task("default",["watch"],function(){
		
		gulp.watch("jade/*.jade",["jade"]);

	})
#### 4、gulp-less
#### 安装：npm install –save-dev  gulp-less

#### Gulpfile.js代码如下：


	var gulp = require('gulp'),

	var less= require("gulp-less");

	gulp.task('compile-less',function() {
	
	  gulp.src('src/less/*.less')
	 
	  .pipe(less())
	  
	  .pipe(gulp.dest('build/css'));

	});

	gulp.task('default',['compile-less']);

#### 5、gulp-sass
#### 安装：npm install –save-dev  gulp-sass

#### 代码如下：

	var gulp = require('gulp'),

	var sass= require("gulp-sass");

	gulp.task('compile-sass',function() {
		 gulp.src('src/sass/*.sass')
		 
		 .pipe(sass())
		 
		 .pipe(gulp.dest('build/css'));

	});

	gulp.task('default',['compile-sass']);

#### 6、gulp-imagemin（图片压缩）
#### 安装：npm install –save-dev  gulp-imagemin

#### 代码如下：


	var gulp = require('gulp');

	var imagemin = require('gulp-imagemin');
	
	gulp.task('uglify-imagemin',function() {returngulp.src('src/images/*')
	
		.pipe(imagemin())
	
		.pipe(gulp.dest('build/images'));

	});

	gulp.task('default',['uglify-imagemin']);

#### 7、理解Browserify

browserify是一个使用node支持的CommonJS模块标准 来为浏览器编译模块的，可以解决模块及依赖管理；

#### 先来看看使用gulp常见的问题：

使用 gulp 过程中，偶尔会遇到 Streaming not supported 这样的错误。这通常是因为常规流与 vinyl 文件对象流有差异、

gulp 插件默认使用了只支持 buffer （不支持 stream）的库。比如，不能把 Node 常规流直接传递给 gulp 及其插件。

比如如下代码：会抛出异常的；


	vargulp = require('gulp');

	varuglify = require('gulp-uglify');

	varconcat = require('gulp-concat');

	varrename = require('gulp-rename');varfs = require('fs');

	gulp.task('bundle',function() {returnfs.createReadStream('./test.txt')
	
		.pipe(uglify())
		
		.pipe(rename('bundle.min.js'))
		
		.pipe(gulp.dest('dist/'));

	});

	gulp.task('default',['bundle']);

文／原创/Dimple（github作者）
原文链接：https://cuidapao.github.io/
著作权归作者所有，转载请联系作者获得授权，并标注“github作者”。
