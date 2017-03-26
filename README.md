给前端小牛参考的git配置搭建博客上传文件等等功能的教程，大牛请绕道，小牛们共勉！


一、安装 hexo
首先打开 git-bash，进入到一个合适的存放 hexo 博客的目录，直接运行
http://www.xp510.com/xiazai/Application/other/28541.html
使用npm先安装node
npm install -g hexo-cli


二、搭建博客
安装完 hexo 之后，还要运行下面三条命令

注： <folder>是你自己的文件夹名，比如博客的文件夹名称是blog,那么命令是： hexo init blog   ->   cd blog   ->  npm install
这个过程可能要花费一点时间
hexo init <folder>

cd <folder>

npm install （自动安装所需的各种插件）

这样就把默认主题的 hexo 博客安装好了，这时候再运行

hexo s

就能够建立起一个本地的服务器，默认端口是4000，打开浏览器 http://localhost:4000 就能访问属于你自己的博客了。打开是默认主题

三、切换主题
hexo 官方提供了大量的优秀主题可以更换，当然也可以选择自己去写一个主题出来。例如http://theme-next.iissnan.com/ Next 主题
1.主题代码拷贝
主题的拷贝也是直接使用 git 即可，首先进入到你博客的根目录blog，再打开 git-bash 运行
git clone https://github.com/iissnan/hexo-theme-next themes/next

2.  启用主题
在博客根目录下找到 _config.yml 文件，找到里面的 theme，改为
3.
theme: next
4.
这时再运行一次 hexo s ，看看主题有没有生效吧。


四、发布博客到 coding
1.配置hexo deploy
hexo 提供了一个部署命令 hexo deploy，首先需要安装一下 hexo-deployer-git插件

npm install hexo-deployer-git --save然后配置一下_config.yml 文件：
1. 修改网站相关信息
# Site
title: Shally
subtitle: 码农的日常
description: start from zero
author: yangfang: zh-CN
timezone: Asia/Shanxi
language和timezone都是有输入规范,自己了解
2. 配置统一资源定位符（个人域名）

url: http://inerdstack.com
对于root（根目录）、permalink（永久链接）、permalink_defaults（默认永久链接）等其他信息保持默认。
3.配置部署

deploy:
  type: git
  repo: https://github.com/yangfang7/yangfang7.github.io.git
  branch: master
2.预览效果
在 coding 上建立一个私人仓库，找到代码的 coding 地址，填好上面的配置，然后直接执行
hexo deploy
不出意外的话会让你填写 coding 的用户名和密码完成上传操作。如果你有配置 ssh 方式的话就更加方便了。
这个时候再到 coding 对应的项目里面打开 pages 服务，根据 coding 建议，因为不是 jekyll 项目，所以需要再新建一个.nojekyll 文件（空文件就行，其实不建立也行），等上一会就能够访问自己的博客了。
配置文件示例: 
# Hexo Configuration
## Docs: https://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/

# Site
title: wally
subtitle: 杨阳洋的博客
description: 我的地盘听我的
author: 平通
language: zh-Hans
avatar: /images/avatar.jpg
timezone:

# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: http://yangfang7.github.io/
root: /
permalink: :year/:month/:day/:title/
permalink_defaults:

# Directory
source_dir: source
public_dir: public
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code
i18n_dir: :lang
skip_render:

# Writing
new_post_name: :title.md # File name of new posts
default_layout: post
titlecase: true # Transform title into titlecase
external_link: true # Open external links in new tab
filename_case: 0
render_drafts: false
post_asset_folder: false
relative_link: false
future: true
highlight:
  enable: true
  line_number: true
  auto_detect: false
  tab_replace:

# Category & Tag
default_category: uncategorized
category_map:
tag_map:

# Date / Time format
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: MM-DD-YYYY
time_format: HH:mm:ss

# Pagination
## Set per_page to 0 to disable pagination
per_page: 10
pagination_dir: page

# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
# theme: landscape
theme: next
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repository: https://git.coding.net/mongos/mongos.git
  branch: coding-pages


NEXT主题完整配置文件示例:
# ---------------------------------------------------------------
# Site Information Settings
# ---------------------------------------------------------------

# Put your favicon.ico into `hexo-site/source/` directory.
favicon: /favicon.ico

# Set default keywords (Use a comma to separate)
keywords: "平通，前端"

# Set rss to false to disable feed link.
# Leave rss as empty to use site's feed link.
# Set rss to specific value if you have burned your feed already.
rss:

# Specify the date when the site was setup
#since: 2015




# ---------------------------------------------------------------
# Menu Settings
# ---------------------------------------------------------------

# When running the site in a subdirectory (e.g. domain.tld/blog), remove the leading slash (/archives -> archives)
menu:
  home: /
  # categories: /categories
  about: /about
  archives: /archives
  # tags: /tags
  commonweal: /404.html


