# Tangent 导航

基于 [Hugo](https://gohugo.io/) 的静态响应式网址导航站，使用 [WebStack-Hugo](https://github.com/shenweiyan/WebStack-Hugo) 主题构建。

**线上地址**: <https://sixingwang2025.github.io/Tangent-nav/>

## 本地开发

```bash
# 克隆仓库（含主题子模块）
git clone --recurse-submodules git@github.com:SixingWang2025/Tangent-nav.git
cd Tangent-nav

# 启动开发服务器
hugo server
```

## 项目结构

```
├── config.toml          # 站点配置
├── content/             # 页面内容
├── data/
│   └── webstack.yml     # 导航数据（分类、链接、图标）
├── layouts/             # 自定义布局覆盖
├── static/
│   └── assets/
│       ├── images/
│       │   └── logos/   # 网站图标
│       └── fontawesome-6.4.0/
└── themes/
    └── WebStack-Hugo    # 主题（Git 子模块）
```

## 修改导航

编辑 `data/webstack.yml`，格式如下：

```yaml
- taxonomy: 分类名称
  icon: fas fa-flask fa-lg
  list:
    - term: 子分类
      links:
        - title: 网站名称
          logo: logo.png
          url: https://example.com
          description: 网站描述。
```

图标文件放入 `static/assets/images/logos/`。

## 部署

推送 `main` 分支后，GitHub Actions 自动构建并部署到 GitHub Pages。

## 致谢

- [WebStackPage/WebStackPage.github.io](https://github.com/WebStackPage/WebStackPage.github.io)
- [shenweiyan/WebStack-Hugo](https://github.com/shenweiyan/WebStack-Hugo)（Hugo 主题）
