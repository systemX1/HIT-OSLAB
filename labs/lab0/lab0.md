# lab 0 环境配置

### 0 VMWare和Ubuntu20.04

仅供参考。在实验开始前，假设  

### 1 



### Reference

[HIT-OSLAB-MANUAL](https://hoverwinter.gitbooks.io/hit-oslab-manual/content/index.html)

[HIT-Linux-0.11/准备安装环境.md at master · Wangzhike/HIT-Linux-0.11 (github.com)](https://github.com/Wangzhike/HIT-Linux-0.11/blob/master/0-prepEnv/准备安装环境.md)

### 安装

```shell
#换源
sudo vi /etc/apt/sources.list
#@添加源
sudo apt-get update
sudo apt-get upgrade

#git
sudo apt install git

#oh-my-zsh
sudo apt install zsh
sudo chsh -s $(which zsh) #@将 Zsh 设为默认 Shell
#@ 注销当前用户重新登录
echo $SHELL
git clone git://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
zsh
source ~/.zshrc

#gcc-3.4
cd gcc-3.4/amd64        #进入该目录
sudo dpkg -i *.deb      #安装所有包

#ssh
sudo /etc/init.d/ssh start
sudo vi /etc/ssh/sshd_config
sudo /etc/init.d/ssh restart

#firewalld
sudo apt install firewalld

#typora
# or use
# sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BA300B7755AFCFAE
wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add -
#@ add Typora's repository
sudo add-apt-repository 'deb https://typora.io/linux ./'
sudo apt-get update
#@ install typora
sudo apt-get install typora

#VS Code  https://code.visualstudio.com/docs/setup/linux
sudo apt install ./<file>.deb

# github_desktop_ubuntu https://gist.github.com/berkorbay/6feda478a00b0432d13f1fc0a50467f1
sudo wget https://github.com/shiftkey/desktop/releases/download/release-2.6.3-linux1/GitHubDesktop-linux-2.6.3-linux1.deb
sudo apt-get install gdebi-core 
sudo gdebi GitHubDesktop-linux-2.6.3-linux1.deb
```

### 错误

```shell
#在vmware虚拟机中安装ubuntu下使用vi编辑文件，发现上下左右方向键不能在文本中移动，出现ABCD字符，backspace也不能删除字符
sudo apt-get remove vim-common 
sudo apt-get install vim

#多版本gcc共存
#@ 查看当前系统中安装的所有的gcc和g++的版本
#@ https://my.oschina.net/u/4411754/blog/3823604
ls /usr/bin/gcc*
ls /usr/bin/g++*
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-3.4 100
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-9 100
sudo update-alternatives --config gcc

#同步时间
sudo apt-get install ntpdate
sudo ntpdate cn.pool.ntp.org
sudo hwclock --systohc

#gcc编译*.c /usr/bin/ld: cannot find crt1.o: No such file or directory
sudo apt-get install libc6-dev-mipsel-cross libc6-dev-mipsel-cross libc-dev-mipsel-cross
export LIBRARY_PATH=/usr/lib/x86_64-linux-gnu/
export LIBRARY_PATH=/usr/lib/i386-linux-gnu/
sudo ln /lib/i386-linux-gnu/libgcc_s.so.1  /usr/lib/gcc/x86_64-linux-gnu/3.4.6/libgcc_s.so
l /lib/x86_64-linux-gnu | grep libgcc
l /lib/i386-linux-gnu | grep libgcc
#@ https://stackoverflow.com/questions/6329887/compiling-problems-cannot-find-crt1-o
#@ https://serverfault.com/questions/266138/cannot-find-lgcc-s-from-gcc-3-4-on-ubuntu-11-04
#@ https://blog.csdn.net/qq_23827747/article/details/54710815
#@ https://www.huaweicloud.com/articles/fe71979abe1909cd2fab54f6d4ae879f.html
```

### 配置

```sh
#VS code连接VMware
#@VS code安装插件ssh-remote
#@VM 
ip address
#@复制ip 192.168.80.129
#@配置虚拟机防火墙
sudo passwd root
su root
#@启用22端口并重启防火墙
firewall-cmd --permanent --add-port=22/tcp
firewall-cmd --reload

# 翻墙
#主机纸飞机允许局域网
#设置Ubuntu Network
```



