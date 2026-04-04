### 前言

在这几天，我写了一个后安装脚本，因为我使用的archlinux不像nixos可以依靠一个配置文件来快速配置系统，这样在新系统上就需要手动的配置和安装软件什么的，需要耗费些时间，这显然不是我可以接受的，所以我写了一个脚本来自动化配置我的系统,来减少在新系统的配置时间
如果你需要这个脚本(appinstall.sh)，你可以在我的仓库里下载使用：

https://github.com/Aidens-fox/dwm

#### 注:appinstall脚本只针对基本系统，如果已经不是基本系统请不要运行!

### 我都写了什么

脚本主要内容：
- 换软件源（清华）
- 添加第三方源(CN源)
- 安装必要软件
- 更换终端解释器（zsh）
- 编译安装dwm和dmenu
- 简体中文本地化

<details>
  <summary>点击查看脚本</summary>

  ```
#!/bin/bash
#作者：Aidens-fox
#2026-04-03
#版本:1.1
echo "set Software mirror site(tuna)"
sudo bash  -c 'echo "Server = https://mirrors.tuna.tsinghua.edu.cn/archlinux/\$repo/os/\$arch" > /etc/pacman.d/mirrorlist'
echo "set archCN"
sudo bash -c 'echo -e "\n[archlinuxcn]\nServer = https://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/\$arch" >> /etc/pacman.conf'
sudo pacman -Syyu
echo "install yay,archlinuxcn-keyring"
sudo pacman -S archlinuxcn-keyring
sudo pacman -S  yay base-devel git
echo "install xorg"
sudo pacman -S xorg-server xorg-xinit xorg-xrandr xorg-xsetroot xorg-xset xsel xorg-xkill libx11 libxft libxinerama
echo "install Font"
sudo pacman -S ttf-sarasa-gothic ttf-jetbrains-mono-nerd noto-fonts-emoji noto-fonts-cjk 
echo "install Terminal nvim"
sudo pacman -S alacritty neovim mpv yazi ueberzugpp  
echo "install zsh"
sudo pacman -S zsh-completions zsh
chsh -s /usr/bin/zsh
echo "cp dwm"
mkdir  -p  $HOME/.config
cp  -r dwm $HOME/.config/
echo "install dwm"
cd $HOME/.config/dwm
sudo make clean install
echo "cp dmenu"
cd $HOME/dwm
cp -r dmenu $HOME/.config/
cd $HOME/.config/dmenu
sudo make clean install
echo "cp alacritty "
cd $HOME/dwm
cp -r alacritty $HOME/.config/
echo "cp nvim "
cd $HOME/dwm
cp -r nvim $HOME/.config/
echo "cp .xinitrc"
cp -r .xinitrc $HOME/
chmod +x $HOME/.xinitrc
echo "cp .zshrc"
cp -r .zshrc $HOME/
echo "install fcitx5"
yay -S fcitx5-im fcitx5-input-support fcitx5-chinese-addons fcitx5-pinyin-zhwiki
sudo bash  -c 'echo "GTK_IM_MODULE=fcitx" >> /etc/environment'
sudo bash  -c 'echo "QT_IM_MODULE=fcitx" >> /etc/environment'
sudo bash  -c 'echo "XMODIFIERS=@im=fcitx" >> /etc/environment'
sudo bash  -c 'echo "SDL_IM_MODULE=fcitx" >> /etc/environment'
sudo bash  -c 'echo "GLFW_IM_MODULE=ibus" >> /etc/environment'
echo "set zh_CN"
sudo bash -c 'echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen'
sudo bash -c 'echo "zh_CN.UTF-8 UTF-8" >> /etc/locale.gen'
sudo locale-gen
 ```
 
 </details>

### 使用脚本

#### 在使用脚本需要注意的是：appinstall脚本只针对基本系统，如果已经不是基本系统请不要运行!

我们要使用肯定是需要下载，我们只需要使用git clone就可以了，如果你网络环境不好请在其他设备上下载并拷贝到u盘上

`git clone https://github.com/Aidens-fox/dwm.git`

然后我们需要给他赋权限

`cd dwm`

`chmod +777 appinstall.sh`

最后执行脚本

`./appinstall.sh`

等待脚本执行完成后需要手动重启（更换终端解释器需要）

`reboot`

重新进入tty后输入命令进入dwm

`startx`