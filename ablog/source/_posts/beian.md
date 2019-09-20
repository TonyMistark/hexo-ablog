---
layout: post
title:  "For the record"
date:   2019-09-20 17:32:40 +0800
categories: Normal
---

### hexo博客hexo主题添加备案号

* 已经用hexo搭建好了博客
* 已经有备案号了

#### 但是应该如何添加备案号到博客最下面呢？

答案是修改footer.swig文件（有的扩展名是.ejs），路径存放博客文件夹/themes/next/layout/_partial/footer.ejs
```html
<footer id="footer">
  <% if (theme.sidebar === 'bottom'){ %>
    <%- partial('_partial/sidebar') %>
  <% } %>
  <div class="outer">
    <div id="footer-info" class="inner">
      &copy; <%= date(new Date(), 'YYYY') %> <%= config.author || config.title %><br>
      <%= __('powered_by') %> <a href="http://hexo.io/" target="_blank">Hexo</a>
    </div>
  </div>
</footer>
```
加入备案代码，最终效果如下：
```html
<footer id="footer">
  <% if (theme.sidebar === 'bottom'){ %>
    <%- partial('_partial/sidebar') %>
  <% } %>
  <div class="outer">
    <div id="footer-info" class="inner">
      &copy; <%= date(new Date(), 'YYYY') %> <%= config.author || config.title %><br>
      <%= __('powered_by') %> <a href="http://hexo.io/" target="_blank">Hexo</a><br>
      <%= '' %> <a href="http://www.beian.miit.gov.cn" target="_blank">粤ICP备19045250号-1</a>
    </div>
  </div>
</footer>
```