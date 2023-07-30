# 在 Windows 中使用 Docker 安装 Linux 操作系统

```shell
# 直接运行debian容器
$ docker run -it debian

# 若本地没有对应的镜像，会自动下载最新版本
Unable to find image 'debian:latest' locally
latest: Pulling from library/debian
785ef8b9b236: Pull complete
Digest: sha256:9f76a008888da28c6490bedf7bdaa919bac9b2be827afd58d6eb1b916e1e5918
Status: Downloaded newer image for debian:latest

# 运行后即可像普通Linux系统一样操作
$ ls -l
total 48
lrwxrwxrwx   1 root root    7 Jul 25 00:00 bin -> usr/bin
drwxr-xr-x   2 root root 4096 Jul 14 16:00 boot
drwxr-xr-x   5 root root  360 Jul 30 03:59 dev
drwxr-xr-x   1 root root 4096 Jul 30 03:59 etc
drwxr-xr-x   2 root root 4096 Jul 14 16:00 home
lrwxrwxrwx   1 root root    7 Jul 25 00:00 lib -> usr/lib
lrwxrwxrwx   1 root root    9 Jul 25 00:00 lib32 -> usr/lib32
lrwxrwxrwx   1 root root    9 Jul 25 00:00 lib64 -> usr/lib64
lrwxrwxrwx   1 root root   10 Jul 25 00:00 libx32 -> usr/libx32
drwxr-xr-x   2 root root 4096 Jul 25 00:00 media
drwxr-xr-x   2 root root 4096 Jul 25 00:00 mnt
drwxr-xr-x   2 root root 4096 Jul 25 00:00 opt
dr-xr-xr-x 341 root root    0 Jul 30 03:59 proc
drwx------   2 root root 4096 Jul 25 00:00 root
drwxr-xr-x   3 root root 4096 Jul 25 00:00 run
lrwxrwxrwx   1 root root    8 Jul 25 00:00 sbin -> usr/sbin
drwxr-xr-x   2 root root 4096 Jul 25 00:00 srv
dr-xr-xr-x  11 root root    0 Jul 30 03:59 sys
drwxrwxrwt   2 root root 4096 Jul 25 00:00 tmp
drwxr-xr-x  14 root root 4096 Jul 25 00:00 usr
drwxr-xr-x  11 root root 4096 Jul 25 00:00 var
```
