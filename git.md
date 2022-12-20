## 给远程仓库设置Personal access tokens，方便push
```
git remote set-url origin https://<your_token>@github.com/<USERNAME>/<REPO>.git
```

## 添加submodule
```
git submodule add xxx.git
```

## 拉取含submodule的完整仓库
```
git clone xxx.git --recursive
```

## 轻量级版本管理工具Gogs
启动Gogs服务器
```
cd /path/to/gogs
gogs web
```
将本地项目初始化为一个本地仓库
```
cd xxx
git init
git add .
git commit -m "first commit"
```
在[Gogs页面](http://localhost:3000/install)新建一个仓库，把仓库地址(xxx.git)复制下来，然后关联本地仓库到git仓库
```
git remote add origin xxx.git
```
把本地文件推送到远程仓库里  
```
git push -u origin master
```
