# docker的使用

## 安装docker
   1. [见此](https://www.cnblogs.com/huangaojiao/p/9159772.html)
   2. 换源一步使用清华源
        ```
        sudo add-apt-repository "deb [arch=amd64] https://mirrors.ustc.edu.cn/docker-ce/linux/ubuntu bionic stable"
        ```
    1. 若添加源失败，就需要手动安装。（**此为depain系列的安装步骤，ubuntu只要把下载的包换一下即可**)
       1. 在[此页面找到对应的包](https://download.docker.com/linux/debian/dists/stretch/pool/). 
       2. 如，我的是[stabel/amd64](https://download.docker.com/linux/debian/dists/stretch/pool/stable/amd64/)
       3. 下载docker-ce-cli与docker-ce两个deb包
       4. 先安装docker-ce-cli
       5. 安装命令为`sudo dpkg -i /path/to/package.deb`
       6. 验证是否安装成功`sudo docker run hello-world`

## 免sudo使用docker
1. 如果还没有 docker group 就添加一个：
`sudo groupadd docker`
2. 将用户加入该 group 内。然后退出并重新登录就生效了。
`sudo gpasswd -a ${USER} docker`
3. 重启 docker 服务
`sudo service docker restart`
4. 切换当前会话到新 group 或者重启 X 会话
`newgrp - docker`