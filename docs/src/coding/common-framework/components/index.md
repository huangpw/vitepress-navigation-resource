---
outline: deep
---

<script setup>
import { NAV_DATA } from './data'
</script>
<!-- <style src="./index.scss"></style> -->

# CSS组件库

<Cards v-for="{title, items} in NAV_DATA" :title="title" :items="items"/>

<br />

::: tip
该导航由 [huangpw](https://github.com/vuejs/vitepress) 开发，如有引用、借鉴的请保留版权声明：<https://github.com/vuejs/vitepress>
:::
