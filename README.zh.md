# zhonger/nav: 1.1.1

[English Version](README.md) / 中文简体

- [简介](#简介)
- [特性](#特性)
  - [开箱即用、维护至简](#开箱即用维护至简)
  - [简洁大气](#简洁大气)
  - [可扩展](#可扩展)
  - [语言](#语言)
  - [天气](#天气)
- [用法](#用法)
  - [修改作者和基础设置](#修改作者和基础设置)
  - [修改链接](#修改链接)
  - [修改搜索引擎](#修改搜索引擎)
  - [修改语言](#修改语言)
  - [修改天气的城市](#修改天气的城市)

# 简介

**Nav**是一个受 [eallion/favorite](https://github.com/eallion/favorite) 启发而开发的开源静态导航软件，主要定位于为个人提供制作和部署个性化导航网站。由于日常使用别人或者某个网站提供的个性化导航功能时，感受到了各种限制或者美中不足，所以萌生了自己开发一款更轻便、漂亮的导航网站的想法。

# 特性

### 开箱即用、维护至简

对于 **Nav**，数据库和任何动态语言运行环境都是没有必要的。你可以把它部署在任何免费的静态站点托管平台，比如说 `Github Pages`、`Netlify`、`Vercel`、`Cloudflare Pags`以及其他。

**Nav**只需要几个静态文件即可（包括`index.html`、`nav.css`、`sites.json`等等文件）。如果你想要把默认的内容修改成你自己的，你只需要非常简单地修改一下`sites.json`文件。

**Nav**不仅仅提供了你喜爱的连接，还提供了搜索引擎。因此你可以直接在搜索框内输入点什么，选择你想要的搜索引擎，然后就可以得到你想要的搜索结果。为了能够更加容易地使用搜索引擎，这里也支持使用`Enter`键来代替鼠标点击搜索按钮。是不是和你的使用习惯很相配呢？这个功能不仅仅适用于电脑端的访问，同样也适用于手机或者平板浏览器。

### 简洁大气

**Nav**并没有使用任何的 Web UI 框架，仅仅使用了第三版的 VueJS 来控制和从 `sites.json` 文件中自动生成导航内容。

一方面，为了保持所有元素的简洁大气仅采用了必要的、最简单的样式文件。

另一方面，为了使多端的呈现效果一致这里采用了媒体查询方法。

值得一提的是，[eallion/favorite](https://github.com/eallion/favorite) 提出的使用特别中文字体呈现的一句诗的特性非常简洁大气，因此这一特性得到了保留。

### 可扩展

因为本软件是基于静态文件，有人可能觉得这维护起收藏的链接和搜索引擎会比较困难。

但是，由于使用了 `VueJS` 所以我们可以很简单地通过修改 `sites.json` 文件的内容来维护链接和搜索引擎。这也意味着，你可以添加任何你知道的搜索引擎，并不限于通用的知名搜索引擎。

除此之外，**Nav** 同样采用了[eallion/favorite](https://github.com/eallion/favorite) 项目中的借助 `Google` 提供的方法直接获取任意站点 favorite 图标。只要是在公网上 `Google` 能访问到站点，都能够获取到站点 favorite 图标。

### 语言

目前支持中文和英文两种语言，默认语言是中文。

如果在 `sites.json` 文件中设置语言类型，那么将会同时被应用在天气区域和版权。

### 天气

一个由 [Qweather](https://www.qweather.com) 提供的天气插件，不过已经根据可用 API 重写代码来支持全国城市以及全球大部分城市。

为了让在 VueJS 编译完成所有天气内容前显得正常，特意增加了一个延迟加载的区域。一旦所有内容成功编译完成，延迟加载将会消失，显示出正常的天气视图。

如果城市名没有被设置或者正确设置，那么天气区域将会被一段文字提醒代替。

# 用法

### 修改作者和基础设置

以下是一个作者信息和基础设置的样例。

在这个例子中，`author`字段表示作者的名字或者别名，这个字段将会出现在导航页底部的版权内容中。

`homepage`是指导航站点的公网链接地址。比如说，如果你使用 `Github Pages` 来部署导航站点，那么默认的链接地址就是 `https://yourname.github.io/nav`。

尽管 **Nav** 采用了[今日诗词](https://www.jinrishici.com) 提供的免费一句诗 API，但是或许不是所有人想要这个功能。所以如果你想要关闭这个功能的话，你可以将 `header_auto` 字段设置为 `false`。然后 `header` 字段中的内容将会生效。你可以使用任何一句话或者词来替换这个字段。

目前已支持自定义页面标题，只需要修改基础配置中 `title` 字段即可。

```json
{
    "author": "zhonger",
  	"title": "自定义标题",
    "homepage": "https://lisz.me",
    "header": "明月几时有，把酒问青天。",
    "header_auto": true,
}
```

### 修改链接

以下是一个链接的样例。

首先，你必须为将要添加的链接预先建立好类别或者版块。这里你可以把任何内容定义为类别或者版块的名称，甚至是 emoji 表情或者其他任何你喜欢的东西。（需要注意的是， emoji 表情可能在不同平台下显示的效果有所差别。）但是这或许也会有点奇怪，因为对于类别或者版块有预先设定好的固定的图标出现在这部分内容的前面。在下一个版本中，这个情况可能会得到改善。

对于添加或修改链接，你可以非常容易地做到。你所需要做的就是准备好链接的名称、链接地址以及所属的定义好的类别或者版块。然后 `Google` 会帮助找到你设定好的链接的图标。

目前已支持版块图标的自定义修改，只需要先声明 `link_ico` 为 `true` 然后在每个版块中添加字段 `ico` 即可。这里我们建议使用 `svg` 格式的图标，因为 `svg` 图标具有大小可扩展和清晰度高的特点。如果你不知道去哪里找适合的图标，或许在 [icon-icons.com](https://icon-icons.com) 或者 [ICONPACKS](https://www.iconpacks.net) 上可以找到你想要的免费图标。

```json
{
  "link_ico": true,
  "links": [
        {
            "type": "常用网站1",
          	"ico": "images/airport-location.png",
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
          	"ico": "images/chronometer.svg",
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

### 修改搜索引擎

以下是一个搜索引擎的样例。

事实上对于不同的搜索引擎，搜索查询的链接地址或许不尽相同。而且对于一些人来说，可能也会存在以下搜索引擎需要经过鉴权后才能使用，比如说在大学里面学生和教师使用的图书馆搜索引擎。

这里所说的搜索引擎只是提供了一种方式去定义你所知的任何搜索引擎。你必须首先具有足够的访问权限才可。这不在 **Nav** 的技术考虑范围之内。

对于每一个搜索引擎而言，都必须有三个重要的字段 -- `name`、`class`和`url`。`name` 会出现在你点击搜索引擎图标并弹出全部搜索引擎的列表的时候。`class` 实际上是搜索引擎的图标。这里提供了 `Icofont` 和 `Font-Awesome` 两个字体图标库。你可以通过访问 [Icofont](https://icofont.com/icons) 和 [Font Awesome](https://fontawesome.com/v5.15/icons) 来找到你想要用的图标。或许这两个字体图标库中的图标也并不完整，而此处暂不支持自定义搜索引擎的图标，所以在下一个版本中可能会对此进行改进。最后的 `url` 是最重要的字段。如果这个字段给的不是那么准确，那么很有可能你就无法正常访问搜索引擎或无法找到你想要搜索的结果。

目前已支持搜索引擎图标的自定义修改，只需要先声明 `search_ico` 为 `true` 然后在每个搜索引擎中添加字段 `ico` 即可。这里我们建议使用 `svg` 格式的图标，因为 `svg` 图标具有大小可扩展和清晰度高的特点。如果你不知道去哪里找适合的图标，或许在 [icon-icons.com](https://icon-icons.com) 或者 [ICONPACKS](https://www.iconpacks.net) 上可以找到你想要的免费图标。

```json
{
  "search_ico": true,
  "search_engines": [
        {
            "name": "Google 搜索",
            "class": "fa fa-google",
          	"ico": "images/google.svg",
            "url": "https://www.google.co.jp/search?q="
        },
        {
            "name": "必应搜索",
            "class": "icofont icofont-brand-bing",
          	"ico": "images/bing.svg",
            "url": "https://bing.com/search?q="
        }
    ]
}
```

### 修改语言

以下是一个语言的样例。

由于语言的设置将会同时应用于页面主要内容和天气区域，我们需要将语言设置为 `zh` （中文）或者 `en` （英文）。凡是其他不规则语言设置均将被视为英文。

```json
{
  "lang": "zh"
}
```

### 修改天气的城市

以下是一个天气的样例。

如下所示，我们在使用该插件之前必须先向 [Qweather](https://www.qweather.com) 申请两个 API 秘钥。第一个秘钥 `qweather_key` 是 web 插件 API 秘钥 （s6 版本，将会在2022年12月之后不再支持）。另一个秘钥 `qweather_key2` 是 web 应用 API 秘钥 （v7 版本，也是 Qweather 提供的最新版本的 API，但是对于普通用户在获取天气质量方面有所限制）。

```json
{
  "qweather_key": "xxxxxxxxxx",
  "qweather_key2": "sxwewewewew",
  "city_name": "Shanghai"
}
```

