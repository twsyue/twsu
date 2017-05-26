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
