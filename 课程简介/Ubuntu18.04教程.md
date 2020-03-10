# 系统设置

#### 设置ubuntu的更新源：

[<https://www.cnblogs.com/kehaimin/p/8616057.html>](https://www.cnblogs.com/kehaimin/p/8616057.html)

1、备份原来的更新源:

```shell
sudo -s cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

2、修改更新源:

```shell
sudo vim /etc/apt/sources.list
```

 修改为清华源： 将下面所有内容复制，粘贴并覆盖`sources.list`文件中的所有内容：

```linux
# 默认注释了源码镜像以提高 apt update 速度，如有需要可自行取消注释
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-security main restricted universe multiverse

# 预发布软件源，不建议启用
# deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-proposed main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-proposed main restricted universe multiverse
```

清华源：进入网址复制可更改系统版本：[<https://mirror.tuna.tsinghua.edu.cn/help/ubuntu/>](https://mirror.tuna.tsinghua.edu.cn/help/ubuntu/)

如果换源之后任然无法创建环境,并且报网络连接的错误，可采取如下办法

```shell
vim  ~/.condarc
删除defaults行
```

3、让更新源生效：

```shell
sudo apt-get update
```

更换源之后可以更新一下系统

```shell
sudo apt-get update && apt-get upgrade
```

#### 设置Ubuntu的root密码

```shell
sudo passwd root
```

#### 重置Ubuntu(18.04)密码

[参考文章](https://ywnz.com/linuxjc/2635.html)

1、开机一直按住`ESC`键，选择`Advanced options for Ubuntu`，回车进入到`Grub`。然后移动到最新的`recovery mode`（注意这里不要回车进入到该模式），而是按下`E`键，进入编辑模式。

2、按下箭头往下翻，在倒数几行找到`recovery nomodeset`几个字，并将这几个字删除，删除之后，在该行末尾追加`quiet splash rw init=/bin/bash`，然后按下`F10`

![ctpMt.png](https://ww1.yunjiexi.club/2020/03/09/ctpMt.png)

![ctmB0.png](https://ww1.yunjiexi.club/2020/03/09/ctmB0.png)

![ctcae.png](https://ww1.yunjiexi.club/2020/03/09/ctcae.png)

之后输入`passwd`来修改root密码。修改用户密码可以在进入到系统中，最后大功告成！

![ctb2p.png](https://ww1.yunjiexi.club/2020/03/09/ctb2p.png)

#### 设置共享文件夹

[https://jingyan.baidu.com/article/d5c4b52ba4f3a3da570dc579.html](https://jingyan.baidu.com/article/d5c4b52ba4f3a3da570dc579.html)

共享文件夹的路径位：`/mnt/hgfs/...`

#### Ubuntu安装deb文件

```shell
sudo dpkg -i <package.deb>
```

#### 终端美化

[https://zhuanlan.zhihu.com/p/49759462](https://zhuanlan.zhihu.com/p/49759462)

[https://www.jianshu.com/p/4fde9ae77922](https://www.jianshu.com/p/4fde9ae77922)

[https://www.jianshu.com/p/a36e1ac468ce](https://www.jianshu.com/p/a36e1ac468ce)

首先安装zsh

```shell
sudo apt-get install zsh
```

替换系统的bash为zsh

```shell
chsh -s /bin/zsh
```

下载oh-my-zsh（第二个链接不上，就直接在本地命名一个文件`install.sh`，然后将网站的内容拷贝过去）

```
sudo apt-get install git (如果没有安装git,先执行这一步)
sudo wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | sh
```

oh-my-zsh推荐插件和主题：

[https://www.cnblogs.com/EasonJim/p/7863099.html](https://www.cnblogs.com/EasonJim/p/7863099.html)

[https://www.cnblogs.com/EasonJim/p/6283190.html](https://www.cnblogs.com/EasonJim/p/6283190.html)

agnoster、autojump、zsh-syntax-highlight、zsh-autosuggestions

```shell
sudo apt install autojump
vi ~/.zshrc
. /usr/share/autojump/autojump.sh 文末添加这一句
```

然后source ~/.zshrc就完成了。

重启

卸载：

```shell
uninstall_oh_my_zsh zsh
```

#### 美化

[https://www.pling.com/s/Gnome/browse/page/2/ord/rating/](https://www.pling.com/s/Gnome/browse/page/2/ord/rating/)

[ubuntu 18.04 - zsh: command not found: ifconfig](https://www.sunzhongwei.com/ubuntu-1804-ifconfig-command-not-found)

#### 更换pip源

清华源：[https://pypi.tuna.tsinghua.edu.cn/simple](https://mirror.tuna.tsinghua.edu.cn/help/pypi/)

临时使用：

```shell
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple some-package
```

注意，`simple` 不能少, 是 `https` 而不是 `http`

设为默认：

升级 pip 到最新的版本 (>=10.0.0) 后进行配置：

```shell
pip install pip -U
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
```

如果您到 pip 默认源的网络连接较差，临时使用本镜像站来升级 pip：

```shell
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple pip -U
```

![](https://i.loli.net/2019/11/09/1aSMZioPs8YvuUp.png)

# 普通软件的安装

#### 安装ssh(实现xshell与Ubuntu互连)

参考

[https://blog.csdn.net/u011596455/article/details/60322568](https://blog.csdn.net/u011596455/article/details/60322568)

[https://blog.csdn.net/qq_31781407/article/details/80949512](https://blog.csdn.net/qq_31781407/article/details/80949512)

[https://blog.csdn.net/lee_x_lee/article/details/83899314](https://blog.csdn.net/lee_x_lee/article/details/83899314)

- 设置防火墙

![cvtj0.png](https://ww1.yunjiexi.club/2020/03/10/cvtj0.png)

- 安装SSH-server服务，并启用

![cvvUt.png](https://ww1.yunjiexi.club/2020/03/10/cvvUt.png)

- 成功

![cvFZp.png](https://ww1.yunjiexi.club/2020/03/10/cvFZp.png)

#### 安装vmtool工具

安装完虚拟机后，vmtools一直是灰色的，不能安装

![](https://i.loli.net/2019/11/07/wr1vl9LFQgdHEY4.png)

接下来安装，首先将压缩包从VMware Tools光盘中拷贝出来，然后再解压

```shell
tar -zxvf VMwareTools-10.3.2-9925305.tar.gz 
```

然后执行：

```shell
sudo ./vmware-install.pl
```

安装完成之后，reboot即可。

#### 安装蓝灯：

[<https://github.com/getlantern/lantern>](https://github.com/getlantern/lantern)

#### 安装enpass：

[<https://www.enpass.io/support/how-to-install-enpass-on-linux/>](https://www.enpass.io/support/how-to-install-enpass-on-linux/)

#### 安装flux：

[<https://github.com/xflux-gui/fluxgui>](<https://github.com/xflux-gui/fluxgui>)

#### 安装typora：

[<https://www.typora.io/#linux>](https://www.typora.io/#linux)

https://mirror.tuna.tsinghua.edu.cn/help/ubuntu/)

#### ubuntu安装vim：

[<https://jingyan.baidu.com/article/046a7b3efd165bf9c27fa915.html>](<https://jingyan.baidu.com/article/046a7b3efd165bf9c27fa915.html>)

```shell
sudo apt install vim
```

#### ubuntu安装搜狗输入法：

[<https://pinyin.sogou.com/linux/?r=pinyin>](<https://pinyin.sogou.com/linux/?r=pinyin>)   和[<https://blog.csdn.net/fx_yzjy101/article/details/80243710>](<https://blog.csdn.net/fx_yzjy101/article/details/80243710>)

```shell
sudo apt-get install fcitx-bin
sudo apt-get install fcitx-bin
```

安装完**fcitx**记得重启一遍，再安装搜狗输入法，在语言设置里安装汉语(中国)，在配置输入法中，添加输入法中取消`only show current language`，然后搜索搜狗输入法。

#### 安装Xtreme Download Manager:

 [<https://blog.csdn.net/qq378947986/article/details/80821237>](<https://blog.csdn.net/qq378947986/article/details/80821237>)

#### 安装anaconda：

[<https://mirrors.tuna.tsinghua.edu.cn/help/anaconda/>](<https://mirrors.tuna.tsinghua.edu.cn/help/anaconda/>)

```shell
chmod a+x Anaconda3-5.3.1-Linux-x86_64.sh
sudo ./Anaconda3-5.3.1-Linux-x86_64.sh
```

安装完成之后配置anaconda的环境变量(当然也可以在安装的时候就输入yes直接配置好环境变量)：

```shell
Do you wish the installer to initialize Anaconda3
in your /home/leo/.bashrc ? [yes|no]
[no] >>> yes
```

#### 安装Dropbox：

[<https://www.dropbox.com/install>](<https://www.dropbox.com/install>)，因为墙的原因装不上，拷贝命令行中的链接：

```shell
cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -
```

将[https://www.dropbox.com/download?plat=lnx.x86_64](https://www.dropbox.com/download?plat=lnx.x86_64)拷贝到浏览器中，使用浏览器下载下来

接着，从新建的 `.dropbox-dist` 文件夹运行 Dropbox 守护程序。

```shell
~/.dropbox-dist/dropboxd
```

如果是首次在服务器上运行 Dropbox，系统会要求您将链接复制并粘贴到运行的浏览器中，以便创建一个新的帐户或将服务器附加到现有帐户上。操作完成后，系统会在您的主目录中创建 Dropbox 文件夹。下载这个 [Python 脚本](https://www.dropbox.com/download?dl=packages/dropbox.py)，通过命令行控制 Dropbox。为了方便访问，请在 PATH 中的任何地方放入此脚本的符号链接。

![](https://s2.ax1x.com/2019/03/24/AY0z5T.png)

#### 安装PicGo：

[<https://github.com/Molunerfinn/PicGo/releases>](<https://github.com/Molunerfinn/PicGo/releases>)

下载[picgo-2.0.4-x86_64.AppImage](https://github.com/Molunerfinn/PicGo/releases/download/v2.0.4/picgo-2.0.4-x86_64.AppImage)版本，然后，[Linux如何运行.AppImage文件](<https://jingyan.baidu.com/article/d5a880ebdfc12d13f047cc62.html>).(修改属性，将权限赋予可执行文件即可)

#### 安装Flameshot截图工具：

[<https://www.omgubuntu.co.uk/2018/01/flameshot-linux-screenshot-tool-annotation>](https://www.omgubuntu.co.uk/2018/01/flameshot-linux-screenshot-tool-annotation)。

```shell
sudo apt-get install flamesho
```

#### 安装shutter截图工具：

[<https://www.cnblogs.com/CZM-/p/5858759.html>](<https://www.cnblogs.com/CZM-/p/5858759.html>)

出现错误：*E: 有未能满足的依赖关系。请尝试不指明软件包的名字来运行“apt-get -f install”(也可以指定一个解决办法)。*

**解决办法：**遇到此类问题，直接在终端输入

```shell
sudo apt-get --fix-broken install
```

卸载软件：

```shell
sudo apt-get remove softname1 softname2 softname3
```

#### 安装网易云音乐：

[https://music.163.com/#/download](https://music.163.com/#/download)

#### 安装wine

1、查看电脑系统是多少位的

```shell
uname -m
```

2、如果是64位，先启动32位架构支持

```shell
sudo dpkg --add-architecture i386
```

3、从wine储存库下载密钥

```shell
wget -q -O - https://dl.winehq.org/wine-builds/Release.key | sudo apt-key add -
```

4、添加程序储存库

```shell
sudo apt-add-repository https://dl.winehq.org/wine-builds/ubuntu/
sudo apt-add-repository ‘deb https://dl.winehq.org/wine-builds/ubuntu/ artful main
```

5、更新软件包

```shell
sudo apt-get update	
```

6、安装wine稳定版

```shell
sudo apt-get install –install-recommends winehq-stable
```



# 开发环境配置

#### 安装PyTorch

##### **禁用noouveau驱动**

在root下执行最好，省去sudo

```shell
sudo vim /etc/modprobe.d/blacklist.conf
```

在文本最后添加：

```shell
blacklist nouveau
options nouveau modeset=0
```

然后执行：

```shell
sudo update-initramfs -u   # 重新生成 kernel initramfs
```

重启后，执行以下命令，如果没有屏幕输出，说明禁用nouveau成功.

```shell
lsmod | grep nouveau
```

##### **安装英伟达驱动**

去英伟达官网下载显卡驱动：[<https://www.nvidia.cn/Download/index.aspx?lang=cn>](<https://www.nvidia.cn/Download/index.aspx?lang=cn>)，

![](https://s2.ax1x.com/2019/03/24/AYfe81.png)

一个`.run`文件，首先赋予可执行权限

```shell
chmod +x NVIDIA-Linux-x86_64-418.56.run 
```

然后以root方式运行该文件

```shell
sudo ./NVIDIA-Linux-x86_64-418.56.run
```

查看是否安装成功

```shell
sudo nvidia-smi
```

如果显示GPU列表，则证明驱动安装成功了。

##### **安装CUDA**

去这里下载CUDA套件：[<https://developer.nvidia.com/cuda-downloads>](<https://developer.nvidia.com/cuda-downloads>)

```shell
sudo dpkg -i cuda-repo-ubuntu1804-10-1-local-10.1.105-418.39_1.0-1_amd64.deb
sudo apt-key add /var/cuda-repo-10-1-local-10.1.105-418.39/7fa2af80.pub
sudo apt-get update
sudo apt-get install cuda
```

安装完成之后，配置环境变量，`vim ~/.bashrc`加上配置信息：

```shell
export CUDA_HOME=/usr/local/cuda-10.1
export LD_LIBRARY_PATH=${CUDA_HOME}/lib64
export PATH=${CUDA_HOME}/bin:${PATH}
```

使用命令`source ~/.bashrc`使它生效，然后用下面命令查看安装版本信息：

```
nvcc -V
```

接着测试是否安装成功：

```
cd /usr/local/cuda-10.1/samples/1_Utilities/deviceQuery
sudo make
./deviceQuery
```

##### **安装CUDNN**

下载CUDNN：[https://developer.nvidia.com/rdp/cudnn-download](https://developer.nvidia.com/rdp/cudnn-download),

当然在下载之前还有登录，然后选择版本界面，我们选择`cuDNN Library for Linux`，下载后是一个压缩包，解压出来，使用以下两条命令复制这些文件到CUDA目录下：

```shell
sudo cp lib64/* /usr/local/cuda-10.1/lib64/
sudo cp include/* /usr/local/cuda-10.1/include/
```

##### **最后安装pytorch**

```
conda install pytorch torchvision cudatoolkit=10.0 -c pytorch
```

若提示权限不足，输入命令：

```shell
sudo chmod -R 777 anaconda3
```

获取权限再执行安装。

##### **测试GPU加速结果**

```Python
import torch

device = torch.cuda.is_available()

print(device)
```

参考：[<https://www.cnblogs.com/iloveblog/p/7683349.html>](<https://www.cnblogs.com/iloveblog/p/7683349.html>),

[https://blog.csdn.net/qq_33200967/article/details/80689543#CUDNN_205](https://blog.csdn.net/qq_33200967/article/details/80689543#CUDNN_205)，

[https://blog.csdn.net/weixin_40294256/article/details/79173174](https://blog.csdn.net/weixin_40294256/article/details/79173174)

https://music.163.com/#/download)

#### 安装Tensorflow

参考：[https://zhuanlan.zhihu.com/p/49759462](https://zhuanlan.zhihu.com/p/49759462)

##### 禁用系统自带的显卡驱动nouveau,安装NVIDIA驱动

参考torch的步骤

##### **检查gcc版本**

g++安装不成功，缺少Libc6-dev，去官网查看：[https://pkgs.org/download/libc6-dev](https://pkgs.org/download/libc6-dev)

```shell
sudo apt-get install libc6-dev
```

ubuntu18.04自带的gcc是7.3.0版本，需要降级为6以下，我们选择4.8，具体命令如下：

```shell
$ sudo apt-get install gcc-4.8
$ sudo apt-get install g++-4.8
$ cd /usr/bin
$ sudo mv gcc gcc.bak  # 备份原来版本
$ sudo ln -s gcc-4.8 gcc # 将gcc链接至4.8
$ sudo mv g++ g++.bak
$ sudo ln -s g++-4.8 g++
$ gcc -v && g++ -v  # 查看系统的gcc版本是否已更改
```



#### 安装Pycharm

首先去官网下载软件安装包，解压，然后在bin文件夹下，执行

```shell
./pycharm.sh	
```

接着，添加桌面快捷方式：`Tools`———> `Create Desktop Entry`，再从所有程序里添加到`喜欢`即可。



