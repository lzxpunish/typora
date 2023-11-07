# linux  实践

下载软件

```sh
yay -S 软件名称
```

如何查找软件名称

在bing.com中用	AUR 搜索软件名称





## 安装lazygit

```sh
sudo pacman -S lazygit
```



## gitlazy使用

a	添加上传文件

c	暂传本地

P	上传文件

p	下载云文件







## Pacman 包管理[#](https://arch.icekylin.online/guide/advanced/system-ctl.html#pacman-包管理)

在 archlinux 上安装的软件都通过 Pacman 来进行管理。

可以把 Pacman 理解为一个软件管理器（软件管家？），可以进行软件的安装、删除、查询等：



bash

```sh
sudo pacman -S package_name # 安装软件包

sudo pacman -Si # 在同步数据库中搜索包，包括包的名称和描述

sudo pacman -Syyu # 升级系统。 -y:标记刷新、-yy：标记强制刷新、-u：标记升级动作（一般使用 -Syu 即可）

sudo pacman -Rns package_name # 删除软件包，及其所有没有被其他已安装软件包使用的依赖包

sudo pacman -R package_name # 删除软件包，保留其全部已经安装的依赖关系

pacman -Qdt # 找出孤立包。-d：标记依赖包、-t：标记不需要的包、-dt：合并标记孤立包

sudo pacman -Rns $(pacman -Qtdq) # 删除孤立包
```





以下的玩意没有就直接	yay -S 软件名字

```sh
neofetch	#	展示系统配置

nvim	#	文本编辑器	下载的名称叫neovim

btop	#	展示系统状态

ranger	#	终端文件管理器

gdu	#	查看硬盘使用

nvim .zshrc	#	.zshrc是zsh的配置文件，zsh 基本兼容 bash

source .zshrc	#	重新加载一遍配置文件
```



## 安装输入法

```sh
sudo pacman -S fcitx5-im # 输入法基础包组

sudo pacman -S fcitx5-chinese-addons # 官方中文输入引擎

sudo pacman -S fcitx5-pinyin-moegirl # 萌娘百科词库。二刺猿必备（archlinuxcn）

sudo pacman -S fcitx5-material-color # 输入法主题
```

此外，我们还需要设置环境变量。通过 `vim` 编辑文件 `/etc/environment`：

```sh
sudo vim /etc/environment
```

在文件中加入以下内容并保存退出：

```sh
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
SDL_IM_MODULE=fcitx
GLFW_IM_MODULE=ibus
```





## 安装和配置 v2ray 和 v2rayA: 

```sh
sudo pacman -S v2ray v2raya
```

安装后启动服务：

```
sudo systemctl enable --now v2raya
```

