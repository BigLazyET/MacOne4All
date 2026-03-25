### 一、什么是Brewfile

Brewfile 是 Homebrew 的“依赖清单文件”

它用来描述：这台 Mac 需要装哪些软件、命令行工具、图形应用、字体、App Store 应用等。有点像：

- Node 的 package.json
- Python 的 requirements.txt
- Docker 的 docker-compose.yml 的“安装软件版”

```shell
# 然后你只要执行一条命令, Homebrew 就会按这个清单，把东西尽量装齐:
brew bundle
```

### 二、Brewfile长什么样

```ruby
tap "antoniorodr/memo"
tap "steipete/tap"
tap "yakitrak/yakitrak"
brew "ffmpeg"
brew "gh"
brew "go"
brew "mole"
brew "nvm"
brew "antoniorodr/memo/memo"
brew "steipete/tap/gifgrep"
brew "steipete/tap/remindctl"
brew "yakitrak/yakitrak/obsidian-cli"
brew "git"
brew "node"
brew "python"
cask "google-chrome"
cask "visual-studio-code"
cask "iterm2"
cask "maccy"
uv "specify-cli"
mas "Xcode", id: 497799835
```

含义是：

- brew：安装命令行工具或库
- cask：安装 Mac 图形应用
- mas：安装 Mac App Store 应用
还可以有：
    - tap：添加第三方仓库
    - vscode 扩展（某些方案里）
    - 字体、服务等

### 三、Brewfile生成和管理

```shell
# 根据当前机器已安装内容生成 Brewfile
# 会在当前目录生成一个 Brewfile
brew bundle dump

# 如果生成+覆盖已有Brewfile
brew bundle dump --force

# 根据 Brewfile 安装软件
# 默认读取当前目录下的 Brewfile
brew bundle

# 也可以读取指定目录下的 Brewfile
brew bundle --file=~/Brewfile

# 检查哪些没装
brew bundle check

# 清理 Brewfile 里没有的包，慎用！！一般不用
# 这个要小心，会卸载未在 Brewfile 里的内容。
brew bundle cleanup
```