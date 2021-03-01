# Mac Dev setup

### Xcode

Manually install Xcode from appstore. Then install command line tools:

```bash
xcode-select --install
# https://developer.apple.com/download/more/
```

### Homebrew, [see usage](homebrew.md)

```bash
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

### Git configuration

1. install git

   ```bash
   brew install git
   ```

1. Download the [.gitconfig](https://raw.githubusercontent.com/nicolashery/mac-dev-setup/master/.gitconfig) file to your home directory:

   ```bash
   cd ~
   curl -O https://raw.githubusercontent.com/nicolashery/mac-dev-setup/master/.gitconfig
   ```

1. define your Git user (should be the same name and email in GitHub):

   ```bash
   git config --global user.name "Guanghui Wang"
   git config --global user.email guanghui-wang@foxmail.com
   git config --global core.editor "code --wait". # make sure vscode is installed before this. And gitlens: enable interactive rebase editor
   ```

   To push code to your GitHub repositories, we're going to use the recommended HTTPS method (versus SSH), so you don't have to type your username and password everytime, let's enable Git password caching as described [here](https://help.github.com/articles/set-up-git/):

   ```bash
   git config --global credential.helper osxkeychain
   ```

### iTerm2

**Set Zsh as your default shell:**

```bash
chsh -s /bin/zsh
```

Refer:

- <https://github.com/sirius1024/iterm2-with-oh-my-zsh>
- <https://zhuanlan.zhihu.com/p/145437836>

Check [zsh_settings](zsh_settings.md) and import iterm2_profile.json to iterm2

### Nodejs configuration

1. [Install nvm](https://github.com/creationix/nvm)

#### Global packages to install

```bash
npm i -g yarn
npm i -g @angular/cli
npm i -g @vue/cli

