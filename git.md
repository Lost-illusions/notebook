# linxu下git使用指南

## git安装
`sudo apt-get install git`

## 本地git与github关联
1. [见此](https://www.cnblogs.com/woider/p/6533709.html)
2. 其中 `id_rsa.pub `文件，在我的电脑上是在`/home/nathaniel`目录下（即主目录）的

## git的一些操作
1. `git add <文件名>`
2. `git commit -m "文字说明“`
3. 关联远程仓库 `git remote add origin git@github.com:Lost-illusions/notebook.git`
4. （第一次提交时使用）提交本地修改到远程仓库`git push -u origin master`
   1. 此后，提交`git push`即可
5. 重新提交最近一次`commit`操作
   1. `git commit --amend -m  "说明"`

## 一些问题
1. git无法显示中文
   `git config --global core.quotepath false`

2. 解除单次100M的限制
   1. 安装git-lfs
      1. `curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.deb.sh | sudo bash`
      2. `sudo apt-get install git-lfs`
      3. `git lfs install`
   2. 追踪大文件**注意文件名要相对路径**
      1. `git lfs track <文件名>`
      2. `git add <文件名>`
      3. `git comiit -m " "`
      4. `git push`
