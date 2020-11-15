# MacOS Development Environment Configuration

***
## 1. Xcode Command Line Tools
### Installation
To install the packages, run:
```
$ xcode-select —-install
```

### Verification
To check if **Xcode Command Line Tools** are properly installed in the system:
```
$ xcode-select -p
```
If the packages exist, it should return:
`/Applications/Xcode.app/Contents/Developer`


All the available commands can be viewed in `/Library/Developer/CommandLineTools/`

## 2. Homebrew
### Installation
**Xcode Command Line Tools** are required. To install **Homebrew**, type in the following script and follow insturctions:
```
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" 
```

### Location
**Homebrew**自身安装位置：`/usr/local/Homebrew`
`brew install`指令安装位置：`/usr/local/Cellar`

以git为例，系统自带git路径：`/usr/bin/git`，通过brew安装git路径：`/usr/local/Cellar/git/2.18.0/bin/git`（链接到`/usr/local/bin/git`）。由于在`$PATH`中`/usr/local/bin`默认优先级高于`/usr/bin`，系统会默认使用brew安装的git而非系统自带git。

### Notes
* 安装完成后brew的启动链接会自动添加到`/usr/local/bin`中，并将`/usr/local`初始化为git工作树，将目录所有者变更为当前所操作的用户，所以brew相关操作不需要sudo。

* 通过`brew install`安装的应用最先放在`/usr/local/Cellar/`目录下。有些应用会自动创建软链接放在`/usr/bin/`或者`/usr/sbin/`，同时也会将整个文件夹放在`/usr/local/`下。可以使用`brew list <package_name>`指令确定安装位置。

### Basic Commands
* 安装包：
`brew install <package_name>`
* 查看已安装的包（包括版本号）：
`brew list --versions`
* 更新服务器端包目录：
`brew update`
* 查看已安装的包是否有更新：
`brew outdated`
* 更新包：
`brew upgrade <package_name>`
* 清理旧版本缓存：
`brew cleanup`

### Install GUI Applications
添加Github上的caskroom/cask库：
`brew tap caskroom/cask`
安装图形应用：
`brew cask install <application_name>`

## 3. iTerm2 & Oh
### Installation
To install iTerm2:
```
$ brew cask install iterm2