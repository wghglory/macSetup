# Homebrew Usage

安装 Homebrew:

```bash
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

更新 Homebrew:

```bash
brew update
```

显示已经安装的软件列表:

```bash
brew list
```

搜索某个软件:

```bash
brew search wget
```

安装某个软件:

```bash
brew install wget
```

查看需要升级的软件:

```bash
brew outdated
```

升级所有的软件:

```bash
brew upgrade
```

升级某个软件:

```bash
brew upgrade wget
```

删除某个软件:

```bash
brew uninstall wget --force
```

查看软件包信息:

```bash
brew info wget
```

列出软件包的依赖关系:

```bash
brew deps wget
```

出错以后的处理:

```bash
brew update
brew doctor
```

## homebrew-cask

homebrew-cask 和 Homebrew 的区别：

- Homebrew 安装的是源文件包, 下载源文件、编译、安装，比如安装 wget, gnupg, mutt 等。
- homebrew-cask 安装的是二进制软件包, 比如 QQ，Chrome，evernote 等。homebrew-cask 安装软件时自动创建软连接到 Application 目录，这样在 Launchpad 中也能查看到安装的软件，方便启动软件。

安装 homebrew-cask

```bash
brew install caskroom/cask/brew-cask
```

常用命令

列出所有可以被安装的软件：

```bash
brew cask search
```

查找所有和 drop 相关的应用:

```bash
brew cask search drop
```

查看迅雷应用的信息:

```bash
brew cask info thunder
```

卸载 QQ:

```bash
brew cask uninstall qq
```

查看已安装的软件

```bash
brew cask list
```

更新 Casks:

```bash
brew update && brew upgrade brew-cask
```

关于软件更新，目前 homebrew-cask 并不提供命令直接更新已安装的软件，软件更新主要是通过软件自身的更新流程，不过也可以通过以下命令先删除软件，再重新安装。

```bash
brew cask uninstall APP && brew cask install APP
```

## [Homebrew](https://brew.sh/)

Install: `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

## Commands

| **Homebrew**                       |                                              |
| ---------------------------------- | -------------------------------------------- |
| brew doctor                        | Check brew for potential problems            |
| brew install [formula]             | Install a formula                            |
| brew uninstall [formula]           | Uninstall a formula                          |
| brew list                          | List all the installed formulas              |
| brew search                        | Display available formulas for brewing       |
| **brew upgrade**                   | Upgrade all outdated and unpinned brews      |
| **brew update**                    | Fetch latest version of homebrew and formula |
| **brew cleanup**                   | Remove older version of installed formula    |
| brew info wget                     | 查看软件包信息                               |
| brew deps wget                     | 查看软件包信息                               |
| brew tap homebrew/cask             | Tap the cask repository from GitHub          |
| brew cask list                     | List all installed casks                     |
| brew cask install [cask]           | Install the given cask                       |
| brew cask uninstall [cask] --force | Uninstall the given cask                     |

出错以后的处理:

```bash
brew update
brew doctor
```

## Homebrew in China

```bash
# 替换brew.git:
cd "$(brew --repo)"
# 中国科大:
git remote set-url origin https://mirrors.ustc.edu.cn/brew.git
# 清华大学:
git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git

# 替换homebrew-core.git:
cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
# 中国科大:
git remote set-url origin https://mirrors.ustc.edu.cn/homebrew-core.git
# 清华大学:
git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git

# 替换homebrew-bottles:
# 中国科大:
echo '\n #homebrew \n export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.ustc.edu.cn/homebrew-bottles' >> ~/.bash_profile
source ~/.bash_profile
# .zprofile??
# 清华大学:
echo '\n #homebrew \n export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles' >> ~/.bash_profile
source ~/.bash_profile

# 应用生效:
brew update
```

如果你之前折腾过不少导致你的 Homebrew 有点问题，那么可以尝试使用如下方案：

```bash
# 诊断Homebrew的问题:
brew doctor

# 重置brew.git设置:
cd "$(brew --repo)"
git fetch
git reset --hard origin/master

# homebrew-core.git同理:
cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
git fetch
git reset --hard origin/master

# 应用生效:
brew update
```

重置更新源 某些时候也有换回官方源的需求:

```bash
# 重置brew.git:
cd "$(brew --repo)"
git remote set-url origin https://github.com/Homebrew/brew.git

# 重置homebrew-core.git:
cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
git remote set-url origin https://github.com/Homebrew/homebrew-core.git
```

完成更新源的更换后，我们可以使用 `brew upgrade` 将现有的软件进行更新至最新版本，这样便能很直接的看出速度上的变化了。最后不要忘记 `brew cleanup` 将旧有的软件安装包进行清理

## Homebrew 安装后的文件位置

```
/usr/local/opt
```

以 nginx 为例，双击目录快捷方式找到 `/usr/local/Cellar/nginx/1.17.3_1/bin`
