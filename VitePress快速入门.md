# VitePress快速入门

## 一、生成初始化 package.json

### 1. 创建项目目录

```bash
mkdir -p projectName
```

### 2. 进入项目目录

```bash
cd projectName
```

### 3. 生成 package.json

```bash
npm init -y
```

## 二、VitePress 安装和初始化

参考：https://vitepress.dev/zh/guide/getting-started

### 1. 安装 vitepress

注意这里是 `npm add`

```bash
npm add -D vitepress
```

### 2. 生成 vitepress 基础配置

```bash
npx vitepress init
```
```
PS C:\Users\Administrator\Desktop> npx vitepress init

┌  Welcome to VitePress!
│
◇  Where should VitePress initialize the config?
│  ./docs
│
◇  Site title:
│  My Awesome Project
│
◇  Site description:
│  A VitePress Site
│
◇  Theme:
│  Default Theme
│
◇  Use TypeScript for config and theme files?
│  No
│
◇  Add VitePress npm scripts to package.json?
│  Yes
│
└  Done! Now run npm run docs:dev and start writing.
```
### 3. 开发环境启动

package.json 配置 start 命令

```json{7}
{
  "name": "ffffee",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "start": "npm run docs:dev", 
    "docs:dev": "vitepress dev",
    "docs:build": "vitepress build",
    "docs:preview": "vitepress preview"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "vitepress": "^1.3.4"
  }
}
```

开发环境启动

```bash
npm start
```

浏览器访问对应 url，查看是否正常

Ctrl + C 可以退出

### 4. 修改 `.vitepress/config.mjs` 配置文件，增加 `outDir: "dist"`、`srcDir: "src"`配置

```js
import { defineConfig } from "vitepress";

// https://vitepress.dev/reference/site-config
export default defineConfig({
  title: "HUANGPW讲前端官网",
  description:
    "HUANGPW讲前端的官网，electron-vlc，electron-screenshort，electron vlc 音视频播放器，electron 截图，electron line 插件",
  outDir: "dist", 
  srcDir: "src", 
  themeConfig: {
    // https://vitepress.dev/reference/default-theme-config
    nav: [
      { text: "首页", link: "/" },
      { text: "Examples", link: "/markdown-examples" },
      { text: "HUANGPW讲前端文档", link: "https://baidu.com" },
    ],

    sidebar: [
      {
        text: "Examples",
        items: [
          { text: "Markdown Examples", link: "/markdown-examples" },
          { text: "VitePress 快速入门", link: "/vitepress-quick-start.md" },
        ],
      },
    ],

    socialLinks: [
      { icon: "github", link: "https://github.com/huangpw/vitepress-navigation-resource" },
    ],
  },
});
```

### 5. 创建 src 目录，移动 `index.md`、`api-examples.md`、`markdown-examples.md`到 `src/`目录下

```bash
mkdir -p src
```

```
src/index.md
src/api-examples.md
src/markdown-examples.md
```

### 6. 增加.npmrc 文件

```
registry=https://registry.npmmirror.com
```

### 7. 打包应用

```
npm run docs:build
```

## 四、初始化项目 git

### 1. 创建 .gitignore

```powershell
touch .gitignore
```

.gitignore 内容如下

```
node_modules
.vitepress/cache/
dist
```

### 2. 初始化

```bash
git init
```

### 3. 添加到暂存区

```bash
git add .
```

### 4. 提交代码

```bash
git commit -m 'feat: init'
```

## 五、VitePress 配置默认主题

VitePress 官网：https://github.com/vuejs/vitepress

配置参考：https://github.com/vuejs/vitepress/blob/main/docs/.vitepress/config/zh.ts

### 1. 修改 `.vitepress/config.mjs`

```js
import { defineConfig } from "vitepress";

// https://vitepress.dev/reference/site-config
export default defineConfig({
  title: "huangpw讲前端官网",
  description:
    "huangpw讲前端的官网，electron-vlc，electron-screenshort，electron vlc 音视频播放器，electron 截图，electron line 插件",
  outDir: "dist",
  srcDir: "src",
  themeConfig: {
    // https://vitepress.dev/reference/default-theme-config
    nav: [
      { text: "首页", link: "/" },
      { text: "Examples", link: "/markdown-examples" },
      { text: "huangpw讲前端文档", link: "https://docs.ffffee.com" },
    ],

    sidebar: [
      {
        text: "Examples",
        items: [
          { text: "Markdown Examples", link: "/markdown-examples" },
          { text: "VitePress 快速入门", link: "/vitepress-quick-start.md" },
        ],
      },
    ],

    socialLinks: [
      { icon: "github", link: "https://github.com/vuejs/vitepress" },
    ],

    footer: {
      message: `<a href="https://beian.miit.gov.cn/" target="_blank">京ICP备20016634号-2</a>`,
      copyright: `版权所有 © 2019-${new Date().getFullYear()} 李少海`,
    },

    docFooter: {
      prev: "上一页",
      next: "下一页",
    },

    // https://vitepress.dev/zh/reference/default-theme-config#outline
    outline: {
      level: [2, 3],
      label: "页面导航",
    },

    lastUpdated: {
      text: "最后更新于",
      formatOptions: {
        dateStyle: "short", // full
        timeStyle: "short", // medium
      },
    },

    langMenuLabel: "多语言",
    returnToTopLabel: "回到顶部",
    sidebarMenuLabel: "菜单",
    darkModeSwitchLabel: "主题",
    lightModeSwitchTitle: "切换到浅色模式",
    darkModeSwitchTitle: "切换到深色模式",
  },
});
```

