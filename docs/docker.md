# Docker

## 安装

通过国内镜像手动安装

- <https://mirrors.tuna.tsinghua.edu.cn/help/docker-ce/>

或者使用脚本自动完成

```sh
curl -fsSL https://get.docker.com | bash -s docker --mirror Aliyun
```

手动通过华为镜像安装

```sh
sudo apt install -y curl gnupg2 ca-certificates lsb-release ubuntu-keyring

curl https://mirrors.huaweicloud.com/docker-ce/linux/ubuntu/gpg | gpg --dearmor \
  | sudo tee /etc/apt/trusted.gpg.d/docker-ce.gpg > /dev/null

sudo add-apt-repository "deb [arch=amd64] https://mirrors.huaweicloud.com/docker-ce/linux/ubuntu $(lsb_release -cs) stable"

sudo apt install -y docker-ce python3-docker

sudo apt-mark hold docker-buildx-plugin docker-ce docker-ce-cli docker-ce-rootless-extras docker-compose-plugin python3-docker
```

手动通过中国科学院镜像安装

```sh
export DOWNLOAD_URL="https://fast-mirror.isrc.ac.cn/docker-ce"
# 如您使用 curl
curl -fsSL https://raw.githubusercontent.com/docker/docker-install/master/install.sh | sh
```

## 参数

```sh
cat << EOF > /etc/docker/daemon.json
{
  "features": {
    "buildkit": true
  },
  "iptables": false,
  "exec-opts": [
    "native.cgroupdriver=systemd"
  ],
  "ip-forward": true,
  "log-driver": "json-file",
  "log-level": "warn",
  "log-opts": {
    "max-size": "100m",
    "max-file": "3"
  },
  "storage-driver": "overlay2",
  "default-ulimits": {
    "nofile": {
      "Name": "nofile",
      "Soft": 1048576,
      "Hard": 1048576
    },
    "memlock": {
      "Name": "memlock",
      "Soft": -1,
      "Hard": -1
    },
    "nproc": {
      "Name": "nproc",
      "Soft": 65535,
      "Hard": 65535
    },
    "core": {
      "Name": "core",
      "Soft": -1,
      "Hard": -1
    }
  },
  "default-shm-size": "1G",
  "default-cgroupns-mode": "host",
  "no-new-privileges": false
}
EOF
```

## 权限

桌面环境还需要添加用户到 docker 组

```sh
sudo usermod -a -G docker $USER
```
