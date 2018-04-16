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


#### 4. Add the desired theme as a git submodule
```
git submodule add https://github.com/digitalcraftsman/hugo-cactus-theme.git themes/hugo-cactus-theme;

```


#### 5. Copy the config file and layout struture of the theme
```
 cp -r themes/hugo-cactus-theme/layout layout/
 mv config.toml config.toml.bak && cp themes/cactus/exampleSite/config.toml .
 ```

 Inside config.toml, I had to make following changes to make the theme work
 ```
 baseurl = "/"
 themesDir = ""
 theme = "themes/cactus"
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

#### 8. Create a repo on github and push the code after commit
```
git commit -m'Initial commit'
git remote add origin git@github.com:ua741/blog.git
git push origin master
```


#### 9. Deploying the blog on Netlify [For free]

>	* Sign up on https://netlify.com
> 	* [Create a new site using github as git provider](/img/setup-01-sign-up-github.png)
> 	* [Select the hugo repo which you want to publish ](/img/setup-02-select-blog-repo.png)
>	* [Deployment Settings](/img/setup-03-build-common.png)

		1. Build command: hugo
		2. Publish Directory: public
		3. Advance Settings -> New environment variable
			Key: HUGO_VERSION
			Version: {version}  
			// use whatever hugo version you are using in development 


### 10. Using custom domain name and SSL
You can by a domain name from https://godaddy.com or https://namecheap.com and follow the instructions on Netlify for setting up a custom domain name for your blog. 
Netlify also allows you to enable SSL for free (thanks to https://letsencrypt.org/), using a single click.






