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
4. 提交本地修改到远程仓库`git push -u origin master`