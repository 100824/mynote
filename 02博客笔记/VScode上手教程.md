---
title: VScode上手教程
date: 2020-03-14 01:31:08
categories:
- 工具
---
## vscode上手教程
由于电脑太多个软件，pycharm，goland，sublime，还有对markdowm的支持不是很友好，所以决定上手传说中强大的vscode  
### 下载
直接从官网下载即可  
https://code.visualstudio.com
### 汉化
为了方便熟悉软件，先使用了汉化版，直接在插件搜索chinese，点击install之后重启，就OK了
### 接入linux子系统
打开后提示我可以安装一个插件，用于直接打开及编辑linux子系统的文件（非常方便），于是就按着提示下载了（remote-WLS）。试了一下，的确非常方便，可以直接打开linux的整个工作目录，而且也能直接运行命令行的命令。
### 搭建运行环境
万能语言运行环境 （Code Runner），安装这个插件，然后打开某个.py文件，ctrl+shift+N即可运行，非常方便
### 搭建python环境
第一次打开.py文件会提示你安装python的插件，按提示安装后就可以调试代码了（前提是电脑已经安装了python）
### 远程开发工具
插件Remote Development，通过SSH(Secure Shell)的方式连接到远程服务器，开发很方便，先记着，以后会用到。
### markdowm插件
Markdown Preview Enhanced，预览的界面得到优化  
Markdown PDF 可以直接导出pdf  
### leetcode插件
直接搜索leetcode插件安装，可能需要另外安装node.js，然后输入登录的账号密码就可以在vscode上刷leetcode

### 快捷操作
* F5              开启调试  
* ctrl+shift+ `   打开终端 
* ctrl+shift+F    打开搜索
* ctrl + delete   删除右边
* home            跳到行头
* end             跳到行尾
* ctrl            单词切分
* Ctrl + ←   删除整个单词
* shift 加方向键 选取
* ctrl+shift+ N  打开新的窗口
* ctrl+shift+ W  关闭当前窗口
* ctrl+ P 快速打开
* ctrl+shift+ P  显示命令面板(同F1)
* ctrl+shift+ \  跳转到匹配括号
* ALT+ ↑  ↓    当前行上移下移
* ctrl + C    复制行
* ctrl + X    剪切行
* ctrl + shift  ↑  ↓  向上向下复制当前行 
* ctrl + shift + K  删除行 
* ctrl + home   跳到文章开头
* ctrl + end    跳到文章末
* ctrl + G  跳转到。。行
* ctrl + H  替换
* ctrl + D  跳到下一个查找匹配
* F12   跳转到定义
* shift + F12  显示引用
* ctrl + K 再加F12  将定义打开到侧边
* ctrl + F4 关闭当前标签页
* ctrl + -  =  放大，缩小
* ctrl + B  打开关闭侧边栏
* F5 调试  
* 继续F5  下一个断点 
* F11 下一步
* shift + F5  停止调试
* ctrl + 1,2,3 切换左中右窗口
