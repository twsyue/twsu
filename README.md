记录日常中好用的代码
==================
（本人技术小白、仅以此记录自己的成长）

##1.1代码片段整理

swiper 轮播图（我很喜欢的一款轮播）
```html
<div class="swiper-container">
  <div class="swiper-wrapper">
    <div class="swiper-slide">  </div>
  </div>
  <div class="swiper-button-next"></div>
  <div class="swiper-button-prev"></div>
</div>
```
```javascript
var swiper = new Swiper('
   .swiper-container', 
     { nextButton: '.swiper-button-next',
       prevButton: '.swiper-button-prev',
       paginationClickable: true,
       spaceBetween: 0, 
       centeredSlides: true,
       autoplay: 2500,
       autoplayDisableOnInteraction: false,
       mousewheelControl: true,
       loop:true  
     }
   ); 
```
pc/移动浏览器判断跳转js
--
方案1
```javascript
  var browser={  
   versions:function(){   
   	   var u = navigator.userAgent, app = navigator.appVersion;   
   	   return {//移动终端浏览器版本信息   
   			trident: u.indexOf('Trident') > -1, //IE内核  
   			presto: u.indexOf('Presto') > -1, //opera内核  
   			webKit: u.indexOf('AppleWebKit') > -1, //苹果、谷歌内核  
   			gecko: u.indexOf('Gecko') > -1 && u.indexOf('KHTML') == -1, //火狐内核  
   			mobile: !!u.match(/AppleWebKit.*Mobile.*/), //是否为移动终端  
   			ios: !!u.match(/\(i[^;]+;( U;)? CPU.+Mac OS X/), //ios终端  
   			android: u.indexOf('Android') > -1 || u.indexOf('Linux') > -1, //android终端或者uc浏览器  
   			iPhone: u.indexOf('iPhone') > -1 , //是否为iPhone或者QQHD浏览器  
   			iPad: u.indexOf('iPad') > -1, //是否iPad    
   			webApp: u.indexOf('Safari') == -1 //是否web应该程序，没有头部与底部  
   		};  
   	 }(),  
   	 language:(navigator.browserLanguage || navigator.language).toLowerCase()  
   }   
   
   if(browser.versions.mobile || browser.versions.ios || browser.versions.android || browser.versions.iPhone || browser.versions.iPad)
   {  
   	window.location = "mobile.html";       	      
   }
```
方案2
```javascript
        function browserRedirect() {  
            var sUserAgent = navigator.userAgent.toLowerCase();  
            var bIsIpad = sUserAgent.match(/ipad/i) == "ipad";  
            var bIsIphoneOs = sUserAgent.match(/iphone os/i) == "iphone os";  
            var bIsMidp = sUserAgent.match(/midp/i) == "midp";  
            var bIsUc7 = sUserAgent.match(/rv:1.2.3.4/i) == "rv:1.2.3.4";  
            var bIsUc = sUserAgent.match(/ucweb/i) == "ucweb";  
            var bIsAndroid = sUserAgent.match(/android/i) == "android";  
            var bIsCE = sUserAgent.match(/windows ce/i) == "windows ce";  
            var bIsWM = sUserAgent.match(/windows mobile/i) == "windows mobile";  
           
              
            if (bIsIpad || bIsIphoneOs || bIsMidp || bIsUc7 || bIsUc || bIsAndroid || bIsCE || bIsWM) {  

            } else {  
                window.location.href="pc.html"; 
            }  
        }  
  
        browserRedirect();  
```
 

css样式书写规范、顺序
--
1.位置属性(position, top, right, z-index, display, float等)

 2.大小(width, height, padding, margin)
 
 3.文字系列(font, line-height, letter-spacing, color- text-align等)
 
 4.背景(background, border等)
 
 5.其他(animation, transition等)
 
 6.CSS有些属性是可以缩写的，比如padding,margin,font等等，这样精简代码同时又能提高用户的阅读体验。
 
 7.去掉小数点前的“0”
 
 8.简写命名 但一定要让人看懂你的命名！
 
 9.16进制颜色代码缩写  有些颜色代码是可以缩写的，我们就尽量缩写吧，提高用户体验为主
 
 10.连字符CSS选择器命名规范
 
   10.1长名称或词组可以使用中横线来为选择器命名。   
   10.2不能用“_”下划线来命名CSS选择器，为什么呢？
       一些浏览器已经不允许使用下划线来命名CSS选择器（就是不兼容）；
       能良好区分JavaScript变量命名.
       
 11.不要随意使用id
    id在JS是唯一的，不能多次使用，而使用class类选择器却可以重复使用，另外id的优先级优先与class，所以id应该按需使用，而不能滥用。
   
 12.为选择器添加状态前缀
    
  有时候可以给选择器添加一个表示状态的前缀，全语义更明了。
  
 网站响应式设计
 ------
 
