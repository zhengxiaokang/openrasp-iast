在 CentOS 7 上安装 docker-compose 的步骤如下：
1. 安装 Docker
docker-compose 依赖于 Docker，因此需要先安装 Docker。

# 卸载旧版本 Docker（如果有）
sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine

# 安装依赖工具
sudo yum install -y yum-utils

# 添加 Docker 官方仓库
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

# 安装 Docker
sudo yum install -y docker-ce docker-ce-cli containerd.io

# 启动 Docker 服务
sudo systemctl start docker

# 设置 Docker 开机自启
sudo systemctl enable docker

# 验证 Docker 是否安装成功
docker --version

2. 安装 docker-compose
docker-compose 是一个独立的二进制文件，可以通过以下步骤安装。

# 下载最新版本的 docker-compose
sudo curl -L "https://github.com/docker/compose/releases/download/v2.23.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

# 授予执行权限
sudo chmod +x /usr/local/bin/docker-compose

3、验证安装
docker-compose --version

