# veightz/site

Veight 的个人网站。目前是占位主页（`noindex`），尚未公开任何文章。线上地址：https://veightz.pages.dev

## 技术栈

- [Astro](https://astro.build) + MDX，纯静态输出（`output: 'static'`）
- 部署到 Cloudflare Pages，项目名 `veightz`
- 暂不使用 Slidev / CopilotKit / Starlight

## 目录

- `src/pages/` 页面
- `src/content.config.ts` 文章内容集合（读取 `content/posts/`，为空也能正常构建）
- `content/posts/` 文章（Markdown / MDX）
- `assets/` 文章用到的素材

## 开发与构建

需要 Node.js 22.x（Astro 当前版本的要求）。

```bash
npm install
npm run dev       # 本地开发
npm run build     # 构建到 dist/
npm run preview   # 预览构建结果
```

## 部署

```bash
npm run build
npx wrangler pages deploy dist --project-name veightz --branch main
# 或：npm run deploy（需先 npm run build）
```

需要环境变量 `CLOUDFLARE_API_TOKEN`（以及必要时 `CLOUDFLARE_ACCOUNT_ID`），不要把令牌写进仓库。

## 内容原则

公开内容只走白名单：只有明确挑选并整理过的文章才会放进 `content/posts/`。私有仓库 knowledge-base 永远不会被直接暴露或构建进来。

## 注意

目前没有配置 GitHub Actions 自动部署（现有 gh 令牌没有 workflow 权限），所以需要手动 build 后用 wrangler 部署。
