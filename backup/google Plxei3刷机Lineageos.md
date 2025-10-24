**Lineageos**

[https://download.lineageos.org/devices/blueline/builds](https://download.lineageos.org/devices/blueline/builds)

**ADB**

[https://developer.android.google.cn/tools/releases/platform-tools?hl=zh-cn](https://developer.android.google.cn/tools/releases/platform-tools?hl=zh-cn)

**谷歌框架**

[https://wiki.lineageos.org/gapps/](https://wiki.lineageos.org/gapps/)

**面具**

[https://github.com/topjohnwu/Magisk/releases/](https://github.com/topjohnwu/Magisk/releases/)

下载好后，把ADB添加到环境变量中

打开手机的开发者模式的USB调试，打开把你的手机用数据线连接到电脑

`adb devices`#查看设备是否被识别

`adb reboot bootloader `# 进入fastboot

`fastboot flashing unlock` # 解锁

重启后再次进入fastboot

`fastboot flash boot boot.img`

使用音量加减进入恢复模式

再清除data

再选择第二个使用adb安装系统

`adb sideload xxx.zip`

注：如果卡在47%是正常的

然后如果你要使用海外应用（google,gmail）请安装谷歌框架

`adb sideload 谷歌框架.zip`

然后重启到系统

进行一系列初始化

注：如果你安装了谷歌，请不要联网

完成后，如果你网络无法连接是因为自Android 5.0起，谷歌引入了Captive Portal机制， 用于检测WiFi网络认证是否正常。 该机制默认检测访问的是谷歌服务器，需要科学才能正常访问谷歌服务器

所以我们继续连接电脑使用ADB

使用ADB 工具，无需要root权限
````
adb shell settings delete global captive_portal_https_url

adb shell settings delete global captive_portal_http_url
````
修改一下服务器的地址：
````
adb shell settings put global captive_portal_http_url http://captive.v2ex.co/generate_204

adb shell settings put global captive_portal_https_url http://captive.v2ex.co/generate_204
````
然后切换一下飞行模式5秒， 激活一下就好

最后再安装面具

把boot.img复制到手机使用面具修补再传回电脑

再次使用ADB

`adb reboot bootloader`

`fastboot flash boot magisk.img`

重启后可以了

其他补充:

高版本尤其是动态分区版本早就不能用twrp了

所以刷写完系统后请不要装twrp