---
layout: home

hero:
  name: 导航-资源库
  text: 收集一些日常使用的网站资源和网站社区
  tagline: 书山有路勤为径，学海无涯苦作舟。
  image:
    src: /logo.png
    alt: 前端导航网站
  actions:
    - text: 开始阅读
      link: /front/
    - text: 前端资源
      link: https://notes.fe-mm.com
      theme: alt
    - text: 编程笔记
      link: https://netease-music.fe-mm.com
      theme: alt
features:
  - icon: 📖
    title: 前端物语
    details: 整理前端常用知识点<small>（面试八股文）</small><br />如有异议按你的理解为主，不接受反驳
    link: https://notes.fe-mm.com/fe/javascript/types
    linkText: 前端常用知识
  - icon: 📘
    title: 源码阅读
    details: 了解各种库的实现原理<br />学习其中的小技巧和冷知识
    link: https://notes.fe-mm.com/analysis/utils/only-allow
    linkText: 源码阅读
  - icon: 💡
    title: Workflow
    details: 在工作中学到的一切<small>（常用库/工具/奇淫技巧等）</small><br />配合 CV 大法来更好的摸鱼
    link: https://notes.fe-mm.com/workflow/utils/library
    linkText: 常用工具库
  - icon: 🧰
    title: 提效工具
    details: 工欲善其事，必先利其器<br />记录开发和日常使用中所用到的软件、插件、扩展等
    link: https://notes.fe-mm.com/efficiency/online-tools
    linkText: 提效工具
  - icon: 🐞
    title: 踩坑记录
    details: 那些年我们踩过的坑<br />总有一些让你意想不到的问题
    link: https://notes.fe-mm.com/pit/npm
    linkText: 踩坑记录
  - icon: 💯
    title: 吾志所向，一往无前。
    details: '<small class="bottom-small">一个想躺平的小开发</small>'
    link: https://notes.fe-mm.com/mao
---

<script setup>
// import MFriends from './components/MFriends.vue'
// import Cards from './components/Cards.vue'
import { FRIEND_DATA } from './home/friend-data';
console.log(FRIEND_DATA)
</script>

<ClientOnly>
  <Cards  v-for="{ title, items } in FRIEND_DATA"
      :title="title"
      :items="items" />
</ClientOnly>

<!-- 样式 -->
<style>
/*爱的魔力转圈圈*/
/* hero-image */
.VPHome .image-src:hover {
  transform: translate(-50%, -50%) rotate(666turn);
  transition: transform 59s 1s cubic-bezier(0.3, 0, 0.8, 1);
}
/* features的样式 */
.VPHome .details small {
  opacity: 0.8;
}
/* features的样式 */
.VPHome .bottom-small {
  display: block;
  margin-top: 2em;
  text-align: right;
}
</style>