# Enable/Disable menu icons.
# Icon Mapping:
#   Map a menu item to a specific FontAwesome icon name.
#   Key is the name of menu item and value is the name of FontAwsome icon. Key is case-senstive.
#   When an question mask icon presenting up means that the item has no mapping icon.
menu_icons:
  enable: true
  #KeyMapsToMenuItemKey: NameOfTheIconFromFontAwesome
  home: home
  about: user
  categories: th
  tags: tags
  archives: archive
  commonweal: heartbeat




# ---------------------------------------------------------------
# Scheme Settings
# ---------------------------------------------------------------

# Schemes
#scheme: Muse
scheme: Mist
#scheme: Pisces


# ---------------------------------------------------------------
# Font Settings
# - Find fonts on Google Fonts (https://www.google.com/fonts)
# - All fonts set here will have the following styles:
#     light, light italic, normal, normal intalic, bold, bold italic
# - Be aware that setting too much fonts will cause site running slowly
# - Introduce in 5.0.1
# ---------------------------------------------------------------
font:
  enable: true

  # Uri of fonts host. E.g. //fonts.googleapis.com (Default)
  host:

  # Global font settings used on <body> element.
  global:
    # external: true will load this font family from host.
    external: true
    family: monaco,"PingFang SC",sans-serif,"Microsoft YaHei"

  # Font settings for Headlines (h1, h2, h3, h4, h5, h6)
  # Fallback to `global` font settings.
  headings:
    external: true
    family:

  # Font settings for posts
  # Fallback to `global` font settings.
  posts:
    external: true
    family:

  # Font settings for Logo
  # Fallback to `global` font settings.
  # The `size` option use `px` as unit
  logo:
    external: true
    family: Lobster Two
    size: 24

  # Font settings for <code> and code blocks.
  codes:
    external: true
    family: monaco,consolas, Menlo,
    size: 16




# ---------------------------------------------------------------
# Sidebar Settings
# ---------------------------------------------------------------


# Social Links
# Key is the link label showing to end users.
# Value is the target link (E.g. GitHub: https://github.com/iissnan)
social:
  GitHub: https://github.com/yangfang7
  微博: http://weibo.com/
  知乎: https://www.zhihu.com

# Social Links Icons
# Icon Mapping:
#   Map a menu item to a specific FontAwesome icon name.
#   Key is the name of the item and value is the name of FontAwsome icon. Key is case-senstive.
#   When an globe mask icon presenting up means that the item has no mapping icon.
social_icons:
  enable: true
  # Icon Mappings.
  # KeyMapsToSocalItemKey: NameOfTheIconFromFontAwesome
  GitHub: github
  微博: weibo
  知乎: weibo


# Sidebar Avatar
# in theme directory(source/images): /images/avatar.jpg
# in site  directory(source/uploads): /uploads/avatar.jpg
#avatar:


# Table Of Contents in the Sidebar
toc:
  enable: true

  # Automatically add list number to toc.
  number: true


# Creative Commons 4.0 International License.
# http://creativecommons.org/
# Available: by | by-nc | by-nc-nd | by-nc-sa | by-nd | by-sa | zero
#creative_commons: by-nc-sa
#creative_commons:


sidebar:
  # Sidebar Position, available value: left | right
  position: left
  #position: right

  # Sidebar Display, available value:
  #  - post    expand on posts automatically. Default.
  #  - always  expand for all pages automatically
  #  - hide    expand only when click on the sidebar toggle icon.
  #  - remove  Totally remove sidebar including sidebar toggler.
  display: post
  #display: always
  #display: hide
  #display: remove


# Blogrolls
links_title: Links
#links_layout: block
#links_layout: inline
links:
  刘洋: http://www.lyblog.net/
  廖雪峰: http://www.liaoxuefeng.com/
  阮一峰: http://www.ruanyifeng.com/blog/
  FED: http://taobaofed.org/
  FEX: http://fex.baidu.com/
  奇舞团: http://www.75team.com/
  AlloyTeam: http://www.alloyteam.com/
  CDC: http://cdc.tencent.com/
  ISUX: http://isux.tencent.com/
  TGideas: http://tgideas.qq.com/
  Nodejs API: http://nodeapi.ucdok.com/

# ---------------------------------------------------------------
# Misc Theme Settings
# ---------------------------------------------------------------

# Custom Logo.
# !!Only available for Default Scheme currently.
# Options:
#   enabled: [true/false] - Replace with specific image
#   image: url-of-image   - Images's url
custom_logo:
  enabled: true
  image: https://coding.net/static/project_icon/scenery-15.png


# Code Highlight theme
# Available value:
#    normal | night | night eighties | night blue | night bright
# https://github.com/chriskempson/tomorrow-theme
highlight_theme: night eighties


