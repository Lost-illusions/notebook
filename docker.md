# docker的使用

## 安装docker
   1. [见此](https://www.jianshu.com/p/e6b6268956ec)
   2. 换源一步使用清华源
        ```
        sudo add-apt-repository "deb [arch=amd64] https://mirrors.ustc.edu.cn/docker-ce/linux/debian stretch stable"
        ```
    1. 若添加源失败，就需要手动安装。
       1. 在[此页面找到对应的包](https://download.docker.com/linux/debian/dists/stretch/pool/). 
       2. 如，我的是[stabel/amd64](https://download.docker.com/linux/debian/dists/stretch/pool/stable/amd64/)
       3. 下载docker-ce-cli与docker-ce两个deb包
       4. 先安装docker-ce-cli
       5. 安装命令为`sudo dpkg -i /path/to/package.deb`
       6. 验证是否安装成功`sudo docker run hello-world`


## nvidia最新驱动的安装(docker)
1. 禁用nouveau驱动
   1. `sudo vim /etc/modprobe.d/blacklist.conf`
   2. 添加以下内容（可能有些不是必须的，我没有一个个尝试）
         ```
         blacklist nouveau
         blacklist lbm-nouveau
         blacklist vga16fb
         blacklist rivafb
         blacklist nvidiafb
         blacklist rivatv
         options nouveau modeset=0
         alias nouveau off
         alias lbm-nouveau off
         ```
   3. 应用更新`sudo update-initramfs -u`
2. 卸载之前安装的驱动`sudo apt-get --purge remove nvidia-*`
3. 重启
4. 关闭图像界面 `sudo service lightdm stop`
5. 进入命令行界面切换：`ctrl+alt+F2`
6. 登录（略）
   1. 有些系统的图像界面可能不是`lightdm`，如果这个命令失败的话，去查与自己系统图像界面对应的关闭命令。
7. 进入 驱动文件的目录， 以`NVIDIA-Linux-x86_64-430.14.run` 为例
   1. 改变权限 `sudo chmod 777 NVIDIA-Linux-x86_64-430.14.run`
   2. 执行 `sudo sh NVIDIA-Linux-x86_64-430.14.run`
   3. 注
      1. DKMS可不安装
      2. 32位的库可不安装
8. 检查是否安装成功`nvidia-smi`

## 免sudo使用docker
1. 如果还没有 docker group 就添加一个：
`sudo groupadd docker`
2. 将用户加入该 group 内。然后退出并重新登录就生效了。
`sudo gpasswd -a ${USER} docker`
3. 重启 docker 服务
`sudo service docker restart`
4. 切换当前会话到新 group 或者重启 X 会话
`newgrp - docker`