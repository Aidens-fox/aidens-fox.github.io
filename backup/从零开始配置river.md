**我的配置**：https://github.com/Aidens-fox/river
**1.轻量级状态栏：dam**
项目链接：codeberg.org/sewn/dam
`git clone "https://codeberg.org/sewn/dam.git"`
`sudo pacman -S wayland  wayland-protocols fcft pixman pkg-config tllist`
项目依赖文件：https://codeberg.org/sewn/drwl
`git clone "https://codeberg.org/sewn/drwl.git"`
克隆完成后把文件移动到c库
`i3status | dam`
**2.字体安装**：
`sudo pacman -S   ttf-maplemono-nf-cn-unhinted`

**3.配置dam**
打开nano config.h
````
#修改位置
static int topbar            = 0; /* 0 means bottom bar */
#修改字体
static const char *fonts[]   = { "Maple Mono NF CN:size=12" };
#修改颜色
static uint32_t colors[][3]  = {
        /*               fg          bg         */
        [SchemeNorm] = { 0xd3c6aaff, 0x2d353baa      },
        [SchemeSel]  = { 0xd3c6aaff, 0x4b533aff },
};
````
保存后再打开dam.c
#设置状态栏间距,第238行
````   
     if (bar == selbar) { /* status is only drawn on selected monitor */
                drwl_setscheme(bar->drw, colors[SchemeNorm]);
                tw = TEXTW(bar, stext);
                drwl_text(bar->drw, bar->width - tw,0, tw, bar->height, bar->lrpad = 15 , stext, 0);
        }
````
最后sudo make install

**4.配置river**
把默认配置复制到.config/river/
`mkdir .config/river`
`cp /usr/share/river/example/init .config/river/init`
打开init文件
````
#修改配色
riverctl border-color-focused "0x6e8343"
riverctl border-color-unfocused "0x585b70"
riverctl border-color-urgent 0xdc322f
#解决音量快捷键问题
    riverctl map $mode None XF86AudioRaiseVolume  spawn 'pactl set-sink-volume @DEFAULT_SINK@ +10%'
    riverctl map $mode None XF86AudioLowerVolume  spawn 'pactl set-sink-volume @DEFAULT_SINK@ -10%'
    riverctl map $mode None XF86AudioMute         spawn 'pamixer --toggle-mute'
````