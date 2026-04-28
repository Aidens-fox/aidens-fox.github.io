#### **什么是ArrowOS？**
Arrow OS 最初于 2017 年推出，作为Android 设备的开源定制 ROM。该项目旨在提供一种简化、轻量级且可定制的 Android 固件替代方案。Arrow OS 的开发始于一小群开发人员，他们热衷于制作用户友好且功能丰富的定制 ROM。
#### **它有什么优点**
设备兼容性,轻量级和简约,灵活性和模块化
#### **下载刷机包**
google pixel3: https://sourceforge.net/projects/arrow-os/files/arrow-12.1/official/blueline/
Arrowos: https://sourceforge.net/projects/arrow-os/files/
- 注：在下载刷机包时要注意包名末尾，GAPPS是包含谷歌套件的，VANIL是不包含的，如果需要使用google服务请下载GAPPS版本的
#### **linux要准备的**
adb
`sudo pacman -S android-tools  android-udev payload-dumper-go`
#### **从刷机包导出boot文件**
`mkdir cc`#创建文件夹
`unzip xxx.zip -d cc`#解压刷机包
`cd cc`#进入
`payload-dumper-go payload.bin`#提取boot
#### **手机设置**
打开手机的开发者模式的USB调试，打开把你的手机用数据线连接到电脑
手机弹出提示是否允许电脑调试点永远允许
#### **开始刷机**
打开终端
`adb devices`#查看设备是否被识别
`adb reboot bootloader `#进入fastboot
`fastboot flashing unlock`#解锁
重启后再次进入fastboot
`fastboot flash boot boot.img`#刷入boot文件
使用音量加减进入恢复模式,洋文RecoveryMode
在恢复模式下选择第三个恢复出厂设置数据
完成后返回主页选择第二个应用更新，选择用adb刷入
`adb sideload xxx.zip`
注：如果卡在47%是正常的
然后重启到系统
进行一系列初始化
#### 解决网络无法连接
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