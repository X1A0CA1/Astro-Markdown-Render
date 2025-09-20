# Astro Markdown <img src="https://jonneal.dev/astro-logo.svg" alt="" width="90" height="90" align="right">

> [!NOTE]
> 这是我为了消除依赖冲突而自制的 npm 包，没有任何新功能。

**Astro Markdown** 允许您在 **[Astro](https://astro.build)** 中渲染任何 Markdown 内容，并可选择与任何现有配置集成。

[![NPM Version][npm-img]][npm-url]
[![NPM Downloads][download-img]][download-url]
[![Open in StackBlitz][stackblitz-img]][stackblitz-url]

```astro
---
import { Markdown } from '@astropub/md'
---
<Markdown of={`# Hi, there!`} /* Renders `<h1>Hi, there!</h1>` */ />
```

```astro
---
import { markdown } from '@astropub/md'
---
{
  /* Renders `<h1>Hi, there!</h1>` */
  await markdown(`# Hi, there!`)
}
```

## 用法

将 **Astro Markdown** 添加到您的项目中。

```shell
pnpm add @astropub/md
```

在您的项目中使用 **Astro Markdown**。

```astro
---
import { markdown } from '@astropub/md'
---
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width" />
    <title>Astro</title>
  </head>
  <body>
    {await markdown(
`# Hi, there!

Welcome to my _website_.`
    )}
  </body>
</html>
```

或者，将 **Astro Markdown** 与您现有的 Astro 配置集成。

```js
// astro.config.js
import { defineConfig } from 'astro/config'
import markdownIntegration from '@astropub/md'

export default defineConfig({
  integrations: [
    markdownIntegration(),
  ],
  markdown: {
    remarkPlugins: [],
    rehypePlugins: [],
    // syntaxHighlight: 'shiki'
    // syntaxHighlight: 'prism'
  }
})
```

现在 `markdown` 配置会自动应用于 `<Markdown>` 组件和 `markdown()` 函数。

使用 `markdown.inline()` 或 `<Markdown.Inline>` 来处理不带段落包围的短文本字符串。

```astro
---
import { Markdown } from '@astropub/md'
---
<Markdown.Inline of={
  /* Renders `Welcome to my <em>website</em>.` */
  `Welcome to my _website_.`
} />
```

```astro
---
import { markdown } from '@astropub/md'
---
{await markdown.inline(
  /* Renders `Welcome to my <em>website</em>.` */
  `Welcome to my _website_.`
)}
```

<br />

尽情享用吧！

## 项目结构

在这个 Astro 项目中，您会看到以下文件夹和文件：

```
/
├── demo/
│   ├── public/
│   └── src/
│       └── pages/
            ├── index.astro
│           └── ...etc
└── packages/
    └── md/
        ├── package.json
        └── ...etc
```

该项目使用 **workspaces** 来开发单个包 `@astropub/md`。

它还包括一个最小的 Astro 项目 `demo`，用于开发和演示该组件。

## 命令

所有命令都在项目的根目录下的终端中运行：

| 命令 | 操作 |
|:---|:---|
| `pnpm install` | 安装依赖 |
| `pnpm run start` | 在 `localhost:3000` 启动本地开发服务器 |
| `pnpm run build` | 构建您的生产站点到 `./dist/` |
| `pnpm run serve` | 在部署前本地预览您的构建 |

想了解更多？
请阅读 [Astro 文档][docs-url] 或加入 [Astro Discord][chat-url]。

[chat-url]: https://astro.build/chat
[docs-url]: https://github.com/withastro/astro

[npm-img]: https://img.shields.io/npm/v/@astropub/md?color=%23444&label=&labelColor=%23CB0000&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjE1MCAxNTAgNDAwIDQwMCIgZmlsbD0iI0ZGRiI+PHBhdGggZD0iTTE1MCA1NTBoMjAwVjI1MGgxMDB2MzAwaDEwMFYxNTBIMTUweiIvPjwvc3ZnPg==&style=for-the-badge
[npm-url]: https://www.npmjs.com/package/@astropub/md
[stackblitz-img]: https://img.shields.io/badge/-Open%20in%20Stackblitz-%231374EF?color=%23444&labelColor=%231374EF&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjEwIDggMTIgMTgiIGhlaWdodD0iMTgiIGZpbGw9IiNGRkYiPjxwYXRoIGQ9Ik0xMCAxNy42aDUuMmwtMyA3LjRMMjIgMTQuNGgtNS4ybDMtNy40TDEwIDE3LjZaIi8+PC9zdmc+&style=for-the-badge
[stackblitz-url]: https://stackblitz.com/github/astro-community/md
[bundlejs-img]: https://img.shields.io/badge/dynamic/json?url=https://bundlejs.com/api?q=@astropub/md&query=size.totalCompressedSize&color=%23444&labelColor=%233B82F6&label=&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA3MDAgNzAwIiBmaWxsPSIjRkZGIj4KCTxwYXRoIGQ9Ik0xNDYgMkExNzEgMTcxIDAgMCAwIDMgMTM5bC0yIDExdjQwMmwyIDExYzE1IDcyIDcxIDEyNSAxNDMgMTM2bDIwOSAxIDE5OS0xIDktMmM3MC0xNiAxMTktNjYgMTM0LTEzNWwyLTEwVjE1MGwtMi0xMkExNzEgMTcxIDAgMCAwIDU2MiAzbC0xMC0yLTE5OS0xQzE4NyAwIDE1MyAwIDE0NiAyem0xODEgMjUxdjM2bDctM2MxMy02IDMzLTkgNTAtNyA0MSA1IDcwIDM0IDgwIDc4IDIgMTIgMiA0MSAwIDUzLTUgMjItMTMgMzgtMjcgNTJhODIgODIgMCAwIDEtNjMgMjZjLTE1IDAtMTkgMC0yNS0yLTEwLTItMTctNi0yNC0xMGwtNS0zdjExaC00NVYyMTdoNTJ2MzZ6bTI5IDcxYy0yMCAzLTMyIDE5LTM1IDQ4LTMgMjUgMyA0OCAxNCA2MCA1IDYgMTMgMTAgMjMgMTEgMjUgNCA0NC05IDUxLTM2bDMtMTljMC0xNy0xLTI3LTctMzktOS0xOS0yNi0yOC00OS0yNXoiLz4KPC9zdmc+&style=for-the-badge
[bundlejs-url]: https://bundlejs.com/?bundle&q=@astropub/md
[download-url]: https://www.npmjs.com/package/@astropub/md
[download-img]: https://img.shields.io/badge/dynamic/json?url=https://api.npmjs.org/downloads/point/last-week/@astropub/md&query=downloads&label=⇓+week&color=%23444&labelColor=%23EEd100&style=for-the-badge