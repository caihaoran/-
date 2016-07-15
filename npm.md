# npm命令总结
[TOC]
## 全局安装
1.`$ npm install xxx -g` 时， 模块将被下载安装到**全局目录**中。
**全局目录**通过 `$ npm config set prefix` 来设置。
通过 `$ npm config get prefix` 来获取当前设置的目录。

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
...
Press ^C at any time to quit.
name: (node_modules) xxx                      # 模块名
version: (1.0.0) 
description: Node.js 测试模块                 # 描述
...
Is this ok? (yes) yes
```
以上的信息，你需要根据你自己的情况输入。在最后输入 "yes" 后会生成 package.json 文件。

接下来我们可以使用以下命令在 npm 资源库中注册用户（使用邮箱注册）：
```
$ npm adduser
Username: caihaoran
Password:
Email: (this IS public) bnsexfire@sina.com
```
接下来我们就用以下命令来发布模块：
`$ npm publish`
## Package.json 属性详解
通常我们在创建一个NPM程序时，可以使用npm init命令，通过交互式的命令，自动生成一个package.json文件，里面包含了常用的一些字段信息，但远不止这么简单。通过完善package.json文件，我们可以让npm命令更好地为我们服务。
#### name
name和version是package.json中最重要的两个字段，也是发布到NPM平台上的唯一标识，如果没有正确设置这两个字段，包就不能发布和被下载。

下面是官方给出的一些建议:

* 名字里不要再包含"js"和"node"，因为默认NPM包就是node.js程序，不过你可以通过engines字段来指定。
* 名字将会被作为url的一部分，所有要符合http url的一般命名规则，不能包含url非法字符，也不能以.和_开头。
* 名字也将作为require()命令的参数，所以应该尽量简明。
* 如果包要发布到NPM平台上的话，最好先检查下有没有重名, 并且字母只能全部小写。

新版本的NPM可以指定scope, 名字可以加前缀标识，如@ijse/mypackage。
#### version 
语义版本号分为X.Y.Z三位，分别代表主版本号、次版本号和补丁版本号。当代码变更时，版本号按以下原则更新。

* 如果只是修复bug，需要更新Z位。
* 如果是新增了功能，但是向下兼容，需要更新Y位。
* 如果有大变动，向下不兼容，需要更新X位。

版本号有了这个保证后，在申明第三方包依赖时，除了可依赖于一个固定版本号外，还可依赖于某个范围的版本号。例如"argv": "0.0.x"表示依赖于0.0.x系列的最新版argv。
#### description
包的描述信息，将会在npm search的返回结果中显示，以帮助用户选择合适的包。
#### keywords
包的关键词信息，是一个字符串数组，同上也将显示在npm search的结果中。
#### homepage
包的主页地址
#### bugs
包的bug跟踪主页地址，应该如下设置：
```
bugs: {  
  "url": "http://github.com/caihaoran/project/issues",
  "email": "bnsexfire@sina.com"
}
```
#### license
包的开源协议名称
#### author
包的作者，可以是字符串或对象：
```
author: {  
  "name": "caihaoran",
  "email": "bnsexfire@sina.com",
  "url": "https://github.com/caihaoran"
}
```
或者:
`author: "caihaoran <bnsexfire@sina.com> (https://github.com/caihaoran)"`
#### contributors, maintainers
包的贡献者，是一个数组。
#### files
包所包含的所有文件，可以取值为文件夹。
通常我们还是用.npmignore来去除不想包含到包里的文件。
#### main
包的入口文件，如index.js
#### bin
如果你的包里包含可执行文件，通过设置这个字段可以将它们包含到系统的PATH中，这样直接就可以运行，很方便。如：
```
"bin": {
"react-native": "local-cli/wrong-react-native.js"
},
```
local-cli/wrong-react-native.js:
```
var script = process.argv[1];
var installedGlobally = script.indexOf('node_modules/.bin/react-native') === -1;
if (installedGlobally) {
  console.error([
    '\033[31mLooks like you installed react-native globally, maybe you meant react-native-cli?',
    'To fix the issue, run:\033[0m',
    'npm uninstall -g react-native',
    'npm install -g react-native-cli'
  ].join('\n'));
  process.exit(1);
} else {
  require('./cli').run();
}
```
当包被安装后，NPM将创建一个cli.js文件的链接到/usr/local/bin/react-native下。
#### man
为系统的man命令提供帮助文档, 如：
`"man": "./man/doc.1"`
帮助文件的文件名必须以数字结尾，如果是压缩的，需要以.gz结尾。
如果是字符串数组：
```
"name": "foo",
"man": ["./man/foo.1", "./man/bar.1", "./man/foo.2" ]
```
则分别可以man foo, man foo-bar, man 2 foo来查看。
#### directories
CommonJS包所要求的目录结构信息，目前除了告诉别人你的程序目录结构，貌似没有别的什么用。
下级字段可以是：lib, bin, man, doc, example。 每个都是字符串
#### repository
包的仓库地址。如：
```
"repository": {
  "type": "git",
  "url": "http://github.com/caihaoran/project.git"
}
```
#### scripts
通过设置这个可以使NPM调用一些命令脚本，封装一些功能。
#### config
添加一些设置，可以供scripts读取用，同时这里的值也会被添加到系统的环境变量中。
```
"name": "foo",
"config": {
  "port": "8080"
}
```
npm start的时候会读取到npm_package_config_port环境变量。

同时也可以使用npm config命令来修改设置：
`npm config set foo:port 8001  `
#### dependencies
指定依赖的其它包，这些依赖是指包发布后正常执行时所需要的，如果是开发中依赖的包，可以在devDependencies设置。
通常使用下面命令来安装：
`npm install --save otherpackage`

形式可以有如下多种：

* version 严格匹配某个版本
* \>version 必须大于某个版本
* \>=version
* <version
* <=version
* ~version 大概匹配某个版本
* ^version 兼容某个版本
* 1.2.x 可以是1.2.0, 1.2.1等等，但不能是1.3.0
* http://... 指定tarball的url地址
* * 任何版本都可以
* "" 同上
* version1 - version2 >=version1 <=version2
* range1 || range2 满足range1 或range2
* git://... git地址
* user/repo 同上
* tag 指定某个tag的版本
* path/path 本地包所有文件夹

下面都是可以用的：
```
{ "dependencies" :
  { "foo" : "1.0.0 - 2.9999.9999"
  , "bar" : ">=1.0.2 <2.1.2"
  , "baz" : ">1.0.2 <=2.3.4"
  , "boo" : "2.0.1"
  , "qux" : "<1.0.0 || >=2.3.1 <2.4.5 || >=2.5.2 <3.0.0"
  , "asd" : "http://asdf.com/asdf.tar.gz"
  , "til" : "~1.2"
  , "elf" : "~1.2.3"
  , "two" : "2.x"
  , "thr" : "3.3.x"
  , "lat" : "latest"
  , "dyl" : "file:../dyl"
  }
}
```
Git URL可以有如下种形式：
```
git://github.com/user/project.git#commit-ish  
git+ssh://user@hostname:project.git#commit-ish  
git+ssh://user@hostname/project.git#commit-ish  
git+http://user@hostname/project/blah.git#commit-ish  
git+https://user@hostname/project/blah.git#commit-ish  
```
#### devDependencies
这些依赖只有在开发时候才需要。
`npm install --save-dev mypack`
#### peerDependencies
相关的依赖，如果你的包是插件，而用户在使用你的包时候，通常也会需要这些依赖（插件），那么可以将依赖列到这里。
举个例子，如karma, 它的package.json中有设置：
```
"peerDependencies": {
  "karma-jasmine": "~0.1.0",
  "karma-requirejs": "~0.2.0",
  "karma-coffee-preprocessor": "~0.1.0",
  "karma-html2js-preprocessor": "~0.1.0",
  "karma-chrome-launcher": "~0.1.0",
  "karma-firefox-launcher": "~0.1.0",
  "karma-phantomjs-launcher": "~0.1.0",
  "karma-script-launcher": "~0.1.0"
}
```
这些都是karma的相关插件，一般使用karma的时候都会需要。
#### bundledDependencies
绑定的依赖包，发布的时候这些绑定包也会被一同发布。
#### optionalDependencies
即使这些依赖没有，也可以正常安装使用
#### engines
指定包运行的环境
```
"engines": {
  "node": ">=0.10.3 < 0.12",
  "npm": "~1.0.20"
}
```
#### engineStrict
设置为true强制限定 engine
#### os
指定你的包可以在哪些系统平台下运行。
`"os": [ "darwin", "linux", "!win32" ]`
即可以在darwin和linux平台下运行，而不能在win32下。这里设定的取值是来自process.platform的。
#### cpu
可以指定包运行的cpu架构，如
`"cpu": [ "x64", "!arm" ]`
取值来自process.arch。
#### preferGlobal
如果你的包是命令行运行的，那可以将其设置为true建议用户全局(npm install -g)安装。但它并不强制用户。
#### private
设为true这个包将不会发布到NPM平台下。
#### publishConfig
这个字段用于设置发布时候的一些设定。尤其方便你希望发布前设定指定的tag或registry。
也可以设定其它子字段，但只有tag和registry会影响到发布。
#### NPM的一些默认值说明
* `"scripts": { "start": "node server.js" } `如果在项目根目录下含有server.js文件，则NPM会自动设置此值。
* `"scripts": { "preinstall": "node-gyp rebuild" }`如果在项目根目录下含有binding.gyp文件，则NPM会自动设置此值。
* `"contributors": [...]`如果项目根目录下含有AUTHORS文件，则NPM会自动将每一行以Name <email> (url)的格式读取并设定此字段。