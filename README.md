# sa-sdk-javascript

Sensors Analytics JavaScript SDK  

# 代码埋点和可视化埋点介绍

代码埋点参考 http://www.sensorsdata.cn/manual/js_sdk.html   
代码埋点只需要把 sdk_url 设置成 sensorsdata.min.js  

可视化埋点参考 https://sensorsdata.cn/manual/vtrack_intro.html    
可视化埋点只需要把 sdk_url 设置成 vtrack.min.js 同时同级目录下必须包含这两个文件 vendor.min.js vendor.min.css   
可视化埋点代码里包含了代码埋点的所有功能，所以使用可视化埋点的话，也可以使用代码埋点的功能。  
***注意*** 能用代码埋点就用代码埋点，尽量不要用可视化埋点！具体原因参考可视化埋点文档。   

如有疑问请联系邮箱 shengyonggen@sensorsdata.cn 比较着急的话可以QQ522370351

# 代码埋点最佳实践
1. 控制台： 在代码埋点时，在控制台会打出 console 。每次 track 都会打出一个对象,里面 event 是你设置的事件名，注意观察数据是否和自己想要的一致！如果没出现，就是埋点失败！同时注意观察控制台的报错，会提示各种错误信息，比如事件名不合法，或者属性值无效等！   
2. 左下角的埋点管理： 这里会汇总数据的错误。  
3. 后端验证： 设置 debug_mode：true。这里除了会打 console 外，还会发一次 ajax 请求，在后端会再次验证数据是否合法。  

# 使用说明
1. /product下的是 代码埋点的最新源文件，欢迎提交修改。可视化埋点较为复杂，没有提供源文件，且不推荐使用。 
2. /dist下的是 可视化埋点和代码埋点的可用发行版文件。请将 /dist/版本号 下的文件都下载到你们自己网站目录下面!!!  
4. ***升级使用新版 SDK 前，请在微信群里先问下你们的神策分析系统版本是否支持!!!***

####1.5.4
增加自定义来源渠道参数source_channel，自定义渠道的参数也会被加到$pageview中，增加$is_first_time,增加异常检测(distinct_id为null的问题),$is_first_day如果为假时候，也会传属性false。把$pageview的$browser_language属性改成用户属性。  
#####1.5.3
可视化埋点定义模式下修复找不到元素时控制台报错的问题，修复定义模式下iframe非本域时加载脚本时控制台报错的问题。
#####1.5.2
可视化埋点增加选择器过滤功能
#####1.5.1
修复如果后端地址是 sa.xx 开头时候，发送地址替换gif错误的问题。增加web_url应对客户自定义后端api地址的问题。修复页面iframe了非同源页面后的bug。
#####1.5  
支持神策分析系统1.5版本多project，全埋点管理查看，以及把$pageview中的utm相关参数改成了$utm，
#####1.4.5  
增加callback，比如在数据发送成功后再跳转页面，sa.track('event',{},function(){location.href="..."})。
#####1.4.4  
可视化埋点支持iframe，代码埋点的$screen_height，$screen_width强制转换成数值类型，某些手机奇葩浏览器对这两个值取值异常。  
#####1.4.3  
增加sa.quick('autoTrack')方法，可以自动追踪pv，增加是否是首日访问等预置属性，和设置首次来源,首次时间等。  
同时对于属性的验证放宽，如果属性名错误，一样会发到后端。之前是会在前端抛掉。目前这样做可以方便在后端看到错误，方便debug错误原因。
#####1.4.2  (2016-6-15 注意此次修改要同步更新神策系统，未更新会导致数据丢失!!!)
使用服务器端时间
#####1.4.1  (稳定版)
把$os 改成 iPhone OS 和 Android 为了跟安卓iphone兼容



