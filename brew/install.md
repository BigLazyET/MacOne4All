参考文档：[brew 安装完全指南：多系统适配与国内源配置技巧](https://github.com/RivTian/blog-articles/issues/29)

### 一、安装
从 Homebrew 最新的 GitHub 发行版下载（推荐）

安装好之后执行：
```shell
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
echo 'export HOMEBREW_AUTO_UPDATE_SECS=604800' >> ~/.zprofile
source ~/.zprofile
```

把上面这行写进去之后：
- 每次打开终端
- Homebrew 的 PATH 都会自动配置好

### 二、配置镜像源（如果慢可选择配置）

#### 1. 中科大镜像配置

```shell
# 替换 brew.git
cd "$(brew --repo)"
git remote set-url origin https://mirrors.ustc.edu.cn/brew.git
 
# 替换 homebrew-core.git
cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
git remote set-url origin https://mirrors.ustc.edu.cn/homebrew-core.git
 
# 替换 homebrew-cask.git (macOS)
cd "$(brew --repo)/Library/Taps/homebrew/homebrew-cask"
git remote set-url origin https://mirrors.ustc.edu.cn/homebrew-cask.git
 
# 配置 bottles 镜像
echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.ustc.edu.cn/homebrew-bottles' >> ~/.zprofile
source ~/.zprofile
```

#### 2. 清华大学镜像配置

```shell
# 临时使用
export HOMEBREW_API_DOMAIN="https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles/api"
export HOMEBREW_BOTTLE_DOMAIN="https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles"
export HOMEBREW_BREW_GIT_REMOTE="https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git"
export HOMEBREW_CORE_GIT_REMOTE="https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git"
 
# 永久配置
echo 'export HOMEBREW_API_DOMAIN="https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles/api"' >> ~/.zprofile
echo 'export HOMEBREW_BOTTLE_DOMAIN="https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles"' >> ~/.zprofile
echo 'export HOMEBREW_BREW_GIT_REMOTE="https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git"' >> ~/.zprofile
echo 'export HOMEBREW_CORE_GIT_REMOTE="https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git"' >> ~/.zprofile
```