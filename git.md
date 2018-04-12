# push problem
- fatal: refusing to merge unrelated histories

```
git pull origin master --allow-unrelated-histories
```



# track problem
```
git ls-files
//查看追踪的文件

git rm -r --cached . 
//清除缓存  

```



# email problem
```
git config --global user.email
//查看当前的全局用户E-mail

git config --global user.email 你的推荐E-mail
//重新设置你的全局用户E-mail

git commit --amend --reset-author
//重置上次提交的作者信息
```
