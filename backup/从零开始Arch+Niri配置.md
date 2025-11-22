1.换源
`sudo nano /etc/pacman.d/mirrorlist`
在文件中添加：
```
#清华源
Server = https://mirrors.tuna.tsinghua.edu.cn/archlinux/$repo/os/$arch
#阿里源
Server = http://mirrors.aliyun.com/archlinux/$repo/os/$arch
#中科大源
Server = https://mirrors.ustc.edu.cn/archlinux/$repo/os/$arch
#日本源
Server = https://mirror.aria-on-the-planet.es/archlinux/$repo/os/$arch
#国际源
Server = https://fastly.mirror.pkgbuild.com/$repo/os/$arch

```
更新一下源`sudo pacman -Syyu`

2. 添加CN源
`sudo nano /etc/pacman.conf`
在文件中添加：
```
[archlinuxcn]
SigLevel = Optional TrustedOnly
#清华源
Server = https://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/$arch
#中科大源
Server = https://mirrors.ustc.edu.cn/archlinuxcn/$arch
#阿里源
Server = https://mirrors.aliyun.com/archlinuxcn/$arch
```
3. 导入 archlinuxcn key和安装yay
`sudo pacman -Syyu archlinuxcn-keyring`
`sudo pacman -Syyu yay base-devel`
4.配置中文字体（简体中文本地化）
中文字体安装
`sudo pacman -S wqy-zenhei adobe-source-han-sans-cn-fonts adobe-source-han-serif-cn-fonts wqy-microhei  noto-fonts noto-fonts-cjk noto-fonts-extra noto-fonts-emoji ttf-dejavu ttf-liberation`
解决waybar字体问题
`sudo pacman -S   ttf-jetbrains-mono-nerd `
系统设置
`sudo nano /etc/locale.gen`
把以下内容前的#去掉zh_CN.UTF-8 UTF-8然后sudo locale-gen
然后在`~/.xinitrc` 和`~/.xprofile`中添加:
```
export LANG=zh_CN.UTF-8
export LANGUAGE=zh_CN:en_US
```
中文输入法安装
`yay -S fcitx5-im fcitx5-input-support fcitx5-chinese-addons fcitx5-pinyin-zhwiki`
或安装rime和雾凇
` sudo pacman -S fcitx5-im fcitx5-rime rime-ice-pinyin-git`

(可选)输入法德古拉主题配置
将整个项目clone到本地：
`mkdir -p ~/.local/share/fcitx5/themes/dracula`
`git clone https://github.com/drbbr/fcitx5-dracula-theme.git ~/.local/share/fcitx5/themes/dracula`
修改配置文件：
`nano  ~/.config/fcitx5/conf/classicui.conf`
添加以下参数：
```
# 垂直候选列表
Vertical Candidate List=False

# 按屏幕 DPI 使用
PerScreenDPI=True

# Font (设置成你喜欢的字体)
Font="思源黑体 CN Medium 13"

# 主题
Theme=dracula
```
5.niri配置
你可以先把我的配置拷贝到u盘或git克隆我的配置（有网络要求）
`git clone https://github.com/Aidens-fox/NiriConfiguration`

然后把配置文件转移到.config/下
6.一些软件的安装
`sudo pacman -Syyu`
`sudo pacman -S kitty swww swaybg imv yazi caja xwayland-satellite udiskie fish file-roller firefox  librewolf nwg-look nwg-bar rofi  power-profiles-daemon  light  mpv`
7.更改sell
 chsh -s  /bin/fish 用户名
或zsh
`sh -c "$(wget https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"`
结尾
       好了，这些东西也算是配置和研究了几个月了，可能有一些设置不合理，请根据实际情况调整
