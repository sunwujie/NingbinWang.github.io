# cnskyline
各位看官，请看[cnskline](http://ningbinwang.github.io/cnskyline/)，我的个人博客。

博客来自于黄玄的[主题](https://github.com/Huxpro/huxpro.github.io)，他还提供了基础版，我就是在这个基础上进行修改的。

#修改笔记
1、一定要注意_config.yml这个文件，在这个文件中将会定义你整个网页中所用的东西。

首先，你得自己先将模版中各类信息换成自己的所属信息。

```
# Site settings
title: Skyline
SEOTitle: 天际线 | skyline
header-img: img/home-bg.jpg #首页背景
email: 188101696@qq.com
description: "摄影，代码，前端，安卓，ios都是我的兴趣哦"
keyword: "工程师"
url: "http://ningbinwang.github.io"              # your host, for absolute URL
baseurl: ""         # for example, '/blog' if your blog hosted on 'host/blog' 这里就是设置你的博客路径的地方，一般申请的io不需要放开此项用＃号注释掉

＃这里是一些账户
# SNS settings
RSS: false
weibo_username:     samuelwnb
zhihu_username:     cnskeyline
github_username:    NingbinWang
facebook_username:  samuel.wnb
jianshu_username:   49e85998a845/timeline



# Build settings
# from 2016, 'pygments' is unsupported on GitHub Pages. Use 'rouge' for highlighting instead.
highlighter: rouge
permalink: pretty
paginate: 10
exclude: ["less","node_modules","Gruntfile.js","package.json","README.md"]
anchorjs: true                          # if you want to customize anchor. check out line:181 of `post.html`



# Gems
# from PR#40, to support local preview for Jekyll 3.0
gems: [jekyll-paginate]



# Markdown settings
# replace redcarpet to kramdown,
# although redcarpet can auto highlight code, the lack of header-id make the catalog impossible, so I switch to kramdown
# document: http://jekyllrb.com/docs/configuration/#kramdown
markdown: kramdown
kramdown:
  input: GFM                            # use Github Flavored Markdown !important



# Disqus settings
#disqus_username: _your_disqus_short_name_

# Duoshuo settings
duoshuo_username: cnskyline
# Share component is depend on Comment so we can NOT use share only.
duoshuo_share: true                     # set to false if you want to use Comment without Sharing




# Analytics settings
# Baidu Analytics
ba_track_id: b44cf755939a409143a63873f969cd7c
# Google Analytics
ga_track_id: 'UA-65717037-2'            # Format: UA-xxxxxx-xx
ga_domain: ningbinwang.github.io/cnskyline/



# Sidebar settings
sidebar: true                           # whether or not using Sidebar.
sidebar-about-description:  "BSP,Android,前端设计爱好者，硬件设计爱好者"
sidebar-avatar: /cnskyline/img/avatar-alex.png   # use absolute URL, seeing it's used in both `/` and `/about/`



# Featured Tags
featured-tags: true                     # whether or not using Feature-Tags
featured-condition-size: 1              # A tag will be featured if the size of it is more than this condition value



# Friends
friends: [
    {
        title: " My CSDN Blog",
        href: "http://blog.csdn.net/u013983194"
    },{
        title: "My Cnblog",
        href: "http://www.cnblogs.com/samuelwnb/"
    }
]
```

##修改aboot.html
将自己的谷歌统计与多说的在这里做相关的注册。

```
	---
	layout: page
	title: "About"
	description: "Hello World"
	header-img: "img/about-bg.jpg"
	---
<!-- Language Selector -->
<select onchange= "onLanChange(this.options[this.options.selectedIndex].value)">
    <option value="0" selected> 中文 Chinese </option>
    <option value="1"> 英语 English </option>
</select>

<!-- Chinese Version -->
<div class="zh post-container">
    <blockquote>
     <p>看看世界，听听风雨</br>生命就是这么奇妙</p>
    </blockquote>
    <p>大家好，我是<strong>alex wang</strong>，Android BSP工程师,前端爱好者，现在任职于<a herf="http://www.asus.com.cn/">华硕科技（苏州）有限公司</a>。</p>
</div>

<!-- English Version -->
<div class="en post-container">
    <blockquote>
        <p>Looking for the World，Listening to the life</br>life is so beautiful</p>  
    </blockquote>
    <p>Hey,My name is <strong>alex wang</strong>，Android BSP Engineer,Web lover.I am working in <a herf="http://www.asus.com.cn/"> ASUS Technology (Suzhou) Co., Ltd</a></p>
</div>

<!-- Handle Language Change -->
<script type="text/javascript">
    var $zh = document.querySelector(".zh");
    var $en = document.querySelector(".en");
    function onLanChange(index){
        if(index == 0){
            $zh.style.display = "block";
            $en.style.display = "none";
        }else{
            $en.style.display = "block";
            $zh.style.display = "none";
        }
    }
    onLanChange(0);
</script>



{% if site.duoshuo_username %}
<!-- 多说评论框 start -->
<div class="comment">
    <div class="ds-thread"
        data-thread-key="{{site.ga_domain}}/about"
        data-title="{{page.title}}"
        data-url="{{site.url}}/about/">
    </div>
</div>
<!-- 多说评论框 end -->

<!-- Duoshuo hacking -->
<input id="dsUser" type="hidden" value="{{site.duoshuo_username}}"  />

<!-- 多说公共JS代码 start (一个网页只需插入一次) -->
<script type="text/javascript">
    // dynamic User hacking by Hux
    var _user = document.getElementById('dsUser').value;
    // duoshuo comment query.
    var duoshuoQuery = {short_name: _user };
    (function() {
        var ds = document.createElement('script');
        ds.type = 'text/javascript';ds.async = true;
        ds.src = (document.location.protocol == 'https:' ? 'https:' : 'http:') + '//static.duoshuo.com/embed.js';
        ds.charset = 'UTF-8';
        (document.getElementsByTagName('head')[0]
         || document.getElementsByTagName('body')[0]).appendChild(ds);
    })();
</script>
<!-- 多说公共JS代码 end -->
{% endif %}


{% if site.disqus_username %}
<!-- disqus 评论框 start -->
<div class="comment">
    <div id="disqus_thread" class="disqus-thread">

    </div>
</div>
<!-- disqus 评论框 end -->

<!-- disqus 公共JS代码 start (一个网页只需插入一次) -->
<script type="text/javascript">
    /* * * CONFIGURATION VARIABLES * * */
    var disqus_shortname = "{{site.disqus_username}}";
    var disqus_identifier = "{{site.disqus_username}}/{{page.url}}";
    var disqus_url = "{{site.url}}{{page.url}}";

    (function() {
        var dsq = document.createElement('script'); dsq.type = 'text/javascript'; dsq.async = true;
        dsq.src = '//' + disqus_shortname + '.disqus.com/embed.js';
        (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(dsq);
    })();
</script>
<!-- disqus 公共JS代码 end -->
{% endif %}
```
