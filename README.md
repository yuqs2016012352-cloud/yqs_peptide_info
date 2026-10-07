# ImmunePeptide Atlas

个人免疫小肽信息数据库，包含静态前端、Netlify Function API 和 Netlify Database PostgreSQL migration。

## 项目结构

- `index.html` 前端页面
- `netlify/functions/peptides.mjs` 小肽 CRUD API
- `netlify/database/migrations/0001_create_peptides.sql` PostgreSQL 数据库结构
- `netlify.toml` Netlify 构建、Function 和 API 路由配置
- `package.json` 依赖

## 部署到 Netlify

1. 将整个项目目录上传到 GitHub 仓库 `yqs_peptide_info`。
2. 在 Netlify 中选择该 GitHub 仓库并创建项目。
3. Netlify 构建完成后，在项目的 Data & Storage > Database 创建 Netlify Database，或按官方文档使用 `netlify database init`。
4. 重新部署项目。数据库 migration 会在部署生命周期中自动应用。
5. 打开网站，右下角应显示“数据库：PostgreSQL 在线”。

## 本地开发

需要 Node.js 和 Netlify CLI：

```bash
npm install
npx netlify dev
```

Netlify Database 的本地开发环境会提供 Postgres 兼容数据库。

## API

- `GET /api/peptides` 获取记录
- `GET /api/peptides/:id` 获取单条记录
- `POST /api/peptides` 新增记录
- `PUT /api/peptides/:id` 更新记录
- `DELETE /api/peptides/:id` 删除记录

## 数据说明

当前项目不向 PostgreSQL 写入虚构的科研文献或 DOI。前端自带的示例数据仅用于页面展示，正式部署后建议逐条录入经过核验的数据。
