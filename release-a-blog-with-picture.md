---
title: 在Hexo中发布一篇带图片的文章
date: 2019-03-29 19:30:00
tags: Hexo使用
---


### 到博客目录：
``` bash
cd /var/www/i99939/hexo_blog/
```

### 创建博客：
``` bash
hexo new "MAC mouse moving speed"
```

### 在source/_posts/下可以看见：
``` bash
ls -l source/_posts/
```

### 将写好的博客文件拷贝覆盖hexo创建的文件：
``` bash
cp your-blog.md /var/www/i99939/hexo_blog/source/_posts/MAC-mouse-moving-speed.md
```

### 目录结构：
``` bash
-rw-r--r-- 1 root root  911 Mar  9 07:52 Mac-mouse-moving-speed.md
drwxr-xr-x 2 root root 4096 Mar  9 14:52 config-ssh-key-login-linux
-rw-r--r-- 1 root root 1680 Mar 10 14:48 config-ssh-key-login-linux.md
```


### 在博文中添加图片

* 将_config.yml文件中的配置项post_asset_folder设为true

``` bash
post_asset_folder: true

hexo new "config ssh key login linux"
```

* 在source/_posts目录下会创建：
``` bash
source/_posts/config-ssh-key-login-linux
```

* 将图片hacking.png拷贝：
``` bash
source/_posts/config-ssh-key-login-linux/hacking.png
```


* 在config-ssh-key-login-linux.md文件中需要显示图片的地方，插入：

``` bash
{% asset_img hacking.png "blogs image" %}
```
{% asset_img hexo.png "blogs image" %}

这样图片在文章和首页中可以同时显示


### 发布

``` bash
cd /var/www/i99939/hexo_blog/
hexo clean
hexo d -g
```