yarn global add hexo-cli
yarn global add gitbook-cli
yarn global add tslint
yarn global add eslint
yarn global add
yarn global add localtunnel
yarn global add yo
yarn upgrade-interactive   # yarn global add npm-check-updates
npm i -g @angular/cli
# yarn global add nodemon
# yarn global add mocha
# yarn global add webpack
```

### MongoDB Installation

Installing it is very easy through Homebrew: <https://docs.mongodb.com/manual/tutorial/install-mongodb-on-os-x/>

```bash
brew install mongodb-community
sudo mkdir -p /data/db/     # create db folder
sudo chown -R $USER /data/db  # give permission
```

**Usage:**

In a terminal, start the MongoDB server:

```bash
mongod
```

In another terminal, connect to the database with the Mongo shell using:

```bash
mongo
```

### Sass Installation

1. install ruby: `brew install ruby`

1. install sass: `sudo gem install sass`

   通过镜像安装:

   比官方安装方法多 2 步：需要先移除默认的源，再添加 Ruby China 的源，查看安装成功之后，最后再执行官方的安装方法。

   ```bash
   gem sources --remove     #移除自带源
   gem sources -a https://gems.ruby-china.org/     #安装RubyChina的源
   gem sources -l         #查看当前的源
   gem install sass
   sass -v
   ```

   安装源的过程中，如果提示 SSL 错误，那就把源地址换一下成<http://gems.ruby-china.org>再试。

1. gem 常见命令

   ```bash
   gem update --system   #升级RubyGems到最新版本。安装镜像前建议先执行此操作。
   gem update sass
   gem uninstall sass
   ```

#### Install MySQL

At this time of writing, Homebrew has MySQL version **5.7.18** as default formulae in its main repository:

- Enter the following command : `brew info mysql`
- Expected output: **mysql: stable stable 5.7.18 (bottled)**

To install MySQL enter : `brew install mysql`

#### Homebrew and MySql

To connect run: `mysql -uroot` To have launched start mysql now and restart at login: `brew services start mysql` Or, if you don't want/need a background service you can just run: **`mysql.server start`**

- Install **brew services** first : `brew tap homebrew/services`
- Load and start the MySQL service : `brew services start mysql`
- Check of the MySQL service has been loaded : `brew services list`
- Verify the installed MySQL instance : `$ mysql -V`

##### Uninstall MySql

```bash
sudo rm /usr/local/mysql
sudo rm -rf /usr/local/mysql*
sudo rm -rf /Library/StartupItems/MySQLCOM
sudo rm -rf /Library/PreferencePanes/My*
# edit /etc/hostconfig and remove the line MYSQLCOM=-YES-
rm -rf ~/Library/PreferencePanes/My*
sudo rm -rf /Library/Receipts/mysql*
sudo rm -rf /Library/Receipts/MySQL*
sudo rm -rf /private/var/db/receipts/*mysql*
```

### vscode extensions

In machine A,

UNIX:

```bash
code --list-extensions | xargs -L 1 echo code --install-extension
```

Windows (PowerShell, e. g. using VSCode's integrated Terminal):

```bash
code --list-extensions | % { "code --install-extension $_" }
copy and paste the echo output to machine B
```

sample output:

```bash
code --install-extension AlanWalk.markdown-toc
code --install-extension CoenraadS.bracket-pair-colorizer
code --install-extension IBM.output-colorizer
code --install-extension akamud.vscode-theme-onelight
code --install-extension Angular.ng-template
code --install-extension boukichi.git-exclude
code --install-extension capaj.vscode-exports-autocomplete
code --install-extension christian-kohler.npm-intellisense
code --install-extension christian-kohler.path-intellisense
code --install-extension codezombiech.gitignore
code --install-extension DavidAnson.vscode-markdownlint
code --install-extension dbaeumer.vscode-eslint
code --install-extension deerawan.vscode-dash
code --install-extension deerawan.vscode-faker
code --install-extension donjayamanne.githistory
code --install-extension eamodio.gitlens
code --install-extension ecmel.vscode-html-css
code --install-extension EditorConfig.EditorConfig
code --install-extension eg2.tslint
code --install-extension eg2.vscode-npm-script
code --install-extension EQuimper.react-native-react-redux
code --install-extension esbenp.prettier-vscode
code --install-extension formulahendry.auto-close-tag
code --install-extension formulahendry.auto-rename-tag
code --install-extension formulahendry.code-runner
code --install-extension Gruntfuggly.todo-tree
code --install-extension hbenl.vscode-jasmine-test-adapter
code --install-extension hbenl.vscode-test-explorer
code --install-extension hollowtree.vue-snippets
code --install-extension humao.rest-client
code --install-extension ionutvmi.path-autocomplete
code --install-extension jvitor83.typings-autoinstaller
code --install-extension kamikillerto.vscode-colorize
code --install-extension kisstkondoros.typelens
code --install-extension mdickin.markdown-shortcuts
code --install-extension Mikael.Angular-BeastCode
code --install-extension mrmlnc.vscode-scss
code --install-extension ms-azuretools.vscode-docker
code --install-extension ms-python.python
code --install-extension ms-vsliveshare.vsliveshare
code --install-extension msjsdiag.debugger-for-chrome
code --install-extension nonoroazoro.syncing
code --install-extension octref.vetur
code --install-extension PKief.material-icon-theme
code --install-extension ritwickdey.live-sass
code --install-extension ritwickdey.LiveServer
code --install-extension robinbentley.sass-indented
code --install-extension Shan.code-settings-sync
code --install-extension shinnn.stylelint
code --install-extension steoates.autoimport
code --install-extension streetsidesoftware.code-spell-checker
code --install-extension techer.open-in-browser
code --install-extension vscode-icons-team.vscode-icons
code --install-extension waderyan.gitblame
code --install-extension WallabyJs.quokka-vscode
code --install-extension wayou.vscode-todo-highlight
code --install-extension wix.vscode-import-cost
code --install-extension xabikos.JavaScriptSnippets
code --install-extension yzane.markdown-pdf
```

#### Completely uninstall VS Code extensions

Turns out the extensions are stored under `%USER%\.vscode\extensions`. Deleting that gets rid of them.

```bash
# For Windows:
rmdir %USERPROFILE%\.vscode\extensions /s
%USER%\\.vscode\extensions (or) %USERPROFILE%\.vscode\extensions

# For Linux/MAC:
rm -rf ~/.vscode/extensions
```

### Install Sublime

1. Clone repo at <https://bitbucket.org/wghglory/sublime.sync>

1. Open Folder with Sublime Text 3 using Terminal:

   ```bash
   sudo cd /usr
   sudo mkdir local
   sudo cd local
   sudo ln -s "/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl" /usr/local/bin/subl
   ```

   After this, use `subl .` to open the folder

### Then see [software.md](software.md)
