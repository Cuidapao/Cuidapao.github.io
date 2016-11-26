---
title: 我们为什么要选择Vue
date: 2016-11-26 11:05:49
tags: [Vue]
---

### 本文阐述了雅各布·沙茨对于vue.js的观点，个人看完之后深有感触！

I had a great conversation with an interviewee a few weeks ago about how one should go about choosing a JavaScript framework.

He pointed out that when a major software company releases their secret sauce, there is going to be hype. Devs think to themselves, "That company writes JS differently than me, and they are prominent and successful. Is their way of writing JS better than mine? And therefore must I adopt it?"

Their secret sauce may be awesome, but don't assume awesomeness just because everyone else gets excited. You wouldn't copy and paste an answer from StackOverflow, without understanding it, so why copy and paste an entire framework?

Which brings me to our decision to use [<font style="color:blue">Vue.js</font>](https://vuejs.org/) at Github.

Simplicity and ease of use
Primarily what drew us to Vue.js is that it allows our team to easily write simple JavaScript. Getting started with Vue.js is extremely easy. Its source code is very readable, and the documentation is the only tutorial you'll ever need. You don't need external libraries. You can use it with or without jQuery. You won't need to install any plugins, though many are available. I like vanilla Vue.js personally, although I can reach for vue-resource when I need it. Hooking Vue.js up to existing code is very straightforward. There's no magic to Vue.js – it's Objects all the way down.

I talk to a lot of JavaScript devs and I find it really interesting that the ones who spend the most time in Angular tend to not know JavaScript nearly as well. I don't want that to be me or our devs. Why should we write "not JavaScript?"

I remember back when I was using Backbone, I had to really force myself to stay DRY, because it's really a blank canvas. Vue.js does not make large assumptions about much of anything either. It really only assumes that your data will change.

But Vue.js comes with the perfect balance of what it will do for you and what you need to do yourself. If Backbone was anarchy (no one in charge) and Angular is a dictatorship (the Angular team is in charge), I'd say Vue.js is like socialism: you are definitely in charge, but Vue.js is always within reach, a sturdy, but flexible safety net ready to help you keep your programming efficient and your DOM-inflicted suffering to a minimum.

To give you an idea of what I mean, here's a simple [<font style="color:blue">Codepen</font>](http://codepen.io/jschatz1/pen/dpQkpx):

	<div id="journal">
  		<input type="text" v-model="message">
  		<div>{{message}}</div>
	</div>
	
#

	var journal = new Vue({
  		el: '#journal',
  		data: {
    		message: 'Your first entry'
  		}
	});
	
	
If you've seen a few JavaScript libraries, it's not hard to understand everything in this example without any documentation. And usually with other frameworks, this is where the simplicity stops. You get nice, simple examples when you're "Getting started", but in reality things get complicated as soon as you to try to get your money's worth out of the framework. Not with Vue.js though – real-life usage seems to stay as simple as the docs.

And that is what we love about Vue.js: it's an elegant combination of structure and simplicity. The data for the view goes in an object called `data`, but the data can get there and look however you want. Any functions you'll write as callbacks for events go into a `methods` object, but they can do or return whatever you want. Vue.js just knows when things change and updates your views. And you write less code.

### Vue.js + GitLab === Less code

So what problem does this solve for GitLab? When I joined, all the JavaScript was written with JQuery. There is nothing wrong with that, except that it takes a lot more code to solve every problem. We knew we could do better. Once we started with Vue.js, we could immediately and consistently solve complex problems in much less time.

A simple, but practical example we're using in production: on a GitLab Issue, the issue's state is displayed as either `closed` or `open`. That simple value can change often and needs to be represented in several views. With JQuery, we had about 30 or so lines of code to propagate those changes, and those lines involved multiple classes and querying the DOM by hand.

In Vue.js, this now requires us to write one line of JavaScript. The only other code we add is in the HTML, and that's just a few additional attributes.

What [Evan You](https://twitter.com/youyuxi) knows is that creating a kick ass framework isn't just about writing great code. You need excellent documentation, a strong community helping each other learn, a supporting cast of libraries and plugins to help users solve the hard problems, and short feedback loops based on user feedback to keep the framework relevant. Vue.js is all of that, plus great code. That's why we're using it. What about you?


# 因为Vue更容易编写，更容易入门！


原文引自/[<font style="color:orange">作者</font>](https://about.gitlab.com/2016/10/20/why-we-chose-vue/)


	