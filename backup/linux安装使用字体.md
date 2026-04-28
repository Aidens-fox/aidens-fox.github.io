- **1.下载字体**
这里以小赖字体为演示：
`https://github.com/lxgw/kose-font`
（注：如果官方仓库有推荐使用包管理器安装）
下载时注意文件名，Mono是等宽字体，Serif 是指有衬线，Sans(-serif) 是指无衬线,推荐下载等宽字体
- **2.添加字体**
下载完成后，可以新建文件夹
        `mkdir Xiaolai`
再把字体移动到文件夹里方便管理，然后把文件夹移动到/usr/share/fonts/下
        `sudo cp -r  XiaoLai /usr/share/fonts/`
然后更新字体缓存
        `sudo fc-cache -f -v`
更新完成后查看字体是否安装
        `fc-list | grep "Xiaolai"`
- **3.使用字体**
我们利用ifc-list | grep "XiaoLai"参考字体信息
````
/usr/share/fonts/Xiaolai/XiaolaiMono-Regular.ttf: 小赖字体等宽,Xiaolai Mono,小賴字體等寬,シャオライ等幅:style=Regular
/usr/share/fonts/Xiaolai/Xiaolai-Regular.ttf: 小赖字体,Xiaolai,小賴字體,シャオライ:style=Regular
````
我们复制.ttf:后面部分的英文：XiaoLai Mono，再把它粘贴到要使用的软件的配置文件中
如果要全局使用，请打开nwg-look在字体选择中选择字体