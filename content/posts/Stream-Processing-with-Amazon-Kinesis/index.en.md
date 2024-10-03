---
weight: 2
title: "Workshop - 2: 👷 Stream Processing with Amazon Kinesis 🌊"
date: 2024-09-22T15:58:26+08:00
lastmod: 2024-09-22T15:58:26+08:00
draft: false
author: "Long Nguyễn"
authorLink: "https://www.facebook.com/profile.php?id=100013806768346"
description: "Setup and build infrastructure for stream processing with Amazon Kinesis on Amazon Web Services (AWS)."
resources:
- name: "featured-image"
  src: "aws-cloud-img.jpg"
- name: "featured-image-preview"
  src: "featured-image-preview.webp"

tags: ["content", "Markdown"]
categories: ["documentation"]

lightgallery: true

toc:
  auto: false
math:
  enable: true
---

Find out how to create and organize your content quickly and intuitively in **FeelIt** theme.

<!--more-->

## 1. 🌍 Introduction

### 1.1. Amazon Lambda

### 1.2. Amazon CloudWatch

### 1.3. Amazon Kinesis Data Streams

### 1.4. Amazon Kinesis Data Firehose


## 2. 📊 Present the problem

## 3. 🔦 Architecture
![Architecture](stream_processing_architecture.drawio.png "Stream Processing with Amazon Kinesis Diagram")

- 📦 Technology and Services:
  - `S3`
  - `Lambda`
  - `Kinesis Data Streams`
  - `Kinesis Data Firehose`
  - `CloudFormation`
  - `CloudWatch`
  - `IAM`


## 4. 📑 Preparation

This part is shown in the [basic markdown syntax page](../basic-markdown-syntax/).

## 5 Extended Markdown Syntax {#extended-markdown-syntax}

**FeelIt** theme has some extended syntax elements for you to write articles.

### Emoji Support

This part is shown in the [emoji support page](../emoji-support/).

### Mathematical Formula

**FeelIt** theme supports mathematical formulas based on [$ \KaTeX $](https://katex.org/).

Set the property `enable = true` under `[params.math]` in your [site configuration](../theme-documentation-basics#site-configuration)
and the property `math: true` of the article front matter to enable the automatic rendering of mathematical formulas.

{{< admonition tip >}}
Here is a list of [$ \TeX $ functions supported by $ \KaTeX $](https://katex.org/docs/supported.html).
{{< /admonition >}}

#### Block Formula

The default block delimiters are `$$`/`$$` and `\\[`/`\\]`:

```markdown
$$ c = \pm\sqrt{a^2 + b^2} $$

\\[ f(x)=\int_{-\infty}^{\infty} \hat{f}(\xi) e^{2 \pi i \xi x} d \xi \\]
```

The rendered output looks like this:

$$ c = \pm\sqrt{a^2 + b^2} $$

\\[ f(x)=\int_{-\infty}^{\infty} \hat{f}(\xi) e^{2 \pi i \xi x} d \xi \\]

#### Inline Formula

The default inline delimiters are `$`/`$` and `\\(`/`\\)`:

```markdown
$ c = \pm\sqrt{a^2 + b^2} $ and \\( f(x)=\int_{-\infty}^{\infty} \hat{f}(\xi) e^{2 \pi i \xi x} d \xi \\)
```

The rendered output looks like this:

$ c = \pm\sqrt{a^2 + b^2} $ and \\( f(x)=\int_{-\infty}^{\infty} \hat{f}(\xi) e^{2 \pi i \xi x} d \xi \\)

{{< admonition tip >}}
You can add more block and inline delimiters in your [site configuration](../theme-documentation-basics#site-configuration).
{{< /admonition >}}

#### Copy-tex

**[Copy-tex](https://github.com/Khan/KaTeX/tree/master/contrib/copy-tex)** is an extension for **$ \KaTeX $**.

By the extension, when selecting and copying $ \KaTeX $ rendered elements, copies their $ \LaTeX $ source to the clipboard.

Set the property `copyTex = true` under `[params.math]` in your [site configuration](../theme-documentation-basics#site-configuration) to enable Copy-tex.

Select and copy the formula rendered in the previous section, and you can find that the copied content is the LaTeX source code.

#### mhchem

**[mhchem](https://github.com/Khan/KaTeX/tree/master/contrib/mhchem)** is an extension for **$ \KaTeX $**.

By the extension, you can write beautiful chemical equations easily in the article.

Set the property `mhchem = true` under `[params.math]` in your [site configuration](../theme-documentation-basics#site-configuration) to enable mhchem.

```markdown
$$ \ce{CO2 + C -> 2 CO} $$

$$ \ce{Hg^2+ ->[I-] HgI2 ->[I-] [Hg^{II}I4]^2-} $$
```

The rendered output looks like this:

$$ \ce{CO2 + C -> 2 CO} $$

$$ \ce{Hg^2+ ->[I-] HgI2 ->[I-] [Hg^{II}I4]^2-} $$

### Ruby Annotation {#ruby}

An extended Markdown syntax for **ruby annotation** is supported in **FeelIt** theme:

```markdown
[Hugo]{?^}(An open-source static site generator)
```

The rendered output looks like this:

[Hugo]^(An open-source static site generator)

### Fraction {#fraction}

{{< version 0.2.0 >}}

An extended Markdown syntax for **fraction** is supported in **FeelIt** theme:

```markdown
[Light]{?/}[Dark]

[99]{?/}[100]
```

The rendered output looks like this:

[Light]/[Dark]

[90]/[100]

### Font Awesome {#fontawesome}

**FeelIt** theme uses [Font Awesome](https://fontawesome.com/) as the icon library.
You can easily use these icons in your articles.

Get the `class` of icons you wanted from the [Font Awesome website](https://fontawesome.com/icons?d=gallery).

```markdown
Gone camping! {?:}(fa-solid fa-campground fa-fw): Be back soon.

That is so funny! {?:}(fa-regular fa-grin-tears):
```

The rendered output looks like this:

Gone camping! :(fa-solid fa-campground fa-fw): Be back soon.

That is so funny! :(fa-regular fa-grin-tears):

### Escape character {#escape-character}

In some special cases (when writing this theme documentation :(fa-regular fa-grin-squint-tears):),
your content will conflict with basic or extended Markdown syntax, and it is inevitable.

The escape character syntax can help you build the content you wanted:

```markdown
{{??}X} -> X
```

For example, two `:` will enable emoji syntax, which is not the behavior you want. The escape character syntax is like this:

```markdown
{{??}:}joy:
```

The rendered output looks like this:

**{?:}joy{?:}** instead of **:joy:**

{{< admonition tip >}}
This is related to **[an issue for Hugo](https://github.com/gohugoio/hugo/issues/4978)**, which has not been resolved.
{{< /admonition >}}

Another example is:

```markdown
[link{{??}]}(#escape-character)
```

The rendered output looks like this:

**[link{?]}(#escape-character)** instead of **[link](#escape-character)**.
