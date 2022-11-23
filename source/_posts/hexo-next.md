---
title: hexo-Next主题教程
date: 2022-11-23 21:11:46
tags:
  - hexo
  - 教程
---
## 配置文件
> 数学公式

```yaml
# Math Formulas Render Support
math:
  # Default (false) will load mathjax / katex script on demand.
  # That is it only render those page which has `mathjax: true` in front-matter.
  # If you set it to true, it will load mathjax / katex script EVERY PAGE.
  every_page: false

  mathjax:
    enable: true
    # Available values: none | ams | all
    tags: none

  katex:
    enable: false
    # See: https://github.com/KaTeX/KaTeX/tree/master/contrib/copy-tex
    copy_tex: false
```