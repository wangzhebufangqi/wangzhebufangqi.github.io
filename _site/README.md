# 开始

## 安装

安装参考[在Windows上安装Jekyll](https://www.jianshu.com/p/58e2c5ea3103)

windows下安装jekyll发生错误：

`Error installing jekyll:	ERROR: Failed to build gem native extension.`

```bash
gem install jekyll
Temporarily enhancing PATH for MSYS/MINGW...
Building native extensions. This could take a while...
ERROR:  Error installing jekyll:
        ERROR: Failed to build gem native extension.

    current directory: D:/Program Files/Ruby27-x64/lib/ruby/gems/2.7.0/gems/http_parser.rb-0.6.0/ext/ruby_http_parser
D:/Program\ Files/Ruby27-x64/bin/ruby.exe -I D:/Program\ Files/Ruby27-x64/lib/ruby/site_ruby/2.7.0 -r ./siteconf20201115-18796-1yz90oj.rb extconf.rb
creating Makefile

current directory: D:/Program Files/Ruby27-x64/lib/ruby/gems/2.7.0/gems/http_parser.rb-0.6.0/ext/ruby_http_parser
make "DESTDIR=" clean
Makefile:269: *** 多个目标匹配。 停止。

current directory: D:/Program Files/Ruby27-x64/lib/ruby/gems/2.7.0/gems/http_parser.rb-0.6.0/ext/ruby_http_parser
make "DESTDIR="
Makefile:269: *** 多个目标匹配。 停止。

make failed, exit code 2

Gem files will remain installed in D:/Program Files/Ruby27-x64/lib/ruby/gems/2.7.0/gems/http_parser.rb-0.6.0 for inspection.
Results logged to D:/Program Files/Ruby27-x64/lib/ruby/gems/2.7.0/extensions/x64-mingw32/2.7.0/http_parser.rb-0.6.0/gem_make.out
```

经过查找[issues](https://github.com/jekyll/jekyll/issues/7000)，发现一个解决方案：

![image-20201115231958940](https://gitee.com/wangzhebufangqi/PictureBed/raw/master/image-20201115231958940.png)

我原先安装路径为`D:\Program Files\Ruby27-x64`，卸载后重新安装在`D:\Ruby27-x64`后，问题就解决了！

## 下载gem包

在执行`gem install jekyll`命令时可能会要很久，这时候可以直接在[RubyGems官网](https://rubygems.org/)下载好相关的gem包后放在相对应的目录下即可。我这里的目录是`D:\Ruby27-x64\lib\ruby\gems\2.7.0\cache`。有下列几个包：

```
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       2020/11/15     14:51         104960 addressable-2.7.0.gem
-a----       2020/11/15     14:51           7168 colorator-1.1.0.gem
-a----       2020/11/15     15:14         356864 concurrent-ruby-1.1.7.gem
-a----       2020/11/15     15:14          33280 em-websocket-0.5.2.gem
-a----       2020/11/15     22:18        6705152 eventmachine-1.2.7-x64-mingw32.gem
-a----       2020/11/15     22:30         322560 ffi-1.13.1-x64-mingw32.gem
-a----       2020/11/15     22:43           6656 forwardable-extended-2.6.0.gem
-a----       2020/11/15     22:29         177664 http_parser.rb-0.6.0.gem
-a----       2020/11/15     22:17          42496 i18n-1.8.5.gem
-a----       2020/11/15     22:48         122880 jekyll-4.1.1.gem
-a----       2020/11/15     22:30           7680 jekyll-sass-converter-2.1.0.gem
-a----       2020/11/15     22:42           6144 jekyll-watch-2.2.1.gem
-a----       2020/11/15     22:42         121344 kramdown-2.3.0.gem
-a----       2020/11/15     22:42          11776 kramdown-parser-gfm-1.1.0.gem
-a----       2020/11/15     22:43          76288 liquid-4.0.3.gem
-a----       2020/11/15     22:42          28672 listen-3.3.1.gem
-a----       2020/11/15     22:43          17920 mercenary-0.4.0.gem
-a----        2020/10/6      9:25          83968 minitest-5.13.0.gem
-a----        2020/10/6      9:25          16896 net-telnet-0.2.0.gem
-a----       2020/11/15     22:43          11776 pathutil-0.16.2.gem
-a----        2020/10/6      9:25          15872 power_assert-1.1.7.gem
-a----       2020/11/15     15:13         108032 public_suffix-4.0.6.gem
-a----        2020/10/6      9:25          87552 rake-13.0.1.gem
-a----       2020/11/15     22:35          50688 rb-fsevent-0.10.4.gem
-a----       2020/11/15     22:35          15872 rb-inotify-0.10.1.gem
-a----       2020/11/15     22:48         495104 rouge-3.25.0.gem
-a----       2020/11/15     22:48          30720 safe_yaml-1.0.5.gem
-a----       2020/11/15     22:35        1150464 sassc-2.4.0-x64-mingw32.gem
-a----       2020/11/15     22:49          13824 terminal-table-1.8.0.gem
-a----        2020/10/6      9:25         133120 test-unit-3.3.4.gem
-a----       2020/11/15     22:49          11776 unicode-display_width-1.7.0.gem
-a----        2020/10/6      9:25          28672 xmlrpc-0.3.0.gem
```

## 基本用法

```bash
$ jekyll build --source <source> --destination <destination>
# => 指定源文件夹<source>中的内容将会生成到目标文件夹<destination>中。缺省source为当前文件夹的内容，缺省destination为./_site 文件夹

$ jekyll build --watch
# => 当前文件夹中的内容将会生成到 ./_site 文件夹中，
#    查看改变，并且自动再生成。
```

Jekyll 同时也集成了一个开发用的服务器，可以使用浏览器在本地进行预览

```bash
$ jekyll serve
# => 一个开发服务器将会运行在 http://localhost:4000/
# Auto-regeneration（自动再生成文件）: 开启。使用 `--no-watch` 来关闭。

$ jekyll serve --detach
# => 功能和`jekyll serve`命令相同，但是会脱离终端在后台运行。
#    如果你想关闭服务器，可以使用`kill -9 1234`命令，"1234" 是进程号（PID）。
#    如果你找不到进程号，那么就用`ps aux | grep jekyll`命令来查看，然后关闭服务器。[更多](http://unixhelp.ed.ac.uk/shell/jobz5.html).
```

还有一些可以配置的[配置选项](http://jekyllcn.com/docs/configuration/). 很多配置选项既可以在命令行中作为标识(flags)设定，也可以在源文件根目录中的 `_config.yml` 文件中进行设定。Jekyll 会自动加载这些配置。比如你在你的 `_config.yml` 文件中添加了下面几行：

```yml
source:      _source
destination: _deploy
```

那么就等价于执行了以下两条命令：

```bash
$ jekyll build
$ jekyll build --source _source --destination _deploy
```

有关配置选项的更详细说明，请查看[配置](http://jekyllcn.com/docs/configuration/)页面.

## 目录结构

```
.
├── _config.yml
├── _drafts
|   ├── begin-with-the-crazy-ideas.textile
|   └── on-simplicity-in-technology.markdown
├── _includes
|   ├── footer.html
|   └── header.html
├── _layouts
|   ├── default.html
|   └── post.html
├── _posts
|   ├── 2007-10-29-why-every-programmer-should-play-nethack.textile
|   └── 2009-04-26-barcamp-boston-4-roundup.textile
├── _site
├── .jekyll-metadata
└── index.html
```

| 文件 / 目录                                          | 描述                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| `_config.yml`                                        | 保存[配置](http://jekyllcn.com/docs/configuration/)数据。很多配置选项都可以直接在命令行中进行设置，但是如果你把那些配置写在这儿，你就不用非要去记住那些命令了。 |
| `_drafts`                                            | drafts（草稿）是未发布的文章。这些文件的格式中都没有 `title.MARKUP` 数据。学习如何 [使用草稿](http://jekyllcn.com/docs/drafts/). |
| `_includes`                                          | 你可以加载这些包含部分到你的布局或者文章中以方便重用。可以用这个标签 `{% include file.ext %}` 来把文件 `_includes/file.ext` 包含进来。 |
| `_layouts`                                           | layouts（布局）是包裹在文章外部的模板。布局可以在 [YAML 头信息](http://jekyllcn.com/docs/frontmatter/)中根据不同文章进行选择。 这将在下一个部分进行介绍。标签 `{{ content }}` 可以将content插入页面中。 |
| `_posts`                                             | 这里放的就是你的文章了。文件格式很重要，必须要符合: `YEAR-MONTH-DAY-title.MARKUP`。 [永久链接](http://jekyllcn.com/docs/permalinks/) 可以在文章中自己定制，但是数据和标记语言都是根据文件名来确定的。 |
| `_data`                                              | 格式化好的网站数据应放在这里。jekyll 的引擎会自动加载在该目录下所有的 yaml 文件（后缀是 `.yml`, `.yaml`, `.json` 或者 `.csv` ）。这些文件可以经由 ｀site.data｀ 访问。如果有一个 `members.yml` 文件在该目录下，你就可以通过 `site.data.members` 获取该文件的内容。 |
| `_site`                                              | 一旦 Jekyll 完成转换，就会将生成的页面放在这里（默认）。最好将这个目录放进你的 `.gitignore` 文件中。 |
| `.jekyll-metadata`                                   | 该文件帮助 Jekyll 跟踪哪些文件从上次建立站点开始到现在没有被修改，哪些文件需要在下一次站点建立时重新生成。该文件不会被包含在生成的站点中。将它加入到你的 `.gitignore` 文件可能是一个好注意。 |
| `index.html` and other HTML, Markdown, Textile files | 如果这些文件中包含 [YAML 头信息](http://jekyllcn.com/docs/frontmatter/) 部分，Jekyll 就会自动将它们进行转换。当然，其他的如 `.html`, `.markdown`, `.md`, 或者 `.textile` 等在你的站点根目录下或者不是以上提到的目录中的文件也会被转换。 |
| Other Files/Folders                                  | 其他一些未被提及的目录和文件如 `css` 还有 `images` 文件夹， `favicon.ico` 等文件都将被完全拷贝到生成的 site 中。这里有一些[使用 Jekyll 的站点](http://jekyllcn.com/docs/sites/)，如果你感兴趣就来看看吧。 |

## 配置



# 博客内容

## 头信息

任何只要包含 [YAML](http://yaml.org/) 头信息的文件在 Jekyll 中都能被当做一个特殊的文件来处理。头信息必须在文件的开始部分，并且需要按照 YAML 的格式写在两行三虚线之间。下面是一个基本的例子：

```
---
layout: post
title: Blogging Like a Hacker
---
```

在这两行的三虚线之间，你可以设置预定义的变量（下面这个例子可以作为参考），甚至创建一个你自己定义的变量。这样在接下来的文件和任意模板中或者在包含这些页面或博客的模板中都可以通过使用 Liquid 标签来访问这些变量。

### 预定义的全局变量

你可以在页面或者博客的头信息里设置这些已经预定义好的全局变量。

| 变量名称    | 描述                                                         |
| ----------- | ------------------------------------------------------------ |
| `layout`    | 如果设置的话，会指定使用该模板文件。指定模板文件时候不需要文件扩展名。模板文件必须放在 `_layouts` 目录下。 |
| `permalink` | 如果你需要让你发布的博客的 URL 地址不同于默认值 `/year/month/day/title.html`，那你就设置这个变量，然后变量值就会作为最终的 URL 地址。 |
| `published` | 如果你不想在站点生成后展示某篇特定的博文，那么就设置（该博文的）该变量为 false。 |

### 自定义变量

在头信息中没有预先定义的任何变量都会在数据转换中通过 Liquid 模板被调用。例如，如果你设置一个 title 变量，然后你就可以在你的模板中使用这个 title 变量来设置页面的标题（title）：

```html
<!DOCTYPE HTML>
<html>
  <head>
    <title>{{ page.title }}</title>
  </head>
  <body>
    ...
```

### 在文章中预定义的变量

在文章中可以使用这些在头信息变量列表中未包含的变量：

| 变量名称                     | 描述                                                         |
| ---------------------------- | ------------------------------------------------------------ |
| `date`                       | 这里的日期会覆盖文章名字中的日期。这样就可以用来保障文章排序的正确。日期的具体格式为`YYYY-MM-DD HH:MM:SS +/-TTTT`；时，分，秒和时区都是可选的。 |
| `category`<br />`categories` | 除过将博客文章放在某个文件夹下面外，你还可以指定博客的一个或者多个分类属性。这样当你的站点生成后，这些文章就可以根据这些分类来阅读。`categories` 可以通过 [YAML list](http://en.wikipedia.org/wiki/YAML#Lists)，或者以逗号隔开的字符串指定。 |
| `tags`                       | 类似分类 `categories`，一篇文章也可以给它增加一个或者多个标签。同样，`tags` 可以通过 YAML 列表或者以逗号隔开的字符串指定。 |

如果不想重复设置常用的头信息变量，只需在配置文件中为它们定义[默认值](http://jekyllcn.com/docs/configuration/#front-matter-defaults)，仅在必要的时候（或者从不）覆盖它们即可。这种方式对预定义变量和自定义变量都有效。

## 撰写博客

### 文章文件夹

所有的文章都在 `_posts` 文件夹中。这些文件可以用 [Markdown](http://daringfireball.net/projects/markdown/) 编写，也可以用 [Textile](http://textile.sitemonks.com/) 格式编写。只要文件中有 [YAML 头信息](http://jekyllcn.com/docs/frontmatter/)，它们就会从源格式转化成 HTML 页面，从而成为你的静态网站的一部分。

发表一篇新文章，你所需要做的就是在 `_posts` 文件夹中创建一个新的文件。文件名的命名非常重要。Jekyll 要求一篇文章的文件名遵循下面的格式：

```
年-月-日-标题.MARKUP
```

在这里，`年`是 4 位数字，`月`和`日`都是 2 位数字。`MARKUP`扩展名代表了这篇文章是用什么格式写的。下面是一些合法的文件名的例子：

```
2011-12-31-new-years-eve-is-awesome.md
2012-09-12-how-to-write-a-blog.textile
```

### 引用图片和其它资源

由于 Jekyll 的灵活性，有很多方式可以解决这个问题。一种常用做法是在工程的根目录下创建一个文件夹，命名为　`assets` 或者 `downloads`，将图片文件，下载文件或者其它的资源放到这个文件夹下。然后在任何一篇文章中，它们都可以用站点的根目录来进行引用。这和你站点的域名/二级域名和目录的设置相关，下面有一些例子（Markdown 格式）来演示怎样利用 `site.url` 变量来解决这个问题。

在文章中引用一个图片

```
… 从下面的截图可以看到：
![有帮助的截图]({{ site.url }}/assets/screenshot.jpg)
```

链接一个读者可下载的 PDF 文件：

```
… 你可以直接 [下载 PDF]({{ site.url }}/assets/mydoc.pdf).
```

> 如果你**确信**你的站点只在域名的根 URL 下做展示，你可以不使用 `{{ site.url }}` 变量。在这种情况下，直接使用 `/path/file.jpg` 即可。

## 创建页面

### 主页

像任何网站的配置一样，需要按约定在站点的根目录下找到 `index.html` 文件，这个文件将被做为主页显示出来。除非你的站点设置了其它的文件作为默认文件，这个文件就将是你的 Jekyll 生成站点的主页。

> 站点上任何 HTML 文件，包括主页，都可以使用 layout 和 include 中的内容作为公用的内容，如页面的 header 和 footer. 将合适的部分抽出放到布局中。

### 其它的页面的位置

将 HTML 文件或者 [Markdown](https://daringfireball.net/projects/markdown/) 放在哪里取决于你想让它们如何工作。有两种方式可以创建页面：

- 将为页面准备的命名好的 HTML 文件或者 [Markdown](https://daringfireball.net/projects/markdown/) 文件放在站点的根目录下。
- 在站点的根目录下为每一个页面创建一个文件夹，并把 index.html 文件或者 index.md 放在每个文件夹里。

这两种方法都可以工作（并且可以混合使用），它们唯一的区别就是访问的 URL 样式不同。

#### 命名 HTML 文件

增加一个新页面的最简单方法就是把给 HTML 文件起一个适当的名字并放在根目录下。一般来说，一个站点下通常会有：主页 (homepage), 关于 (about), 和一个联系 (contact) 页。根目录下的文件结构和对应生成的 URL 会是下面的样子：

```
.
|-- _config.yml
|-- _includes/
|-- _layouts/
|-- _posts/
|-- _site/
|-- about.html    # => http://example.com/about.html
|-- index.html    # => http://example.com/
|-- other.md      # => http://example.com/other.html
└── contact.html  # => http://example.com/contact.html
```

#### 命名一个文件夹并包含一个 index.html 文件

上面的方法可以很好的工作，但是有些人不喜欢在 URL 中显示文件的扩展名。用 Jekyll 达到这种效果，你只需要为每个顶级页面创建一个文件夹，并包含一个 `index.html` 文件。这样，每个 URL 就将以文件夹的名字作为结尾，网站服务器会将对应的 `index.html` 展示给用户。下面是一个示例来展示这种结构的样子：

```
.
├── _config.yml
├── _includes/
├── _layouts/
├── _posts/
├── _site/
├── about/
|   └── index.html  # => http://example.com/about/
├── contact/
|   └── index.html  # => http://example.com/contact/
|── other/
|   └── index.md    # => http://example.com/other/
└── index.html      # => http://example.com/
```

这种方式可能不适合每个人，对那些喜欢干净 URL 的人这是一种简单有效的方法。最终选择哪种方法完全由你来决定！

> 干净的 URLs 也可以通过在头信息中定义　`permalink`　实现。就上边的第一个例子而言，在 other.md 文件的头信息中定义：`permalink: /other`，你就能得到 URL `http://example.com/other`

## 静态文件

除了用于渲染和转换的内容之外，我们还可以使用**静态文件**。

静态文件不包含任何 YAML 头信息，譬如图片、PDF 和其他不必渲染的内容。

它们在 Liquid 中可以通过 `site.static_files` 访问，还包括以下元数据：

| 变量                 | 描述                                                     |
| -------------------- | -------------------------------------------------------- |
| `file.path`          | 文件的相对路径，如：`/assets/img/image.jpg`              |
| `file.modified_time` | 文件的最后修改时间，如：`2016-04-01 16:35:26 +0200`      |
| `file.name`          | 文件名称（带扩展名），如：文件`image.jpg`对应`image.jpg` |
| `file.basename`      | 文件名称（不带扩展名） 如：文件`image.jpg`对应`image`    |
| `file.extname`       | 文件的扩展名，如 `image.jpg` 中的 `.jpg`                 |







# 参考

[博客搭建详细教程](https://github.com/qiubaiying/qiubaiying.github.io/wiki/%E5%8D%9A%E5%AE%A2%E6%90%AD%E5%BB%BA%E8%AF%A6%E7%BB%86%E6%95%99%E7%A8%8B)



[jekyll官网](https://jekyllrb.com/)

[jekyll官网中文翻译版](http://jekyllcn.com/)