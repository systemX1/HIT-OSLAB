# 实验说明

[实验说明和记录](./labs) ./labs/

[代码](./linux-0.11) ./linux-0.11

- 0 环境配置
- 1 实践项目∶控制操作系统启动
- 2 实践项目∶添加系统调用
- 3 实践项目∶打印进程日志
- 4 实践项目∶基于内核栈完成进程切换
- 5 实践项目∶信号量的实现与应用
- 6 实践项目∶地址映射与共享
- 7 实践项目∶终端设备字符显示的控制
- 8 实践项目∶proc文件的实现
- 9 大型实践项目:内核级线程的设计与 实现
- 10 大型实践项目:虚拟内存与交换分区的设计与实现
- 11 大型实践项目:鼠标驱动和简单的图形接口实现
- 12 大型实践项目:网卡驱动与网络协议的设计与实现



# Reference

[bilibili操作系统（哈工大李治军）32讲（全）超清](https://www.bilibili.com/video/BV1d4411v7u7)

[HIT-OSLAB-MANUAL](https://hoverwinter.gitbooks.io/hit-oslab-manual/content/index.html)

[*A Heavily Commented Linux Kernel Source Code* Website](http://oldlinux.org/)

[The Linux Kernel Archives](https://www.kernel.org/)

[Linux man pages online](https://man7.org/linux/man-pages/)

# Resource

**带目录电子书**

操作系统原理、实现与实践 李治军 刘宏伟 978-7-04-049245-3

*A Heavily Commemted Linux Kernel Source Code* V5.0.1

汇编语言第4版 王爽 978-7-302-53941-4

链接：https://pan.baidu.com/s/1_98NxYjNSv_kPxBEk6P6CQ 
提取码：yyds 

# Deploy

```shell
# 参考https://hoverwinter.gitbooks.io/hit-oslab-manual/content/environment.html https://github.com/Wangzhike/HIT-Linux-0.11/blob/master/0-prepEnv/%E5%87%86%E5%A4%87%E5%AE%89%E8%A3%85%E7%8E%AF%E5%A2%83.md

git clone https://github.com/systemX1/HIT-OSLAB
# 解压
# 安装gcc-3.4和必要依赖
./gcc-3.4-ubuntu/inst.sh amd64
sudo apt install build-essential bin86 manpages-dev libc6-dev-i386 ia32-libs ia32-libs-gtk libsm6:i386 libxpm4:i386 libx11-6:i386
# 切换gcc版本
ls /usr/bin/gcc*
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-3.4 100
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-9 100
sudo update-alternatives --config gcc
# 编译linux0.11并运行bochs
cd linux-0.11 & make -j 2 & ../run
```

