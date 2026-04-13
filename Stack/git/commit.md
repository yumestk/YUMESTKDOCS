# git提交命令
## 首次提交
- 初始化git仓库
        git init

- 添加所有(单个)文件
git add .
git add 文件名
- 推单个文件夹
git add /src  

- 提交
git commit -m "first commit"  

- 关联你的GitHub仓库（把链接换成你自己的）
git remote add origin https://github.com/yumestk/yourRepositoryname.git

- 推送到main分支
git push -u origin main
---
## 以后提交
- 添加所有文件
git add .

- 添加至缓存区
git commit -m "这里写你这次改了什么"

- 推送远程仓库  
git push


