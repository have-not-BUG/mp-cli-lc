# 多页面模版生成器
# 一、具备的功能
### 支持自定义快速生成多页面，生成的多页面具备以下功能:   
a、资源加载错误或被删除时自动刷新页面  
b、接口网络错误、4xx、5xx和errno不为0时 在页面上进行提示 (alert/tips/html上提示)  
c、接入了fundebug 错误监控系统  
d、增加了 用户主动反馈网页问题 功能（用户点击后，可在后台查看用户当时页面地址、浏览器信息、SessionStorage、localStorage等信息），且可以调用自己写的Alert、Confirm、Prompt及Tip方法(因为在webview中这些常用方法均不支持)  
e、js ES6+语法转换成ES5语法、生成sourceMap/压缩混淆/添加hash值(控制缓存)   
f、css 添加兼容性前缀/压缩/添加hash值(控制缓存) ；  
g、html 自动修改内部引用文件hash值/压缩及自动插入polyfill.min.js 功能；  
h、支持自主选择是否压缩图片功能；  
i、实时监控文件变化后刷新页面(即支持热更新)；  




# 二、使用方法
#### （一）、初始化
1、下载该项目后 ```npm install```；  
2、在控制台运行```npm run init```或 ```node bin/init``` (如果觉得输太多，可以执行 `npm link`，后面只要执行 `init`即可)按照提示输入 项目名称、HTML/CSS/JS文件名(首次初始化时建议使用`index`名称)、网页title、fundebug的apikey及选择是否引入jQuery；     
![生成模板步骤](https://publicimage-1251317493.file.myqcloud.com/reportBug/202007290948571637.png)
#### （二）、编写代码
1、执行```npm run dev```或者```gulp``` 启动项目;       
2、打开workspace文件夹编写对应的html，css及js文件夹下的css、js；  
#### （三）、打包
完成项目后在控制台执行```gulp build```会打包你的项目至workspace/dist文件夹中并打开浏览器运行你打包后的项目；不同指令，打包的结果不一样:    
a、gulp build --- 不压缩图片，不注入Polyfill，启动打包后的项目   
b、gulp buildES --- 不压缩图片，但注入Polyfill，启动打包后的项目      
c、gulp buildJK --- 不压缩图片，不注入Polyfill，不启动打包后的项目  【Jenkins上部署时采用】   
d、gulp build0 --- 压缩图片，注入Polyfill，启动打包后的项目  

# 三、注意事项
1、请严格按照预设好的项目目录结构编写css、js及html文件，别移动文件位置哦；   
2、内联在html中的css、js不会进行兼容性优化、压缩及添加hash值；   
3、确保自己的html文件中`<head>`和`<meta>`相邻，因为插入polyfill.min.js 需要利用这两个标签来定位；   
