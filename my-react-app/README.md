## 一个React项目中会安装
1.react：React项目的核心（语法状态处理等）
2.react-dom：React项目的渲染核心【基于React构建webApp（Html页面）】或者 react-native：构建渲染APP
3.react-scripts：脚手架为了让项目目录看起来干净，将webpack打包规则以及相关插件（loader等）都隐藏到了node_modules目录下，react-scripts就是脚手架中自己对打包命令的一种封装，基于它打包，会调用node_modules中的webpack进行处理
4.web-vitals：性能检测工具
## config文件中的重点文件（eject暴露后）
1.webpackDevServer.config：webpack-dev-server的配置
2.webpack.config：脚手架默认的webpack打包规则的配置
3.path：打包中需要的一些路径管理
## scripts
后期执行相关打包命令的入口文件
## package.json新增的打包需要的所有模块（eject暴露后）
1.@babel/core：将es6转成es5
2.@pmmmwh/react-refresh-webpack-plugin：刷新react
3.@babel-preset-react-app：对@babel/preset-env语法包的重写；把ES6转化为ES5；让语法包可以识别React的语法，实现代码转化
4.@browserslist：浏览器兼容列表
5.@camelcase：同名语法，语言包的一个处理
6.@css-loader：css特殊语法的处理
7.@css-minimizer-webpack-plugin：用来压缩css
8.@eslint：语法检测
9.@file-loader：处理图片的
10.@html-webpack-plugin：打包html的，能够把打包后的ts和css自动导入到html
11.@jest：测试
12.@mini-css-extract-plugin：提取css，将js中的css代码可以提取出单独的css文件的
13.@postcss：实现css加前缀
14.@sass-loader：脚手架默认配置sass预编译语言，如果是用的less/stylus,则需要自己处理
15.@style-loader:以内嵌式的方式放入页面中？
16.@terser-webpack-plugin：压缩ts
17.@web-vitals：react性能检测工具
18.@webpack-dev-server：打包的时候能在本地启动web服务的
===============================================================================================
# 常见配置修改
1.把sass改成less：$yarn add less less-loader@8(用8版本不能用最新版本)   $yarn remove sass-loader（移除sass）
                webpack.config.js中，将const sassRegex = /\.(scss|sass)$/;改为const lessRegex = /\.(less)$/;
                const sassModuleRegex = /\.module\.(scss|sass)$/;改为const lessModuleRegex = /\.module\.(less)$/; 然后将module中rules中的sass的相关配置改成less
2.配置别名：webpack.config.js中的resolve（解析器）中的alias（设置别名）中添加'@': paths.appSrc
3.修改域名和端口号：start.js中DEFAULT_PORT代表端口号，HOST是域名；如果想基于process.env，首先需要安装yarn add cross-env，然后在package.json中start命令中添加cross-env PORT=8080
4.修改浏览器兼容：通过修改package.json中的browserslist（兼容列表）来实现浏览器的兼容（1.对postcss-loader生效：控制css3的前缀；2对babel-loader生效：控制ES6的转换）
  遗留问题：无法处理ES6内置API的兼容 ————>需要babel/prlyfill插件（对常见内置api重写）