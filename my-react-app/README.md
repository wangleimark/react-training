## 一个React项目中会安装
1.react：React项目的核心（语法状态处理等）
2.react-dom：React项目的渲染核心【基于React构建webApp（Html页面）】或者 react-native：构建渲染APP
3.react-scripts：脚手架为了让项目目录看起来干净，将webpack打包规则以及相关插件（loader等）都隐藏到了node_modules目录下，react-scripts就是脚手架中自己对打包命令的一种封装，基于它打包，会调用node_modules中的webpack进行处理
4.web-vitals：性能检测工具