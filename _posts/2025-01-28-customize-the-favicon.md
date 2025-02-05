---
title: 自定义图标
description: 本文将指导您创建并替换默认的网站图标。
authors: cotes
date: 2025-01-28 11:00:00 +0800
categories: [博客, 教程]
tags: [图标]
---

 [**Chirpy**](https://github.com/cotes2020/jekyll-theme-chirpy/) 的网站图标 [favicons](https://www.favicon-generator.org/about/) 放置在目录 `assets/img/favicons/`{: .filepath}中。您或许想用自己的图标替换它们。以下部分将指导您创建并替换默认的网站图标。

## 生成图标

准备一张尺寸为 512x512 或更大的方形图像（PNG、JPG 或 SVG），然后访问在线工具 [**Real Favicon Generator**](https://realfavicongenerator.net/) 并点击 <kbd>Select your Favicon image</kbd> 按钮上传您的图片文件。

在下一步中，网页会显示所有使用场景。您可以保持默认选项，滚动到页面底部，然后点击 <kbd>Generate your Favicons and HTML code</kbd> 按钮以生成网站图标。

## 下载和替换

下载生成的压缩包，解压并从解压的文件中删除以下两个文件：

- `browserconfig.xml`{: .filepath}
- `site.webmanifest`{: .filepath}

然后将剩余的图片文件（`.PNG`{: .filepath} 和 `.ICO`{: .filepath}）复制到您的 Jekyll 站点的 `assets/img/favicons/`{: .filepath} 目录下覆盖原文件。如果您的 Jekyll 站点还没有此目录，只需创建一个。

下表将帮助您了解对网站图标文件的更改：

| 文件            | 来自在线工具                  | 来自 Chirpy |
|---------------------|:---------------------------------:|:-----------:|
| `*.PNG`             | ✓                                 | ✗           |
| `*.ICO`             | ✓                                 | ✗           |

<!-- markdownlint-disable-next-line -->
>  ✓ 表示保留，✗ 表示删除。
{: .prompt-info }

您下次构建网站时，该网站图标将被替换为自定义版本。
