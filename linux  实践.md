# linux  实践

下载软件

```
yay -S 软件名称
```

如何查找软件名称

在bing.com中用	AUR 搜索软件名称



gitlazy使用

a	添加上传文件

c	暂传本地

P	上传文件

p	下载云文件







## Pacman 包管理[#](https://arch.icekylin.online/guide/advanced/system-ctl.html#pacman-包管理)

在 archlinux 上安装的软件都通过 Pacman 来进行管理。

为了使用 Pacman 额外的命令需要先安装 [`pacman-contrib`](https://archlinux.org/packages/extra/x86_64/pacman-contrib/)extra / aur。

安装 `pacman-contrib` ：

extraaur (git)

bash

```
sudo pacman -S pacman-contrib
```

1

可以把 Pacman 理解为一个软件管理器（软件管家？），可以进行软件的安装、删除、查询等：

bash

```
sudo pacman -S package_name # 安装软件包

pacman -Ss # 在同步数据库中搜索包，包括包的名称和描述

sudo pacman -Syu # 升级系统。 -y:标记刷新、-yy：标记强制刷新、-u：标记升级动作（一般使用 -Syu 即可）

sudo pacman -Rns package_name # 删除软件包，及其所有没有被其他已安装软件包使用的依赖包

sudo pacman -R package_name # 删除软件包，保留其全部已经安装的依赖关系

pacman -Qi package_name # 检查已安装包的相关信息。-Q：查询本地软件包数据库

pacman -Qdt # 找出孤立包。-d：标记依赖包、-t：标记不需要的包、-dt：合并标记孤立包

sudo pacman -Rns $(pacman -Qtdq) # 删除孤立包

sudo pacman -Fy # 更新命令查询文件列表数据库

pacman -F some_command # 当不知道某个命令属于哪个包时，用来在远程软件包中查询某个命令属于哪个包（即使没有安装）

pactree package_name # 查看一个包的依赖树
```





