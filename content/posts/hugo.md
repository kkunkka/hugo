+++
date = '2025-11-12T20:29:01+08:00'
title = 'Hugo的安装与部署'
+++

## 1.安装

```
hugo new site kkunkka

cd kkunkka

git init

git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/parperMod

echo "theme = 'parperMod'" >> hugo.toml

hugo new content content/posts/hugo.md

hugo server
```

## 2.部署

```
hugo 
```

将 public 目录下的文件复制到服务器上，通过nginx访问