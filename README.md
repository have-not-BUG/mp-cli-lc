# 一、具备的功能
a、js ES6+语法转换成ES5语法、生成sourceMap/压缩混淆/添加hash值(控制缓存)   
b、css 添加兼容性前缀/压缩/添加hash值(控制缓存) ；  
c、html 自动修改内部引用文件hash值/压缩及自动插入polyfill.min.js 功能；  
d、支持自主选择是否压缩图片功能；  
e、实时监控文件变化后刷新页面；  
f、增加了 用户主动反馈网页问题 功能（用户点击后，可在后台查看用户当时页面地址、浏览器信息、SessionStorage、localStorage等信息），且可以调用Alert、Confirm、Prompt及Tip方法(因为在webview中这些常用方法均不支持)  
g、资源加载错误或被删除时自动刷新页面  
h、接口网络错误、4xx、5xx和errno不为0时 在页面上进行提示 (alert/tips/html上提示)  
i、接入了fundebug 错误监控系统  

# 二、使用步骤
1、下载该项目后 ```npm install```；  
2、在控制台运行```gulp``` 启动项目(支持热更新)；  
3、打开workspace文件夹编写对应的html，css及js文件夹下的css、js；  
4、根据index.html中的第一至四步的注释填写相应信息；
5、完成后在控制台执行```gulp build```会打包你的项目至workspace/dist文件夹中并打开浏览器运行你打包后的项目；不同指令，打包
具体用法 见 https://docs.qq.com/doc/DQlpsS3hyZUlMYWhx 中的 ```六、 多页面项目使用gulp实现打包功能```