# Automatically scroll page to section which is under <!-- more --> mark.
scroll_to_more: true


# Automatically Excerpt. Not recommand.
# Please use <!-- more --> in the post to control excerpt accurately.
auto_excerpt:
  enable: false
  length: 150


# Wechat Subscriber
#wechat_subscriber:
  #enabled: true
  #qcode: /path/to/your/wechatqcode ex. /uploads/wechat-qcode.jpg
  #description: ex. subscribe to my blog by scanning my public wechat account

# 打赏
reward_comment: 坚持原创技术分享，您的支持将鼓励我继续创作！
wechatpay: /uploads/wxpay.png
alipay: /uploads/alipay.jpg


# ---------------------------------------------------------------
# Third Party Services Settings
# ---------------------------------------------------------------

# MathJax Support
mathjax:
  enable: false
  cdn: //cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML


# Swiftype Search API Key
#swiftype_key:

# Baidu Analytics ID
#baidu_analytics:

# Duoshuo ShortName
duoshuo_shortname: "yfang"

# Disqus
#disqus_shortname:

# Baidu Share
# Available value:
#    button | slide
#baidushare:
##  type: button

# Share
#jiathis:
#add_this_id:

# Share
duoshuo_share: true

# Google Webmaster tools verification setting
# See: https://www.google.com/webmasters/
#google_site_verification:


# Google Analytics
#google_analytics:

# CNZZ count
#cnzz_siteid:


# Make duoshuo show UA
# user_id must NOT be null when admin_enable is true!
# you can visit http://dev.duoshuo.com get duoshuo user id.
duoshuo_info:
  ua_enable: true
  admin_enable: true
  user_id: 0
  admin_nickname: "yfang"


# Facebook SDK Support.
# https://github.com/iissnan/hexo-theme-next/pull/410
facebook_sdk:
  enable: false
  app_id:       #<app_id>
  fb_admin:     #<user_id>
  like_button:  #true
  webmaster:    #true

search:
  path: search.xml
  field: post
  format: html
  limit: 10000

# Show number of visitors to each article.
# You can visit https://leancloud.cn get AppID and AppKey.
leancloud_visitors:
  enable: true
  app_id: "icBW7OnYytaPAOf6yjFE7a1M-gzGzoHsz"
  app_key: "uclxPv0g8Ebku9LNqoD5XX1B"

# Show PV/UV of the website/page with busuanzi.
# Get more information on http://ibruce.info/2015/04/04/busuanzi/
busuanzi_count:
  # count values only if the other configs are false
  enable: false
  # custom uv span for the whole site
  site_uv: true
  site_uv_header: <i class="fa fa-user"></i>
  site_uv_footer:
  # custom pv span for the whole site
  site_pv: true
  site_pv_header: <i class="fa fa-eye"></i>
  site_pv_footer:
  # custom pv span for one page only
  page_pv: true
  page_pv_header: <i class="fa fa-file-o"></i>
  page_pv_footer:

# Tencent analytics ID
tencent_analytics: ""

# Enable baidu push so that the blog will push the url to baidu automatically which is very helpful for SEO
baidu_push: true



#! ---------------------------------------------------------------
#! DO NOT EDIT THE FOLLOWING SETTINGS
#! UNLESS YOU KNOW WHAT YOU ARE DOING
#! ---------------------------------------------------------------

# Motion
use_motion: true

# Fancybox
fancybox: true

# since
since: 2013

# Wechat Subscriber
wechat_subscriber:
  enabled: true
  qcode: /uploads/wechat-qcode.jpg
  description: 扫一扫,关注我！


# Script Vendors.
# Set a CDN address for the vendor you want to customize.
# For example
#    jquery: https://ajax.googleapis.com/ajax/libs/jquery/2.2.0/jquery.min.js
# Be aware that you should use the same version as internal ones to avoid potential problems.
vendors:
  # Internal path prefix. Please do not edit it.
  _internal: vendors

  # Internal version: 2.1.3
  jquery:

  # Internal version: 2.1.5
  # http://fancyapps.com/fancybox/
  fancybox:
  fancybox_css:

  # Internal version: 1.0.6
  # https://github.com/ftlabs/fastclick
  fastclick:

  # Internal version: 1.9.7
  # https://github.com/tuupola/jquery_lazyload
  lazyload:

  # Internal version: 1.2.1
  # http://VelocityJS.org
  velocity:

  # Internal version: 1.2.1
  # http://VelocityJS.org
  velocity_ui:

  # Internal version: 0.7.9
  # https://faisalman.github.io/ua-parser-js/
  ua_parser:

  # Internal version: 4.4.0
  # http://fontawesome.io/
  fontawesome:


# Assets
css: css
js: js
images: images

# Theme version
version: 5.0.1




