---
layout: LayoutPage
title: 作品集
works:
- title: QuickPark
  img:
  desc: 大學畢業專題，獲得第一名
  album:
  - img:
    caption: 首頁
  - img:
    caption: 會員列表
- title: 會展系統
  img:
  desc: 各大型展覽售票系統
  album:
  - img:
    caption: 首頁
  - img:
    caption: 會員列表
---

<div class="card-columns">
  <WorkCard v-for="work in $page.frontmatter.works" :key="work.title" :work="work"/>
</div>