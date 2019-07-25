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


## docker保存修改后的容器
1. `sudo docker commit -m "Configuration environment" -a "nathaniel" 0b2616b0e5a8 `
2. -m 来指定提交的说明信息，跟我们使用的版本控制工具一样；-a 可以指定更新的用户信息；之后是用来创建镜像的容器的 ID；最后指定目标镜像的仓库名和 tag 信息。创建成功后会返回这个镜像的 ID 信息。

## 一些命令
1. 删除镜像
   1. `docker rmi <image id>`
   2.想要删除untagged images，也就是那些id为<None>的image的话可以用 `docker rmi $(docker images | grep "^<none>" | awk "{print $3}")`
   3. 

