### Xcode

Manually install Xcode from appstore. Then install command line tools:

```bash
xcode-select --install
# https://developer.apple.com/download/more/
```

### 安装 Homebrew, [see usage](homebrew.md)

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
   ```

   To push code to your GitHub repositories, we're going to use the recommended HTTPS method (versus SSH), so you don't have to type your username and password everytime, let's enable Git password caching as described [here](https://help.github.com/articles/set-up-git/):

   ```bash
   git config --global credential.helper osxkeychain
   ```

   Note: On a Mac, it is important to remember to add .DS_Store (a hidden OS X system file that's put in folders) to your .gitignore files. You can take a look at this repository's [.gitignore](https://github.com/nicolashery/mac-dev-setup/blob/master/.gitignore) file for inspiration.

### Prezto Installation

Refer <https://github.com/sorin-ionescu/prezto> to install.

Refer **<https://medium.com/@oldwestaction/beautifying-your-terminal-with-zsh-prezto-powerlevel9k-9e8de2023046> to config terminal.**

**Configure your .zpreztorc**

enable modules and configure them. [the order of modules matters](https://github.com/sorin-ionescu/prezto/blob/master/runcoms/zpreztorc#L25)

Here is my .zpreztorc:

```bash
# Set the Prezto modules to load (browse modules).
# The order matters.

zstyle ':prezto:load' pmodule \
  'environment' \
  'terminal' \
  'editor' \
  'history' \
  'spectrum' \
  'utility' \
  'directory' \
  'utility' \
  'completion' \
  'git' \
  'prompt' \
  'syntax-highlighting' \
  'history-substring-search' \
  'autosuggestions'

```

- [directory](https://github.com/sorin-ionescu/prezto/tree/master/modules/directory): sets directory options
- [utility](https://github.com/sorin-ionescu/prezto/tree/master/modules/utility): defines aliases and functions (highlight matches when pressing \<tab\>)
- [completion](https://github.com/sorin-ionescu/prezto/tree/master/modules/completion): offers tab-completion from the [zsh-completions project](https://github.com/zsh-users/zsh-completions)
- [git](https://github.com/sorin-ionescu/prezto/tree/master/modules/git): displays git repository information in the terminal
- [prompt](https://github.com/sorin-ionescu/prezto/tree/master/modules/prompt): defines a theme for your terminal
- [syntax-highlighting](https://github.com/sorin-ionescu/prezto/tree/master/modules/syntax-highlighting): offers fish-like-highlighting
- [history-substring-search](https://github.com/sorin-ionescu/prezto/tree/master/modules/history-substring-search): type in a word and press up and down to cycle through matching commands

**Set Zsh as your default shell:**

```bash
chsh -s /bin/zsh
```

Check [zsh_settings](zsh_settings.md) and import iterm2_profile.json to iterm2

### Nodejs configuration

1. [Install nvm](https://github.com/creationix/nvm)

   ```bash
   curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.6/install.sh | bash
   ```

   **Restart the terminal**, To verify that nvm has been installed, do:

   ```bash
   command -v nvm
   ```

1. install nodejs `nvm install node`

1. in any new shell just use the installed version: `nvm use node` Or you can just run it: `nvm run node --version`

1. test npm Installation:

   Open a new terminal and run `npm -v`

   We also need to tell npm where to find the Xcode Command Line Tools, by running:

   ```bash
   sudo xcode-select -switch /Library/Developer/CommandLineTools/
   ```

   If Xcode Command Line Tools were installed by Xcode, try instead:

   ```bash
   sudo xcode-select -switch /Applications/Xcode.app/Contents/Developer
   ```

   > Error: EACCES: permission denied, access '/usr/local/lib/node_modules'

   ```bash
   sudo chown -R $USER ~/.npm
   sudo chown -R $USER /usr/lib/node_modules
   sudo chown -R $USER /usr/local/lib/node_modules
   ```

#### Migrating global packages while installing

If you want to install a new version of Node.js and migrate npm packages from a previous version:

```bash
nvm install node --reinstall-packages-from=node
```

This will first use "nvm version node" to identify the current version you're migrating packages from. Then it resolves the new version to install from the remote server and installs it. Lastly, it runs "nvm reinstall-packages" to reinstall the npm packages from your prior version of Node to the new one.

You can also install and migrate npm packages from specific versions of Node like this:

```bash
nvm install 6 --reinstall-packages-from=5
nvm install v4.2 --reinstall-packages-from=iojs
```

#### Useful commands

- check node version: `node -v`
- check node installation path: `which node`(mac), `where node`(windows)

### Npm usage

To install a package:

```bash
npm install <package> # Install locally
npm install -g <package> # Install globally
```

To install a package and save it in your project's package.json file:

```bash
npm install <package> --save
```

To see what's installed:

```bash
npm list # Local
npm list -g -depth=0 # Global
```

To find outdated packages (locally or globally):

```bash
npm outdated [-g]
```

To upgrade all or a particular package:

```bash
npm update [<package>]
```

To uninstall a package:

```bash
npm uninstall <package>
```

#### Global packages to install

```bash
npm i -g cnpm
npm i -g yarn
yarn global add hexo-cli
yarn global add gitbook-cli
yarn global add tslint
yarn global add eslint
yarn global add vue-cli
yarn global add localtunnel
yarn global add yo
yarn global add generator-react-fullstack
# yarn config set registry https://registry.npm.taobao.org
# https://yarnpkg.com/en/docs/cli/list
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

