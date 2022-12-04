---
title: Scoop
date: 2022-12-02 12:00:44
tags:
  - 工具
  - 文章
categories:
---

## 安装

```powershell
# 设置环境
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
irm get.scoop.sh -outfile 'install.ps1'
.\install.ps1  -RunAsAdmin -ScoopDir 'D:\scoop\user' -ScoopGlobalDir 'D:\scoop\global' -NoProxy
# 添加镜像
scoop bucket add main https://mirror.nju.edu.cn/git/scoop-extras.git/ 
scoop bucket add extras https://mirror.nju.edu.cn/git/scoop-extras.git/ 
# 更新scoop
scoop update
```
## 使用
### 目录结构

apps——所有通过scoop安装的软件都在里面。
buckets——管理软件的仓库，用于记录哪些软件可以安装、更新等信息，默认添加main仓库，主要包含无需GUI的软件，可手动添加其他仓库或自建仓库，具体在推荐软件仓库中介绍。
cache——软件下载后安装包暂存目录。
persit——用于储存一些用户数据，不会随软件更新而替换。
shims——用于软链接应用，使应用之间不会互相干扰，实际使用过程中无用户操作不必细究。

## 参考
1. [Scoop 助力 windows 进行软件管理](https://zhuanlan.zhihu.com/p/426775599)
2. [Scoop (un)installer](https://github.com/ScoopInstaller/Install#readme)
3. [ Scoop 不完全上手指南 ](https://www.iamzs.top/archives/scoop-guidebook.html)
4. [Scoop——也许是Windows平台最好用的软件（包）管理器](https://zhuanlan.zhihu.com/p/463284082)
5. [scoop的安装及基本使用](https://www.cnblogs.com/lioa/p/13565622.html)
6. [Scoop-wiki](https://github.com/ScoopInstaller/Scoop/wiki)