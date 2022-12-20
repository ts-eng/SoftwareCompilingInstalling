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