#### MySQL command

Open Terminal and execute the following command to set the root password: `mysqladmin -u root password 'yourpassword'`

> **Important** : Use the single 'quotes' to surround the password and make sure to select a strong password!

#### Database Management

To manage your databases, I recommend using [Sequel Pro](http://www.sequelpro.com), a MySQL management tool designed for macOS.

#### MySql Installation directly from official website

download link: <https://cdn.mysql.com//Downloads/MySQL-5.7/mysql-5.7.19-macos10.12-x86_64.dmg>

因为 mysql 命令的路径在`/usr/local/mysql/bin`下面，所以你直接使用 mysql 命令时，系统在`/usr/bin`下面查此命令。

```bash
sudo ln -s /usr/local/mysql/bin/mysql /usr/bin
```

如果还不好用，参见<http://blog.csdn.net/sinat_26696701/article/details/49619207> <http://jingyan.baidu.com/article/4853e1e568787b1909f726f3.html>

设置用户密码：Navicat Premium

| username | Password | connectionName |
| :------- | :------- | :------------- |
| root     | root     | mysqlRoot      |
| derek    | derek    | mysqlDerek     |

"MysqlConnection": "Server=localhost;Database=Food;userid=derek;pwd=derek;port=3306;sslmode=none;CharSet=utf8;"

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

### Python2 Installation

```bash
brew install python   # brew will automatically isntall pip
pip install requests  # install requests module for markdown-img-upload to qiniu
```

### [AspNet Core](https://docs.microsoft.com/en-us/aspnet/core/getting-started)

1. Visit <https://www.microsoft.com/net/core#macos> to see setup in detail

   ```bash
   brew update
   brew install openssl
   mkdir -p /usr/local/lib
   ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
   ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
   ```

1. Install .NET Core SDK

   [Download .NET Core SDK](https://go.microsoft.com/fwlink/?linkid=848823)

1. Install Visual Studio from BaiduDisk

   "extensions" --> "Gallery" --> "IDE extensions" --> "Nuget Package Explorer" and "Nuget Package Management Extensions"

### Visual Studio Code Installation

1. Install plugin "syncing", find token and gistId from github, restore
1. Install `code` command in PATH (in terminal, `code .` will open vscode for that folder)
1. Make sure alfred "open with visual studio code" is installed
1. `shift+cmd+p` and then "download .net core debugger"
1. Add "open in VS code" on contextMenu: copy the content of zip file "Open.in.VS.Code.workflow" into the folder: `~/Library/Services`. Now right click a folder --> Services --> open in VS code
1. copy files from "OneDrive/vscode files" to "/Users/derek/Library/Application Support/Code/User"

#### vscode extensions

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
