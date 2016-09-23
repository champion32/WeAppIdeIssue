#微信小应用 IDE的安装以及安装过程的常见问题

本文内容主要解决下载安装IDE和hello world的问题.----以Windows平台为主

本文写于 2016/09/23 日,截止写文时, 微信小应用在内测阶段.所以本文针对的是无内测权限的"破解版"IDE的操作步骤.按照此文最终可以实现:本地预览调试,无法发布.

本文主要参照[github/gavinkwoe](https://github.com/gavinkwoe/weapp-ide-crack)以及[清澈@Cherry的博客](http://blog.csdn.net/nihaoqiulinhe/article/details/52634056),额外工作是收集了常见问题项(文章最底部).

亦可以参考[教程](http://wxopen.notedown.cn/)

[IDE等文件下载路径](https://pan.baidu.com/s/1c21aS0o)
![下载图片](http://upload-images.jianshu.io/upload_images/1355213-a491cad72179e0e3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

Mac和Windows平台均需要下载四个文件,分别为 :

IDE 0.7和0.9版本 + crack-master.zip + demo.zip



1. 安装0.7版本的程序并打开,微信扫描二维码登录.
2. 安装对应平台的0.9版本的程序(可以选择覆盖/不覆盖0.7版本,无影响),然后 替换如下三个文件(文件在crack-master.zip中)
`

Windows：

\package.nw\app\dist\components\create\createstep.js

\package.nw\app\dist\stroes\projectStores.js

\package.nw\app\dist\weapp\appservice\asdebug.js

Mac：(右键点击图标,选择[包内容显示])

/Resources/app.nw/app/dist/components/create/createstep.js

/Resources/app.nw/app/dist/stroes/projectStores.js

/Resources/app.nw/app/dist/weapp/appservice/asdebug.js

`

3. 如果一切顺利,那么0.9版本的IDE已经成功打开(失败的话重复1步骤),会出现下列画面:
![ IDE ](http://upload-images.jianshu.io/upload_images/1355213-332d44216451a01c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
4. 第3步成功后,添加项目.则会出现下图."Hello World"显示出来.左上角的头像时你扫描二维码时使用的微信的头像.至于红框标示的几处,可以随意点击一下试试效果.
![](http://upload-images.jianshu.io/upload_images/1355213-b98f16af64cf1386.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
点击项目标签会出现下图,但是因为非内测人员是没有appID的,所以此处的上传和预览按钮都无效,点击会出现"invalid appid"提示,因为此处会与微信后台进行交互和验证身份
![](http://upload-images.jianshu.io/upload_images/1355213-3e5ecc941af5bb78.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

那应该如何调试代码呢?切换到 编辑标签,点击左侧边栏下方的"编译"按钮即可,如图
![](http://upload-images.jianshu.io/upload_images/1355213-905b365ca001a022.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

5,运行demo
新建的目录结构如下
![](http://upload-images.jianshu.io/upload_images/1355213-97088bbdf45a6cab.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

demo.zip中的文件解压缩后 

1.先把上图中 WeAppProjects/Blog下的所有(是所有)删除后,粘贴进去

2.通过步骤3新增项目导入进去

就会出现官方的demo了
![](http://upload-images.jianshu.io/upload_images/1355213-85a8f1510a8ce702.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



以下为常见错误项
错误1,打开IDE时appid无效,如图.解决方案:0.7版本负责且仅负责扫描登录,然后打开0.9版本
![](http://upload-images.jianshu.io/upload_images/1355213-34dced6fecc824dd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

错误2,保证三个  .js文件都替换,不能少.如下问题是少了asdebug.js
![](http://upload-images.jianshu.io/upload_images/1355213-4fb78347ef614cb5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

错误3,40013错误,是appid无效.不要上传/预览来运行程序.参照步骤4

错误4,Failed to load resource: net::ERR_NAME_NOT_RESOLVED

问题原因：通常是由于系统设置了代理如Shadowsocks等。

解决方案：关闭代理，或者依次点击工具栏“动作”-"设置"，选择“不使用任何代理，勾选后直连网络”。
