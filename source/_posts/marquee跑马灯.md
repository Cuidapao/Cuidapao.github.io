---
title: marquee跑马灯
date: 2016-12-26 15:36:37
tags:[HTML]
---

### <marquee>标签 HTML跑马灯

<marquee>标签，它是成对出现的标签，首标签<marquee>和尾标签</marquee>之间的内容就是滚动内容。<marquee>标签的属性主要有behavior、bgcolor、direction、width、height、hspace、vspace、loop、scrollamount、scrolldelay等，它们都是可选的。

### behavior属性 
behavior属性的参数值为alternate、scroll、slide中的一个，分别表示文字来回滚动、单方向循环滚动、只滚动一次，需要注意的是：如果在<marquee>标签中同时出现了direction和behavior属性，那么scroll和slide的滚动方向将依照direction属性中参数的设置。 
    <marquee behavior="alternate">我来回滚动</marquee> 
    <marquee behavior="scroll">我单方向循环滚动</marquee>
    <marquee behavior="scroll" direction="up" height="30">我改单方向向上循环滚动</marquee>            
    <marquee behavior="slide">我只滚动一次</marquee> 
    <marquee behavior="slide" direction="up">我改向上只滚动一次了</marquee> 
    
### bgcolor属性
文字滚动范围的背景颜色，参数值是16进制（形式：#AABBCC或#AA5566等）或预定义的颜色名字（如red、yellow、blue等）。如下所示：<marquee behavior=="slide" direction="left" bgcolor="red">我的背景色是红色的</marquee> 

### direction属性 
文字滚动的方向，属性的参数值有down、left、right、up共四个单一可选值，分别代表滚动方向向下、向左、向右、向上。如下所示： 
    <marquee direction="right">我向右滚动</marquee> 
    <marquee direction="right">我向下滚动</marquee> 

### width和height属性 
width和height属性的作用决定滚动文字在页面中的矩形范围大小。width属性用以规定矩形的宽度，height属性规定矩形的高度。这两个属性的参数值可以是数字或者百分数，数字表示矩形所占的（宽或高）像素点数，百分数表示矩形所占浏览器窗口的（宽或高）百分比。如下所示： 
    <marquee width="300" height="30" bgcolor="red">我宽300像素，高30像素。</marquee> 

### hspace和vspace属性 
这两个属性决定滚动矩形区域距周围的空白区域. 
    <marquee width="300" height="30" vspace="10" hspace="10" bgcolor="red">我矩形边缘水平和垂直距周围各10像素。</marquee> 
    <marquee width="300" height="30" vspace="50" hspace="50" bgcolor="red">我矩形边缘水平和垂直距周围各50像素。</marquee> 

### loop属性 
loop属性决定滚动文字的滚动次数，缺省是无限循环。参数值可以是任意的正整数，如果设置参数值为-1或infinite时将无限循环。如下所示： 
    <marquee loop="2">我滚动2次。</marquee> 
    <marquee loop="infinite">我无限循环滚动。</marquee> 
    <marquee loop="-1">我无限循环滚动。</marquee> 

### scrollamount和scrolldelay属性 
这两个属性决定文字滚动的速度（scrollamount）和延时（scrolldelay），参数值都是正整数。如下所示： 
    <marquee scrollamount="100">我速度很快.</marquee> 
    <marquee scrollamount="50">我慢了些。</marquee> 
    <marquee scrolldelay="30">我小步前进。</marquee> 
    <marquee scrolldelay="1000" scrollamount="100">我大步前进。</marquee> 
    
### align属性
这个属性决定滚动文字位于距形内边框的上下左右位置。您也可以将<marquee>和</marquee>之间的内容替换为图像或其它对象等功能。

### 参数 
　　direction 表示滚动的方向，值可以是left，right，up，down，默认为left 
　　behavior 表示滚动的方式，值可以是scroll（连续滚动）slide（滑动一次）alternate（来回滚动） 
　　loop 表示循环的次数，值是正整数，默认为无限循环 
　　scrollamount 表示运动速度，值是正整数，默认为6 
　　scrolldelay 表示停顿时间，值是正整数，默认为0，单位是毫秒 
　　align 表示元素的垂直对齐方式，值可以是top，middle，bottom，默认为middle 
　　bgcolor 表示运动区域的背景色，值是16进制的RGB颜色，默认为白色 
　　height、width 表示运动区域的高度和宽度，值是正整数（单位是像素）或百分数，默认width=100% height为标签内元素的高度。 
　　hspace、vspace 表示元素到区域边界的水平距离和垂直距离，值是正整数，单位是像素。 
　　onmouseover=this.stop() onmouseout=this.start() 表示当鼠标以上区域的时候滚动停止，当鼠标移开的时候又继续滚动。 

### 注释 
　　MARQUEE 元素的默认宽度与其父元素的宽度相等。如果 MARQUEE 位于没有指定宽度的 TD 内，你就需要明确设置 MARQUEE 的宽度。如果 MARQUEE 和 TD 的宽度都没有指定，那么滚动字幕就将限定于 1 个像素宽。
　　要创建垂直滚动的字幕，请将其 scrollLeft 属性设定为 0。要创建水平滚动的字幕，请将其 scrollTop 属性设定为 0，这将覆盖任何脚本设置。 
　　scrollLeft 和 scrollTop 属性当字幕滚动时为只读。当不处于滚动状态时，scrollLeft 对于设置为水平滚动的字幕来说为可读写，scrollTop 对于设置为垂直滚动的字幕来说为可读写。 
　　此元素在 Microsoft® Internet Explorer 3.0 的 HTML 中可用，在 Internet Explorer 4.0 的脚本中可用。 
　　此元素是块元素。 
　　此元素需要关闭标签。 

### 示例 
　　下面的例子使用了 MARQUEE 元素创建了由左向右的滚动字幕，移动速度为每 200 毫秒 10 像素。 
　　<MARQUEE DIRECTION=RIGHT BEHAVIOR=SCROLL SCROLLAMOUNT=10 SCROLLDELAY=200>这是一个滚动字幕。</MARQUEE> 
　　下面的例子显示了 marquee 元素的 scrollLeft 和 scrollTop 属性的一些用途。 
　　<MARQUEE id=m1 direction=right style="border-width:2px;border-style:solid;" width=200 height=200>向右</MARQUEE> 
　　<!-- 单击此按钮可在字幕滚动时读取 scrollLeft 和 scrollTop 属性的值。 --> 
　　<BUTTON onclick="alert('scrollLeft: ' + m1.scrollLeft + ' scrollRight: ' + m1.scrollTop)">读取</BUTTON> 
　　<!-- 当字幕停止时，你可以设置水平字幕的 scrollLeft，或者设置垂直字幕的 scrollTop。 --> 
　　<BUTTON onclick="m1.stop();m1.scrollLeft = 190;">停止并设置 scrollLeft=190</BUTTON> 
　　<BUTTON onclick="m1.start();">开始</BUTTON> 

