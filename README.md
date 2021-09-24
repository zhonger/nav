# zhonger/nav:1.0.0

English Version / [中文简体](README.zh.md)

- [Introduction](#introduction)
- [Features](#features)
  - [Easy to use and mange](#easy-to-use-and-mange)
  - [Simple and beautiful](#simple-and-beautiful)
  - [Scaleable](#scaleable)

- [Usages](#usages)
  - [Change the owner and basis settings](#change-the-owner-and-basis-settings)
  - [Change the links](#change-the-links)
  - [Change the search engines](#search-the-search-engines)

# Introduction

**Nav** is an open source static navigatioin software, which is inspired by [eallion/favorite](https://github.com/eallion/favorite). It aims to make and host a personal navigation website by yourself. Because of some limitation when using the navigation provided by someone or some websites, it's very boring and limited for me. I need a more simple and beautiful navigation website. So **Nav** came.

# Features

### Easy to use and mange

There is no need for any databases or runtime environment. You can deploy it to any free static hosting platforms, such as `Github Pages`, `Netlify`, `Vercel`, `Cloudflare Pages` and so on.

**Nav** is just mainly based on several static files -- `index.html`, `nav.css`, `sites.json` and others. If you want to change the content to yours, it's very easy only by changing the `sites.json`.

**Nav** provides not only favorite links but also search engines for you. So you can just input something and select the search engines you want, and then get your needed results. In order to use the search engine easily, `Enter` key is also supported. Once you have typed your words or sentence successfully, you can search it by click the search button in the right or click the `Enter` key in the keyboard. It also works in mobile phones or tablet pad.

### Simple and beautiful

**Nav** doesn't use any Web UI framework, and only uses `VueJS@3` to control and generate the navigation content automatically from `sites.json`. 

On the one hand, the simple css file has been used in order to keep all things simple and beautiful.

On the other hand, a media query method has been defined in the css file to make the similar performance for mobile phone or tablet pad.

It's worthy to be noticed that the idea of one poem with special chinese font proposed by [eallion/favorite](https://github.com/eallion/favorite) is very good and beautiful. So it has been kept.

### Scaleable

Because it's based on static files, someone maybe think that it's a little difficult to manage the links or search engines. 

However, thanks to `VueJS` we can mange the links or search engines very easily by chaning the content in `sites.json`. It means that you can set any search engines you know.

Except this, **Nav** followed the website icon method in [eallion/favorite](https://github.com/eallion/favorite), which works with the help of `Google`. It supports  any public websites which can be accessed by `Google`.

# Usages

### Change the owner and basis settings

Here is a sample for the owner and basis settings. 

In this sample, `author` means your name or nickname, which will appear in the copyright of the page. 

`homepage` means the url of your site. For example, if you uses `Github Pages` to deploy it, your default url will be `https://yourname.github.io/nav`. 

Although **Nav** provides one chinese poem, it may be not so good for anyone. So if your want to disable this feature, you can just set `header_auto` into `false`. Then the `header` setting will be used. You can use any sentences or words you like to replace it. 

```json
{
    "author": "zhonger",
    "homepage": "https://lisz.me",
    "header": "明月几时有，把酒问青天。",
    "header_auto": true,
}
```

### Change the links

Here is a sample for links.

First of all, you have to include it in one type for each favorite link. Here you can define anything as the name of type, even just a emoji or otherthing you like. (It's noticed that emoji may be different in various platforms.) But maybe it will be some strange, because one default icon in the front of each type has been defined fixedly. An improvement about this may will appear in the next version.

It's very easy to add or change a link. What you need is just to prepare a name and url with one defined type. Then `Google` will help to find the icon for the link you set.

```json
{
  "links": [
        {
            "type": "常用网站1",
            "sites": [
                {
                    "name": "博客",
                    "url": "https://lisz.me"
                },
                {
                    "name": "谷歌学术",
                    "url": "https://scholar.google.com"
                }
            ]
        },
        {
            "type": "常用网站2",
            "sites": [
                {
                    "name": "筑波大学",
                    "url": "https://www.tsukuba.ac.jp"
                },
                {
                    "name": "NIMS",
                    "url": "https://www.nims.go.jp"
                }
            ]
        }
    ]
}
```

### Change the search engines

Here is a sample for search engines.

Actually for different search engines, the query url may be not similar. And for someone, there exist some search engines which can be only accessed by some verified people, such as the library search engine for the students and teachers in the University.

Here the search engine settings just provide a way to define any search engines you know. You have to verify your privilege by yourself. It should be not a technical problem for **Nav**. 

For each search engine, there are three important keys -- `name`, `class` and `url`. The `name` appears only when you click the search engine icon and get the list of all search engines. The `class` actually is the icon of the search engine. `Icofont` and `Font-Awesome` have beend used here. Your can find which icon you want to use by visiting [Icofont](https://icofont.com/icons) and [Font Awesome](https://fontawesome.com/v5.15/icons). Maybe it's still limited. An improvement about this may will appear in the next version. Finally, the `url` is the most important thing. If the url is not so right, you will cannot access or find your results you want.

```json
{
  "search_engines": [
        {
            "name": "Google 搜索",
            "class": "fa fa-google",
            "url": "https://www.google.co.jp/search?q="
        },
        {
            "name": "必应搜索",
            "class": "icofont icofont-brand-bing",
            "url": "https://bing.com/search?q="
        }
    ]
}
```
