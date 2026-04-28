#### 前言
字幕可以增加视频的可读性，也可以给一些特殊人群一些照顾，在windows上有卡卡字幕助手，而在linux上也有一个软件，也就是whisper
#### 特点
whisper没有图形化界面，所以可以减少不必要的性能开销，而且whisper可以自由选择语言模型，可以说对老旧设备十分友好
#### 下载
在archlinux上我们可以使用aur仓库里的软件包来安装
`yay -S whisper.cpp-git`
除了下载软件本体还需要下载语言模型
https://huggingface.co/ggerganov/whisper.cpp/tree/main
在下载模型的时候选择适合的模型，经过本人测试small模型准确率相对较高，而且时间也可以接受，本人使用笔记本，性能教差，所以只能使用较低级的模型，如果追求高质量，请下载更高级的模型
#### 使用
我们需要先使用ffmpeg提取视频音频
`ffmpeg -i xxx.mp4 xxx.mp3`
如何使用whisper制作字幕文件
`whisper.cpp -m ggml-tiny-q5_1.bin -f ss.mp3 -l zh -osrt`
完成后会在当前目录创建.srt文件，我们可以先使用emacs,nvim等编辑器窗口有没有文字错误
在检查完成后就可以导入到kdenlive里使用
