### 一、安装准备

参考[nvm安装](../nvm/install.md)，通过nvm来安装node，npm伴随着node一同安装

### 二、镜像配置

```shell
# 查看当前镜像
npm config get registry

# 设置国内镜像
npm config set registry https://registry.npmmirror.com

# 切回官方镜像
npm config set registry https://registry.npmjs.org
```