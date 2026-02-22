**什么是crDroid？**
crDroid 是一个基于 AOSP（Android Open Source Project） 的开源 Android 定制系统，旨在提供一个 稳定、流畅且功能丰富的用户体验。
**它有什么优点**
高度可定制化,小窗和分屏功能
**下载刷机包**
 crDroid: https://sourceforge.net/projects/crdroid/files/
 Google Pixel3 : https://sourceforge.net/projects/crdroid/files/blueline/11.x/
 注:在下载刷机包之前请参考设备代号，如Google Pixel3代号blueline（蓝鳍鱼），然后在sourceforge里使用Ctrl+f来搜索，**然后不要忘记下载boot和dtbo文件** 
**linux要准备的**
adb
`sudo pacman -S android-tools  android-udev payload-dumper-go`
**手机设置**
打开手机的开发者模式的USB调试，打开把你的手机用数据线连接到电脑
手机弹出提示是否允许电脑调试点永远允许
**开始刷机**
打开终端
`adb devices`#查看设备是否被识别
`adb reboot bootloader `#进入fastboot
`fastboot flashing unlock`#解锁
重启后再次进入fastboot
`fastboot flash boot boot.img`#刷入boot文件
`fastboot flash dtbo dtbo.img`#刷入dtbo文件
使用音量加减进入恢复模式,洋文RecoveryMode
在恢复模式下选择第三个恢复出厂设置数据
完成后返回主页选择第二个应用更新，选择用adb刷入
`adb sideload xxx.zip`
注：如果卡在47%是正常的
然后重启到系统
进行一系列初始化
解决网络无法连接
完成后，如果您网络无法连接是因为自Android 5.0起，谷歌引入了Captive Portal机制，用于检测WiFi网络认证是否正常。该机制默认检测访问的是谷歌服务器，需要科学才能正常访问谷歌服务器
所以我们可以继续使用ADB连接电脑
使用ADB工具，无需root权限
````
adb shell settings delete global captive_portal_https_url

adb shell settings delete global captive_portal_http_url
````
修改一下服务器地址：
````
adb shell settings put global captive_portal_http_url http://captive.v2ex.co/generate_204

adb shell settings put global captive_portal_https_url http://captive.v2ex.co/generate_204
````
然后切换一下飞行模式5秒，激活一下就好

安装面具
把boot.img复制到手机使用屏幕修复再传回电脑
再次使用ADB
`adb reboot bootloader`
`fastboot flash boot magisk.img`
重启后就可以了