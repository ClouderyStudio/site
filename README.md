# ClouderySite (New)

这是 Cloudery 的网站前端仓库（基于 Nuxt 3），包含一组可复用的 UI 组件与页面模板，使用 TypeScript、Tailwind CSS 与 Vite 构建。

**主要特性**

- 采用 Nuxt 3 + Vite 的现代前端架构
- 使用 Tailwind CSS 进行原子化样式管理
- 组件按目录组织，便于复用（见 `app/components/Ui`）
- TypeScript 支持与组合式 API（Composables）

## 快速开始

推荐使用 `pnpm`（仓库包含 `pnpm-lock.yaml`）：

安装依赖：

```bash
pnpm install
```

开发模式（热重载）：

```bash
pnpm dev
```

构建生产包：

```bash
pnpm build
```

本地预览生产构建：

```bash
pnpm preview
```

如果你习惯使用 `npm` 或 `yarn`，也可以使用对应的命令替代 `pnpm`。

## 项目结构概览

- `app/`：Nuxt 应用主目录
  - `app.vue`：应用根组件
  - `assets/`：静态资源（CSS、图片等）
  - `components/Ui/`：主要可复用 UI 组件集合（Button、Container、Navigation 等）
  - `composables/`：组合式函数（如 `useMouseState.ts`、`useScrollspy.ts`）
- `public/`：静态文件（如 `robots.txt`）
- `nuxt.config.ts`：Nuxt 配置
- `package.json`、`pnpm-lock.yaml`、`tsconfig.json`：项目元信息与依赖配置

建议阅读 `app/components/Ui` 下的子目录来了解各组件的用法和导出接口。

## 开发规范与提示

- 代码风格遵循 TypeScript 与 Tailwind 的惯例，组件尽量维持小而单一的职责。
- 新建组件或 composable 时，请在 `components/Ui` 或 `composables` 下建立子目录并添加 `index.ts` 导出接口，便于统一引入。

## 常见命令

- 安装依赖：`pnpm install`
- 本地开发：`pnpm dev`
- 生产构建：`pnpm build`
- 预览构建：`pnpm preview`

## 贡献

欢迎提交 issue 和 PR。建议的工作流程：

1. Fork 仓库并创建 feature 分支
2. 在本地编写并测试代码
3. 提交 PR，描述变更和复现步骤

## 部署

部署方式依赖你的目标平台（Vercel、Netlify、Cloudflare Pages 等）。请参考 Nuxt 官方部署文档： https://nuxt.com/docs/getting-started/deployment

## 许可证

本项目使用 GNU GPL v2 开源许可证，详见 LICENSE 文件内容
