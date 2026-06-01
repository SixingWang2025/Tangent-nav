# Tangent Nav

基于 [Hugo](https://gohugo.io/) + [WebStack-Hugo](https://github.com/shenweiyan/WebStack-Hugo) 主题的网址导航站，部署在 [sixingwang2025.github.io/nav/](https://sixingwang2025.github.io/nav/)。

## 目录结构

```
Tangent-nav/
├── config.toml          # Hugo 配置（站点信息、主题参数、Logo、页脚等）
├── data/
│   ├── webstack.yml     # 导航链接数据（分类、名称、URL、Logo、描述）
│   ├── friendlinks.yml  # 友情链接
│   └── headers.yml      # 顶部公告/提示
├── content/
│   └── about.md         # "关于导航"页面
├── layouts/             # 自定义模板（覆盖主题）
├── static/
│   └── assets/
│       └── images/      # Logo 图片、背景图等
├── themes/
│   └── WebStack-Hugo/   # WebStack 主题（git submodule）
└── public/              # 构建输出（提交到仓库用于部署）
```

## 添加/修改导航链接

编辑 `data/webstack.yml`：

```yaml
- taxonomy: 分类名称
  icon: far fa-star      # Font Awesome 图标类
  links:
    - title: 网站名称
      url: https://example.com
      logo: example.png   # 放在 static/assets/images/logos/
      description: 网站描述
```

**注意**：每条链接的 `logo` 字段不能重复定义（YAML 不允许重复 key）。

## Logo 说明

所有站点 logo 放在 `static/assets/images/logos/` 目录下，参考 `config.toml` 中的 `[params.assets]` 配置：

```toml
logosPath   = "assets/images/logos"
defaultLogo = "assets/images/logos/default.webp"
```

侧栏 Logo（展开/折叠、浅色/深色）也在此目录中配置。

## 本地预览

```bash
~/go/bin/hugo server --port 1313
# 访问 http://localhost:1313/nav/
```

## 构建与部署

```bash
# 构建
~/go/bin/hugo --minify --baseURL "https://sixingwang2025.github.io/nav/"

# 提交并推送
git add data/ public/
git commit -m "更新导航链接"
git push
```

推送到 `main` → GitHub Actions 将 `public/` 部署到 `gh-pages` 分支 → 触发主仓库拉取到 `/nav` 路径。

## 定制说明

本仓库对原 WebStack-Hugo 主题做了以下修改：

- `layouts/` 覆盖了侧栏和头部模板，修复了新版 Hugo 的兼容性问题
- `data/webstack.yml` 包含个性化导航链接
- `config.toml` 配置了自己的 Logo、页脚版权信息
