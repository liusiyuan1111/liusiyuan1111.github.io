---
title: 使用git多分支管理博客
date: 2021-01-17 18:25:38
tags:
- 搭建博客
- GitHub
- Hexo
---

最近使用GitHub page+Hexo搭建了一个独立博客，有一个小问题，现在只能在自己这台电脑上写博客，换一台电脑就无法使用了，所以在网上找了一下教程，最后决定通过git分支来进行多终端工作，具体教程如下：

## 机制

首先需要明白的是，通过hexo d上传部署到GitHub的其实是hexo编译之后的文件，用来生成网页的，并不包含源文件

![image-20210117172156337](https://i.loli.net/2021/01/17/XVlwK8WrsH3oCcE.png)

只有本地目录下自动生成的.deploy_git文件夹会被上传到GitHub，而其他的配置文件，主题文件和写在post的博客都是没有上传到GitHub的

![image-20210117172503099](https://i.loli.net/2021/01/17/2NPHxu9wvnpr7IV.png)

![image-20210117172324582](https://i.loli.net/2021/01/17/71RDuQgTSVapNjM.png)

知道了这个机制，我们就可以利用git的分支管理，把源文件上传到GitHub的另一个分支即可。

## 上传分支

1. 首先在仓库下新建一个hexo分支

![image-20210117173409933](https://i.loli.net/2021/01/17/n6hZ3zg4tY7QsIx.png)

2. 在setting里更改hexo为默认分支

![image-20210117173443554](https://i.loli.net/2021/01/17/lnQr34VD5iUYufw.png)

3. 在本地目录打开git bash，将仓库clone到本地，此时默认分支是hexo，所以clone时只clone了hexo。在本地目录打开clone下来的文件夹，把除了.git文件夹以外的所有文件全部删除。

   ![image-20210117174348551](https://i.loli.net/2021/01/17/emEt35SnNvouF2X.png)

4. 然后把博客源文件全部复制过来，除了.deploy_git。

   注意1：复制过来的源文件应该有一个.gitignore，用来忽略一些不需要的文件，如果没有的话可以自己新建一个，写入以下的内容：

   ```text
   .DS_Store
   Thumbs.db
   db.json
   *.log
   node_modules/
   public/
   .deploy*/
   ```

   注意2：theme主题文件夹中的.git文件夹也要删掉，所以需要显示隐藏文件，检查一下有没有，否则上传的时候会出错

5. 提交commit，然后push，打开GitHub看一下是否已经正确上传，此时hexo分支下是这些源文件了。

![image-20210117175409885](https://i.loli.net/2021/01/17/ZopbY8mNtWkhRBP.png)

## 更换电脑操作

此时和之前的环境搭建差不多

1. 在新的电脑上安装git，然后设置全局邮箱和用户名，设置ssh key，详细步骤见之前的博文

   [GitHub+Hexo搭建个人博客 (liusiyuan.site)](https://liusiyuan.site/2021/01/11/GitHub+Hexo搭建个人博客/)

2. 安装node.js和hexo，但是注意，此时不用hexo init

3. 直接在任意目录下git clone即可

4. 进入到clone的文件夹中，执行

   ```text
   npm install
   npm install hexo-deployer-git --save
   ```

5. 然后生成，部署

   ```text
   hexo g
   hexo d
   ```

6. 然后就可以写博客了

   ```
   hexo new newpage
   ```

   

7. 注意，最好每次写完可以同步上传到GitHub上