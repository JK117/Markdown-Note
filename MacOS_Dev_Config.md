# MacOS Development Environment Configuration

***
## 1. Xcode Command Line Tools
### 1.1 Check if already exists:
Run:
```
$ xcode-select -p
```
If not installed, terminal should prompt command not available.
If **Xcode Command Line Tools** is installed **with Xcode**, which is **NOT** necessary, terminal should return: `/Applications/Xcode.app/Contents/Developer`

If it is installed **without Xcode**, terminal returns: `/Library/Developer/CommandLineTools`, which is the path of all available xcode commands.

### 1.2 Installation
To install the packages, run:
```
$ xcode-select —-install
```
Then check with operations in 1.1.

## 2. Homebrew
### 2.1 Installation
**Xcode Command Line Tools** are required to install **Homebrew**
Run:
```
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" 
```

### 2.2 Configure Completions
Follow the [instruction][Configuring Completions] to configure completions.

### 2.3 Notes
- **Homebrew**自身安装位置：`/usr/local/Homebrew`
- 安装完成后brew的启动链接会自动添加到`/usr/local/bin`中，并将`/usr/local`初始化为**git**工作树，将目录所有者变更为当前所操作的用户，所以brew相关操作不需要sudo。
- 通过`brew install`安装的应用最先放在`/usr/local/Cellar/`目录下。有些应用会自动创建软链接放在`/usr/bin/`或者`/usr/sbin/`，同时也会将整个文件夹放在`/usr/local/`下。可以使用`brew list <package_name>`指令确定安装位置。
以**git**为例，系统自带**git**路径：`/usr/bin/git`，通过**brew**安装**git**路径：`/usr/local/Cellar/git/2.18.0/bin/git`（链接到`/usr/local/bin/git`）。由于在`$PATH`中`/usr/local/bin`默认优先级高于`/usr/bin`，系统会默认使用**brew**安装的**git**而非系统自带**git**。

### 2.4 Basic Commands
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

### 2.5 Install GUI Applications
添加Github上的caskroom/cask库：
`brew tap caskroom/cask`
安装图形应用：
`brew cask install <application_name>`

## 3. Oh My Zsh
To install **Oh My Zsh**, run:
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
After installation, `~/.zshrc` will be the new shell profile.

## 4. iTerm2
### Installation
To install iTerm2, run:
```
$ brew cask install iterm2
```

[Configuring Completions]:https://docs.brew.sh/Shell-Completion#configuring-completions-in-zsh