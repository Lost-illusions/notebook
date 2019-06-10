# 安装

1. 安装git
   `sudo apt-get install git`

2. 安装VsCode
   1. 下载deb包
   2. 执行如下命令
        ```
        sudo dpkg -i <file>.deb
        sudo apt-get install -f
        ```
3. 安装Popcorn Time 
   1. 下载
        ```
        $ sudo mkdir /opt/popcorn-time
        FOR 32-BIT SYSTEM EXECUTE:
        $ sudo wget -qO- https://get.popcorntime.sh/build/Popcorn-Time-0.3.10-Linux-32.tar.xz | sudo tar Jx -C /opt/popcorn-time
        FOR 64-BIT SYSTEM EXECUTE:
        $ sudo wget -qO- https://get.popcorntime.sh/build/Popcorn-Time-0.3.10-Linux-64.tar.xz | sudo tar Jx -C /opt/popcorn-time
        ```
    1. 链接
        `sudo ln -sf /opt/popcorn-time/Popcorn-Time /usr/bin/popcorn-time`
4. 安装g++
    ```
    sudo apt-get update
    sudo apt-get install g++
    ```

# 配置
1. VsCode的C++环境配置
   [见此](https://blog.csdn.net/qq_34347375/article/details/80851417)
2. PyCharm的PyQt5配置
   1. 安装PyQt5
        `conda install pyqt`
   2. 安装qtdesigner
        ` sudo apt-get install qt5-default qttools5-dev-tools`
   3. 这时，在终端输入`designer`就可以启动绘制界面了
   4. PyCharm中工具的配置
      1. QtDesigner的配置
         1. ![QtDesigner的配置](img/1.png)
         2. Program 填写的内容 可在终端使用`whereis designer`查看，例：`/home/nathaniel/anaconda3/bin/designer`
         3. Working directory是工作目录
      2. PyUIC的配置
         1. ![PyUIC的配置](img/2.png)
         2. Program 是工作环境的python的位置，例：`/home/nathaniel/anaconda3/bin/python`
         3. Arguments 填写`-m PyQt5.uic.pyuic $FileName$ -o $FileNameWithoutExtension$.py `
         4. Working directory 填写 `$FileDir$`


# 一些命令
1. 解压
   `

# 一些杂乱的问题
1. 权限问题
   若无写入文件失败，应修改文件夹/文件权限

    ```
    chmod 777 -R  需要改变存取模式的目录
    ```
    sudo chmod 600 ××× （只有所有者有读和写的权限）
    sudo chmod 644 ××× （所有者有读和写的权限，组用户只有读的权限）
    sudo chmod 700 ××× （只有所有者有读和写以及执行的权限）
    sudo chmod 666 ××× （每个人都有读和写的权限）
    sudo chmod 777 ××× （每个人都有读和写以及执行的权限）

2. github访问慢
   1. 打开hosts文件
   `sudo vim /etc/hosts`
   1. 添加以下内容
        ```
        192.30.253.113  github.com
        151.101.25.194 github.global.ssl.fastly.net
        192.30.253.121 codeload.github.com
        ```
    1. 保存并退出，重启网络服务
        `sudo /etc/init.d/networking restart`

3. 播放音乐杂音问题
   1. 终端 `alsamixer
   2. ` 进入声卡设置
   3. 按F6，选择HDA Intel PCH
   4. 将所有有红色的调至没有红色
   5. 感觉这样好了些，但没有完全消除

4. 开机进入BusyBox界面(initramfs)
   1. 输入`exit`，观察显示的英文，是哪个地方出现了error,例如：`/dev/sdc2`
   2. 输入`fsck -y /dev/sdc2`,等待
   3. 输入`exit`，进入桌面系统
