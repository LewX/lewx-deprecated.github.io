---
title: "Hugo Tutorial"
date: 2021-10-26T00:04:56+08:00
draft: true
---

## 1 安装Hugo

- 打开一个终端 Terminal，输入与操作系统对应的 Hugo 安装命令
  
  `brew install hugo`

- 安装完成后，输入以下命令来确认
  
  `hugo version`

## 2 新建网站

- 进入你想存放 Hugo 网站文件夹的目录，如
  
  `cd ~/Documents`

- 执行以下命令新建一个 Hugo 网站

  `hugo new site myblog #myblog是网站文件夹名`

- 选择主题

  打开 https://themes.gohugo.io 页面，选择一个你喜欢的主题，如*blackburn*

- 将选择的主题`clone`至本地

  ```
  #进入网站目录
  cd ~/Documents/myblog

  #创建"themes"目录
  mkdir -p themes

  #进入"themes"目录
  cd themes

  #将blackburn主题克隆至"blackburn"目录
  git clone https://github.com/yoshiharuyamashita/blackburn.git blackburn
  ```

- 编辑配置文件
  
  ```
  cd ~/Documents/myblog
  echo theme = \"blackburn\" >> config.toml
  ```

## 3 添加文章

- 使用以下命令新建一篇文章

  `hugo new post/my-first-post.md`

- 编辑新建的文章，添加一些内容，如
  
  ```
  ---
  title: "My First Post"
  date: 2019-03-26T08:47:11+01:00
  draft: true
  ---
  ```

## 4 本地预览

- 启动本地服务
  
  `hugo server -D`

- 使用浏览器打开 http://localhost:1313 预览
  
  **注意**：具体端口号以命令行提示为准

- 修改`config.toml`来个性化设置
  
  ```
  baseURL = "https://example.org/"
  languageCode = "en-us"
  title = "My New Hugo Site"
  theme = "ananke"
  ```

## 5 构建

- 预览完成后构建静态网页
  
  ```
  cd ~/Documents/myblog
  hugo -D
  ```
  **注意**：Hugo 会将构建的网站内容默认保存至网站根目录的 `public/`文件夹中

## 6 将网站文件夹转换为 Git 库

- 初始化Git仓库

  ```
  cd ~/Documents/myblog
  git init
  ```

## 7 将 Git 本地库关联至远程库

- 在`myblog/public`目录下执行
  
  `git remote add origin git@github.com:XX/XX.github.io.git`

- 查看config文件
  
  `cat .git/config`
  结果如下：
  ```
  [core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
    ignorecase = true
    precomposeunicode = true
  [remote "origin"]
    url = git@github.com:XX/XX.github.io.git
    fetch = +refs/heads/*:refs/remotes/origin/*
  ```
  如果`[remote "origin"]`信息正常显示，说明你的 Git 本地库已成功关联至远程库

## 8 提交修改至本地仓库

- 在`myblog/public`目录下，通过`commit`提交修改，并写一个`commit message`来简洁描述你的修改
  
  ```
  git status
  git add .  #添加所有修改过的文件。你也可以只添加某个文件。
  git commit -m "Add a new post"
  ```

## 9 将修改推到远程仓库

- 在`myblog/public`目录下，将修改推至远程库
  
  `git push -u origin master`