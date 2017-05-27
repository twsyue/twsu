记录日常中好用的代码
==================
（本人技术小白、仅以此记录自己的成长）

##1.1代码片段整理

swiper 轮播图（我很喜欢的一款轮播）
```
<div class="swiper-container">
  <div class="swiper-wrapper">
    <div class="swiper-slide">  </div>
  </div>
  <div class="swiper-button-next"></div>
  <div class="swiper-button-prev"></div>
</div>
<script>
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
</script>
```
pc/移动浏览器判断跳转js
--
```
<script>
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
</script>
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
  
