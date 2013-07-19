package
=======

Cloud Foundry使用Chef 方式安装的时候，需要从网上下载大量的源码包，这些源码包从国外网站下载的话速度很慢，用github要提高不少的速度
使用命令:

  $ sudo mkdir /var/cache/dev_setup

  $ git clone git@github.com:ChenMingHe/package.git /var/cache/dev_setup

耐心等待一段时间，之后再安装的时候就不会出现下载超时的问题了

注意：因为otp_src_R14B01.tar.gz的安装需要gcc4.4的版本，如果在安装这个包的时候出现错误，请如下尝试：

确认已经安装了gcc-4.4，不确定就运行下面的命令

$ sudo apt-get install gcc-4.4

将gcc版本更换成gcc4.4，执行命令：

$ sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-4.4 50

然后确定使用的gcc版本是gcc4.4，可以用命令查看

$ gcc -v

然后进入到otp_src_R14B01的缓存目录下，因为Chef安装的时候将这个压缩包解压到了/tmp目录下，所以执行以下命令

$ cd /tmp/otp_src_R14B01

$ make clean 

$ make

如果顺利，这里应该就可以将otp_src_R14B01编译完成了，然后重新执行Chef的安装脚本就可以自动安装了
