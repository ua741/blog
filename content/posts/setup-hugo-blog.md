---
title: "Steps to set up a hugo blog"
date: 2018-04-16T11:41:03+05:30
draft: false
tags: [
    "development"
]
---


In the very first post, I am just going to document the steps which I followed to set up this personal blog. 



##### 1. Install hugo
```
brew install hugo
```
##### 2. Create a new hugo site/project
```
hugo new site blog
```
##### 3. Initialize git for source control
```
cd blog
git init
```


#### 4. Add the themse as a git submodule
```
git submodule add https://github.com/digitalcraftsman/hugo-cactus-theme.git themes/hugo-cactus-theme;
```


#### 5. Copy the config file and layout struture of the theme
```
 cp -r themes/hugo-cactus-theme/layout layout/
 mv config.toml config.toml.bak && cp themes/cactus/exampleSite/config.toml .
 ```

#### 6. Create a new post
```
hugo new post/setupblog.md
```


#### 7. Start the hugo server 
With -D flag if you want to see draft posts.

```
hugo server -D
```

