---
outline: [2, 3, 4]
---

<script setup>
// import MNavLinks from '../../components/MNavLinks.vue'

import { NAV_DATA } from './data'
</script>
<!-- <style src="./index.scss"></style> -->

# 图标库

<MNavLinks v-for="{title, items} in NAV_DATA" :title="title" :items="items"/>

<br />

::: tip
该导航由 [huangpw](https://github.com/huangpw/) 开发，如有引用、借鉴的请保留版权声明：<https://github.com/huangpw/vitepress-navigation-resource>
:::
