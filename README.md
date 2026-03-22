# 个人博客（Hexo）

基于 [Hexo](https://hexo.io/) 的静态博客，主题 [Butterfly](https://github.com/jerryc127/hexo-theme-butterfly)（[中文文档](https://butterfly.js.org/)）。

## 环境要求

- Node.js 18 或以上

## 常用命令

在项目根目录执行：

| 命令 | 说明 |
|------|------|
| `npm install` | 安装依赖（首次克隆后执行） |
| `npm run server` | 本地预览（可选，默认 <http://localhost:4000>） |
| `npm run build` | 生成静态站点到 `public/` |
| `npm run clean` | 清理缓存与 `public/` |
| `npx hexo new "文章标题"` | 新建文章（Markdown 在 `source/_posts/`） |

## 站点配置

- 根目录 `_config.yml`：站点标题、作者、`url` / `root` 等。
- **`_config.butterfly.yml`**：Butterfly 主题配置（已从主题默认复制，可放心改；升级主题时不会被 `npm install` 覆盖）。

更多选项见 [Butterfly 文档](https://butterfly.js.org/posts/21cfbf15/)。

**线上地址**：当前按「GitHub 用户 `wenbinwang`、仓库名 `blog_cursor`」配置了：

- `url: https://wenbinwang.github.io/blog_cursor`
- `root: /blog_cursor/`

若你的 GitHub 用户名或仓库名不同，请同时修改这两项；若使用 **`用户名.github.io`** 这种用户主页仓库，应改为 `url: https://你的用户名.github.io` 且 `root: /`。

## 部署到 GitHub Pages（推荐）

已配置 [GitHub Actions](.github/workflows/github-pages.yml)：推送到 `main` 会自动执行 `npm ci`、`hexo generate`，并把 `public/` 发布到 Pages。

### 一次性操作

1. **登录 GitHub CLI**（本机执行一次）  
   ```bash
   gh auth login
   ```
2. **在 GitHub 新建仓库**（名称建议 `blog_cursor`，与 `_config.yml` 里 `root` 一致），不要勾选初始化 README。
3. **启用 Pages**：仓库 **Settings → Pages → Build and deployment**，**Source** 选 **GitHub Actions**。
4. **推送代码**（把下面地址换成你的仓库）：
   ```bash
   cd /Users/wenbinwang/Desktop/blog_cursor
   git remote add origin git@github.com:你的用户名/blog_cursor.git
   git push -u origin main
   ```

推送后打开 **Actions** 查看运行结果；成功后站点地址一般为：

`https://你的用户名.github.io/blog_cursor/`

### 部署没生效？先查这三点

1. **是否已关联远程并推送**（最常见）  
   在本机项目根目录执行：
   ```bash
   git remote -v
   ```
   若**没有任何输出**，说明还没执行过 `git remote add` / `git push`，GitHub 上不会有代码，Actions 也不会跑，站点自然不会更新。

2. **仓库是否用 Actions 发布 Pages**  
   **Settings → Pages → Build and deployment** 里，**Source** 必须是 **GitHub Actions**（不要选 Deploy from a branch 除非你知道自己在做什么）。

3. **Actions 是否跑绿**  
   打开仓库的 **Actions** 标签，最新 workflow 应成功；若失败，点进去看日志（常见原因：`npm ci` 与本地 `package-lock.json` 不一致，需提交 lock 文件后重推）。

### 不用 `gh` 时

在 GitHub 网页新建空仓库后，同样设置 Pages 源为 **GitHub Actions**，再执行上面的 `git remote` 与 `git push`（可用 HTTPS）。

## 其他部署方式（可选）

仍可在 `_config.yml` 里配置 `hexo-deployer-git` 的 `deploy`，使用 `npm run deploy` 推送到分支。说明见 [Hexo 部署文档](https://hexo.io/docs/one-command-deployment)。

## 备注

若 `hexo init` 提示目录非空，可先清空除本 README 外的文件，或使用空临时目录初始化后再拷贝到本文件夹。
