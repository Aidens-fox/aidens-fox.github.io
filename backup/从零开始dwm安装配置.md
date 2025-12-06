  dwm是一个十分轻量的窗口管理器，所以就对一些老旧的设备更加友好，不过这也对使用者的的能力提出了新要求，在本篇博文中我将会从零开始教你安装配置dwm的补丁，状态栏等
   那么我们首先先克隆下配置
dwm（本体）
`git clone https://git.suckless.org/dwm`
slstatus（状态栏）
`git clone https://git.suckless.org/slstatus`
dmenu（应用启动器）
git clone https://git.suckless.org/dmenu
你也可以克隆我的配置
` git  clone https://github.com/Aidens-fox/dwm.git`
你也可以使用aur的dwm包，相较于官方的文件，多了如desktop文件，让显示管理器（登录管理器）可以识别来提供启动dwm的选项，不过对于我来说，我还是个偏向于使用官方的，所以克隆完成后就cd到此文件下
`cd dwm`
   我们ls可以看到有很多文件，不过我们可以先编译安装一下(其他软件同理)
`sudo make clean install`
然后打开config.h文件，这是dwm中的配置文件、
下面我们开始配置dwm
1.亮度音量调节
在config.h中添加下面内容，启用多媒体按键
`#include <X11/XF86keysym.h>`
调节音量
```
static const char *up_vol[]   = { "pactl", "set-sink-volume", "@DEFAULT_SINK@", "+10%",   NULL };
static const char *down_vol[] = { "pactl", "set-sink-volume", "@DEFAULT_SINK@", "-10%",   NULL };
static const char *mute_vol[] = { "pactl", "set-sink-mute",   "@DEFAULT_SINK@", "toggle", NULL };
...

static const Key keys[] = {
       ...
       
       { 0, XF86XK_AudioMute,        spawn, {.v = mute_vol } },
       { 0, XF86XK_AudioLowerVolume, spawn, {.v = down_vol } },
       { 0, XF86XK_AudioRaiseVolume, spawn, {.v = up_vol } },
       
       ... 
};
```
调节亮度
```
static const char *brighter[] = { "brightnessctl", "set", "10%+", NULL };
static const char *dimmer[]   = { "brightnessctl", "set", "10%-", NULL };
...

static const Key keys[] = {
       ...
       
       { 0, XF86XK_MonBrightnessDown, spawn, {.v = dimmer } },
       { 0, XF86XK_MonBrightnessUp,   spawn, {.v = brighter } },
       
       ...
};
```
2.修改mod键
在dwm中默认是alt为mod键，我本人不太习惯，所以我把它更改为win键
`#define MODKEY Mod4Mask`
3.窗口标签配置
`static const char *tags[] = { "壹", "貳", "叁", "肆", "伍", "陸", "柒", "捌", "玖" };`
4.更改默认终端
dwm默认的st我用不太惯，所以我换成了alacritty
`static const char *termcmd[]  = { "alacritty", NULL };`
5.配置状态栏内容
状态栏我使用的是slstatus，cd到slstatus后还是编译安装
在config.h中添加
```
static const struct arg args[] = {
        /* function format          argument */
         {  wifi_perc,         " wlan0:%s|",         "wlan0" },
         { disk_free,    "Disk%s|",     "/" },
         { vol_perc,     "Volume:%s|",   "/dev/mixer" },
        { battery_perc, "Battery%s%%|","BAT0" },
        { cpu_perc, "CPU:%s%%|", NULL },
        { ram_used, "RAM:%sMB|", NULL },
        { datetime, "%s", "%F %T"          },

};
```
6.自启动软件
我们编辑.xinitrc文件
在里面添加
```
exec  fcitx5 & slstatus &
exec dwm
```
7.打补丁
补丁是dwm的一大特色，我们可以到https://dwm.suckless.org/patches/去找补丁，然后在dwm目录下新建一个叫patches的文件夹
`mkdir patches`
再把你想要的补丁下载下来，如attachaside，再安装补丁
`patch -F3 -i patches/dwm-xxxxxxx.diff`
卸载补丁
`patch -R < patches/dwm-xxxxxxxxx.diff`
       好了这就是全部内容了，感谢你的阅读，祝你拥有美好的一天
