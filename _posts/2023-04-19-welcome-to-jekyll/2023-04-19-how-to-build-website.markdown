---
layout: post
title:  "怎样使用Jekyll搭建个人网站？"
date:   2023-04-19 14:45:13 +0800
categories: tools
---

<style>  
  /* 可选样式，为名言添加一些基本的样式 */  
  .quote {  
    font-family: 'SimSun', serif; /* 使用常见的中文字体 */  
    font-size: 18px;  
    text-align: justify; /* 两端对齐 */  
    margin: 20px 0; /* 上下外边距 */  
    padding: 10px; /* 内边距 */  
    border: 1px solid #ccc; /* 边框 */  
    border-radius: 5px; /* 边框圆角 */  
    background-color: #f5f5f5; /* 背景色 */  
  }  
  /* 突出显示的样式 */  
  .highlight {  
    background-color: #E6E6FA; /* 黄色背景 */  
    color: black; /* 黑色文本 */  
  }  
</style>  
  
<div class="quote">  
  <p>积土成山，风雨兴焉；积水成渊，蛟龙生焉；积善成德，而神明自得，圣心备焉。</p>  
  <p>故不积跬步，无以至千里；不积小流，无以成江海。</p>  
  <p>骐骥一跃，不能十步；驽马十驾，功在不舍。</p>  
  <p>锲而舍之，朽木不折；锲而不舍，金石可镂。</p>  
  <p>蚓无爪牙之利，筋骨之强，上食埃土，下饮黄泉，<mark class="highlight">用心一也</mark>。</p>  
  <p>蟹六跪而二螯，非蛇鳝之穴无可寄托者，<mark class="highlight">用心躁也</mark>。</p>  
</div>  

<p>上承先贤之志，积跬步至千里，积小流成江海，用心专一。</p>  

<h1> 如何使用Jekyll搭建个人网站 </h1>

**Jekyll** 是一个简单的博客形态的静态站点生产机器。它有一个模版目录，其中包含原始文本格式的文档，通过一个转换器（如Markdown）和我们的Liquid渲染器转化成一个完整的可发布的静态网站，你可以发布在任何你喜爱的服务器上。Jekyll 也可以运行在GitHub Page上，也就是说，你可以使用 GitHub 的服务来搭建你的项目页面、博客或者网站，而且是完全免费的。

<h2> 本地环境准备 </h2>

rubgem的安装可参考官网[Download RubyGems](https://rubygems.org/pages/download)
```
gcc, g++ >=5.4.0
sudo add-apt-repository ppa:brightbox/ruby-ng
sudo apt-get update
sudo apt-get install ruby2.6 ruby2.6-dev
最后 >> gem install jekyll, bundler
```

最后确认下各依赖软件版本
```text
cat /etc/issue | Ubuntu 16.04.7 LTS \n \l
gem -v      | 3.4.12
gcc -v      | 5.4.0
g++ -v      | 5.4.0
ruby -v     | ruby 2.6.6p146 (2020-03-31 revision 67876) [x86_64-linux-gnu]
bundler -v　 | bundler-2.4.12
jekyll -v　　 |　　jekyll 4.3.2
```

<h2> 本地创建jekyll项目 </h2>

```
本地新建jekyll项目测试，命令行
>> jekyll new cyBlog　　 #如一直卡着ctrl+c即可
>> cd cyBlog
>> jekyll server
```
弹出本地测试地址，点击即可本地预览静态网站。
>> Server address: http://127.0.0.1:4000/

<h2> 项目推送到github上 </h2>
将Jekyll构建的静态网站 推到github上托管运行起来，个人博客网站就可以在公网访问。新建一个工程，设置好名称
和发布分支。也支持自定义域名，需要单独购买后再配置。

<div style="text-align: center;">  
    <img src="{{site.baseurl}}/_posts/2023-04-19-welcome-to-jekyll/github_pages.jpg" style="display: block;">  
</div>



<h2> 总结</h2>

1. MarkDown在这里也支持html的众多标签和样式，可以适当使用来改变显示风格。

2. 新增post和更新: 在_posts新增页面, 本地"jekyll server"查看网页效果. 确定效果一致后,再push到远程仓库

3. 域名绑定可参考 [Su3Says:域名绑定](https://zhuanlan.zhihu.com/p/671540743)