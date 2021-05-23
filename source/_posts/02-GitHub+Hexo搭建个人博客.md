---
title:  GitHub+Hexo搭建个人博客
date: 2021-01-11 23:59:53
tags:
- 搭建博客
- Hexo
---
##  GitHub+Hexo搭建个人博客

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="//music.163.com/outchain/player?type=2&id=863073353&auto=1&height=66"></iframe>

Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

这里我把个人博客托管在 GitHub Pages 上。GitHub Pages 是一种静态站点托管服务，每个 GitHub 帐户或组织都可以有一个站点。

## Github Pages上创建博客

### GitHub创建仓库

新建一个名为 用户名.github.io的仓库，比如我的GitHub用户名为`liusiyuan1111` ，那么就新建一个 `liusiyuan1111.github.io` 的仓库，这样我的网站访问地址就是 https://liusiyuan1111.github.io 。

创建成功后，打开网址，此时显示404

![image-20210111205132097](https://i.loli.net/2021/01/11/RlYJ6xDaZyp8grt.png)

### Hexo安装

安装Hexo前需要有Node.Js的环境，安装步骤省略

Node.js 安装包及源码下载地址为：https://nodejs.org/en/download/

有了nodejs的环境后，就可以安装hexo

```
npm install -g hexo
```

###  Hexo初始化

在想要的路径下新建一个文件夹，比如我的是D:\hexo ，这个文件夹内就是你的Hexo博客的源文件，在这个文件夹下右键单击鼠标，点击 Git Bash Here，依次输入以下 npm 命令即可初始化。

```
hexo init
npm install
```

输入以上命令后，hexo 会自动下载一些文件到这个目录，包括 `node_modules`，其中比较重要的几个文件的目录结构如下：

```
.
├── _config.yml
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts
└── themes
```

注意：hexo 有 2 个`_config.yml` 文件，一个是站点根目录下的`_config.yml`，一个是 theme（主题）下的`_config.yml` 文件。

博客生成、预览：

```
hexo g # 生成
hexo s # 启动服务
```

执行以上命令之后，hexo 就会在 public 文件夹生成相关 html 文件，这些就是你博客的静态文件，后续需要把这些提交到 GitHub 上。

`hexo s` 是开启本地预览服务，打开浏览器访问 `http://localhost:4000` 即可看到内容，很多人会碰到浏览器一直在转圈但是就是加载不出来的问题，一般情况下是因为端口占用的缘故。

![image-20210111215225751](https://i.loli.net/2021/01/11/di1oyQeEmbC5gRA.png)

![image-20210111215142547](https://i.loli.net/2021/01/11/GwLBhxZ1f4Jgei8.png)

按ctrl+c关闭本地服务器。

**我们以后常用到的Hexo命令：**

- hexo s等价于 hexo server #Hexo 会监视文件变动并自动更新，除修改站点配置文件外,无须重启服务器,直接刷新网页即可生效。
- hexo g 等价于 hexo generate #生成静态网页 (执行 $ hexo g后会在站点根目录下生成public文件夹, hexo会将”/blog/source/“ 下面的.md后缀的文件编译为.html后缀的文件,存放在”/blog/public/ “ 路径下)
- hexo d 等价于 hexo deploy #将本地数据部署到远端服务器(如github)
- hexo clean #清除缓存 ,网页正常情况下可以忽略此条命令,执行该指令后,会删掉站点根目录下的public文件夹

## 链接Github与本地

### 生成密钥

右键单击鼠标，点击 Git Bash Here输入以下命令：

```
git config --global user.name "Name"
git config --global user.email "Email"
```

**Name和Email是我们注册Github时的用户名和邮箱。**

然后生成密钥：

```
ssh-keygen -t rsa -C "Email"
```

**Email是我们注册Github时的邮箱**

然后会出现：

```
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/you/.ssh/id_rsa):
//到这里可以直接回车将密钥按默认文件进行存储
```

回车之后：

```
Enter passphrase (empty for no passphrase):
//这里是要你输入密码，其实不需要输什么密码，直接回车就行
Enter same passphrase again:
```

接下来会有：

```
Your identification has been saved in /c/Users/you/.ssh/id_rsa.
Your public key has been saved in /c/Users/you/.ssh/id_rsa.pub.
The key fingerprint is:
这里是各种字母数字组成的字符串，结尾是你的邮箱
The key's randomart image is:
这里也是各种字母数字符号组成的字符串
```

现在密钥已经生成，一般存放在（/c/Users/you/.ssh/id_rsa.pub.），我们运行下面的命令将密钥复制为粘贴板：

```
 clip < ~/.ssh/id_rsa.pub
```

![image-20210111212538215](https://i.loli.net/2021/01/11/FGz8qAbODEsSfti.png)

## 部署到Github

在Github头像下面点击Settings，再点击SSH and GPG keys，新建一个SSH，名字任意。

然后将刚才复制的密钥添加就可以了，像这样：

![image-20210111212701304](https://i.loli.net/2021/01/11/JZwLOSPWeG4MpCr.png)

**本地连接Github**

右键单击鼠标，点击 Git Bash Here输入以下命令，如果如下图所示，出现你的用户名，那就成功了

```
ssh -T git@github.com
//注意不要做任何修改
```

![image-20210111212935613](https://i.loli.net/2021/01/11/JYnibqIWA3ed2kx.png)

打开博客根目录下的`_config.yml`文件，这是博客的配置文件，我们需要修改一下才能连接Github。

![image-20210111213124756](https://i.loli.net/2021/01/11/Z8PokJyKAX6v9lB.png)

修改最后一行的配置：

```
# Deployment

\## Docs: https://hexo.io/docs/one-command-deployment

deploy:

 type: ''
```

改为：

```
# Deployment

\## Docs: https://hexo.io/docs/one-command-deployment

deploy:

 type: 'git'

 repository: git@github.com:liusiyuan1111/liusiyuan1111.github.io.git

 branch: master

 
```

注意：

- **repository修改为你自己的github项目地址**。
- **每一个冒号后面都有一个空格。**

直接部署一般会报如下错误：

```
Deployer not found: git
```

这是因为缺少了一个插件，我们可以通过如下命令安装：

```
npm install hexo-deployer-git --save
```

然后输入 `hexo d` 就会将本次有改动的代码全部提交。

## 写文章、发布文章

打开hexo安装目录，我的是D:\Blog\source\_posts ，可以发现里面有一个`hello-world.md`的文件，可以把自己写的md文件直接放进来

![image-20210111220734944](https://i.loli.net/2021/01/11/rgTiDvU6xfYMEqz.png)

然后hexo g生成静态网页，hexo s可以本地预览效果，最后hexo d部署到GitHub即可。