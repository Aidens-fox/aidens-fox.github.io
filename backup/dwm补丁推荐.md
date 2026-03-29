### 前言

当你使用git克隆下dwm源代码后进行简单配置修改然后编译安装，在.xinitrc添加exec dwm后启动dwm,你可能会发现这dwm也太干净了，输入确实可以使用，但是可能有一些地方不太喜欢，所以我们可以使用补丁来增强或改善dwm的功能体验,本篇博文将会推荐7个dwm补丁来改善你的dwm体验，你也可以看看我的dwm配置:

https://github.com/Aidens-fox/dwm

### 补丁介绍

#### 1.[pertag](https://dwm.suckless.org/patches/pertag/)

当你打开2个以上的tag时，如果你在其中一个tag使用mod+j等来调整布局，那么在切换到下一个tag时你会发现这个tag的布局和上一个的tag一样，这样的话，如果下一个tag打开浏览器然后一个终端，本来是默认相同宽度的，但因为上一个tag调整了布局，让这个tag失去了刚才的布局，这就有点一些体验了，而pertag可以让tag相互独立，而不是同步更改，由此来提升使用体验

#### 2.[restartsig](https://dwm.suckless.org/patches/restartsig/)

当你修改完配置编译完成之后，你需要退出重新进入，如果只是偶然修改一些还好，但是如果是需要多次修改就有的麻烦了，退出进入要花时间，而且之前打开的窗口也没用了，也要重新打开，这就和麻烦了，而restartsig可以让你在不退出进入的情况下刷新配置，不过在编译安装之前需要指定快捷键不然可能会报错，像我就是绑定mod+ctrl+q

`{ MODKEY|ControlMask, XK_q, quit, {1} },`

#### 3.[attachaside](https://dwm.suckless.org/patches/attachaside/)

我们在打开新窗口时，它会自动抢占“主窗口（Master）”的位置，而原来的主窗口会被挤到右侧的“堆栈区（Stack），如果我们是使用浏览器，然后在打开终端后又打开几个窗口，主窗口早就不在浏览器了，这就很影响使用了，而attachaside可以让新窗口自动到堆栈区，保持当前主窗口不变,如果需要改变主窗口只需要mod+enter就可以切换了

默认:新窗口（N）抢占左侧，原窗口（P）被挤到右侧

``` text
+-----------------+-------+
|                 |       |
|                 |   P   |
|        N        +-------+
|                 |       |
|                 |       |
+-----------------+-------+
``` 

使用补丁:主窗口（P）不动，新窗口（N）出现在右侧堆栈区的顶部

``` text
+-----------------+-------+
|                 |   N   |
|                 |       |
|        P        +-------+
|                 |       |
|                 |       |
+-----------------+-------+
```

#### 4.[actualfullscreen](https://dwm.suckless.org/patches/actualfullscreen/)

dwm 默认的全屏模式（例如某些浏览器触发的全屏）有时会保留状态栏，或者只是简单地平铺充满。actualfullscreen 可以让当前窗口会真正遮盖住状态栏，并填满整个显示器，而不改变原有的窗口平铺布局，但是在编译之前还是有先设置一些快捷键，不然可能报错

`{ MODKEY|ShiftMask,                       XK_f,   togglefullscr, {0} },`

#### 5.[alwayscenter](https://dwm.suckless.org/patches/alwayscenter/)

在默认的 dwm 中，当你打开一个设置为“浮动”的窗口（比如确认弹窗、或者简单的文件选择框）时，它们通常会出现在屏幕的左上角,十分的反直觉，需要移动鼠标到左上角才可以操作，十分不便，而alwayscenter可以让所有新创建的浮动窗口自动显示在屏幕正中央

6.[tagshift](https://dwm.suckless.org/patches/tagshift/)

在默认的dwm中只有使用mod+数字来切换tag，有点无聊，而tagshift可以使用方向键或其他来切换tag，但需要绑定快捷键：

````
        /* 移动视图（切换当前显示的标签组） */
        { MODKEY,                       XK_Left,  shiftview, {.i = -1 } },
        { MODKEY,                       XK_Right, shiftview, {.i = +1 } },
        /* 移动窗口（改变当前窗口的归属标签） */
        { MODKEY|ShiftMask,             XK_Left,  shifttag,  {.i = -1 } },
        { MODKEY|ShiftMask,             XK_Right, shifttag,  {.i = +1 } },
````

7.[resizecorners](https://dwm.suckless.org/patches/resizecorners/)

在默认的 dwm 中，调整浮动窗口大小只能通过点击窗口的右下角来拖拽。这在现代大屏幕或者多窗口操作时显得非常笨拙,resizecorners 补丁打破了这个限制，让你从四个角都能进行缩放


