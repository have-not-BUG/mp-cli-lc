# 功能齐全的多页面模版生成器脚手架mp-cli-lc
mp-cli-lc 名字由来mp表示multiple page，多页面的意思，cli表示脚手架的意思，lc这个大家应该懂的

![https://www.npmjs.com/package/mp-cli-lc](https://img.shields.io/npm/v/mp-cli-lc)
![https://www.npmjs.com/package/mp-cli-lc](https://img.shields.io/npm/dt/mp-cli-lc)
![https://github.com/have-not-BUG/mp-cli-lc](https://img.shields.io/github/languages/code-size/have-not-BUG/mp-cli-lc)
![https://github.com/have-not-BUG/mp-cli-lc](https://img.shields.io/github/issues-raw/have-not-BUG/mp-cli-lc)
![https://github.com/have-not-BUG/mp-cli-lc](https://img.shields.io/github/license/have-not-BUG/mp-cli-lc)
![https://www.npmjs.com/package/mp-cli-lc](https://img.shields.io/badge/maintained%20with-gulp-cc00ff.svg)

# 一、具备的功能
### （一）生成的多页面具备以下功能:   
1、资源加载错误或被删除时自动刷新页面
  
2、接口网络错误、4xx、5xx和errno不为0时，会自动在页面上进行提示
 
3、接入了fundebug 错误监控系统
  
4、增加了 用户主动反馈网页问题 功能（用户点击后，可在fundebug后台查看用户当时页面地址、浏览器信息、SessionStorage、localStorage等信息）
 
5、js ES6+语法转换成ES5语法(内置函数如Promise、静态方法如Array.from及实例方法includes等均支持按需转换兼容)、生成sourceMap/压缩混淆/添加hash值(控制缓存) 
  
6、css 添加兼容性前缀/压缩/添加hash值(控制缓存) 
  
7、html 自动修改内部引用文件hash值/压缩；
  
8、支持自主选择是否压缩图片功能；
  
9、实时监控文件变化后刷新页面(即支持热更新、实时更新)

10、文件及接口监控插件支持网速慢提示（仅支持webkit内核），支持断网及重连提示（各常见内核均支持）

11、项目支持`git commit`前进行eslint及git commit message规范检测


### （二）内置的网页问题反馈插件reportself.js具备以下功能:  
1、有自定义的alert、confirm、prompt及tips方法(具体用法详见reportself.js内注释) 

2、支持不传递某些localStorage及sessionStorage至fundebug

3、网页问题反馈标志支持左或右放置

以上具体配置请详见页面引用处下方注释


### （三）内置的资源及api异常监控插件monitorFileApiError.js具备以下功能:  
1、支持是否监听资源异常或是否监听api接口异常

2、支持是否监听跨域资源异常并刷新页面

3、支持errno不为0时是否进行alert弹窗

以上具体配置请详见页面引用处下方注释




# 二、使用方法
#### (一)、环境要求
1、**node版本需低于12**，因为gulp3与node12不兼容。推荐使用11.15.0
2、安装该脚手架时需要从墙外下载资源，因此你的命令行要能够科学上网

#### （二）、初始化
1、Windows系统全局安装(建议以管理员身份)  ```npm install mp-cli-lc -g``` mac ```sudo npm install mp-cli-lc -g```；  

2、进入你自己的工作目录后在控制台运行```mp init```，按照提示输入 项目名称、HTML/CSS/JS文件名(首次初始化时建议使用`index`名称)、网页title、fundebug的apikey及选择是否引入jQuery；

3、`mp init`项目后如果想再创建html/css/js文件，则执行`mp add`即可。     
![mp及mp init示例](https://publicimage-1251317493.file.myqcloud.com/reportBug/202103292003151304.png)
#### （三）、编写代码
1、执行```npm run dev```或者```gulp``` 启动项目;       
2、打开workspace文件夹编写对应的html,css,js及img文件夹(img文件夹默认没有)下的css、js、img(这些文件夹名称不能变动)；  
#### （四）、打包
以下适合mp-cli-lc v3+版本，v2及以下强烈建议升级至v3+

完成项目后在控制台执行```npm run build```或者```gulp build```会打包你的项目至workspace/dist文件夹中并打开浏览器运行你打包后的项目；不同指令，打包的结果不一样:   

##### 1、生成sourceMap

a、npm run build 或者 gulp build ---    不压缩图片，生成sourceMap，启动打包后的项目

b、npm run build:jk 或者 gulp buildJK ---  不压缩图片，生成sourceMap，不启动打包后的项目  【Jenkins上部署时采用】

##### 2、最终会删除SourceMap文件（以便单独上传SourceMap，与线上文件名对应）
a、npm run build:rmsm 或者 gulp build:rmsm ---    不压缩图片，最终会删除SourceMap文件，以便单独上传SourceMap，与线上文件名对应，启动打包后的项目

b、npm run build:jkrmsm 或者 gulp buildJK:rmsm ---  不压缩图片，最终会删除SourceMap文件，以便单独上传SourceMap，与线上文件名对应，不启动打包后的项目  【Jenkins上部署时采用】

##### 3、不生成sourceMap
a、npm run build:nosm 或者 gulp build:nosm ---    不压缩图片，不生成sourceMap，启动打包后的项目

b、npm run build:jknosm 或者 gulp buildJK:nosm ---  不压缩图片，不生成sourceMap，不启动打包后的项目  【Jenkins上部署时采用】

##### 4、图片相关
a、npm run build:img 或者 gulp buildImg ---    压缩图片，不启动打包后的项目

b、npm run build:imgrun 或者 gulp buildImgRun --- 压缩图片，启动打包后的项目



# 三、注意事项
1、请严格按照预设好的项目目录结构编写css、js及html文件，别移动文件位置哦；   
2、内联在html中的css、js不会进行兼容性优化、压缩及添加hash值；   

# 四、变更记录 changelog
[CHANGELOG](CHANGELOG.md)

# 五、资源说明

1、本脚手架中的`.eslintrc.js`、`.gitignore`及`commitlint.config.js`默认从[这里的仓库](https://github.com/have-not-BUG/mp-cli-lc-config-files) 下载，你可以根据需要自己修改相应配置

2、本脚手架 `mp init`后的样例 [可以查看这里](https://github.com/have-not-BUG/mp-cli-lc-test)


# 六、后续计划

1、内置的`gulp-imagemin`里面的 `imagemin-gifsicle`、`imagemin-mozjpeg`、`imagemin-optipng`、`imagemin-svgo`、`imagemin-svgo`、`imagemin-pngquant` 等依赖包的依赖包会从`https://raw.githubusercontent.com`下载资源，其在中国访问很慢，因此需要换成`https://raw.githubusercontents.com`进行加速

2、时间允许将由gulp改为webpack或vite

3、css重新启用rem或vw适配工具

