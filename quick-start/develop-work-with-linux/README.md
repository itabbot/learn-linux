# 完全使用 Linux 操作系统进行开发和工作

1. 考察和评估
    - 后端开发相关的环境和工具基本都支持 Linux，准确来说应该是 Linux 更佳。
    - 很多常用的应用程序也提供 Linux 版本。
    - 但是也有一部分（不少）应用程序并不提供 Linux 版本。
    - 所以，最好是能安装双系统，多安装一个 Windows 以备不时之需。
2. 确定目标系统
    - Linux： 应用程序普遍支持 Ubuntu，那就安装目前最新版本 Ubuntu 22.04.2 LTS。
    - Windows： 目前最高版本是 Windows 11，但本人不太喜欢，所以选择 Windows 10 专业版。
3. 准备安装 U 盘
    - 下载 [Ubuntu 官方镜像](https://ubuntu.com/download/desktop)。
    - 下载 [Windows 镜像](https://msdn.itellyou.cn)（网络资源）。
    - 使用 [balenaEtcher](https://etcher.balena.io/) 烧录 Ubuntu 镜像到 U 盘。
    - 使用 [rufus](https://github.com/pbatard/rufus) 烧录 Windows 镜像到 U 盘（同上分开）。
4. 安装 Ubuntu
    - 备份电脑中重要的资料。
    - 按照[官方安装教程](https://ubuntu.com/tutorials/install-ubuntu-desktop)进行操作。
    - 注意磁盘分区：
        - 引导分区： 保留原有的 ESP 分区作为引导分区。
        - 挂载根目录（/）： 主分区，ext4格式，200G。
        - 挂载主目录（/home）： 逻辑分区，ext4格式，150G。
        - 虚拟内存分区（SWAP）： 逻辑分区，16G。
        - 剩下的留给后续安装 Windows。
5. 安装 Windows
    - 按照安装流程提示进行。
    - 注意磁盘分区： 主分区，NTFS格式，使用剩余的所有容量。
6. 设置默认引导启动 Ubuntu。
