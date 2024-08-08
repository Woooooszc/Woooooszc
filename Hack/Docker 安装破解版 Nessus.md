# Docker 安装破解版 Nessus

> TIME : 2024-07-17
> TAGS : Docker ; Nessus

## docker 镜像源

/etc/docker/daemon.json

```json
{ "registry-mirrors": ["https://docker.1panel.live/"] }
```

重启 docker：`systemctl restart docker`

## Nessus

- 拉取镜像：

  `docker pull ramisec/nessus`

- 启动容器：

  `docker run -itd --name=ramisec_nessus -p 8834:8834 ramisec/nessus`

- 修改容器中的 update.sh：

  `docker cp ramisec_nessus:/nessus/update.sh /opt/update.sh`

  将 update_url 修改为`https://plugins.nessus.org/v2/nessus.php?f=all-2.0.tar.gz&u=56b33ade57c60a01058b1506999a2431&p=1ee9c89d5379a119a56498f2d5dff674`

  放回容器中：`docker cp /opt/update.sh ramisec_nessus:/nessus/up1.sh`

- 更新插件&修改密码

  进入容器 bash：`docker exec -it ramisec_nessus /bin/bash`

  运行 up1.sh 进行更新：`./up1.sh`

  更新编译完成后，进入 /opt/nessus/sbin/ ，运行`./nessuscli chpasswd admin`修改 admin 密码
