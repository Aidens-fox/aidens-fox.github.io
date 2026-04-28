- **前言**
    你印象中的终端是什么样子？黑底白字，对比度高，十分刺眼丑陋，那本篇博文可能要打破你的刻板印象了，在本篇博文中我会向你推荐我喜欢的终端主题(github上评分也挺高的):Gruvbox
- **特点**
    gruvbox受badwolf, jellybeans和solarized的启发,采用柔和的“复古”颜色,Gruvbox的主要重点是保持色彩清晰易辨、对比度适中，同时兼顾视觉舒适度。
项目地址：https://github.com/morhetz/gruvbox?tab=readme-ov-file
- **预览**

<img width="1430" height="765" alt="Image" src="https://github.com/user-attachments/assets/742502f2-c861-4f65-8f25-c2f36935c9a5" />

- **色调**

<img width="2784" height="1038" alt="Image" src="https://github.com/user-attachments/assets/a69984b8-eb16-494b-b1b5-2a953d60dfd9" />

**配置主题**
    配置Gruvbox主题很简单，因为主流的终端都内置了这款主题，所以只要去看看官方的维基或论坛就可以了，不过想我正在使用的alacritty就没有内置主题，你可以下载主题在配置文件中指定主题或直接按照参考Gruvbox配色方案设置：
````
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
````
- **其他**
    值得注意的是由于Gruvbox的知名，所以再其他软件也或多或少有这款主题，就比如:nvim/vim,gkt主题等
gruvbox.nvim:
链接:https://github.com/ellisonleao/gruvbox.nvim
gruvbox gtk theme:
链接:https://github.com/Fausto-Korpsvart/Gruvbox-GTK-Theme
