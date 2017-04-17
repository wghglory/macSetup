# Hackintosh

## Mac 黑苹果创建 usb 系统盘

### Copy OS to USB

格式化 U 盘：

将要用于制作启动盘的 U 盘插入 USB 上，打开 `应用程序 → 实用工具 → 磁盘工具`，将 U 盘`抹掉`(格式化) 成`Mac OS X 扩展（日志式）`格式、`GUID 分区图`，并将 U 盘命名为`USB`

    **注意 **：这里的盘符名称你可以随意指定，但是下一步制作U盘启动的时候选择的U盘名称要和这里设置的一样。

```bash
sudo  /Volumes/Len\ Install\ macOS\ Catalina/Install\ macOS\ Catalina.app/Contents/Resources/createinstallmedia --volume /Volumes/USB /Applications/Install\ macOS\ Catalina.app --nointeraction
```

方式二: 下载网上资源镜像制作

​ 如果你没有 Mac 环境，没办法从 AppStore 下载镜像的话或者你怕自己命令行制作有问题的话，也可以从网上查找网友大神们已经制作好的镜像制作，此步骤适用于 Windows、Mac 环境。你可以到[黑苹果乐园](https://imac.hk/category/macos/)下载镜像，下载下来的是一个 dmg 结尾的文件,使用烧录软件烧录即可。

烧录软件我使用 [etcher](https://www.balena.io/etcher/) 或者 DiskMaker X

### 挂载 EFI 分区(优盘/硬盘是同样的步骤操作)

​ 使用你喜欢的任何可以挂载 EFI 分区的方式，将 EFI 引导文件复制到 U 盘启动器的 EFI 分区内。

打开了`Clover Configurator`软件后，切到`Mount EFI`标签，找到你的 U 盘名字，点击`Mount Partition`输入用户密码挂载 EFI 分区。

![image-20190213151458936](https://ws2.sinaimg.cn/large/006tNc79gy1g04thg6n71j31hw0u0too.jpg)

挂载之后可以看到盘符，现在这个盘符里面内容是空的，什么也没有![image-20190213154052143](https://ws1.sinaimg.cn/large/006tNc79gy1g04u8di62gj316u0o4thy.jpg)

把你准备好的`EFI文件`复制到刚才`挂载的U盘的EFI分区`即可，**注意一定要带 EFI 文件夹名称**

![image-20190213154158135](https://ws3.sinaimg.cn/large/006tNc79gy1g04u9iiofxj316s0o8thz.jpg)

至此 U 盘制作成功。

## EFI

系统启动都有一个引导自检的过程，像 Android 的 bootloader 一样，PC 也有，以前有 BIOS 启动，现在是 UEFI 启动(Unified Extensible Firmware Interface), UEFI 是一种详细描述类型接口的标准。这种接口用于操作系统自动从预启动的操作环境，加载到一种操作系统上。

黑苹果就是在这个阶段去做一些"手脚"的，最重要的就是整理这一部分的 EFI 引导文件。

## 安装 MacOS 系统

- 选择 U 盘启动

  将你制作好的 U 盘启动器插入到你将要安装系统的机器的 USB 口上，将机器开机，查找你主板的`Boot Menu`快捷键（一般都是 F11 或者 F12，技嘉主板的是按 F12），进入到启动选择界面，找到你的 U 盘启动器的名字，选择它的 UEFI 启动，例如我的 U 盘的名字是`SanDisk`，则我就选择 `UEFI`那个分区启动，如果你的 U 盘品牌不一样，请找到你的 U 盘并且对号入座选择正确的启动项：

  ![image-20190228213550795](https://ws4.sinaimg.cn/large/006tKfTcgy1g0mgscrvcbj31g00u0npd.jpg)

- Clover 引导界面选择安装

上面选择之后，就进入到了 Clover 的引导界面，如果你的系统盘够干净，那么应该只会剩下一个安装的选项

![image-20190228214049098](https://ws2.sinaimg.cn/large/006tKfTcgy1g0mgxjmitsj318c0u0hdv.jpg)

![image-20190228214437758](https://ws4.sinaimg.cn/large/006tKfTcgy1g0mh1hihkaj31400u0npd.jpg)

之后会来到`macOS实用工具`界面，我们需要将系统盘进行`抹掉`操作，所以要选择`磁盘工具`，进行抹盘，就是要格式化的意思，所以如果你将要安装的系统盘之前有什么重要的数据，那么事先就要先做好备份了。

![image-20190228214625338](https://ws3.sinaimg.cn/large/006tKfTcgy1g0mh3dg6xqj31400u0e81.jpg)

之后进项抹盘操作，选择系统盘，然后点击`抹掉`

![image-20190228214821413](https://ws4.sinaimg.cn/large/006tKfTcgy1g0mh5dkgkqj31ba0u01ky.jpg)

弹出抹盘的选项，系统盘符名称可以随便填写，我这填`MacOS`抹盘格式选择`MacOS拓展（日志式）`，之后点击`抹掉`按钮

![image-20190228215016715](https://ws4.sinaimg.cn/large/006tKfTcgy1g0mh7d7hcyj31bw0u0kjl.jpg)

抹盘成功提示：

![image-20190228215218246](https://ws3.sinaimg.cn/large/006tKfTcgy1g0mh9gwtebj31400u04qp.jpg)

回到`macOS实用工具`界面，选择`安装macOS`

![image-20190228215313180](https://ws4.sinaimg.cn/large/006tKfTcgy1g0mhafhg69j31400u0hdt.jpg)

下面这里要选择系统安装位置了，选择刚才抹掉的系统盘，然后继续点击`安装`

![image-20190228220155070](https://ws3.sinaimg.cn/large/006tKfTcgy1g0mhjh371yj311y0u0b2a.jpg)

之后会出现安装进度条，在这个阶段机器会重启若干次，所以你要仔细盯着屏幕了，等机器重启的时候你要像之前那样，手动选择以 U 盘启动器方式启动，不然进不到下面的步骤，谨记，如果你晃了神，没能及时选择 U 盘启动，那么重新关机，再开机选择一次，安装进度也能继续进行。

![image-20190228220510291](https://ws4.sinaimg.cn/large/006tKfTcgy1g0mhmv88tyj31400u01kx.jpg)

当你的机器再次重启的时候，在 Clover 的引导界面会多出一个选项，这个选项就是我们刚才安装的系统盘，这一次选择启动到我们的系统盘

![image-20190228220743645](https://ws2.sinaimg.cn/large/006tKfTcgy1g0mhpjayzmj30zf0u01l0.jpg)

继续之前的安装工作

![image-20190228220924568](https://ws4.sinaimg.cn/large/006tKfTcgy1g0mhr9t2o3j31400u07s6.jpg)

这个步骤可能还是会有重启，所以和之前上面的操作一样，手动选择 U 盘启动器，clover 引导界面选择启动到我们的系统盘，大概十几分钟后安装完毕会提示下面即将要重启的提示，记住，只要重启，你就要手动选择 U 盘启动，现在的引导文件只在我们的 U 盘启动器里面，还没有在我们的系统盘里面，所以要引导系统，就需要选择 U 盘引导启动。

![image-20190228221034996](https://ws1.sinaimg.cn/large/006tKfTcgy1g0mhshw8ixj31400u01kx.jpg)

重启之后再一次来到 clover 引导界面，这一回，又多了几个启动项了，最左边就是我们的重装启动项了（就是之前我们第一次引导出现的那个）第二个和第三个是都是预启动的启动项我们不选它们，只选择启动到我们的系统盘

![image-20190228221518335](https://ws1.sinaimg.cn/large/006tKfTcgy1g0mhxes1lzj31420u0npf.jpg)

## 把 U 盘中的 EFI 拷贝到 MAC 系统上

类似 EFI 拷贝到 U 盘，现在把 U 盘 EFI 拷贝到电脑

## 后续

Hackintosh 不支持休眠（挂起到磁盘或 S4 睡眠），所以在安装/更新后应该将 hibernatemode 禁用。

系统更新会重新启用它，创建 sleepimage 目录可以避免再次创建，同时禁用其他与休眠相关的选项。

```bash
sudo pmset -a hibernatemode 0
sudo rm /var/vm/sleepimage
sudo mkdir /var/vm/sleepimage
sudo pmset -a standby 0
sudo pmset -a autopoweroff 0
```