::: tip 关于 VitePress 配置了看不到最后更新时间

你必须使用`git commit`提交 markdown 文件才能看到最后更新时间。

相关文档：https://vitepress.dev/zh/reference/default-theme-last-updated
:::

### 2. 配置完成效果

![nav1001.png](https://s2.loli.net/2025/02/08/LYfTHKuwz12bhis.png)

![nav1002.png](https://s2.loli.net/2025/02/08/6qhPe8ulLE5tRYW.png)

### 3. 配置 icon、logo、首页右边大图

1. 修改 `.vitepress/config.mjs`

```js
import { defineConfig } from "vitepress";

// https://vitepress.dev/reference/site-config
export default defineConfig({
  title: "huangpw讲前端官网",
  description:
    "huangpw讲前端的官网，electron-vlc，electron-screenshort，electron vlc 音视频播放器，electron 截图，electron line 插件",
  head: [
    [
      "link",
      {
        rel: "apple-touch-icon",
        sizes: "180x180",
        href: "/favicon-180x180.png",
      },
    ],
    [
      "link",
      {
        rel: "icon",
        type: "image/png",
        sizes: "32x32",
        href: "/favicon-32x32.png",
      },
    ],
    [
      "link",
      {
        rel: "icon",
        type: "image/png",
        sizes: "16x16",
        href: "/favicon-180x180.png",
      },
    ],
    ["link", { rel: "shortcut icon", href: "/favicon-16x16.ico" }],
  ],
  outDir: "dist",
  srcDir: "src",
  themeConfig: {
    logo: "/logo.png",
    // https://vitepress.dev/reference/default-theme-config
    nav: [
      { text: "首页", link: "/" },
      { text: "Examples", link: "/markdown-examples" },
      { text: "huangpw讲前端文档", link: "https://docs.ffffee.com" },
    ],
  },
});
```

2. 修改 `src/index.md`

```markdown
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
    - text: Get Started
      link: /front/
    - text: HPW管理后台
      link: https://notes.fe-mm.com
      theme: alt
    - text: 我的博客
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

<!-- <script setup>
import MFriends from './components/MFriends.vue'
</script>

<ClientOnly>
  <MFriends/>
</ClientOnly> -->

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
```

3. 创建 `src/public/` 文件夹

```
src/
  public/
    favicon-16x16.ico
    favicon-16x16.png
    favicon-32x32.png
    favicon-180x180.png
    logo.png
```

### 4. 最终效果

![nav1001.png](https://s2.loli.net/2025/02/08/LYfTHKuwz12bhis.png)

## 六、VitePress 自定义 Vite 配置

希望把 `src/public/` 目录修改为与 `src/` 目录同级别怎么做，这里就需要修改 `vite` 配置了

修改前目录：

```
src/
  public/
    favicon-16x16.ico
    favicon-16x16.png
    favicon-32x32.png
    favicon-180x180.png
    logo.png
```

修改后目录：

```
public/
  favicon-16x16.ico
  favicon-16x16.png
  favicon-32x32.png
  favicon-180x180.png
  logo.png
src/
```

修改 `.vitepress/config.mjs` 添加一个 vite 配置项，配置内容如下

配置参考：https://cn.vitejs.dev/config/shared-options.html#publicdir

```js{18,21}
import { defineConfig } from "vitepress";

// https://vitepress.dev/reference/site-config
export default defineConfig({
  title: "李钟意讲前端官网",
  // ...
  outDir: "dist",
  srcDir: "src",
  themeConfig: {
    logo: "/logo.png",
    // https://vitepress.dev/reference/default-theme-config
    nav: [
      { text: "首页", link: "/" },
      { text: "Examples", link: "/markdown-examples" },
      { text: "李钟意讲前端文档", link: "https://docs.ffffee.com" },
    ],
  },
  vite: { 
    // https://cn.vitejs.dev/config/shared-options.html#publicdir  //
    publicDir: "../public", // 指定 public 目录路径 //
  },  
});
```





https://docs.ffffee.com/vitepress/vitepress-quick-start.html#_4-%E4%BF%AE%E6%94%B9-vitepress-config-mjs-%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6-%E5%A2%9E%E5%8A%A0-outdir-dist-%E3%80%81srcdir-src-%E9%85%8D%E7%BD%AE
