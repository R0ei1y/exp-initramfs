 # 下载Linux内核
wget https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.4.226.tar.xz

# 编译Linux内核
make menuconfig

# busybox
位于initramfs下，和init文件在一起

# Makefile
文件添加了三四个命令，建议从最后几行贴到自己的源码中。

initramfs: 初始化内存文件系统，会把initramfs中的文件打包，装入根目录的initramfs.cpio.gz
run-qemu: 初始化内存文件系统，并启动qemu
clean-fs: 清空initramfs.cpio.gz

# qemu-driver
需要手动构建磁盘镜像

dd if=/dev/zero of=./disk.img bs=1M count=1024
mkfs.ext2 -q ./disk.img

完成后使用mount挂载，往里面装文件即可。