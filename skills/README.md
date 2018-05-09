---
layout: LayoutPage
title: 技能
skills:
  - title: 前端
    icon: chrome
    items:
      Bootstrap: 3
      CSS: 2
      HTML: 3
      JavaScript: 2
      jQuery: 3
      Vue.js: 2
  - title: 後端
    icon: desktop
    items:
      PHP: 3
      Node.js: 2
  - title: 資料庫
    icon: database
    items:
      MySQL: 3
      SQLite: 2
      MongoDB: 1
      Redis: 1
  - title: 其他
    icon: server
    items:
      Apache: 3
      Docker: 1
      Ubuntu: 2
      Selenium IDE: 2
      GoAccess: 2
---
# <span class="fa fa-bar-chart-o fa-fw"></span> 技能

<div class="row">
  <div class="col-md-6 p-md-2">
    <SkillCard :skill="$page.frontmatter.skills[0]"/>
    <SkillCard :skill="$page.frontmatter.skills[2]"/>
  </div>
  <div class="col-md-6 p-md-2">
    <SkillCard :skill="$page.frontmatter.skills[1]"/>
    <SkillCard :skill="$page.frontmatter.skills[3]"/>
  </div>
</div>