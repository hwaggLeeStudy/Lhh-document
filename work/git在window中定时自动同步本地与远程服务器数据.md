
git在window中定时自动同步本地与远程服务器数据
===

关注公众号"一束光阴的留恋" ，回复"全部",可以查看所有文章关键字。    
输入"`bat`、`git`、`自动化脚本工具`、`windows`"，可快速查找到本文。



---

> 提交代码是每天必不可少的工作，这里介绍自动提交的一个方向。供大家参考（本次使用windows 7 系统做的bat）

> 制作完成后感觉非常方便，最重要的还能每天刷刷gitHub的动作

# 思路
* 每天早晨定时更新下载资源到`本地`
* 每天下班定时同步到`远程`
* `windows`系统使用`bat脚本`
* 我使用的是git，所以本地`必须`有`git的环境变量`


# 脚本
```text
title GIT提交批处理——LhhDoc

echo 设置控制窗口颜色，16蓝色
color 16

@echo off

set yyyy=%date:~,4%
set mm=%date:~5,2%
set day=%date:~8,2% 
set hh=%time:~0,2%
set mi=%time:~3,2%
set ss=%time:~6,2% 
set "YYYYmmdd=%yyyy%-%mm%-%day% %hh%:%mm%:%ss%"
echo 当前时间: %YYYYmmdd% 
echo;
echo;

echo  *************************************************************
echo  *  GIT 代码提交                                             *
echo  *  Author: hwaggLee                                         *
echo  *************************************************************
echo;
echo;

echo  1.进入指定目录D:\\workspace\\mygit\\LhhDoc
echo ------------------------------------
D:
cd D:\\workspace\\mygit\\LhhDoc
echo  当前目录是：%cd%
echo ------------------------------------
echo;
echo;

echo  2.开始识别当前git的版本 git --version
echo ------------------------------------
git --version
echo ------------------------------------
echo;
echo;

echo  3.当前GIT指向信息 git config --get remote.origin.url
echo  ------------------------------------
git config --get remote.origin.url 
echo  ------------------------------------
echo;
echo;

echo  4.当前GIT的branch(分支)信息 git branch
echo ------------------------------------
git branch
echo ------------------------------------
echo;
echo;

echo  5.当前git的tag(版本)信息 git tag
echo ------------------------------------
git tag
echo ------------------------------------
echo;
echo;

echo  6.当前时间%YYYYmmdd%，将时间追加到day.txt中
echo ------------------------------------
echo %YYYYmmdd%>>day.txt
echo  追加时间到day.txt完成
echo ------------------------------------
echo;
echo;

echo  7.更新代码 git pull
echo ------------------------------------
git pull 
echo ------------------------------------
echo;
echo;

echo  8.添加变更 git add .
echo ------------------------------------
git add -A .
echo  执行结束！
echo ------------------------------------
echo;
echo;

echo  8.提交变更到本地仓库 git commit -m 
echo ------------------------------------
git commit -m "%YYYYmmdd%"
echo ------------------------------------
echo;
echo;

echo  10.将变更情况提交到远程git服务器 git push origin master
echo ------------------------------------
git push origin master
echo ------------------------------------
echo;
echo;

echo  11.查看状态 git status
echo ------------------------------------
git status
echo ------------------------------------
echo;
echo;

echo  12.查看状态 git show
echo ------------------------------------
git show
echo ------------------------------------
echo;
echo;

echo  批处理执行完毕！
echo;
echo;

pause
```
上面脚本介绍：

* 设置代码在指定指定目录（`写死`）,进入到指定目录
> D:  
> cd D:\\workspace\\mygit\\LhhDoc

* 使用`git pull`命令 下载远程代码
> git pull

* 打印下`git --version` 版本支持
> git --version

* 向版本库追加变更申请 `git add .`
> git add .

* 自动设置commit的信息`时间`
> set yyyy=%date:~,4%   
  set mm=%date:~5,2%   
  set day=%date:~8,2%    
  set hh=%time:~0,2%   
  set mi=%time:~3,2%   
  set ss=%time:~6,2%    
  set "YYYYmmdd=%yyyy%-%mm%-%day% %hh%:%mm%:%ss%"   

* 将时间写入到指定文件（`day.txt`）,`day.txt`文件不存在默认会创建
> echo %YYYYmmdd%>>day.txt

* 提交到本地仓库 `git commit -m "%YYYYmmdd%"'`
> git commit -m "%YYYYmmdd%"'

* 自动同步到远程仓库`git push origin master`
> git push origin master

* 脚本完成见下图


![img](../images/git在windows中定时自动同步到远程服务器.png)


# windows 设置自动执行事件
* 进入计算机管理(右击`计算机` - > `管理`)
![img](../images/git在windows中定时自动同步到远程服务器2.png);

* 创建任务
![img](../images/git在windows中定时自动同步到远程服务器3.png)

* 设置指定执行脚本和时间，完成任务
![img](../images/git在windows中定时自动同步到远程服务器4.png)


# 测试调整时间成果
![img](../images/git在windows中定时自动同步到远程服务器1.png)


# 完成
我本地在需要的时候就设置一个，停方便的
![img](../images/git在windows中定时自动同步到远程服务器5.png)



---
本文共学习使用，更多学习总结，扫一扫关注公众号

![img](../images/公众号.jpg)



动力源于生活，如果您觉得不错，可以支持我，感谢！
<center class="half">
    <img src="../images/收钱码-微信.png" width="200"/>
    <img src="../images/收钱码-支付宝.jpg" width="200"/>
</center>
