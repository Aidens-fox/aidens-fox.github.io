首先先展示一下配置效果

<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/ec830154-a467-4cc7-93b9-470a24c9cb3c" />

从左到右的模块分别是：应用启动器，硬盘占用，工作区，当前应用信息，音量，网络，性能，处理器，内存，温度，亮度，电池，时间，后台应用状态，开关
你也可以直接克隆我的配置
https://github.com/Aidens-fox/archlinuxinstall-swaywmConfiguration


        那我们就先打开config.jsonc吧
第一个就是应用启动器
````
"custom/os_button": {
        "format": "  󰏖  ",
        "on-click": "rofi -show drun  -show-icons -theme .config/rofi/themes/launchpad.rasi",
        "tooltip": false
    },
````
第二个是开关

````
 "custom/powewe": {
        "format" : " ⏻ ",
                "tooltip": false,
        "on-click": "nwg-bar",
},

````
要注意的模块写好后记得在style.css  文件添加说明如
````
#custom-powewe {
  font-size: 20px;
        background-color: #225699
}

#custom-os_button {
        font-family: "JetBrainsMono Nerd Font";
  font-size: 20px;
/*      transition: all 0.25s cubic-bezier(0.165, 0.84, 0.44, 1); */
        background-color: #225699
}
````
如后我们来讲讲美化
还是打开style.css 文件
添加圆角
`border-radius: 4px;`
隐藏白线条
````
window#waybar {
    background-color: rgba(43, 48, 59, 0.0);
    border-bottom: 0px solid rgba(100, 114, 125, 0.5);
    color: #ffffff;
    transition-property: background-color;
    transition-duration: .5s;
}
````
工作区美化
````
#workspaces button {
    padding: 0 8px;
    background-color: transparent;
    color: #ffffff;
     border-radius: 4px;
}

#workspaces button.focused {
    background-color: #225699;
    box-shadow: inset 0 -0px #ffffff;
         border-radius: 4px;
}

````
剩下就是统一颜色了
你也可以直接克隆我的配置
https://github.com/Aidens-fox/archlinuxinstall-swaywmConfiguration
