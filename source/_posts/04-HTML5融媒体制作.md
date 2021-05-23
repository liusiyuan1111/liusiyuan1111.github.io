---
title: HTML5融媒体制作竞赛团队操作教程
date: 2021-01-13 14:20:19
tags:
- HTML5
- 融媒体
- web
- 前端
- GitHub
---

# HTML5融媒体制作竞赛团队操作教程

这是一个用于广东工贸职业技术学院的软件工程系参加HTML5融媒体内容制作职业技能大赛的教程资料，主要是关于如何使用GitHub管理项目，托管代码。

团队仓库：[liusiyuan1111/HTML5 (github.com)](https://github.com/liusiyuan1111/HTML5)

该仓库主要用于存放学习资料，和同学的项目代码。

## 创建一个GitHub账号

1. 创建账号，此步骤省略

2. 下载一个GitHub桌面客户端，下载链接[GitHub Desktop | Simple collaboration from your desktop](https://desktop.github.com/)

## clone仓库到本地

1. fork到自己的仓库

   ![image-20210114175326921](https://i.loli.net/2021/01/14/moCZsLJ1MIPacKG.png)

2. fork之后可以在自己的Repositories中看到这个仓库

3. 在GitHub桌面版登录自己的账号，然后选择`Clone a repository from the Internet`,把fork的HTML5仓库clone到本地

4. clone时选择第一个`To contribute to the parent project`,这样就可以pull requests到团队的仓库

   ![image-20210114180309546](https://i.loli.net/2021/01/14/RkTFEKSMGAHgcPL.png)

5. clone之后可以在本地看到整个仓库的文件夹

   ![image-20210114180705376](https://i.loli.net/2021/01/14/xQIpodYi1L8B2Rm.png)

6. 在学生项目文件夹内，以自己的名字创建一个文件夹，然后在该文件夹内创建两个文件夹，一个是学习，用于存放平时练习的代码；另一个是项目，用来存放练习竞赛的项目代码。

   ![image-20210114180834949](https://i.loli.net/2021/01/14/AuSfkMHitajzvNq.png)

7. 创建好文件夹后，在两个文件夹内分别放入两个文档，一个用于记录学习的情况，一个用于记录项目的情况，可以使用txt格式或者doc格式，建议使用markdown格式（空文件夹无法提交到仓库，所以需要在两个文件夹里分别创建这两个文档，文档里可以不用写任何东西，之后我会告诉大家怎么写文档）

   ![image-20210114181217448](https://i.loli.net/2021/01/14/EhMUVwcxz16oCup.png)

   ![image-20210114181234619](https://i.loli.net/2021/01/14/Xyz82bPfnckriYF.png)

8. 把自己写的代码分别放入这两个文件夹，然后打开GitHub桌面版，可以在Changes里看到你所做的改动，“+号”（绿色）表示你新增的内容，“-号”（红色）表示你删除的内容

   

   ![image-20210114181753268](https://i.loli.net/2021/01/14/O9Uc6BLWps3tjyv.png)

9. 在Summary里（必填）可以填入自己的姓名和提交时间，在Description里可以填写此次提交的简要说明（比如：完成了项目1），然后点击`commit to main`

   ![image-20210114181828830](https://i.loli.net/2021/01/14/1os7vka8wpHPbih.png)

10. 然后把写好的代码，提交到原始仓库

    ![image-20210114181939936](https://i.loli.net/2021/01/14/UnfkYL9XmzHBclo.png)

11. 提交之后可以在自己的仓库看到提交的内容，但是原始仓库需要我同意合并才能看到。

    ![image-20210114182104304](https://i.loli.net/2021/01/14/J8yMPUY64tR7jnb.png)

12. 注意，把仓库clone到本地之后，只在自己创建的文件夹内操作，不要随意删除其他的内容

13. 大家先按照这个流程练习一次，自己创建文件夹和空白文档。参赛同学必须完成，其他同学随意。

## 与源仓库同步

现在大家都已经在仓库里创建了自己的文件夹，但是大家fork的时间不同，clone的仓库也是不同时间点的仓库，如何保持自己的仓库和源仓库保持一致呢。在这里给大家介绍一种比较简单的，无需命令行的教程，方便大家操作。

简单来说与源仓库保持同步就是反向的pull request，通过对比你现在的仓库和源仓库来实现更新与同步。

操作步骤如下

1. 在Branch里选择`create pull request`![image-20210118192712571](https://i.loli.net/2021/01/18/HjrXZI7ABGDbuPL.png)

2. 会跳到网页版，查看交叉对比你的仓库和源仓库发生的变化。在这里调换顺序，左边选择你的仓库，右边选择源仓库

   ![image-20210118192845940](https://i.loli.net/2021/01/18/8WecKGuQxOjZdvM.png)

3. 更换顺序之后，就会出现上次fork之后，源仓库发生的所有变化，在这里点击`create pull request`

   ![image-20210118193025291](https://i.loli.net/2021/01/18/g6ex42kmAWh38qD.png)

4. 填写必要的信息，然后继续`create pull request`![image-20210118193142529](C:/Users/lsy/AppData/Roaming/Typora/typora-user-images/image-20210118193142529.png)

5. 在新的页面，`merge pull request`合并这些发生更改的请求即可![image-20210118193316198](https://i.loli.net/2021/01/18/7IqOPrtiJ641CNE.png)

6. `confirm merge` 确认合并

   ![image-20210118193356274](https://i.loli.net/2021/01/18/k8Jdqz7bTMBDvio.png)

7. 此时你的仓库里就有了上次fork以后，源仓库更新的内容

8. 回到GitHub桌面版，`fetch origin` 更新

   ![image-20210118193458922](https://i.loli.net/2021/01/18/TQPBE1pfS3OjW27.png)

9. 可以看到相比之前有了17个commit的改变，pull origin 下载这些请求即可

   ![image-20210118193647902](https://i.loli.net/2021/01/18/Ma34Q7bjLzOTkWh.png)

10. 之后每次更新就不用这么麻烦了，只要在Branch里选择 `merge into current branch`

    ![image-20210118194043521](https://i.loli.net/2021/01/18/wA4m8kRM3jgU2VW.png)

11. 选择下面这个分支，然后merge合并

    ![image-20210118194150229](https://i.loli.net/2021/01/18/E1G5kJYxLQt2jlR.png)

12. 最后push更新到你的仓库即完成了更新

    ![image-20210118194255291](https://i.loli.net/2021/01/18/5NTspa7dF3eQYnB.png)

13. 第一次更新需要完成1-9步。之后的每次更新只要完成10-12步即可。

14. 除了上述使用GitHub反向pull request来完成与源仓库的同步更新以外，还可以通过git来实现，这里就不详细介绍了，有兴趣了解git的同学可以去学习一下，可以参考以下教程：

    [fork分支与源分支同步代码_lewis-CSDN博客](https://lewis.blog.csdn.net/article/details/64440602?utm_medium=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.control&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.control)

    [github使用 - 简书 (jianshu.com)](https://www.jianshu.com/p/79454cf00945)

