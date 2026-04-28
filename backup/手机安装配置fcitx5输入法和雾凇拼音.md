### 前言

在手机上，输入法是我们经常使用的东西，所以一个好用的输入法就非常重要了，像比较主流的输入法有：搜狗输入法，讯飞输入法，百度输入法等，这些输入法在应用市场评分都还可以，但是我是不太可能使用这些输入法的，因为我对隐私还有大小是有要求的，而上面说的输入法普遍有数据收集问题，对数据安全十分不利，这些输入法的大小也较大，很多功能也根本不需要，所以我放弃了使用这些输入法的想法，而是使用了一个开源方案-[fcitx5](https://github.com/fcitx5-android/fcitx5-android)

本博文部分内容参考[晨鹤部落格](https://chenhe.me/zh/posts/rime-android/)

### 安装fcitx5

我们在fcitx5的仓库里下载安装

仓库地址:

https://github.com/fcitx5-android/fcitx5-android

安装后根据软件提示进行更换输入法，完成后就可以使用了，不过默认的拼音方案可能会有点不太好用，所以我们可以使用另一个方案-雾凇拼音，在使用雾凇拼音之前我们需要先安装一个插件-rime:我们在fcitx5的[发布页面](https://github.com/fcitx5-android/fcitx5-android/releases),可以看到表格中有Download那一栏，选择下载plugin.rime那一列，一般都是arm64-v8a,如果无法运行安装请下载armeabi-v7a(fcitx5也同理)

<img width="1117" height="850" alt="Image" src="https://github.com/user-attachments/assets/29f9a888-889c-468b-a506-2256433fa1a9" />

发布页面:

https://github.com/fcitx5-android/fcitx5-android/releases

下载安装好插件后我们还需要下载雾凇拼音，雾凇拼音有长期维护词库，支持简体 | 全拼 | 双拼，是一个十分成熟的方案，在github上有16多过star,所以相对于之前的拼音有更好的体验

仓库地址:

https://github.com/iDvel/rime-ice

我们在发布页面选择full.zip文件下载，full.zip包含以下所有文件，可以一次性安装好所以功能，其他比如all_dicts.zip这些就不太建议下载了

<img width="1089" height="745" alt="Image" src="https://github.com/user-attachments/assets/dfe8db2c-65d2-43a5-82cb-cbb2cf596865" />

### 配置雾凇拼音

下载好雾凇拼音的zip文件后，我们需要把它解压，这里推荐一个十分好用的文件管理器-MT管理器

软件官网：

https://mt2.cn/

解压完成后把所以文件移动到Android\data\org.fcitx.fcitx5.android\files\data\rime里就可以了

移动完成后，随便打开一个可以唤出输入法的软件，点击候选词栏的更多按钮（三个点），点击重载配置，过程会持续一段时间，请耐心等待，完成后你应该可以看到空格键变成"中州韵(雾)"了

![Image](https://github.com/user-attachments/assets/a5f65e03-fb17-4f25-91f0-62c2e29310ed)


