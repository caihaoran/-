#APP上传发布流程
>前言：作为一名iOS开发者，把开发出来的App上传到App Store是必须的。下面就来详细介绍下具体流程。

####1.打开苹果开发者中心：https://developer.apple.com</h4>
打开后点击：Member Center
<p><img alt="这里写图片描述" height="570" src="./img/iOS APP上架流程/2015121616172072.png" title="" width="871" style="width: 630px; height: 412.466px;"></p>
如果你的电脑没有保存密码，则会提示你输入开发者帐号和密码，因为我的电脑已经保存了，所以直接进入。
####2.点击：Certificates, Identifiers &amp; Profiles</h4>
<p><img alt="这里写图片描述" height="590" src="./img/iOS APP上架流程/2015121616172273.png" title="" width="861" style="width: 630px; height: 431.765px;"></p>
####3.点击Devices
<p><img alt="这里写图片描述" height="602" src="./img/iOS APP上架流程/2015121616172374.png" title="" width="832" style="width: 630px; height: 455.505px;"></p>
###一.创建App IDs和Boudle ID
####4.点击App IDs，会进入如下界面，点击右上角的 + 号
<p><img alt="这里写图片描述" height="560" src="./img/iOS APP上架流程/2015121616172375.png" title="" width="780" style="width: 630px; height: 452.087px;"></p>
####5.填写App IDs和Boudle ID
<p><img alt="这里写图片描述" height="574" src="./img/iOS APP上架流程/2015121616172478.png" title="" width="729" style="width: 630px; height: 495.948px;"></p>
####6.点击continue
<p><img alt="这里写图片描述" height="576" src="./img/iOS APP上架流程/2015121616172579.png" title="" width="732" style="width: 630px; height: 495.948px;"></p>
####7.点击Submit
<p><img alt="这里写图片描述" height="548" src="./img/iOS APP上架流程/2015121616172693.png" title="" width="696" style="width: 630px; height: 495.948px;"></p>
####8.点击Done
<p><img alt="这里写图片描述" height="538" src="./img/iOS APP上架流程/2015121616172794.png" title="" width="683" style="width: 630px; height: 495.948px;"></p>
###二.创建发布证书（已创建过发布证书，可直接跳到第21步）
####9.点击Production后，点击 + 号
<p><img alt="这里写图片描述" height="530" src="./img/iOS APP上架流程/2015121616172795.png" title="" width="673" style="width: 630px; height: 495.948px;"></p>
####10.点击App Store and Ad Hoc
<p><img alt="这里写图片描述" height="545" src="./img/iOS APP上架流程/2015121616172896.png" title="" width="692" style="width: 630px; height: 495.948px;"></p>
####11.点击Continue
<p><img alt="这里写图片描述" height="552" src="./img/iOS APP上架流程/2015121616172897.png" title="" width="701" style="width: 630px; height: 495.948px;"></p>
####12.点击Continue
<p><img alt="这里写图片描述" src="./img/iOS APP上架流程/2015121616172898.png" title="" style="height: 560px; width: 542.362px;"></p>
###创建本地证书
####13.此时返回到桌面，在点开LaunchPad，在其他中找到钥匙串访问，切记不要关闭浏览器
<p><img alt="这里写图片描述" height="379" src="./img/iOS APP上架流程/2015121616172999.png" title="" width="673" style="width: 630px; height: 354.375px;"></p>
####14.打开钥匙串访问，点击电脑左上角的钥匙串访问–证书助理–从证书颁发机构请求证书
<p><img alt="这里写图片描述" height="331" src="./img/iOS APP上架流程/20151216161730100.png" title="" width="674" style="width: 630px; height: 309.702px;"></p>
####15.会出现如下界面，选择存储到磁盘，点击继续
<p><img alt="这里写图片描述" src="./img/iOS APP上架流程/20151216161730101.png" title="" style="width: 630px; height: 474.231px;"></p>
####16.选择存储到桌面，存储
<p><img alt="这里写图片描述" src="./img/iOS APP上架流程/20151216161730102.png" title="" style="width: 630px; height: 474.231px;"></p>
####17.点击完成
<p><img alt="这里写图片描述" src="./img/iOS APP上架流程/20151216161730103.png" title="" style="width: 630px; height: 474.231px;"></p>
####18.你会在桌面上看到下面的文件
<p><img alt="这里写图片描述" src="./img/iOS APP上架流程/20151216161730104.png" title="" style="width: 254px; height: 179px;"></p>
####19.然后回到浏览器，点击choose File.. 选择创建好的：CertificateSigningRequest.certSigningRequest 文件，点击Generate
<p><img alt="这里写图片描述" src="./img/iOS APP上架流程/20151216161730105.png" title="" style="height: 560px; width: 594.819px;"></p>
####20.点击Download下载创建好的发布证书（cer后缀的文件），然后点击Done，你创建的发布证书就会存储在帐号中。
<p><img alt="这里写图片描述" src="./img/iOS APP上架流程/20151216161730106.png" title="" style="width: 128px; height: 124px;"></p>
####注：一般一个开发者帐号创建一个发布证书就够了，如果以后需要在其他电脑上上架App，只需要在钥匙串访问中创建p12文件，把p12文件安装到其他电脑上。这相当于给予了其他电脑发布App的权限。
###创建PP文件
####21.找到Provisioning Profiles ，点击All，然后点击右上角 + 号
<p><img alt="这里写图片描述" height="565" src="./img/iOS APP上架流程/20151216161732107.png" title="" width="718" style="width: 630px; height: 495.948px;"></p>
####22.选择App Store，点击Continue
<p><img alt="这里写图片描述" height="618" src="./img/iOS APP上架流程/20151216161732108.png" title="" width="785" style="width: 630px; height: 495.948px;"></p>
####23.在App ID 这个选项栏里面找到你刚刚创建的：App IDs（Bundle ID） 类型的套装，点击Continue
<p><img alt="这里写图片描述" height="620" src="./img/iOS APP上架流程/20151216161733109.png" title="" width="787" style="width: 630px; height: 495.948px;"></p>
####24.选择你刚创建的发布证书（或者生成p12文件的那个发布证书），点击Continue
<p><img alt="这里写图片描述" height="608" src="./img/iOS APP上架流程/20151216161733110.png" title="" width="773" style="width: 630px; height: 495.948px;"></p>
####25.在Profile Name栏里输入一个名字（这个是PP文件的名字，可随便输入，在这里我用工程名字，便于分别），然后点击Generate
<p><img alt="这里写图片描述" height="481" src="./img/iOS APP上架流程/20151216161734111.png" title="" width="772" style="width: 630px; height: 495.948px;"></p>
####26.Download生成的PP文件，然后点击Done
<p><img alt="这里写图片描述" height="604" src="./img/iOS APP上架流程/20151216161734112.png" title="" width="767" style="width: 630px; height: 495.948px;"></p>
###在App Store开辟空间
####27.回到Member Center，点击iTunes Connect
<p><img alt="这里写图片描述" height="580" src="./img/iOS APP上架流程/20151216161734113.png" title="" width="751" style="width: 630px; height: 486.456px;"></p>
####28.点击我的App
<p><img alt="这里写图片描述" height="600" src="./img/iOS APP上架流程/20151216161734114.png" title="" width="777" style="width: 630px; height: 486.456px;"></p>
####29.点击新建 iOSApp
<p><img alt="这里写图片描述" height="635" src="./img/iOS APP上架流程/20151216161735115.png" title="" width="822" style="width: 630px; height: 486.456px;"></p>
####30.依次按提示填入对应信息，然后点击创建
<p><img alt="这里写图片描述" height="621" src="./img/iOS APP上架流程/20151216161736116.png" title="" width="804" style="width: 630px; height: 486.456px;"></p>
####31.依次把不同尺寸的App截图拉入到对应的里面
<p><img alt="这里写图片描述" height="626" src="./img/iOS APP上架流程/20151216161737117.png" title="" width="811" style="width: 630px; height: 486.456px;"></p>
####32.填入App简介
<p><img alt="这里写图片描述" height="592" src="./img/iOS APP上架流程/20151216161738118.png" title="" width="767" style="width: 630px; height: 486.456px;"></p>
####33.按提示依次输入
<p><img alt="这里写图片描述" height="545" src="./img/iOS APP上架流程/20151216161738119.png" title="" width="706" style="width: 630px; height: 486.456px;"></p>
####34.此时这个构建版本还没有生成，我们先把基本信息填写完毕，然后再进入Xcode中把项目打包发送到过来。
####注意：填写完一定要点击右上角的保存。
<p><img alt="这里写图片描述" height="592" src="./img/iOS APP上架流程/20151216161738120.png" title="" width="767" style="width: 630px; height: 486.456px;"></p>
###在Xcode中打包工程
####找到你刚刚下载的发布证书后缀为cer或者p12文件和pp文件双击看起来没反应但是他们已经加入到你的钥匙串中
*找到你刚刚下载的发布证书（后缀为.cer）或者p12文件，和PP文件，双击，看起来没反应，但是他们已经加入到你的钥匙串中。*
####35.在Xcode中选择模拟器为iOS Device，按照下图提示操作
<p><img alt="这里写图片描述" height="546" src="./img/iOS APP上架流程/20151216161740121.png" title="" width="740" style="width: 630px; height: 464.568px;"><br>
<img alt="这里写图片描述" height="452" src="./img/iOS APP上架流程/20151216161741122.png" title="" width="742" style="width: 630px; height: 383.631px;"><br>
<img alt="这里写图片描述" height="578" src="./img/iOS APP上架流程/20151216161742123.png" title="" width="785" style="width: 630px; height: 463.662px;"></p>
####36.修改.plist文件，两个.plist文件都要修改
<p><img alt="这里写图片描述" height="583" src="./img/iOS APP上架流程/20151216161743124.png" title="" width="793" style="width: 630px; height: 463.662px;"></p>
####37.然后发送到我的App
<p><img alt="这里写图片描述" height="502" src="./img/iOS APP上架流程/20151216161743125.png" title="" width="839" style="width: 630px; height: 376.887px;"></p>
####38.发送成功后返回到我对App，刷新页面，在构建版本处就会有个 + 号，点击 + 号把发送过来的程序添加上去就行了
####39.然后在定价处设置你的App上架后是免费还是收费。
####40.回到我的App，点击发布就ok了。
