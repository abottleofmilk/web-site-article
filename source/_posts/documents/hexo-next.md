---
title: hexo-Next主题教程
date: 2022-11-23 21:11:46
tags:
  - hexo
  - 教程
categories:
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
### 添加分类和标签
```shell
hexo new page categories
hexo new page tags
```

## 参考
1. [hexo之next主题添加分类](https://blog.csdn.net/u011240016/article/details/79422462)
2. [【Hexo】nexT主题使用攻略基础——添加分类、标签及关于](https://blog.csdn.net/weixin_48927364/article/details/123295436)