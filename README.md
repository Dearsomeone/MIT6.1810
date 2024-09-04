# MIT6.1810
`MIT6.1810 2024 Fall`（前身为`MIT6.S081`）课程的学习笔记和代码
## 课程资源
- 课程官网：[6.1810 / Fall 2024 (mit.edu)](https://pdos.csail.mit.edu/6.828/2024/schedule.html)
- 课程视频：[【操作系统工程】精译【MIT 公开课 MIT6.S081】_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1rS4y1n7y1/?spm_id_from=333.337.search-card.all.click&vd_source=698b8d2028c9b521a334cbd824e0fd59)
- 参考教材：《xv6: a simple, Unix-like teaching operating system》
- `xv6`中文文档：[介紹 | xv6 中文文档 (gitbooks.io)](https://th0ar.gitbooks.io/xv6-chinese/content/)
## 环境配置
环境配置使用`Docker Desktop`下载`Dockerhub`上的`ubuntu24.04`镜像。并且`Docker Desktop`使用`WSL2 ubuntu22.04`作为后端，以下指令在`WSL2 ubuntu22.04`中输入。
```bash
# 查看镜像列表
docker image ls
#REPOSITORY    TAG       IMAGE ID       CREATED         SIZE
#ubuntu        24.04    edbfe74c41f8   4 weeks ago     78.1MB
#hello-world   latest    d2c94e258dcb   16 months ago   13.3kB

# 运行该镜像的容器，名为test_ubuntu
docker run -it --name MIT6.1810 ubuntu:24.04

# 进入家目录
cd ~

# 进入了容器的SHELL
# 首先更新apt，否则无法通过apt安装软件
apt update && apt-get update && apt install -y sudo

# 安装MIT 6.1810 2024 Fall 所需的软件
# Tips：不挂vpn，反而下的快
sudo apt-get install git build-essential gdb-multiarch qemu-system-misc gcc-riscv64-linux-gnu binutils-riscv64-linux-gnu 

# 安装中途，tzdata需要设置时区，选择Asia/Shanghai即可

# 测试安装是否成功
qemu-system-riscv64 --version
#QEMU emulator version 8.2.2 (Debian 1:8.2.2+ds-0ubuntu1.2)
#Copyright (c) 2003-2023 Fabrice Bellard and the QEMU Project developers

riscv64-linux-gnu-gcc --version
#riscv64-linux-gnu-gcc (Ubuntu 13.2.0-23ubuntu4) 13.2.0
#Copyright (C) 2023 Free Software Foundation, Inc.
#This is free software; see the source for copying conditions.  There is NO
#warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

#退出容器
exit
```
## 重启容器
```bash
# 启动容器
docker start MIT6.1810
# 进入shell
docker exec -it MIT6.1810 /bin/bash

# 退出容器，但仍在后台运行
exit
# 停止容器
docker stop MIT6.1810
```
## 推送代码到github
参考：[版本控制 · 6.S081 All-In-One (dgs.zone)](https://xv6.dgs.zone/labs/use_git/git1.html)
