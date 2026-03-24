### 一、安装

#### 1. 偏向于GUI界面操作，直接装Docker desktop (官方推荐)

- [下载地址](https://desktop.docker.com/mac/main/arm64/Docker.dmg?utm_source=docker&utm_medium=webreferral&utm_campaign=dd-smartbutton&utm_location=module)

#### 2. 偏向于命令行操作

```shell
brew install --cask docker
```

### 二、配置镜像源

#### 1. 在Docker desktop中配置

然后Docker Desktop 里直接重启

#### 2. 控制台直接修改daemon.json

```shell
echo '{
  "registry-mirrors": ["https://***.xuanyuan.run"]
}' | sudo tee ~/.docker/daemon.json > /dev/null
```

### 三、验证

```shell
docker info | grep -A 10 "Registry Mirrors"
```