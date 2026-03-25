### 一、安装
```shell
brew install nvm
```

### 二、配置
```shell
# 创建nvm目录
mkdir -p ~/.nvm

cat >> ~/.zshrc <<'EOF'
### NVM CONFIG START ###
export NVM_DIR="$HOME/.nvm"
[ -s "$(brew --prefix nvm)/libexec/nvm.sh" ] && \. "$(brew --prefix nvm)/libexec/nvm.sh"
[ -s "$(brew --prefix nvm)/etc/bash_completion.d/nvm" ] && \. "$(brew --prefix nvm)/etc/bash_completion.d/nvm"
export NVM_NODEJS_ORG_MIRROR=https://npmmirror.com/mirrors/node
export NVM_IOJS_ORG_MIRROR=https://npmmirror.com/mirrors/iojs
### NVM CONFIG END ###
EOF
```

### 三、生效

```shell
source ~/.zshrc
```

### 四、卸载

**如果要卸载，以下仅供参考**

```shell
echo "===== 1. 卸载旧的 Homebrew node ====="
brew uninstall --ignore-dependencies node 2>/dev/null || true
brew uninstall --force node 2>/dev/null || true
echo "===== 2. 删除常见旧 Node 软链接和目录 ====="
rm -f /usr/local/bin/node /usr/local/bin/npm /usr/local/bin/npx 2>/dev/null || true
rm -f /opt/homebrew/bin/node /opt/homebrew/bin/npm /opt/homebrew/bin/npx 2>/dev/null || true
rm -rf /usr/local/lib/node_modules 2>/dev/null || true
rm -rf /opt/homebrew/lib/node_modules 2>/dev/null || true
echo "===== 3. 尝试删除 pkg 安装残留（需要 sudo 时会提示） ====="
sudo rm -f /usr/local/bin/node /usr/local/bin/npm /usr/local/bin/npx 2>/dev/null || true
sudo rm -rf /usr/local/include/node 2>/dev/null || true
sudo rm -rf /usr/local/lib/node_modules 2>/dev/null || true
sudo rm -rf /usr/local/share/man/man1/node.1 2>/dev/null || true
echo "===== 4. 清理旧 ~/.nvm ====="
rm -rf ~/.nvm
echo "===== 5. 清理 ~/.zshrc 中旧 NVM 配置块 ====="
touch ~/.zshrc
awk '
BEGIN {skip=0}
 /### NVM CONFIG START ###/ {skip=1; next}
 /### NVM CONFIG END ###/   {skip=0; next}
 skip==0 {print}
' ~/.zshrc > ~/.zshrc.tmp && mv ~/.zshrc.tmp ~/.zshrc
```