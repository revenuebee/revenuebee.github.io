---
title: 撰写新文章
description: 本文将指导您如何在 Chirpy 中撰写文章
authors: [cotes, revenuebee]
date: 2025-01-28 16:00:00 +0800
categories: [博客, 教程]
tags: [写作]
render_with_liquid: false
---

本教程将指导您如何在 _Chirpy_ 模板中撰写文章，即使您以前使用过 Jekyll，也值得阅读，因为许多功能需要设置特定变量。

## 命名和路径

创建一个名为 `YYYY-MM-DD-TITLE.EXTENSION`{: .filepath} 的新文件，并将其放入根目录的 `_posts`{: .filepath} 中。请注意，`EXTENSION`{: .filepath} 必须是 `md`{: .filepath} 或 `markdown`{: .filepath} 之一。 如果您想节省创建文件的时间，请考虑使用 [`Jekyll-Compose`](https://github.com/jekyll/jekyll-compose) 插件来实现这一点。

## Front Matter

基本上，您需要在文章顶部填写如下的 [Front Matter](https://jekyllrb.com/docs/front-matter/) ：

```yaml
---
title: TITLE
date: YYYY-MM-DD HH:MM:SS +/-TTTT
categories: [TOP_CATEGORIE, SUB_CATEGORIE]
tags: [TAG]     # TAG 名称应始终为小写
---
```

> 文章的布局已默认设置为 `post`，因此不需要在Front Matter中添加变量 _layout_ 。
{: .prompt-tip }

### 日期和时区

为了准确记录文章的发布日期，您不仅应该设置 `_config.yml`{: .filepath} 的 `timezone`，还需要在其前置信息块的 `date` 变量中提供文章的时区。格式： `+/-TTTT`，例如 `+0800`。

### 分类和标签

每篇文章的 `categories` 设计为包含最多两个元素，而 `tags` 的元素数量可以是零到无穷多个。例如：

```yaml
---
categories: [Animal, Insect]
tags: [bee]
---
```

### 作者信息

文章的作者信息通常不需要在 _Front Matter_ 中填写，默认情况下， 它们将从配置文件的 `social.name` 和 `social.links` 的第一个条目中获取。 但您也可以通过以下方式覆盖此设置：

在 `_data/authors.yml` 中添加作者信息（如果您的网站没有此文件，不妨创建一个）。

```yaml
<author_id>:
  name: <full name>
  twitter: <twitter_of_author>
  url: <homepage_of_author>
```
{: file="_data/authors.yml" }

然后使用 `author` 来指定单个作者，或使用 `authors` 来指定多个作者：

```yaml
---
author: <author_id>                     # 表示单个作者
# 或
authors: [<author1_id>, <author2_id>]   # 表示多个作者
---
```

话虽如此，键 `author` 也可以标识多个作者。

> 从文件 `_data/authors.yml`{: .filepath } 读取作者信息的好处在于，该页面将拥有元标签 `twitter:creator`，这会丰富 [Twitter Cards](https://developer.twitter.com/en/docs/twitter-for-websites/cards/guides/getting-started#card-and-content-attribution) 对SEO有益。
{: .prompt-info }

### 文章概述

默认情况下，文章的第一句话将用于显示在文章列表的主页上、进一步阅读部分以及 RSS 源的 XML 中。 如果您不想显示自动生成的文章描述，可以在 _Front Matter_ 中使用 `description` 字段进行自定义，如下所示：

```yaml
---
description: 文章的简短摘要。
---
```

另外，`description` 文本也将显示在文章的页面标题下方。

## 目录

默认情况下，the **目录** (TOC) 显示在文章的右侧面板中。 如果您想全局关闭它，请转到 `_config.yml`{: .filepath} 并将变量 `toc` 的值设置为 `false`。如果您想为特定文章关闭目录，请在文章的 [Front Matter](https://jekyllrb.com/docs/front-matter/) 中添加以下内容：

```yaml
---
toc: false
---
```

## 评论

全局评论设置由 `_config.yml`{: .filepath} 文件中的 `comments.provider` 选项定义。一旦为该变量选择了一个评论系统，所有文章将启用评论。

如果您想关闭特定文章的评论，请在文章的 **Front Matter** 中添加以下内容：

```yaml
---
comments: false
---
```

## 媒体

在  _Chirpy_ 中，我们将图片、音频和视频称为媒体资源。

### URL 前缀

有时我们需要为文章中的多个资源定义重复的URL前缀，这是一项乏味的任务，您可以通过设置两个参数来避免。

- 如果您使用CDN来托管媒体文件，可以在 `_config.yml`{: .filepath } 中指定 `cdn`。然后网站头像和文章的媒体资源URL会以CDN域名为前缀。

  ```yaml
  cdn: https://cdn.com
  ```
  {: file='_config.yml' .nolineno }

- 要为当前文章/页面范围指定资源路径前缀，请在文章的 _front matter_ 中设置 `media_subpath`：

  ```yaml
  ---
  media_subpath: /path/to/media/
  ---
  ```
  {: .nolineno }

选项 `site.cdn`  和 `page.media_subpath` 可以单独使用，也可以组合使用，以灵活地构建最终的资源 URL：`[site.cdn/][page.media_subpath/]file.ext`

### 图像

#### 说明

在图像下一行添加斜体文字，然后它会成为说明并显示在图像底部：

```markdown
![img-description](/path/to/image)
_Image Caption_
```
{: .nolineno}

#### 尺寸

为防止在加载图像时页面内容布局发生变化，我们应该为每个图像设置宽度和高度。

```markdown
![图片描述](/assets/img/sample/mockup.png){: width="700" height="400" }
```
{: .nolineno}

> 对于 SVG，您至少需要指定其 _width_，否则它将无法渲染。
{: .prompt-info }

从 _Chirpy v5.0.0_开始， `height` 和 `width` 支持缩写 (`height` → `h`, `width` → `w`)。以下示例与上述具有相同的效果：

```markdown
![图片描述](/assets/img/sample/mockup.png){: w="700" h="400" }
```
{: .nolineno}

#### 位置

默认情况下，图像是居中的，但您可以使用 `normal`、`left` 和 `right` 之一来指定位置。

> 一旦指定了位置，就不应添加图像标题。
{: .prompt-warning }

- **正常位置**

  在以下示例中，图像将左对齐：

  ```markdown
  ![图片描述](/assets/img/sample/mockup.png){: .normal }
  ```
  {: .nolineno}

- **向左浮动**

  ```markdown
  ![图片描述](/assets/img/sample/mockup.png){: .left }
  ```
  {: .nolineno}

- **向右浮动**

  ```markdown
  ![图片描述](/assets/img/sample/mockup.png){: .right }
  ```
  {: .nolineno}

#### 暗/亮模式

您可以让图像跟随暗/亮模式的主题偏好。为此，您需要准备两张图片，一张用于暗模式，一张用于亮模式，然后为它们分配特定的类 (`dark` 或 `light`):

```markdown
![仅浅色模式](/path/to/light-mode.png){: .light }
![仅暗黑模式](/path/to/dark-mode.png){: .dark }
```

#### 阴影

程序窗口的截图可以显示阴影效果：

```markdown
![图片描述](/assets/img/sample/mockup.png){: .shadow }
```
{: .nolineno}

#### 预览图片

如果您想在文章顶部添加一张图片，请提供分辨率为 `1200 x 630`的图片。请注意，如果图片的宽高比不符合 `1.91 : 1`，则图片会被缩放和裁剪。

了解这些先决条件后，您可以开始设置图片的属性：

```yaml
---
image:
  path: /path/to/image
  alt: 图片替代文本
---
```

请注意，[`media_subpath`](#url-prefix) 也可以传递给预览图片，即当它已经设置时，属性 `path` 只需要图片文件名即可。

对于简单使用，您也可以仅使用 `image` 来定义路径。

```yml
---
image: /path/to/image
---
```

#### 低质量图像占位符 (LQIP)

对于预览图片：

```yaml
---
image:
  lqip: /path/to/lqip-file # 或 base64 URI
---
```

> 您可以在文章 \"[文字与排版](../text-and-typography/)\" 的预览图片中观察到 LQIP。

对于普通图片：

```markdown
![图片描述](/path/to/image){: lqip="/path/to/lqip-file" }
```
{: .nolineno }

### 视频

#### 社交媒体平台

您可以使用以下语法嵌入社交媒体平台的视频：

```liquid
{% include embed/{Platform}.html id='{ID}' %}
```

其中 `Platform` 是平台名称的小写形式， `ID` 是视频的编号。

下表显示了如何在给定的视频 URL 中获取我们所需的两个参数，以及当前支持的视频平台。

| 视频 URL                                                                                          | 平台   | ID             |
| -------------------------------------------------------------------------------------------------- | ---------- | :------------- |
| [https://www.**youtube**.com/watch?v=**LHOVDbuWPB8**](https://www.youtube.com/watch?v=LHOVDbuWPB8) | `youtube`  | `LHOVDbuWPB8`  |
| [https://www.**twitch**.tv/videos/**1634779211**](https://www.twitch.tv/videos/1634779211)         | `twitch`   | `1634779211`   |
| [https://www.**bilibili**.com/video/**BV1jv4UetEfb**](https://www.bilibili.com/video/BV1jv4UetEfb) | `bilibili` | `BV1jv4UetEfb` |

#### 视频文件

如果您想直接嵌入视频文件，请使用以下语法：

```liquid
{% include embed/video.html src='{URL}' %}
```

其中 `URL` 是指向视频文件的 URL，例如 `/path/to/sample/video.mp4`。

您还可以为嵌入的视频文件指定其他属性。以下是允许的属性完整列表。

- `poster='/path/to/poster.png'` — 视频下载时显示的视频海报图像
- `title='Text'` — 视频下方出现的标题，与图片相同
- `autoplay=true` — 视频一旦可以就会自动开始播放
- `loop=true` — 达到视频末尾时自动回到视频开头
- `muted=true` — 音频将最初被静音
- `types` — 指定附加视频格式的扩展名，以 | 分隔。确保这些文件与您的主视频文件位于同一目录中。

考虑一个使用上述所有属性的示例：

```liquid
{%
  include embed/video.html
  src='/path/to/video.mp4'
  types='ogg|mov'
  poster='poster.png'
  title='演示视频'
  autoplay=true
  loop=true
  muted=true
%}
```

### 音频

如果您想直接嵌入音频文件，请使用以下语法：

```liquid
{% include embed/audio.html src='{URL}' %}
```

其中 `URL` 是指向音频文件的 URL，例如 `/path/to/audio.mp3`.

您还可以为嵌入的音频文件指定其他属性。以下是允许的属性完整列表。

- `title='Text'` — 音频下方出现的标题，与图片相同
- `types` — 指定附加音频格式的扩展名，以 `|` 分隔。确保这些文件与您的主音频文件位于同一目录中。

考虑一个使用上述所有属性的示例：

```liquid
{%
  include embed/audio.html
  src='/path/to/audio.mp3'
  types='ogg|wav|aac'
  title='演示音频'
%}
```

## 置顶文章

您可以将一个或多个文章固定在主页顶部，并且置顶文章根据其发布日期按逆序排序。通过以下方式启用：

```yaml
---
pin: true
---
```

## 提示

提示有多种类型：`tip`、`info`、`warning` 和 `danger`。它们可以通过将类 `prompt-{type}` 添加到引用块来生成。例如，定义一个类型为 `info` 的提示如下：

```md
> Example line for prompt.
{: .prompt-info }
```
{: .nolineno }

## 语法

### 内联代码

```md
`inline code part`
```
{: .nolineno }

### 文件路径高亮

```md
`/path/to/a/file.extend`{: .filepath}
```
{: .nolineno }

### 代码块

Markdown symbols ```` ``` ```` can easily create a code block as follows:

````md
```
This is a plaintext code snippet.
```
````

#### 指定语言

使用 ```` ```{language} ```` 可以得到带有语法高亮的代码块：

````markdown
```yaml
key: value
```
````

> Jekyll 标签 `{% highlight %}` 与此主题不兼容。
{: .prompt-danger }

#### 行号

默认情况下，除 `plaintext`、`console` 和 `terminal` 之外的所有语言都会显示行号。当您想隐藏代码块的行号时，请为其添加 `nolineno` 类：

````markdown
```shell
echo '不再有行号！'
```
{: .nolineno }
````

#### 指定文件名

您可能已经注意到，代码语言会显示在代码块的顶部。如果您想用文件名替换它，可以通过添加 `file` 属性来实现：

````markdown
```shell
# 内容
```
{: file="path/to/file" }
````

#### Liquid 代码

如果您想展示 **Liquid** 片段，请将 Liquid 代码用 `{% raw %}` 和 `{% endraw %}`包围：

````markdown
{% raw %}
```liquid
{% if product.title contains 'Pack' %}
  This product's title contains the word Pack.
{% endif %}
```
{% endraw %}
````

或者在文章的YAML区块中添加 `render_with_liquid: false` （需要 Jekyll 4.0 或更高版本）。

## 数学公式

我们使用 [**MathJax**][mathjax] 来生成数学公式。出于网站性能原因，数学公式功能默认不会加载。但可以通过以下方式启用：

[mathjax]: https://www.mathjax.org/

```yaml
---
math: true
---
```

启用数学公式功能后，您可以使用以下语法添加数学公式：

- **Block math** 应该使用 `$$ math $$` 添加，**mandatory** 在 `$$` 之前和之后保留空行
  - **Inserting equation numbering** 应该使用 `$$\begin{equation} math \end{equation}$$` 添加
  - **Referencing equation numbering** 应该在方程块中使用 `\label{eq:label_name}` ，并在文本中内联使用 `\eqref{eq:label_name}`（见下面的示例）
- **Inline math** （以行为单位） 应该使用 `$$ math $$` 添加，不需要在 `$$` 之前或之后留空行
- **Inline math** （在列表中）应添加 `\$$ math $$`

```markdown
<!-- Block math, 保留所有空行 -->

$$
LaTeX_math_expression
$$

<!-- Equation numbering, 保留所有空行  -->

$$
\begin{equation}
  LaTeX_math_expression
  \label{eq:label_name}
\end{equation}
$$

Can be referenced as \eqref{eq:label_name}.

<!-- Inline math in lines, 无需空行 -->

"Lorem ipsum dolor sit amet, $$ LaTeX_math_expression $$ consectetur adipiscing elit."

<!-- Inline math in lists, 转义第一个 `$` -->

1. \$$ LaTeX_math_expression $$
2. \$$ LaTeX_math_expression $$
3. \$$ LaTeX_math_expression $$
```

> 从`v7.0.0`开始，**MathJax**的配置选项已移动到文件 `assets/js/data/mathjax.js`{: .filepath }中，您可以根据需要更改选项，例如添加[extensions][mathjax-exts]。
> 如果您通过`chirpy-starter`构建站点，请从 gem 安装目录（使用命令`bundle info --path jekyll-theme-chirpy` 检查）中复制该文件到您的仓库中的相同目录。
{: .prompt-tip }

[mathjax-exts]: https://docs.mathjax.org/en/latest/input/tex/extensions/index.html

## Mermaid

[**Mermaid**](https://github.com/mermaid-js/mermaid) 是一个很好的图表生成工具。要在您的文章中启用它，在 YAML 区块中添加以下内容：

```yaml
---
mermaid: true
---
```

然后您可以像其他 Markdown 语言一样使用它：用  ```` ```mermaid ```` 和 ```` ``` ````包围图形代码。

## 了解更多

有关 Jekyll 文章的更多信息，请访问 [Jekyll 文档: Posts](https://jekyllrb.com/docs/posts/).
