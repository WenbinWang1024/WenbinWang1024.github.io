# 个人博客（Hexo）

基于 [Hexo](https://hexo.io/) 的静态博客，默认主题 [Landscape](https://github.com/hexojs/hexo-theme-landscape)。

## 环境要求

- Node.js 18 或以上

## 常用命令

在项目根目录执行：

| 命令 | 说明 |
|------|------|
| `npm install` | 安装依赖（首次克隆后执行） |
| `npm run server` | 本地预览，默认 <http://localhost:4000> |
| `npm run build` | 生成静态站点到 `public/` |
| `npm run clean` | 清理缓存与 `public/` |
| `npx hexo new "文章标题"` | 新建文章（Markdown 在 `source/_posts/`） |

## 站点配置

编辑根目录 `_config.yml`：站点标题、作者、`url`（上线后务必改成真实域名）、`theme` 等。

## 部署（Git）

已安装 `hexo-deployer-git`。在 `_config.yml` 末尾配置 `deploy`，例如推送到 GitHub Pages：

```yaml
deploy:
  type: git
  repo: git@github.com:用户名/用户名.github.io.git
  branch: main
```

然后执行 `npm run deploy`。

更多说明见 [Hexo 部署文档](https://hexo.io/docs/one-command-deployment)。

## 备注

若 `hexo init` 提示目录非空，可先清空除本 README 外的文件，或使用空临时目录初始化后再拷贝到本文件夹。
