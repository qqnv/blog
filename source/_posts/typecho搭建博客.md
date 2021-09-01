---
title: typecho搭建博客
tags:
  - typecho
  - blog
categories: 教程
description: typecho搭建博客
abbrlink: 63692
date: 2021-07-24 19:40:10
cover:
top_img:
highlight_shrink: true
---

[我的Typecho博客](https://www.qqnv.com)

## Typecho建站

1. 在本地电脑浏览器上输入宝塔 Linux 面板登录地址，输入用户名和密码后点击【登录】按钮进入后台

2. 点击左侧导航菜单“网站”>> 点击【添加站点】按钮 >> 在“添加网站”窗口中填写相关信息并点击【提交】按钮。

   * 填写想要建立的站点域名如 baidu.com
   * 备注和根目录自动生成不用理会
   * FTP 是否创建取决与你（PS：如果经常用 FTP 上传下载文件就创建），这里老古选择不创建；
   * 数据库建议选择创建 MySQL，utf-8，数据库设置不用理会；
   * 程序类型和网站分类不用理会；
   * PHP 版本选择是 7以上

   即可成功创建一个站点，建议将以下数据库名称、用户名和密码记录下来

3. 前往[Typecho 官网](http://typecho.org/)下载 Typecho 安装包，目前有正式稳定版 1.1，也有开发板，建议使用正式版比较稳妥，所以点击【下载 1.1 正式版】按钮下载安装包

4. 点击左侧导航菜单“文件”>> 点击进入刚才第 2 步所创建的网站根目录 >> 点击【上传】按钮 >> 点击【选择文件】按钮并选择第 3 步所下载的 Typecho 安装包 >> 点击【开始上传】按钮

5. 选择第 4 步上传的 Typecho 安装包 >> 点击右侧对应的“解压”链接按钮 >> 点击【解压】按钮

6. 进入到 build 文件夹并勾选所有文件 >> 点击【剪切】按钮，回到第 2 步所创建的站点根目录点击【粘贴所有】按钮即可将 build 文件夹内的 Typecho 文件移动到站点根目录中，然后可以删除 build 文件夹

7. 在本地电脑浏览器上打开第 2 步创建站点的域名即可进行 Typecho 站点的安装，点击【我准备好了，开始下一步》】按钮

8. 数据库名和数据库密码改成第二步创建时保存的（若未保存，可在面板左侧导航选择数据库查看数据库名和密码），用户名和登录密码自己设置记住就好，填写自己的邮件，其他默认，然后确认安装即可

## 主题及插件

1. 访问[handsome购买链接](https://www.ihewro.com/archives/489/)消费88元购买主题，购买后联系客服会发给你授权平台的账号密码访问[handsome用户管理系统](https://auth.ihewro.com/admin/)并登录，然后域名管理，添加自己的域名即可
2. 访问[handsome主题教程](https://auth.ihewro.com/user/docs/#/start)即可安装并使用教程
3. 访问[AliceStyle插件教程](https://racns.com/374.html)按照教程为主题添加插件

# 基于handsome主题的优化

##  crisp客服

1. 到[crisp官网](https://app.crisp.chat/initiate/signup/)注册
2. 注册完成后，点击 设置-网站设置-显示整合-HTML，复制代码添加至后台主题设置 自定义输出head 头部的HTML代码即可

##  首页新年倒计时

将以下代码添加至**设置外观-开发者设置-首页列表最前方广告位**

```html
/*首页倒计时*/
<style> 
.gn_box{     border: none;     border-radius: 15px; } 
.gn_box {     padding: 10px 14px;     margin: 10px;     margin-bottom: 20px;     text-align: center;     background-color: #fff; } 
#t_d{     color: #982585;     font-size: 18px; } 
#t_h{     color: #8f79c1;     font-size: 18px; } 
#t_m{     color: #65b4b5;     font-size: 18px; } 
#t_s{     color: #83caa3;     font-size: 18px; } 
</style> 
<div class="gn_box">   
<h1><font color=#E80017>2</font><font color=#D1002E>0</font><font color=#BA0045>2</font><font color=#A3005C>1</font><font  color=#8C0073>年</font><font color=#75008A>-</font>
<font color=#5E00A1>新</font><font color=#4700B8>年</font><font color=#3000CF>倒</font><font color=#1900E6>计</font><font color=#0200FD>时</font></h1><center>
<div id="CountMsg" class="HotDate"><span id="t_d"> 天</span><span id="t_h"> 时</span><span id="t_m"> 分</span><span id="t_s"> 秒</span></div></center>
<script type="text/javascript"> 
function getRTime() {   
    var EndTime = new Date('2021/01/01 00:00:00');  
    var NowTime = new Date();  
    var t = EndTime.getTime() - NowTime.getTime();   
    var d = Math.floor(t / 1000 / 60 / 60 / 24);   
    var h = Math.floor(t / 1000 / 60 / 60 % 24);   
    var m = Math.floor(t / 1000 / 60 % 60);   
    var s = Math.floor(t / 1000 % 60); 
    var day = document.getElementById("t_d");
    if (day != null) {
        day.innerHTML = d + " 天";   
    }
    var hour = document.getElementById("t_h");
    if (hour != null) {
        hour.innerHTML = h + " 时";  
    }
    var min = document.getElementById("t_m");
    if (min != null) {
        min.innerHTML = m + " 分";   
    }
    var sec = document.getElementById("t_s");
    if (sec != null) {
        sec.innerHTML = s + " 秒";
    }
}   
setInterval(getRTime, 1000);   
</script> </div>
```

##  彩色标签云

**设置外观-开发者设置-自定义JavaScript**中添加

```javascript
let tags = document.querySelectorAll("#tag_cloud-2 a");
let infos = document.querySelectorAll(".badge");
let colorArr = ["#428BCA", "#AEDCAE", "#ECA9A7", "#DA99FF", "#FFB380", "#D9B999"];
tags.forEach(tag => {
    tagsColor = colorArr[Math.floor(Math.random() * colorArr.length)];
    tag.style.backgroundColor = tagsColor;
});
infos.forEach(info => {
    infosColor = colorArr[Math.floor(Math.random() * colorArr.length)];
    info.style.backgroundColor = infosColor;
});
function addNumber(a) {
    var length = document.getElementById("comment").value.length;
    if(length> 0){
        document.getElementById("comment").focus()
        document.getElementById("comment").value += '\n' + a + new Date
    }else{
        document.getElementById("comment").focus()
        document.getElementById("comment").value += a + new Date
    }
}
```

**设置外观-PJAX-PJAX回调函数**中添加

```javascript
let tags = document.querySelectorAll("#tag_cloud-2 a");
let infos = document.querySelectorAll(".badge");
let colorArr = ["#428BCA", "#AEDCAE", "#ECA9A7", "#DA99FF", "#FFB380", "#D9B999"];
tags.forEach(tag => {
    tagsColor = colorArr[Math.floor(Math.random() * colorArr.length)];
    tag.style.backgroundColor = tagsColor;
});
infos.forEach(info => {
    infosColor = colorArr[Math.floor(Math.random() * colorArr.length)];
    info.style.backgroundColor = infosColor;
});
function addNumber(a) {
    var length = document.getElementById("comment").value.length;
    if(length> 0){
        document.getElementById("comment").focus()
        document.getElementById("comment").value += '\n' + a + new Date
    }else{
        document.getElementById("comment").focus()
        document.getElementById("comment").value += a + new Date
    }
}
```

## 首页文章版式圆角化

本项修改的是首页文章版式，包括图片使其四个角由方形变成圆角形状。将以下代码添加至后台**主题设置- 自定义CSS**

```css
/*首页文章版式圆角化,圆角大小可修改15px数值*/
.panel{
    border: none;
    border-radius: 15px;
}

.panel-small{
    border: none;
    border-radius: 15px;
}

.item-thumb{
    border-radius: 15px;  
}
```

## 首页文章图片获取焦点放大

本项修改的是首页文章图片，将鼠标放到首页头图后使其放大。将以下代码添加至后台**主题设置-自定义CSS**

```css
/*首页文章图片获取焦点放大,放大的时间和大小自行修改以下数值*/
.item-thumb{
    cursor: pointer;  
    transition: all 0.6s;  
}

.item-thumb:hover{
      transform: scale(1.05);  
}

.item-thumb-small{
    cursor: pointer;  
    transition: all 0.6s;
}

.item-thumb-small:hover{
    transform: scale(1.05);
}
```

## 首页头像转动放大

本项修改的是首页头像，将鼠标放至头像后使其转动并放大。将以下代码添加至后台**主题设置-自定义CSS**

```css
/*首页头像自动旋转,转动快慢和头像大小自行修改数值*/
.thumb-lg{
    width:130px;
}

.avatar{
    -webkit-transition: 0.4s;
    -webkit-transition: -webkit-transform 0.4s ease-out;
    transition: transform 0.4s ease-out;
    -moz-transition: -moz-transform 0.4s ease-out; 
}

.avatar:hover{
    transform: rotateZ(360deg);
    -webkit-transform: rotateZ(360deg);
    -moz-transform: rotateZ(360deg);
}

#aside-user span.avatar{
    animation-timing-function:cubic-bezier(0,0,.07,1)!important;
    border:0 solid
}

#aside-user span.avatar:hover{
    transform:rotate(360deg) scale(1.2);
    border-width:5px;
    animation:avatar .5s
}
```

## 文章标题居中

本项修改的是文章标题，使其居中。将以下代码添加至后台**主题设置-自定义CSS**

```css
/*文章标题居中*/
.panel h2{
    text-align: center; 
}
.post-item-foot-icon{
    text-align: center;
}
```

## 首页文章版式阴影化

本项修改的是文章版式阴影化。将以下代码添加至后台**主题设置-自定义CSS**

```css
/*panel阴影,阴影颜色修改rgba后面的值*/
.panel{
   box-shadow: 1px 1px 5px 5px rgba(255, 112, 173, 0.35);
    -moz-box-shadow: 1px 1px 5px 5px rgba(255, 112, 173, 0.35);
}

.panel:hover{
    box-shadow: 1px 1px 5px 5px rgba(255, 112, 173, 0.35);
    -moz-box-shadow: 1px 1px 5px 5px rgba(255, 112, 173, 0.35);
}

.panel-small{
    box-shadow: 1px 1px 5px 5px rgba(255, 112, 173, 0.35);
    -moz-box-shadow: 1px 1px 5px 5px rgba(255, 112, 173, 0.35);
}

.panel-small:hover{
    box-shadow: 1px 1px 5px 5px rgba(255, 112, 173, 0.35);
    -moz-box-shadow: 1px 1px 5px 5px rgba(255, 112, 173, 0.35);
}

/*如果也想使盒子四周也有阴影，加上以下代码*/
.app.container {
    box-shadow: 0 0 30px rgba(255, 112, 173, 0.35);
}
```

## mac代码高亮插件

详细教程请到[Xcnte's Blog](https://www.xcnte.com/archives/523/)查看
此外，按教程修改后可能会出现行号遮住代码且和代码不齐问题，可能是cdn或浏览器缓存引起的，可尝试清理浏览器缓存

## 显示评论者的信息

详细教程请到[松鼠的博客](https://doge.uk/coding/useragent-modify.html)查看

## 响应耗时访客总数全站字数

宝塔面板进入目录**/usr/themes/handsome/libs/Content.php**，将下面代码复制到class Content{}之前

```php
    /*访问总量*/
     function theAllViews(){
             $db = Typecho_Db::get();
             $row = $db->fetchAll('SELECT SUM(VIEWS) FROM `typecho_contents`');
                 echo number_format($row[0]['SUM(VIEWS)']);
     }

    /*响应时间*/
    function timer_start() {
        global $timestart;
        $mtime = explode( ' ', microtime()  );
        $timestart = $mtime[1] + $mtime[0];
        return true; 
    }
    timer_start();
    function timer_stop( $display = 0, $precision = 3  ) {
        global $timestart, $timeend;
        $mtime = explode( ' ', microtime()  );
        $timeend = $mtime[1] + $mtime[0];
        $timetotal = number_format( $timeend - $timestart, $precision  );
        $r = $timetotal < 1 ? $timetotal * 1000 . " ms" : $timetotal . " s";
        if ( $display  ) {
            echo $r;
        }
        return $r;
    }
```

在**/usr/themes/handsome/component/sidebar.php**的开头加入下面的代码:

```php
<?php
//字数统计
function allOfCharacters() {
    $chars = 0;
    $db = Typecho_Db::get();
    $select = $db ->select('text')->from('table.contents');
    $rows = $db->fetchAll($select);
    foreach ($rows as $row) { $chars += mb_strlen(trim($row['text']), 'UTF-8'); }
    $unit = '';
    if($chars >= 10000)     { $chars /= 10000; $unit = '万'; } 
    else if($chars >= 1000) { $chars /= 1000;  $unit = '千'; }
    $out = sprintf('%.2lf %s',$chars, $unit);
    return $out;
}
?>
```

在**/usr/themes/handsome/component/sidebar.php**，找到博客信息下面添加以下代码

```php
<li class="list-group-item text-second"> <span class="blog-info-icons"> <i data-feather="users"></i></span>
	<span class="badge
	pull-right"><?php echo theAllViews();?></span><?php _me("访客总数") ?></li>
	<li class="list-group-item text-second"> <span class="blog-info-icons"> <i data-feather="refresh-ccw"></i></span>
		<span class="badge
		pull-right"><?php echo timer_stop();?></span><?php _me("响应耗时") ?></li>
		<li class="list-group-item text-second"><span class="blog-info-icons"><i data-feather="edit-2"></i></span>
			<span class="badge 
			pull-right"><?php echo allOfCharacters(); ?></span><?php _me("全站字数") ?></li>
```

## 全站友链显示小图

在**/usr/themes/handsome/component/aside.php**里面大约209行的地方替换代码

```php
 <!--使用links插件，输出全站友链-->
 <?php $mypattern1 = "<li data-original-title=\"{title}\" data-toggle=\"tooltip\"
 data-placement=\"top\"><a rel='noopener' href=\"{url}\" target=\"_blank\"><img style=\"width:18px;height:18px;border-radius:50%;margin-right:3px;\" src=\"{image}\" /><span>{name}</span></a></li>";
 Handsome_Plugin::output($mypattern1, 0, "ten");?>

```

## 右键自定义

在**设置外观-开发者设置-自定义输出body尾部**添加以下代码

```html
<style type="text/css">
    a {text-decoration: none;}
    div.usercm{background-repeat:no-repeat;background-position:center center;background-size:cover;background-color:#fff;font-size:13px!important;width:130px;-moz-box-shadow:1px 1px 3px rgba
(0,0,0,.3);box-shadow:0px 0px 15px #333;position:absolute;display:none;z-index:10000;opacity:0.9; border-radius: 8px;}
    div.usercm ul{list-style-type:none;list-style-position:outside;margin:0px;padding:0px;display:block}
    div.usercm ul li{margin:0px;padding:0px;line-height:35px;}
    div.usercm ul li a{color:#666;padding:0 15px;display:block}
    div.usercm ul li a:hover{color:#fff;background:rgba(170,222,18,0.88)}
    div.usercm ul li a i{margin-right:10px}
    a.disabled{color:#c8c8c8!important;cursor:not-allowed}
    a.disabled:hover{background-color:rgba(255,11,11,0)!important}
    div.usercm{background:#fff !important;}
    </style>
<div class="usercm" style="left: 199px; top: 5px; display: none;">
    <ul>
        <li><a href="https://muyu.mobi/"><i class="fa fa-home fa-fw"></i><span>首页</span></a></li>
        <li><a href="javascript:void(0);" onclick="getSelect();"><i class="fa fa-copy fa-fw"></i><span>复制</span></a></li>
        <li><a href="javascript:void(0);" onclick="baiduSearch();"><i class="fa fa-search fa-fw"></i><span>搜索</span></a></li>
        <li><a href="javascript:history.go(1);"><i class="fa fa-arrow-right fa-fw"></i><span>前进</span></a></li>
        <li><a href="javascript:history.go(-1);"><i class="fa fa-arrow-left fa-fw"></i><span>后退</span></a></li>
        <li style="border-bottom:1px solid gray"><a href="javascript:window.location.reload();"><i class="fa fa-refresh fa-fw"></i><span>重载网页</span></a></li>
        <li><a href="https://muyu.mobi/links.html"><i class="fa fa-meh-o fa-fw"></i><span>和我当邻居</span></a></li>  
           <li><a href="https://muyu.mobi/message.html"><i class="fa fa-pencil-square-o fa-fw"></i><span>给我留言吧</span></a></li>
    </ul>
</div>
<script type="text/javascript">
    (function(a) {
        a.extend({
            mouseMoveShow: function(b) {
                var d = 0,
                    c = 0,
                    h = 0,
                    k = 0,
                    e = 0,
                    f = 0;
                a(window).mousemove(function(g) {
                    d = a(window).width();
                    c = a(window).height();
                    h = g.clientX;
                    k = g.clientY;
                    e = g.pageX;
                    f = g.pageY;
                    h + a(b).width() >= d && (e = e - a(b).width() - 5);
                    k + a(b).height() >= c && (f = f - a(b).height() - 5);
                    a("html").on({
                        contextmenu: function(c) {
                            3 == c.which && a(b).css({
                                left: e,
                                top: f
                            }).show()
                        },
                        click: function() {
                            a(b).hide()
                        }
                    })
                })
            },
            disabledContextMenu: function() {
                window.oncontextmenu = function() {
                    return !1
                }
            }
        })
    })(jQuery);

    function getSelect() {
        "" == (window.getSelection ? window.getSelection() : document.selection.createRange().text) ? layer.msg("啊噢...你没还没选择文字呢！") : document.execCommand("Copy")
    }
    function baiduSearch() {
        var a = window.getSelection ? window.getSelection() : document.selection.createRange().text;
        "" == a ? layer.msg("啊噢...你没还没选择文字呢！") : window.open("https://www.baidu.com/s?wd=" + a)
    }
    $(function() {
        for (var a = navigator.userAgent, b = "Android;iPhone;SymbianOS;Windows Phone;iPad;iPod".split(";"), d = !0, c = 0; c < b.length; c++) if (0 < a.indexOf(b[c])) {
            d = !1;
            break
        }
        d && ($.mouseMoveShow(".usercm"), $.disabledContextMenu())
    });
    </script>
```

## 时光机添加置顶视频

在**/usr/themes/handsome/component/say.php**的?php if ($comments->have()): ?> div class="streamline b-l m-l-lg m-b padder-v"之后(大概202行)添加代码

```php
<!--视频-->
<div id="comment-867" class="comment-body comment-parent comment-odd comment-by-author">
<div class="panel-heading pos-rlt b-b b-light">
<center>如此便好</center>
</div>
<div class="panel-body">
<p><video src="视频地址" style="background-image:url(视频封面图);background-size: cover;" preload="preload"></video><div class="play-button"></div></p> </div>
</div>
```