随后在开始菜单中搜索 v2rayA，点击即可打开浏览器页面。在其中加入订阅(没有魔法上网节点？请参考[原文档相关内容](https://archlinuxstudio.github.io/ArchLinuxTutorial/#/rookie/fxckGFW?id=已有科学上网的节点的情况))。在设置中建议开启全局透明代理(选择`大陆白名单`)，同时开启防止 DNS 劫持功能，否则可能会拿不到被 DNS 污染的资源(如 github raw)。



## 基础功能包

```sh
sudo pacman -S sof-firmware alsa-firmware alsa-ucm-conf # 声音固件
sudo pacman -S ntfs-3g # 使系统可以识别 NTFS 格式的硬盘
sudo pacman -S adobe-source-han-serif-cn-fonts wqy-zenhei # 安装几个开源中文字体。一般装上文泉驿就能解决大多 wine 应用中文方块的问题
sudo pacman -S noto-fonts noto-fonts-cjk noto-fonts-emoji noto-fonts-extra # 安装谷歌开源字体及表情
sudo pacman -S firefox google-chrome  # 安装常用的火狐、chrome浏览器
sudo pacman -S ark # 压缩软件。在 dolphin 中可用右键解压压缩包
sudo pacman -S packagekit-qt5 packagekit appstream-qt appstream # 确保 Discover（软件中心）可用，需重启
sudo pacman -S gwenview # 图片查看器
sudo pacman -S steam # 游戏商店。稍后看完显卡驱动章节再使用
```



## 安装使用zsh及其精简包

```sh
# 找一个地方clone本仓库 例如 ~/.config
git clone https://github.com/yaocccc/omz

# 在你的zsh配置里 source ~/.config/omz/omz.zsh (举例)
echo "source ~/.config/omz/omz.zsh" >> ~/.zshrc
```

要求以下配置

- zsh

  ```sh
  sudo pacman -S zsh	#	 通过以下命令安装 zsh 相关的包
  ```

  

- fzf

  ```sh
  请自行安装fzf
  git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
  ~/.fzf/install
  ```

  

- fd

	```sh
	# 请自行安装fd
	On Arch Linux: pacman -S fd
	```

- bat (可选 更好的文本预览效果)

- exa (可选 更好的目录预览效果)

- ueberzug (可选 可在x11终端下预览图片)



## openbox的快捷命令

**这里的mod在键盘上为win键**

| Keybinding                                    | Function                                                     |
| --------------------------------------------- | ------------------------------------------------------------ |
| **mod+Return**                                | Open a terminal (alacritty)    打开终端                      |
| **mod+f**                                     | Open a file manager (thunar)    打开文件管理器               |
| **mod+w**                                     | Open a browser (firefox)    打开浏览器（火狐）               |
| **mod+e**                                     | Open a text editor (geany)    打开文本编辑器                 |
| **mod+(1-5)**                                 | Change Workspaces    更改工作区                              |
| **mod+Shift+(1-5)**                           | Move application to a specific Workspace    将应用程序移动到特定的工作区 |
| **alt/mod+Tab**                               | Switch applications (Microsoft windows style)    切换应用程序(Microsoftwindows 样式) |
| **mod+(Up/Down/Left/Right)**                  | Snap window to corners    弹窗到角落                         |
| **mod+k**                                     | Snap window to top right    对齐窗口到右上角                 |
| **mod+h**                                     | Snap window to top left    对齐窗口到左上角                  |
| **mod+j**                                     | Snap window to bottom left    对齐窗口到左下角               |
| **mod+l**                                     | Snap window to bottom right    对齐窗口到右下角              |
| **mod+alt+up**                                | Move Window up    上移窗口                                   |
| **mod+alt+down**                              | Move Window down    下移窗口                                 |
| **mod+alt+left**                              | Move Window left  左移窗口                                   |
| **mod+alt+right**                             | Move Window right    右移窗口                                |
| **control+alt+right**                         | Resize window to right  向右调整窗口大小                     |
| **control+alt+left**                          | Resize window to left    向左调整窗口大小                    |
| **control+alt+down**                          | Resize window to down    向下调整窗口大小                    |
| **control+alt+up**                            | Resize window to up    向上调整窗口大小                      |
| **mod+Shift+Left/Right**                      | Send Application to next/prev desktop    将应用程序发送到下一个/上一个桌面 |
| **up+up+down+down+left+right+left+right+B+A** | Get super powers    芜湖  上上下下左右左右baba               |
| **alt+F1**                                    | Opens app launcher    打开应用程序启动器                     |
| **mod+n**                                     | Opens network menu  打开网络菜单                             |
| **mod+x**                                     | Opens a powermenu  打开电源菜单                              |
| **mod+m**                                     | Opens the music menu    打开音乐菜单                         |
| **mod+i**                                     | Opens internet menu    打开网络菜单  目前已经失效            |
| **mod+s**                                     | Opens screenshoting menu  打开屏幕截图菜单                   |
| **mod+r**                                     | Runs apps as root   作为 root 用户运行应用程序               |
| **mod+w**                                     | Opens windows menu    打开颜色选择器                         |
| **mod+p**                                     | Opens the color picker  打开颜色选择器                       |
| **Print**                                     | Takes a screenshot    截屏                                   |
| **mod+Print**                                 | Takes a screenshot (5s delay)    截屏（5秒延迟）             |
| **Shift+Print**                               | Takes a screenshot (10s delay)    截屏（10秒延迟）           |
| **Control+Print**                             | Takes a screenshot of active window    活动窗口的截图        |
| **Control+Alt+Print**                         | Takes a screenshot of an area    区域截图                    |
| **mod+v**                                     | Open tasks menu    打开任务菜单                              |
| **Control+Alt+t**                             | Open xfce4-terminal    打开 xfce4-终端                       |
| **Control+Alt+v**                             | Open vim   打开vim                                           |
| **Control+Alt+n**                             | Open neovim    打开neovim                                    |
| **Control+Alt+r**                             | Open ranger    打开ranger  终端文件管理器                    |
| **Control+Alt+h**                             | Open htop  打开htop 查看进程，内存占用                       |
| **Control+Alt+b**                             | Open bashtop 打开bashtop                                     |
| **alt+Control+l**                             | Launches the lockscreen    打开锁定屏幕                      |
| **control+shift+Escape**                      | Exit openbox                                                 |
| **control+Shift+BackSpace**                   | Restart openbox                                              |
| **control+shift+R**                           | Reconfigure openbox  重新配置                                |
| **mod+Escape**                                | Select window and kill it (xkill)    选择窗口并杀死它        |
| **mod+c/q**                                   | Close focused window    关闭聚焦窗口                         |
| **alt+F5**                                    | Minimise window to taskbar    最小化任务栏窗口               |
| **alt+F6**                                    | Toggle Maximize    切换最大化                                |
| **alt+F7**                                    | ToggleDecorations  切换装饰                                  |
| **mod+d**                                     | Show desktop  显示桌面                                       |
| **alt+r**                                     | Resize window    缩放窗口                                    |
| **alt+m**                                     | Move window    移动窗口                                      |
| **mod+Space**                                 | Show root menu    显示root菜单                               |
| **control+alt+space**                         | Show app menu    显示应用程序菜单                            |
| **alt+space**                                 | Show client Menu    显示用户菜单                             |

