# Switch Registry Source

## homebrew 替换中科大镜像
### 第一步：替换`brew.git`
```
cd "$(brew --repo)"
git remote set-url origin https://mirrors.ustc.edu.cn/brew.git
```
### 第二步：替换`homebrew-core.git`
```
cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
git remote set-url origin https://mirrors.ustc.edu.cn/homebrew-core.git
```
到这一步已完成Homebrew的默认镜像配置，可以满足日常基本使用。
### 可选：替换`homebrew bottles`
进一步优化速度需要为`homebrew bottles`也配置镜像。
关于`homebrew bottles`, 我们在使用`brew install`安装软件时，通常由两种方式。一种是将源代码下载到本地然后编译，另一种是直接下载二进制文件，即`bottles`。正常情况下后者效率高于前者，因为不用进行构建和编译。
配置`homebrew bottles`镜像时，首先要区分使用的是哪种终端工具。如果使用的是Bash，可以通过以下方式来配置：
```
echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.ustc.edu.cn/homebrew-bottles' >> ~/.bash_profile
source ~/.bash_profile
```
如果使用的是Zsh，则可以进行如下配置：
```
echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.ustc.edu.cn/homebrew-bottles' >> ~/.zshrc
source ~/.zshrc
```
至此`homebrew`镜像完全配置完毕。

## pip
以`pip`安装`markdown`为例，一般情况下直接安装使用命令：
```
pip install markdown
```
若需要临时把安装源替换为国内的源，可以添加属性`-i`：
```
# 清华大学源
pip install markdown -i https://pypi.tuna.tsinghua.edu.cn/simple
```
如果不想每次都添加临时源，则可以修改默认源：
```
# 清华源
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple

# 阿里源
pip config set global.index-url https://mirrors.aliyun.com/pypi/simple/

# 腾讯源
pip config set global.index-url http://mirrors.cloud.tencent.com/pypi/simple

# 豆瓣源
pip config set global.index-url http://pypi.douban.com/simple/
```

## npm
使用国内的registry镜像主要有两种方法。

### 配置文件替换镜像源
```
# 淘宝镜像源
npm config set registry https://registry.npm.taobao.org

# 华为云镜像源
npm config set registry https://mirrors.huaweicloud.com/repository/npm/

# 验证
npm config get registry
```

### 直接使用第三方源
```
# 安装cnpm
npm install -g cnpm --registry=https://registry.npm.taobao.org

# 使用cnpm
cnpm install
```
