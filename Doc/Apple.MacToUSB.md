#Mac OS X 10.9 制作安装U盘/应急启动U盘

首先 下载 OS X 10.9 安装镜像([Install OS X Mavericks.app.dmg]())  并拷贝至Mac系统下

![MacToUSB](../images/apple/mactousb01.png?raw=true)

点击 `前往` - `实用工具` 

![MacToUSB](../images/apple/mactousb02.png?raw=true)

打开 `终端` 

![MacToUSB](../images/apple/mactousb03.png?raw=true)

输入显示隐藏文件的命令：
```
defaults write com.apple.finder AppleShowAllFiles YES  
或  
defaults write com.apple.finder AppleShowAllFiles -bool true
```

>**注：**  
关闭显示隐藏文件命令为:  
defaults write com.apple.finder AppleShowAllFiles NO  
defaults write com.apple.finder AppleShowAllFiles -bool false

![MacToUSB](../images/apple/mactousb04.png?raw=true)

关闭 `终端` ，返回 `实用工具` ，打开 `磁盘工具` 

![MacToUSB](../images/apple/mactousb05.png?raw=true)

双击桌面上的 OSX 1.9镜像文件，系统会将镜像挂载成一个磁盘，显示在系统的最右侧。
可以点击 `跳过` 来绕过验证

![MacToUSB](../images/apple/mactousb06.png?raw=true)

屏幕右方出现了挂载安装镜像的 `磁盘` ，双击打开，对 `安装OS X Mavericks` 文件 `右键` - `显示包内容` 
>**注：**  
挂载完后会默认打开 `磁盘`

![MacToUSB](../images/apple/mactousb07.png?raw=true)

进入目录 `Contents/SharedSupport` ，双击目录下的镜像 `InstallESD.dmg` ，再将这个镜像挂载成一个 `磁盘`

![MacToUSB](../images/apple/mactousb08.png?raw=true)
![MacToUSB](../images/apple/mactousb09.png?raw=true)


屏幕右方会出现挂载好的  `OS X Install ESD`  磁盘，双击打开，将其中的镜像 `BaseSystem.dmg` 镜像拖至 `磁盘工具` 

![MacToUSB](../images/apple/mactousb10.png?raw=true)

插入U盘，在 `磁盘工具` 左侧点击插入的U盘，选择 `抹掉` ，格式选择为 `Mac OS 扩展(日志式)` ，点击 `抹掉` 进行格式化

![MacToUSB](../images/apple/mactousb11.png?raw=true)

点击 `分区` ，可以设置多个分区。
用来制作启动盘的分区，格式需要选择 `Mac OS 扩展(日志式)` ，并预留好足够的空间。
点击 `选项` 设置分区方案

![MacToUSB](../images/apple/mactousb12.png?raw=true)

分区方案需选择为 `GUID分区表` 
>**注：**  
其它分区也必须更改为GUID分区表

![MacToUSB](../images/apple/mactousb13.png?raw=true)

其他分区可以选择为  `ExFAT` 格式，可以用来存储文件，并可以在Windows系统下使用。
同样要点击 `选项` 设置分区方案为 `GUID` ，设置完毕后点击 `应用` 进行分区
>**注：**  
我这样设置之后Windows并不能正常访问ExFAT分区，猜测的故障点可能是ExFAT分区的分区方案应该设置为MBR，但不知这样设置后还能不能成功引导OSX系统

![MacToUSB](../images/apple/mactousb14.png?raw=true)

U盘分区完毕后，点击磁盘工具中之前弄好的 `BaseSystem.dmg` 镜像，点击 `恢复` ，并将需要制作为引导分区的U盘分区拖进 `目的磁盘` 
点击 `恢复` 按钮开始恢复U盘

![MacToUSB](../images/apple/mactousb15.png?raw=true)

恢复完毕后，该U盘分区的名称会自动更改为 `OS X Base System` 
进入该分区的 `System/Installation` 目录下，删除文件 `Packages` 

![MacToUSB](../images/apple/mactousb16.png?raw=true)

回到之前挂载的 `磁盘` : `OS X Install ESD` ，将磁盘内的文件全部拷贝至 U盘分区 `OS X BaseSystem` 下的 `System/Installation` 目录
>**注：**  
`.DS_Stone` 为OSX系统目录文件，不用拷贝

![MacToUSB](../images/apple/mactousb17.png?raw=true)

文件较大，请耐心等待，拷贝完毕后，OS X 10.9 的安装U盘就制作完毕了。正常 `推出` U盘，即可用于在苹果电脑上安装/急救系统。
>**注：**  
使用方法： 开机按住  `option` 键，选择从U盘启动

![MacToUSB](../images/apple/mactousb18.png?raw=true)