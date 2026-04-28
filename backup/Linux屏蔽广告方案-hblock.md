### 前言
我们在使用浏览器浏览一些网站时，网站就会跳出一些广告，一些还包含恶意链接，对我们的数据安全十分不利，所以就要借助一些工具来尽可能的避免悲剧的方式，也就是我们的hblock

### hblock是什么
hblock是通过屏蔽广告、跟踪和恶意软件域名来提升您的安全性和隐私性的软件，让你的设备保持安全

### 它是怎么实现这个功能的
hblock通过修改添加hosts文件来阻止您的系统通过与它们建立联系，简单粗暴

##### 注意：因为是直接修改hosts文件，所以一定要在使用之前备份文件

安装软件

`sudo pacman -S hblock`

### 配置软件
我们使用文本编辑器打开配置文件
`sudo -E nvim /etc/hblock.conf`
我们在文件中添加：

````
SOURCES=(
 https://raw.githubusercontent.com/TG-Twilight/AWAvenue-Ads-Rule/main/AWAvenue-Ads-Rule.txt
 https://raw.githubusercontent.com/jdlingyu/ad-wars/master/hosts 
 https://raw.githubusercontent.com/Goooler/1024_hosts/master/hosts 
 https://raw.githubusercontent.com/yous/YousList/master/hosts.txt 
 https://raw.githubusercontent.com/Discover999/Host-Ban-Tik-Tok/master/TikTokHost.txt

)

````
配置文件中SOURCES是规则链接，个人建议是至少有一个全能规则，不然可能效果不佳
规则链接:
1.yhosts:

https://raw.githubusercontent.com/vokins/yhosts/master/hosts （国内维护者屏蔽国内网站广告）

2.大圣净化：

https://raw.githubusercontent.com/jdlingyu/ad-wars/master/hosts （主要针对国内视频网站）

3.1024_hosts：

https://raw.githubusercontent.com/Goooler/1024_hosts/master/hosts （1024网站和澳门皇家赌场）

4.YousList: 

https://raw.githubusercontent.com/yous/YousList/master/hosts.txt （主要屏蔽韩国人使用的网站广告）

5.秋风广告规则

https://raw.githubusercontent.com/TG-Twilight/AWAvenue-Ads-Rule/main/AWAvenue-Ads-Rule.txt

或

https://gcore.jsdelivr.net/gh/TG-Twilight/AWAvenue-Ads-Rule@main/AWAvenue-Ads-Rule.txt

### 更新规则
我们在配置好文件后执行

`hblock`

等待命令执行完成

### 测试是否屏蔽广告
我们使用去广告效果检测网站

1.https://checkadblock.ru/

2.https://blockads.fivefilters.org/

3.https://canyoublockit.com/extreme-test/ 
