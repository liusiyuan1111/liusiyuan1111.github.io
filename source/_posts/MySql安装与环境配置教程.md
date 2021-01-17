---
title: MySql安装与环境配置教程
date: 2021-01-12 16:15:40
tags:
- 环境配置
- MySql
- 数据库
---

# MySql安装与环境配置教程

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="//music.163.com/outchain/player?type=2&id=1368756097&auto=1&height=66"></iframe>

MySQL 是最流行的关系型数据库管理系统，在 WEB 应用方面 MySQL 是最好的 RDBMS(Relational Database Management System：关系数据库管理系统)应用软件之一。

这篇博文主要是安装与配置MySql的详细步骤。

## 下载安装包

MySql有免费的版本也有收费的版本，这里选择MySql的免费版本，也就是社区版下载，链接：[MySQL :: Download MySQL Community Server (Archived Versions)](https://downloads.mysql.com/archives/community/)

点开后可以看到这个界面，Product Version选择版本，这里选择最新的8.0.21，操作系统选择windows，安装包选择第一个稳定版本。

![image-20210112162635970](https://i.loli.net/2021/01/12/m9bgoEMwDNxdK4A.png)

下载完成后，把安装包放到放在指定位置，并解压，**注意路径中不要有中文**

![image-20210112163438586](https://i.loli.net/2021/01/12/3MCTHbEqSKIF4V1.png)

## MySql安装

### 安装MySQL的服务

以管理员身份打开命令行，因为我这里是放在D盘，所以先进入D盘

![image-20210112164459773](https://i.loli.net/2021/01/12/gxiDAUmMQ1uve5P.png)

然后进入mysql的bin目录

![image-20210112164554951](https://i.loli.net/2021/01/12/PfzQ2ywYx8Spc1j.png)

然后执行安装MySQL的服务：

```
mysqld --install
```

出现Service successfully installed的提示，表示安装成功

### 初始化MySQL

使用以下代码初始化MySQL，然后会产生一个随机密码，记住这个密码，以后会遇到

```
mysqld --initialize --console
```

![微信图片编辑_20210112165801](https://i.loli.net/2021/01/12/X6lL1VGJaKWygcD.jpg)

### 开启MySQL的服务

```
net start mysql
```

![image-20210112165929472](https://i.loli.net/2021/01/12/cxd4WsnElwmGB9F.png)

### 登录验证

```
mysql -u root -p
```

![image-20210112170159522](https://i.loli.net/2021/01/12/r4wmMBPFKc5oTbX.png)

### 修改密码

```
alter user 'root'@'localhost' identified by '你的密码';
```

![image-20210112170435900](https://i.loli.net/2021/01/12/coGptdW3NlxXMzu.png)

### 再次登录验证密码

![image-20210112170713439](https://i.loli.net/2021/01/12/jqUc7yrXBzZTH9P.png)

## 设置系统变量

为了方便登录操作mysql，需要设置一个全局变量。

点击“计算机”-“属性”-“高级系统设置”-“环境变量”

![image-20210112170852791](https://i.loli.net/2021/01/12/aW6CLhfxDwsvdXS.png)



![image-20210112171441077](https://i.loli.net/2021/01/12/JHNaqKUwAjzl6eV.png)

把mysql变量添加到path路径变量中，点击确定，即可完成![image-20210112172214333](https://i.loli.net/2021/01/12/yP5jAIBSc4lEKqQ.png)

此时配置完成，当需要命令行使用mysql时，只需要打开cmd，之后输入登录sql语句即可。

![image-20210112172502950](https://i.loli.net/2021/01/12/tycT48kWSxFjNZd.png)