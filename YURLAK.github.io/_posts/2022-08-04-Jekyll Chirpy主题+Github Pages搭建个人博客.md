---
layout: post
title:  "Jekyll Chirpy主题+Github Pages搭建个人博客"
date:   2022-08-04
categories: Jekyll 博客搭建
tags: [博客搭建]
---
>还没想好作为第一篇正式博客该写些什么，那就谈谈此网站是如何搭建的吧!

## 前言
在开始之前，请确保：

&emsp;&emsp;**1.你十分了解编程，这不用说了吧:-)**

&emsp;&emsp;**2.你能熟练使用git，对Github，网站开发有一定了解(markdown和html)。**

&emsp;&emsp;**3.配置好远程SSH key，不然是无法将本地博客传输到云端的。**

&emsp;&emsp;**4.你做事十分严谨，很少出现低级错误。**

&emsp;&emsp;**4.你自主探索能力强，网站开发尤其需要耐心。**

## Let's Start!
完全可以按照[Jekyll官网](https://jekyllrb.com/docs/)搭建博客。本文主要讲讲测试过程中会遇到的一些问题。

**Jekyll的默认主题是minima，我选择了适合编写个人BLOG的Chirpy主题。**
首先在Github创建一个名字为`<GH-username>.gihtub.io`的仓库，例如我的用户名是`YURLAK`，那就创建`YURLAK.github.io`，然后把仓库clone到本地。你还需要创建两个分支，一个为`main`，一个为`gh-pages`，这是构建页面默认的名称，当然你可以改成`master`之类的，但时要在`pages-deploy.yml.hook`文件里将`main`修改为新的分支名。

然后clone Chripy模版，虽然官方推荐的是使用[Chirpy Starter](https://www.github.com/cotes2020/chirpy-starter)模版，但相比模版还是[默认仓库](https://github.com/cotes2020/jekyll-theme-chirpy)更加全面。
```
git clone git@github.com:cotes2020/jekyll-theme-chirpy.git
```
clone好之后，cd到博客文件夹，对网站进行初始化
```
cd ~./tools #cd到文件夹
./init.sh #运行init.sh程序，初始化网站
```
然后编写自己的`_config.yml`文件，以下是我的`_config.yml`配置：
```
# The Site Configuration

# Import the theme
theme: jekyll-theme-chirpy

# Change the following value to '/PROJECT_NAME' ONLY IF your site type is GitHub Pages Project sites
# and doesn't have a custom domain.
baseurl: ''

# The language of the webpage › http://www.lingoes.net/en/translator/langcode.htm
# If it has the same name as one of the files in folder `_data/locales`, the layout language will also be changed,
# otherwise, the layout language will use the default value of 'en'.
lang: zh-CN

# Additional parameters for datetime localization, optional. › https://github.com/iamkun/dayjs/tree/dev/src/locale
prefer_datetime_locale:

# Change to your timezone › http://www.timezoneconverter.com/cgi-bin/findzone/findzone
timezone: Asia/Shanghai

# jekyll-seo-tag settings › https://github.com/jekyll/jekyll-seo-tag/blob/master/docs/usage.md
# ↓ --------------------------

title: YURLAK's Blog                          # the main title

tagline: 即使被全世界孤立，也要一个人笑得精彩！   # it will display as the sub-title

description: >-                        # used by seo meta and the atom feed
  YURLAK的个人Blog

# fill in the protocol & hostname for your site, e.g., 'https://username.github.io'
url: 'https://YURLAK.github.io'

github:
  username: YURLAK             # change to your github username
twitter:
  username: YURLAKSUN            # change to your twitter username
social:
  # Change to your full name.
  # It will be displayed as the default author of the posts and the copyright owner in the Footer
  name: YurlakSun
  email: yurlaksun@gmail.com            # change to your email address
  links:
    # The first element serves as the copyright owner's link
    - https://twitter.com/YURLAKSUN     # change to your twitter homepage
    - https://github.com/YURLAK       # change to your github homepage
    # Uncomment below to add more social links
    # - https://www.facebook.com/username
    # - https://www.linkedin.com/in/username

google_site_verification:               # fill in to your verification string

# ↑ --------------------------
# The end of `jekyll-seo-tag` settings

google_analytics:
  id:                 # fill in your Google Analytics ID
  # Google Analytics pageviews report settings
  pv:
    proxy_endpoint:   # fill in the Google Analytics superProxy endpoint of Google App Engine
    cache_path:       # the local PV cache data, friendly to visitors from GFW region

# Prefer color scheme setting.
#
# Note: Keep empty will follow the system prefer color by default,
# and there will be a toggle to switch the theme between dark and light
# on the bottom left of the sidebar.
#
# Available options:
#
#     light  - Use the light color scheme
#     dark   - Use the dark color scheme
#
theme_mode:   # [light|dark]

# The CDN endpoint for images.
# Notice that once it is assigned, the CDN url
# will be added to all image (site avatar & posts' images) paths starting with '/'
#
# e.g. 'https://cdn.com'
img_cdn:

# the avatar on sidebar, support local or CORS resources
avatar: assets/img/profilephoto.jpeg

# boolean type, the global switch for ToC in posts.
toc: true

comments:
  active: 'giscus'       # The global switch for posts comments, e.g., 'disqus'.  Keep it empty means disable
  # The active options are as follows:
  disqus:
    shortname:    # fill with the Disqus shortname. › https://help.disqus.com/en/articles/1717111-what-s-a-shortname
  # utterances settings › https://utteranc.es/
  utterances:
    repo:         # <gh-username>/<repo>
    issue_term:   # < url | pathname | title | ...>
  # Giscus options › https://giscus.app
  giscus:
    repo:            'YURLAK/YURLAK.github.io' # <gh-username>/<repo>
    repo_id:         'R_kgDOHtjxxA'
    category:        'Announcements'
    category_id:     'DIC_kwDOHtjxxM4CQhHC'
    mapping:         'pathname' # optional, default to 'pathname'
    input_position:  'top' # optional, default to 'bottom'
    lang:            'zh-CN' # optional, default to the value of `site.lang`

# Self-hosted static assets, optional › https://github.com/cotes2020/chirpy-static-assets
assets:
  self_host:
    enabled:      # boolean, keep empty means false
    # specify the Jekyll environment, empty means both
    # only works if `assets.self_host.enabled` is 'true'
    env:          # [development|production]

pwa:
  enabled: true   # the option for PWA feature

paginate: 5

# ------------ The following options are not recommended to be modified ------------------

kramdown:
  syntax_highlighter: rouge
  syntax_highlighter_opts:   # Rouge Options › https://github.com/jneen/rouge#full-options
    css_class: highlight
    # default_lang: console
    span:
      line_numbers: false
    block:
      line_numbers: true
      start_line: 1

collections:
  tabs:
    output: true
    sort_by: order

defaults:
  - scope:
      path: ''          # An empty string here means all files in the project
      type: posts
    values:
      layout: post
      comments: true    # Enable comments in posts.
      toc: true         # Display TOC column in posts.
      # DO NOT modify the following parameter unless you are confident enough
      # to update the code of all other post links in this project.
      permalink: /posts/:title/
  - scope:
      path: _drafts
    values:
      comments: false
  - scope:
      path: ''
      type: tabs             # see `site.collections`
    values:
      layout: page
      permalink: /:title/
  - scope:
      path: assets/img/favicons
    values:
      swcache: true
  - scope:
      path: assets/js/dist
    values:
      swcache: true

sass:
  style: compressed

compress_html:
  clippings: all
  comments: all
  endings: all
  profile: false
  blanklines: false
  ignore:
    envs: [development]

exclude:
  - '*.gem'
  - '*.gemspec'
  - tools
  - README.md
  - CHANGELOG.md
  - LICENSE
  - gulpfile.js
  - node_modules
  - package*.json

jekyll-archives:
  enabled: [categories, tags]
  layouts:
    category: category
    tag: tag
  permalinks:
    tag: /tags/:name/
    category: /categories/:name/
```
其中comments那一段我添加了[giscus评论](https://www.giscus.app/)，如果你想为自己的网站添加评论功能，那么详见我的另一篇文章。

## 编写博客

来到`_posts`文件夹，用`YYYY-MM-DD-title.md`对你的文章命名，例如`2022-07-28-Welcome.md`，注意个位数之前用0填充，否则无法识别你的文章。

现在编写你的博客头文件，例如：
```
---
layout: post
title:  "Jekyll Chirpy Theme+Github Pages搭建个人博客"
date:   2022-08-04
categories: Jekyll 博客搭建
tags: [博客搭建]
---
```

## 传输到远程仓库

保存好博客后在文件夹下打开终端：

`git add .`

`git commit -m "First commit"`

`git push --force`

其中`--force`是为了防止远程仓库与本地仓库不匹配的情况。

## 常见问题解答

**Q1:如何添加tag？例如你的“音乐”tag。**

**A1：在`_tabs`文件夹内新建`XXXX.md`文件，例如`donation.md`。注意文件的开头这样写：**

```
---
title: 打赏
icon: fas fa-info-circle
order: 5
---
```
文件命不做规定，其中title是你要显示tag的名字，order是tag的排列顺序，icon那行不用改。

**Q2:为什么Automatic Build->Setup Ruby->bundle install那一步会出现Jekyll exit code 16？**

**A2:是的，我也碰到过exit code 16的问题，但是现在仍未解决，唯一的方法是在本地网站文件夹下执行`bundle exec jekyll build`构建网站，然后将`_site`里的文件传输到远程仓库。**

# 持续更新！欢迎在下方留下你的评论:-)


