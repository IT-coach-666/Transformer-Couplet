# 1、git提交代码到 github
从 github 中下载代码，并将本地代码放置到下载下来的相应目录中，随后进入 repositories 执行如下：
```shell
# 以下如没有提示、非必须：
git config --global user.email "929277335@qq.com"
git config --global user.name "JiaYueHuang"


git add --all                    # 更新所有文件（注意是两个“-”）
git add /path/to/file      # 只更新一个文件

git commit -m "first commit"
git push -u origin main  [-f]   # 其中，黄色标注根据实际情况填写，可能是“master”，可通过“git branch”查看；根据提示，输入账号密码：92**35@qq.com + hj***3）
```


