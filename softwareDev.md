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

```shell
code --install-extension bierner.markdown-preview-github-styles
code --install-extension boukichi.git-exclude
code --install-extension bradlc.vscode-tailwindcss
code --install-extension capaj.vscode-exports-autocomplete
code --install-extension christian-kohler.path-intellisense
code --install-extension chrmarti.regex
code --install-extension dariofuzinato.vue-peek
code --install-extension Dart-Code.dart-code
code --install-extension Dart-Code.flutter
code --install-extension dbaeumer.vscode-eslint
code --install-extension deerawan.vscode-faker
code --install-extension donjayamanne.githistory
code --install-extension dsznajder.es7-react-js-snippets
code --install-extension eamodio.gitlens
code --install-extension EditorConfig.EditorConfig
code --install-extension esbenp.prettier-vscode
code --install-extension formulahendry.auto-close-tag
code --install-extension formulahendry.auto-rename-tag
code --install-extension formulahendry.code-runner
code --install-extension GitHub.vscode-pull-request-github
code --install-extension GitLab.gitlab-workflow
code --install-extension Gruntfuggly.todo-tree
code --install-extension hollowtree.vue-snippets
code --install-extension johnpapa.Angular2
code --install-extension jpoissonnier.vscode-styled-components
code --install-extension kisstkondoros.vscode-gutter-preview
code --install-extension KnisterPeter.vscode-github
code --install-extension MariusAlchimavicius.json-to-ts
code --install-extension mdickin.markdown-shortcuts
code --install-extension mhutchie.git-graph
code --install-extension mikestead.dotenv
code --install-extension ms-vsliveshare.vsliveshare
code --install-extension msjsdiag.debugger-for-chrome
code --install-extension msjsdiag.vscode-react-native
code --install-extension Nash.awesome-flutter-snippets
code --install-extension OBKoro1.autoCommit
code --install-extension octref.vetur
code --install-extension oderwat.indent-rainbow
code --install-extension Orta.vscode-jest
code --install-extension quicktype.quicktype
code --install-extension rangav.vscode-thunder-client
code --install-extension redhat.vscode-yaml
code --install-extension richie5um2.vscode-sort-json
code --install-extension ritwickdey.LiveServer
code --install-extension ryu1kn.text-marker
code --install-extension sdras.night-owl
code --install-extension Shan.code-settings-sync
code --install-extension silvenon.mdx
code --install-extension steoates.autoimport
code --install-extension streetsidesoftware.code-spell-checker
code --install-extension VisualStudioExptTeam.vscodeintellicode
code --install-extension vscode-icons-team.vscode-icons
code --install-extension waderyan.gitblame
code --install-extension WallabyJs.quokka-vscode
code --install-extension zhuangtongfa.material-theme
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