Ctrl+c —终止命令
Git diff --cached 暂存区的不同
Git diff checkout -- index.html 撤销暂存区修改文件

GITHUB指令
Welcome to Portable Git (version ghfw)


Run 'git help git' to display the help index.
Run 'git help <command>' to display help for specific commands.

Administrator@OPN9JS0KRUYCSIG ~/Documents/GitHub
$ git commit -m"add index"
fatal: Not a git repository (or any of the parent directories): .git

Administrator@OPN9JS0KRUYCSIG ~/Documents/GitHub
$ git push origin master
fatal: Not a git repository (or any of the parent directories): .git

Administrator@OPN9JS0KRUYCSIG ~/Documents/GitHub
$ git add .
fatal: Not a git repository (or any of the parent directories): .git

Administrator@OPN9JS0KRUYCSIG ~/Documents/GitHub
$ git commit -m"已经修改"
fatal: Not a git repository (or any of the parent directories): .git

Administrator@OPN9JS0KRUYCSIG ~/Documents/GitHub
$ git push origin master
fatal: Not a git repository (or any of the parent directories): .git

Administrator@OPN9JS0KRUYCSIG ~/Documents/GitHub
$ git clone https://github.com/bai1994/back.github.io.git
Cloning into 'back.github.io'...
remote: Counting objects: 4, done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 4 (delta 0), reused 4 (delta 0), pack-reused 0
Unpacking objects: 100% (4/4), done.
Checking connectivity... done.

Administrator@OPN9JS0KRUYCSIG ~/Documents/GitHub
$ cd f:

Administrator@OPN9JS0KRUYCSIG /f
$ git clone https://github.com/bai1994/back.github.io.git
fatal: destination path 'back.github.io' already exists and is not an empty dire
ctory.

Administrator@OPN9JS0KRUYCSIG /f
$ git add .
fatal: Not a git repository (or any of the parent directories): .git

Administrator@OPN9JS0KRUYCSIG /f
$ cd back.github.io

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ git add .

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ git commit -m"已经修改"
[master 2465705] 已经修改
 1 file changed, 1 insertion(+)

Warning: Your console font probably doesn't support Unicode. If you experience s
trange characters in the output, consider switching to a TrueType font such as L
ucida Console!

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ git push origin master
Counting objects: 5, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 358 bytes | 0 bytes/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local objects.
To https://github.com/bai1994/back.github.io.git
   09f2df6..2465705  master -> master

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ git diff

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ git diff

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ git add index.html

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ git diff

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ git diff --cashed
error: invalid option: --cashed

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ git diff --cached

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ git diff --cached

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ git checkout -- index.html

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ git add .

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   text.txt


Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ git re -f text.txt
git: 're' is not a git command. See 'git --help'.

Did you mean one of these?
        rebase
        reset
        grep
        rm

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ rm
rm: too few arguments
Try `rm --help' for more information.

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ rm'text.txt'
bash.exe": rmtext.txt: command not found

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ git rm -f text.txt
rm 'text.txt'

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ git reset -- hard HEAD^

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ git reset --hard HEAD^
HEAD is now at 09f2df6 jq文件

Warning: Your console font probably doesn't support Unicode. If you experience s
trange characters in the output, consider switching to a TrueType font such as L
ucida Console!

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ git add .

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ status
bash.exe": status: command not found

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ git status
On branch master
Your branch is behind 'origin/master' by 1 commit, and can be fast-forwarded.
  (use "git pull" to update your local branch)

nothing to commit, working directory clean

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ git commit -m"this.txt"
On branch master
Your branch is behind 'origin/master' by 1 commit, and can be fast-forwarded.
  (use "git pull" to update your local branch)

nothing to commit, working directory clean

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ git reflog
09f2df6 HEAD@{0}: reset: moving to HEAD^
2465705 HEAD@{1}: commit: 已经修改
09f2df6 HEAD@{2}: commit (initial): jq文件

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ git reset --hard HEAD^
fatal: ambiguous argument 'HEAD^': unknown revision or path not in the working t
ree.
Use '--' to separate paths from revisions, like this:
'git <command> [<revision>...] -- [<file>...]'

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ git rm -f this.txt
fatal: pathspec 'this.txt' did not match any files

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ git rm -f this.txt
fatal: pathspec 'this.txt' did not match any files

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ git rm -f this.txt
fatal: pathspec 'this.txt' did not match any files

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$ git rm -f text.txt
fatal: pathspec 'text.txt' did not match any files

Administrator@OPN9JS0KRUYCSIG /f/back.github.io (master)
$





Npm—node package manager 


Gulp工具命令





Gulp+变量名
gulp.task('变量名',function(){
    gulp.src('travelling-find/iconfont/*.*')
    .pipe(gulp.dest('travel-find/fonts'))
});
Gulp+server
