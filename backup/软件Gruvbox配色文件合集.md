### 前言

Gruvbox是我最喜欢的一个主题，所以我肯定是希望我打开的大部分软件都是Gruvbox配色的，但是很多软件在默认的配色方案是没有Gruvbox这个配色方案的，所以就要借助一些配置文件来实现Gruvbox配色方案

#### 1.alacritty

由于alacritty默认是没有主题文件的，所以需要借助一些仓库：

https://github.com/alacritty/alacritty-theme

克隆仓库,或下载您选择的主题:

```
mkdir -p ~/.config/alacritty/themes
git clone https://github.com/alacritty/alacritty-theme ~/.config/alacritty/themes

```

添加一个导入alacritty.toml替换{theme}与你的理想色度处理:

```
[general]
import = [
    "~/.config/alacritty/themes/themes/{theme}.toml"

]

```

或者你也可以在配置文件中添加：

<details>
  <summary>点击查看脚本</summary>

```
# Colors (Gruvbox dark)

# Default colors
[colors.primary]
# hard contrast background = = '#1d2021'
background = '#282828'
# soft contrast background = = '#32302f'
foreground = '#ebdbb2'

# Normal colors
[colors.normal]
black   = '#282828'
red     = '#cc241d'
green   = '#98971a'
yellow  = '#d79921'
blue    = '#458588'
magenta = '#b16286'
cyan    = '#689d6a'
white   = '#a89984'

# Bright colors
[colors.bright]
black   = '#928374'
red     = '#fb4934'
green   = '#b8bb26'
yellow  = '#fabd2f'
blue    = '#83a598'
magenta = '#d3869b'
cyan    = '#8ec07c'
white   = '#ebdbb2'
```

 </details>
 
#### 2.GTK主题

我们可以使用nwg-look来切换主题

`sudo pacman -S nwg-look`

仓库链接：

https://github.com/Fausto-Korpsvart/Gruvbox-GTK-Theme

如果你是archlinux，你也可以使用aur仓库

`yay -S gruvbox-gtk-theme-git`

#### 3.Telegram

Telegram默认是没有gruvbox的配色方案的，所以我们可以使用配色文件来添加gruvbox配色

仓库地址：

https://github.com/y0av/telegram-gruvbox

#### 4.qbittorrent 

在默认的qbittorrent 是只有白色的，在晚上就十分刺眼，我们可以使用配色文件来效果

仓库地址：

https://github.com/MahdiMirzadeh/qbittorrent

#### 5.图标主题

在默认的软件图标是软件的默认图标，十分不统一，所以可以借助图标主题来增加美观性

仓库地址：

https://github.com/SylEleuth/gruvbox-plus-icon-pack

#### 6.鼠标主题

仓库地址：

https://www.gnome-look.org/p/2302110

7.fcitx5主题

仓库地址：

https://github.com/pu-007/fcitx5-gruvbox-dark-theme

或者使用aur

`yay -S fcitx5-gruvbox-dark-theme-git`

#### 7.nvim主题

仓库地址：

https://github.com/ellisonleao/gruvbox.nvim

如果你是packer，在packer配置文件中添加

` use { "ellisonleao/gruvbox.nvim" }`

然后在nvim配置文件中启用

`vim.cmd([[colorscheme gruvbox]])`

#### 8.emacs

仓库地址：

https://github.com/Greduan/emacs-theme-gruvbox
