# 个人博客

基于 [Astro](https://astro.build) 搭建的个人博客，部署在 Cloudflare Pages。

## 功能

- 文章标签与分类
- 全文搜索（Pagefind）
- 明暗主题切换（跟随系统 + 手动）
- RSS 订阅
- Sitemap 自动生成
- 响应式布局

## 目录结构

```
src/
├── components/     # 公共组件
├── content/blog/   # Markdown 文章
├── layouts/        # 页面布局
├── pages/          # 路由页面
└── styles/         # 全局样式
```

## 本地开发

```bash
pnpm install
pnpm dev        # 启动开发服务器 http://localhost:4321
```

## 构建

```bash
pnpm build      # 构建 + 生成搜索索引
pnpm preview    # 本地预览构建产物
```

> Node.js 版本要求 >= 22.12.0，项目通过 `.npmrc` 的 `use-node-version` 自动管理，无需手动切换。

## 写文章

在 `src/content/blog/` 下新建 `.md` 或 `.mdx` 文件，frontmatter 格式：

```yaml
---
title: '文章标题'
description: '文章简介'
pubDate: '2026-01-01'
tags: ['技术', 'web']
---
```

## 部署到 Cloudflare Pages

1. 将仓库推送到 GitHub
2. Cloudflare Dashboard → Pages → Connect to Git → 选择此仓库
3. 构建配置：
   - Build command: `pnpm build`
   - Build output: `dist`
4. 环境变量：`NODE_VERSION = 22.22.0`
5. 部署完成后更新 `astro.config.mjs` 中的 `site` 为实际域名
