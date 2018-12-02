1.在目录下建立.htaccess伪静态：
`RewriteEngine On
RewriteRule ^(\w+)\.jpg$ image.php?p=$1 [L]
order deny,allow`


这个文件的作用是把目录下所有.jpg后缀图片重定向到image.php

2.建立image.php程序：
`<?php
header('Content-Type:image/jpeg');
if(!empty($_SERVER['HTTP_REFERER'])){header('Location:https://bwh8.net/aff.php?aff=-1');die;}
ob_clean();flush();readfile('image.jpg');
?>`


这个程序判断如果没有REFERER，则读取真实图片，防止有人手贱去复制图片地址一探究竟。

3.上传一个image.jpg

就是用作替换的真实图片。

【好处】

1.直接插入图片地址写入AFF，不会像iframe那样明显。

2.可以判断HTTP_REFERER，决定哪些网站定位至AFF。

3.也可以根据$SETVER['REQUEST_URI']参数展现具体图片。这个功能同样可以用作防盗链，盗链者复制你的图片使用，会被定位到AFF地址，从而实现赚钱。

4.可以设置图片时间，文件名写成插入时间时的时间戳，超出指定时间（比如5天），就自动跳转AFF链接。这样可以在公共论坛发帖的前几天内，让别人看不出是AFF，过了几天再跳转到AFF。



大佬,在css里面引用的写法,怎么写呢?

简单点的给某个DIV元素做背景：https://bbs.csdn.net/topics/200020558
复杂点的用伪元素：https://segmentfault.com/a/1190000010597978
