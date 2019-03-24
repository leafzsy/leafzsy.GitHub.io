---
layout: post
title:  "ubuntu bash"
date:   2018-12-29 22:18
comments: true
tag: 
- ubuntu
- notes
---

## blog biulding
```bash
bundle exec jekyll serve 
```

## git
```bash
git add -A .
git add -u
git commit -m "new"
git push origin master
```
## 常用
```bash
cd {directory}  #转换当前目录
ls -lha  #列出目录文件（详细信息）
vim or nano  #命令行编辑器
touch {file}  #创建一个新的空文件
cp -R {original_name} {new_name}  #复制一个文件或目录（包含内部所有文件）
mv {original_name} {new_name}  #移动或重命名文件
rm {file}  #删除文件
rm -rf {file/folder}  #永久删除文件或文件夹（小心使用）
pwb  #打印当前工作目录
cat or less or tail or head -n10 {file}  #文件的标准输出内容
mkdir {directory}  #创建一个空的目录
grep -inr {string}  #在当前目录或子目录的文件中搜索一个字符串
column -s, -t <delimited_file>  #在 columnar 格式中展示逗号分隔文件
ssh {username}@{hostname}  #连接到远程机器中
tree -LhaC 3  #向下展示三级目录结构（带有文件大小信息和隐藏目录信息）
htop (or top)  #任务管理器
pip install --user {pip_package}  #Python 安装包管理器，安装包到~/.local/bin 目录下
pushd . ; popd ; dirs; cd -  #在堆栈上 push/pop/view 一个目录，并变回最后一个目录
sed -i "s/{find}/{replace}/g" {file}  #替代文件中的一个字符串
find . -type f -name '*.txt' -exec sed -i "s/{find}/{replace}/g" {} \;  #替换当前目录和子目录下后缀名为.txt 文件的一个字符串
tmux new -s session, tmux attach -t session  #创建另一个终端会话界面而不创建新的窗口 [高级命令]
wget {link}  #下载一个网页或网页资源
curl -X POST -d "{key: value}" http://www.google.com  #发送一个 HTTP 请求到网站服务器
find <directory>  #递归地列出所有目录和其子目录的内容
```
