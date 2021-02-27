# MacSetup

- windows 系统请看[windowsSetup](windowsSetup.md)
- 黑苹果请看[hackinstosh](hackintosh/README.md)

## 一、安装之前

重装之前，使用时光机器(Time Machine)，将所有硬盘资料备份到移动硬盘上。这个也可以方便地作为系统快照，恢复之前某个时刻的机器的状态。安装时，请将语言选为**English**

## 二、制作安装盘

### 1. 分区

准备一个 U 盘或移动硬盘（大于等于 8G），最好使用移动硬盘作为介质，速度比 U 盘快，同时可以将移动硬盘作为时光机器和恢复磁盘助手(Recovery Disk Assistant)。

首先在磁盘工具内的 "Options" 里，选择 GUID，否则无法启动，然后在"Partition Layout"将移动硬盘分成三个分区：

- 分区名字 OS，大小 8G，格式是 Mac OS Extended(Journaled)，本地磁盘安装介质，方便以后安装系统。
- 分区名字 Recovery，大小 2G，格式是 Mac OS Extended(Journaled)，恢复助手，用于对系统进行恢复。
- 分区名字 Data，剩余的磁盘空间，格式是 Mac OS Extended(Journaled)，数据备份和时光机器的介质。

### 2. 制作安装盘

- 从 App Store 完成下载后，OS X Yosemite 安装程序会自动启动，不要点击继续，停在安装界面第一页。插入刚才分区好的移动硬盘或者 U 盘，在命令行输入下面的命令，制作安装盘:
- sudo /Applications/Install\ OS\ X\ Yosemite.app/Contents/Resources/createinstallmedia --volume /Volumes/Yosemite --applicationpath /Applications/Install\ OS\ X\ Yosemite.app --nointeraction
- 也可以用 DiskMaker X

Use [Etcher](https://www.balena.io/etcher/)

## 三、安装 OS

安装盘制作完毕后，**重启并按 Option 键**，选择安装盘安装。安装或者恢复之前，一般使用时光机器进行备份，然后用磁盘工具删掉之前的机器磁盘上的内容。

## 四、安装以后

1. 更改安全设置，Sierra allow download app anywhere:

   ```bash
   sudo spctl --master-disable
   ```

   允许从所有来源安装应用程序，在 Security and Privacy 里设置 "Allow apps downloaded from" 选项为 "Anywhere"

1. 更改 trackpad: 在 "Trackpad" 里打开 "Tap to click" 设置. check everything
1. Accessibility Mouse & Trackpad => trackpad options => enable dragging (three finger drag)
1. Accessibility Zoom check use keyboard shortcuts to zoom

## 五、Time Machine

需要注意的是，Mac OS X 会在运行中产生一些临时数据或者中间数据，这些数据往往占用空间较大，而没有保存价值，可以设置成 exclude，常见的有：

```
/Library/Application Support/
/Library/Caches/
/private/var/log/
/private/var/vm/
/private/var/tmp/
~/Downloads/
~/Library/Caches
~/Library/Application Support/MobileSync/
~/.Trash/
~/Documents/Virtual\ Machines.localized/
~/Library/Parallels
```

## 六、安装字体 Consolas

字体保存在 icloud 中，双击安装。

## 七、Partially disable System Integrity Protection

1. Boot to Recovery OS by restarting your machine and holding down the `Command + R` at startup.
1. Launch Terminal from the Utilities menu.
1. Enter the following command: `csrutil disable --without debug`
1. Type `reboot` in terminal to reboot your computer.

> Note: For Hackintosh OSX To disable SIP you need to edit Clover's config.plist (https://www.tonymacx86.com/threads/how-to-disable-sip.244637/) config.plist/RtVariables (CsrActiveConfig=0x67, BooterConfig=0x28)

```xml
<key>RtVariables</key>
<dict>
    <key>CsrActiveConfig</key>
    <string>0x67</string>
    <key>BooterConfig</key>
    <string>0x28</string>
</dict>
```

## 八、Issues

### Set permissions to avoid read/write fail or password required

```shell
sudo chmod -R 777 <Your Folder>
```

## Next [安装 softwareDev](softwareDev.md)
