---
layout: post
title:  "TOOL: 如何使用Jekyll搭建个人博客？"
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

------

<h1> 如何使用Jekyll搭建个人博客 </h1>

**Jekyll** 是一个简单的博客形态的静态站点生产机器。它有一个模版目录，其中包含原始文本格式的文档，通过一个转换器（如Markdown）和我们的Liquid渲染器转化成一个完整的可发布的静态网站，你可以发布在任何你喜爱的服务器上。Jekyll 也可以运行在GitHub Page上，也就是说，你可以使用 GitHub 的服务来搭建你的项目页面、博客或者网站，而且是完全免费的。

------
<h2> 本地环境准备 </h2>

rubgem的安装可参考官网[Download RubyGems](https://rubygems.org/pages/download)
```
sudo apt update
sudo apt install ruby-full

# 添加 TUNA 源并移除默认源
gem sources --add https://mirrors.tuna.tsinghua.edu.cn/rubygems/ --remove https://rubygems.org/
# 列出已有源
gem sources -l
# 应该只有 TUNA 一个

#配置bundle的国内源 
bundle config mirror.https://rubygems.org https://mirrors.tuna.tsinghua.edu.cn/rubygems

最后 >> gem install jekyll, bundler
如果要安装指定版本 gem install bundler -v 2.4.12 #安装指定版本的bundler
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

------
<h2> 本地创建jekyll项目 </h2>

```
本地新建jekyll项目测试，命令行
>> jekyll new cyBlog　　 #如一直卡着ctrl+c即可
>> cd cyBlog
>> jekyll server
```
弹出本地测试地址，点击即可本地预览静态网站。
>> Server address: http://127.0.0.1:4000/

------
<h2> 项目推送到github上 </h2>

将Jekyll构建的静态网站 推到github上托管运行起来，个人博客网站就可以在公网访问。新建一个工程，设置好名称
和发布分支。也支持自定义域名，需要单独购买后再配置。

<div style="text-align: center;">  
    <img src="https://github.com/chenyangMl/chenyangml.github.io/raw/main/_posts/2023-04-19-welcome-to-jekyll/github_pages.jpg" style="width: 100%;margin-bottom: 20px;">  
</div>


<h2> Jekyll构建静态网站tips </h2>

- **categories**标签的作用

```
在每一个.markdown文档的开头可以配置，比如你做如下设置


---
layout: post
title:  "大语言模型——如何构建词表(Tokenizer)"
date:   2023-08-14 14:48:11 +0800
categories: jekyll update
---


构建网站后，会在 _site 中看到它自动的进行分类。其中jekyll是一级目录，update是二级目录。
所以categories可以用来很好管理文档大类别，大类别的子类可以用空格分开进行设置。

_site/jekyll/
└── update
    ├── 2023
    │   └── 08
    │       └── 14
    │           └── llama2.c.zh.html
    └── 2024
        └── 03
            └── 22
                └── keyword-spotting.html
```


<h2> 本地迁移静态网站 </h2>
如果本地工程目录project，从一个构建环境，移动到另外一个构建环境。

```
要使用更新版本的 Jekyll 和 Bundle 更新您的原始静态网站，您可以按照以下步骤进行操作：

1. 进入项目目录：打开命令行终端，并进入包含您原始静态网站的项目目录。 >> cd /project

2. 更新 Gemfile：检查项目目录中的 Gemfile 文件，确保其中的 Jekyll 和其他依赖项版本指定为您想要使用的最新版本。如果需要，您可以手动编辑 Gemfile 文件，将版本号更新为您想要使用的最新版本。

3. 更新依赖项：执行以下命令，使用最新的 Gemfile 更新项目的依赖项：

   bundle update

   这将根据您在 Gemfile 中指定的版本要求，更新项目所需的 Gem 包到最新版本。

4. 构建静态网站：执行以下命令，使用更新后的 Jekyll 和依赖项构建您的静态网站：

   bundle exec jekyll build

   这将使用最新版本的 Jekyll 和依赖项生成更新后的静态网站。

6. 部署或本地运行：根据您的需求，将更新后的静态网站部署到服务器上，或者在本地运行开发服务器进行预览：

   bundle exec jekyll serve

   这将启动 Jekyll 的开发服务器，并在本地主机上运行您的静态网站，以便您可以在浏览器中进行预览和测试。

```


<h2> 总结</h2>

1. MarkDown在这里也支持html的众多标签和样式，可以适当使用来改变显示风格。

2. 新增post和更新: 在_posts新增页面, 本地"jekyll server"查看网页效果. 确定效果一致后,再push到远程仓库

3. 域名绑定可参考 [Su3Says:域名绑定](https://zhuanlan.zhihu.com/p/671540743)