# echarts3.0 二次开发系列教程
## 获取eharts源码
源代码可以直接从github上clone下来<https://github.com/ecomfe/echarts>，不熟悉git操作的可以参考这篇文章<https://github.com/caihaoran/front-end-doc/blob/master/git.md>。

进入到目录下，运行`npm install`安装开发所需的工具
## eharts目录说明
#### src
最初的源码，amd模式封装，我们只修改这个目录下的代码。
#### lib
转化成cmd模式的源码。
#### dist
经过webpack打包过的最终代码。
## 如何打包源代码
#### src->lib
`$ npm run prepublish` 
#### lib->dist
`$ webpack --display-error-details` 