网页响应式设计 字体相关
rem作为单位适配


简单问题简单解决
我觉得有些web app并一定很复杂，结构简单的就是：

顶部与底部的bar不管分辨率怎么变，它的高度和位置都不变
中间内容每条信息不管分辨率怎么变，招聘公司的图标等信息都位于条目的左边，薪资都位于右边
这种app是一种典型的弹性布局：关键元素高宽和位置都不变，只有容器元素在做伸缩变换。
对于这类app，记住一个开发原则就好：文字流式，控件弹性，图片等比缩放。以图描述：

rem为单位的方法 
```javascript
// JavaScript Document
// 该代码来自http://www.ghugo.com/mobile-h5-fluid-layout-for-iphone6/
(function (doc, win) {
    // 分辨率Resolution适配
    var docEl = doc.documentElement,
        resizeEvt = 'orientationchange' in window ? 'orientationchange' : 'resize',
        recalc = function () {
            var clientWidth = docEl.clientWidth;
            if (!clientWidth) return;
            docEl.style.fontSize = 100 * (clientWidth / 320) + 'px';
        };
    
    // Abort if browser does not support addEventListener
    if (!doc.addEventListener) return;
    win.addEventListener(resizeEvt, recalc, false);
    doc.addEventListener('DOMContentLoaded', recalc, false);
    
    // 一物理像素在不同屏幕的显示效果不一样。要根据devicePixelRatio来修改meta标签的scale,要注释上面的meta标签
    (function(){
        return;
        var dpr = scale =1;
         var isIPhone = win.navigator.appVersion.match(/iphone/gi);
        var devicePixelRatio = win.devicePixelRatio;
        if (isIPhone) {
            // iOS下，对于2和3的屏，用2倍的方案，其余的用1倍方案
            if (devicePixelRatio >= 3 && (!dpr || dpr >= 3)) {                
                dpr = 3;
            } else if (devicePixelRatio >= 2 && (!dpr || dpr >= 2)){
                dpr = 2;
            } else {
                dpr = 1;
            }
        } else {
            // 其他设备下，仍旧使用1倍的方案
            dpr = 1;
        }
           scale = 1 / dpr;
           
           // 
           var metaEl = "";
           metaEl = doc.createElement('meta');
        metaEl.setAttribute('name', 'viewport');
        metaEl.setAttribute('content', 'initial-scale=' + scale + ', maximum-scale=' + scale + ', minimum-scale=' + scale + ', user-scalable=no');
        if (docEl.firstElementChild) {
            docEl.firstElementChild.appendChild(metaEl);
        } else {
            var wrap = doc.createElement('div');
            wrap.appendChild(metaEl);
            doc.write(wrap.innerHTML);
        }
    })();
        
})(document, window);    
```
H5微信播放全屏问题
 ------
 在ios和安卓手机里的微信环境下做网页播放视频时，会遇到很多问题，不自动播放啊，播放结束后会出现视频推荐广告，出现控制条等有很多坑
 一下记录一下日常的解决方案 各位朋友有更好的方案也一定要告诉我呀
 ```html
<video 
  id="videoW"
  src="demo.mp4"
  poster="demo.jpg" /*视频封面*/
  preload="auto" 
  webkit-playsinline="true" /*这个属性是ios 10中设置可以
                     让视频在小窗内播放，也就是不是全屏播放*/  
  playsinline="true"  /*IOS微信浏览器支持小窗内播放*/ 
  x5-video-player-type="h5"  /*启用H5播放器,是wechat安卓版特性*/
  x5-video-player-fullscreen="true" /*全屏设置，设置为 true 是防止横屏*/
  x5-video-orientation="portraint" /*播放器支付的方向，
                     landscape横屏，portraint竖屏，默认值为竖屏*/
  style="object-fit:fill">
</video>
```