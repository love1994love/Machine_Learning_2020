# 课程环境准备

## 0.操作系统

[Ubuntu](https://wiki.ubuntu-tw.org/index.php?title=%E9%A6%96%E9%A0%81)

## 1.安装zsh

首先安装zsh

```shell
sudo apt-get install zsh
```

替换系统的bash为zsh

```shell
chsh -s /bin/zsh
```

下载oh-my-zsh

```
sudo apt-get install git 
sudo wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | sh
```

## 2.安装Pyenv

[Github地址](https://github.com/pyenv/pyenv)

### 1.安装

```shell
git clone https://github.com/pyenv/pyenv.git ~/.pyenv
```

### 2.配置环境变量

```shell
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.zshrc
exec "$SHELL"
```

### 3.pyenv的指令

```shell
•	pyenv versions
	列出目前系統中所有安裝的 Python
•	pyenv version
	显示目前预设的 Python 版本
• 	pyenv global <python_version>
	设定预设 Python 版本
• 	pyenv install <python_version>
	安装特定版本的 Python
• 	pyenv uninstall <python_version>
	移除特定版本的 Python 
```

使用 pyenv 后，仍然可以通过 pip 管理套件，所有 pip 操作的对象都在预设的 Python 版本。比如：

```shell
>> pyenv install 3.6.8 	#安装python3.6.8版本
>> pip install numpy==1.17.5    #默认安装在pyenv versions中带星号的python环境中
# readtime out错误
>> pip install --default-timeout=100 --no-cache-dir numpy # 给个时间限制即可
```

[Ubuntu18.04下使用pyenv安装python报错：BUILD FAILED (Ubuntu 18.04 using python-build 20180424)](https://blog.csdn.net/BigData_Mining/article/details/100100375)

[https://stackoverflow.com/questions/37227854/pyenv-build-failed-ubuntu-15-04-using-python-build-20160509](https://stackoverflow.com/questions/37227854/pyenv-build-failed-ubuntu-15-04-using-python-build-20160509)

### 4 出错解决方案：

执行如下命令：

```shell
sudo apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils tk-dev
```

然后在执行安装即可。

### 5 安装离线安装包

- 手动下载python3.6.8

  pyenv安装python时会给出下载地址, 去这个地址下载即可, 把安装包传给linux。

-  在~/.pyenv目录下创建cache文件夹, 把安装包移动到cache文件夹下

- 进入cache文件夹下, 再次使用pyenv install 3.6.8 即可离线安装

![8PaJXT.png](https://s2.ax1x.com/2020/03/10/8PaJXT.png)

### 6 权限不够，有警告

问题？

WARNING: The directory '/home/zhex/.cache/pip/http' or its parent directory is not owned...

```shell
sudo chmod -R 777 /home/$USERNAME/.cache/pip/
# 之后执行,clear可实现清屏
pip install ...
```

## 3 安装Git

### 1.安装

```shell
sudo apt-get install git
```

### 2.Git指令

```
•	git init
	初始化目前的目录
• 	git clone <url>
	將网路上的资料 ”clone” 到本地端
• 	git add <files>
	將档案加入追踪
• 	git rm --cached <file>
	取消追踪档案
• 	git status
	查看目前的工作环境状态
• 	git commit -m <description>
	將追踪的档案提交一下
• 	git remote add origin <url>
	將本地端与远端连接起来
• 	git push -u origin <branch>
	將 commit的内容同步到 GitHub
```

### 3.开始

- 告诉git你是谁

```shell
>> git config --global user.name "leo" 
>> git config --global user.email "z_wjun9407@163.com"

>> git config --list    #查看
```

![8iPwXF.png](https://s2.ax1x.com/2020/03/10/8iPwXF.png)

- 初始化同步目录

```shell
 >> git init
Initialized empty Git repository in /home/leo/Desktop/homework/.git/
```

- 添加文件

```shell
git add ML2020SPRING\ Python\ Packages.xlsx
```

- 提交文件

```
git commit -m "ML2020SPRING"
```

- 连接远程端

```
git remote add origin https://github.com/love1994love/Machine_Learning_2020.git
```

- 推送到远程端

```
git push -u origin master
```

![8iPBm4.png](https://s2.ax1x.com/2020/03/10/8iPBm4.png)

![8iPr79.png](https://s2.ax1x.com/2020/03/10/8iPr79.png)

