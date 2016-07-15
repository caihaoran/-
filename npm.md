# npm命令总结
[TOC]
## 全局安装
1.`$ npm install xxx -g` 时， 模块将被下载安装到**全局目录**中。
**全局目录**通过 `$ npm config set prefix` 来设置。
通过 `$ npm config get prefix` 来获取当前设置的目录。
## Package.json
## 卸载模块
`$ npm uninstall express`
卸载后，你可以到 /node_modules/ 目录下查看包是否还存在，或者使用以下命令查看：
`$ npm ls`
## 更新模块
`$ npm update express`
## 搜索模块
`$ npm search express`
## 创建模块
创建模块，package.json 文件是必不可少的。我们可以使用 NPM 生成 package.json 文件，生成的文件包含了基本的结果。
```
$ npm init
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help json` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg> --save` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
name: (node_modules) runoob                   # 模块名
version: (1.0.0) 
description: Node.js 测试模块(www.runoob.com)  # 描述
entry point: (index.js) 
test command: make test
git repository: https://github.com/runoob/runoob.git  # Github 地址
keywords: 
author: 
license: (ISC) 
About to write to ……/node_modules/package.json:      # 生成地址

{
  "name": "runoob",
  "version": "1.0.0",
  "description": "Node.js 测试模块(www.runoob.com)",
  ……
}

Is this ok? (yes) yes
```
以上的信息，你需要根据你自己的情况输入。在最后输入 "yes" 后会生成 package.json 文件。

接下来我们可以使用以下命令在 npm 资源库中注册用户（使用邮箱注册）：
```
$ npm adduser
Username: mcmohd
Password:
Email: (this IS public) mcmohd@gmail.com
```
接下来我们就用以下命令来发布模块：
`$ npm publish`
## 版本号 
语义版本号分为X.Y.Z三位，分别代表主版本号、次版本号和补丁版本号。当代码变更时，版本号按以下原则更新。

* 如果只是修复bug，需要更新Z位。
* 如果是新增了功能，但是向下兼容，需要更新Y位。
* 如果有大变动，向下不兼容，需要更新X位。

版本号有了这个保证后，在申明第三方包依赖时，除了可依赖于一个固定版本号外，还可依赖于某个范围的版本号。例如"argv": "0.0.x"表示依赖于0.0.x系列的最新版argv。