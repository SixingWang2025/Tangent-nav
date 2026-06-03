# Tangent Nav

基于 [Hugo](https://gohugo.io/) + [WebStack-Hugo](https://github.com/shenweiyan/WebStack-Hugo) 主题的个人网址导航站，上线地址：[**sixingwang2025.github.io/nav/**](https://sixingwang2025.github.io/nav/) 。

## 导航内容

| # | 分类 | 站点数 | 说明 |
|---|------|--------|------|
| 1 | 常用推荐 | 1 | 关注我们 |
| 2 | 搜索引擎 | 10 | Google、百度、Bing、DuckDuckGo 等 |
| 3 | 人工智能 | 33 | 对话助手 / AI搜索 / 图像视频 / 编程音乐 |
| 4 | 编程开发 | 31 | 编程语言 / 开发工具 / 部署平台 |
| 5 | 开发者社区 | 15 | GitHub、掘金、V2EX、Product Hunt 等 |
| 6 | 云服务器 | 10 | 阿里云、AWS、Azure、GCP 等 |
| 7 | 学术科研 | 15 | Google Scholar、PubMed、arXiv、知网等 |
| 8 | 设计素材 | 27 | 设计工具 / 图标 / 图片 / 色彩 / 字体 |
| 9 | 实用工具 | 18 | 图片处理 / 格式转换 / 开发者工具 / 其他 |
| 10 | 网盘存储 | 10 | 百度网盘、阿里云盘、OneDrive 等 |
| 11 | 办公学习 | 17 | 翻译 / 笔记协作 / 学习平台 |
| 12 | 资讯阅读 | 15 | 技术资讯 / 书籍阅读 |
| 13 | 休闲娱乐 | 15 | 影音视频 / 音乐 / 游戏 |

**总计**：13 个分类，217 个站点。

## 目录结构

```
Tangent-nav/
├── config.toml              # Hugo 主配置（baseURL、站点信息、Logo 等）
├── data/
│   ├── webstack.yml         # ★ 导航数据（分类、站点、URL、描述）
│   ├── friendlinks.yml      # 友链
│   └── headers.yml          # 顶部导航栏链接
├── content/
│   └── about.md             # "关于导航"页面
├── layouts/                 # 自定义模板（覆盖主题）
├── static/assets/images/
│   └── logos/               # ★ 所有站点图标（211 个 logo 文件）
├── themes/WebStack-Hugo/    # 主题（git submodule）
└── public/                  # Hugo 构建输出（提交到仓库）
```

## 添加 / 修改导航

编辑 `data/webstack.yml`，支持两种结构：

### 扁平列表

```yaml
- taxonomy: 分类名称
  icon: fas fa-robot         # Font Awesome 图标
  links:
    - title: 站点名称
      url: https://example.com
      logo: example.png       # 放入 static/assets/images/logos/
      description: 一句话描述站点的核心价值
```

### 带子分类的列表

```yaml
- taxonomy: 编程开发
  icon: fas fa-code
  list:
    - term: 编程语言
      links:
        - title: Python
          url: https://www.python.org/
          logo: Python.png
          description: 数据科学与 AI 领域的首选语言
    - term: 开发工具
      links:
        - title: VS Code
          url: https://code.visualstudio.com/
          logo: VS Code.png
          description: 微软跨平台免费代码编辑器
```

## 获取站点 Logo

### 方法一：favicon.im（推荐，国内可访问）

```bash
curl -o logo.png 'https://favicon.im/example.com'
```

### 方法二：直连 favicon

```bash
curl -o logo.png 'https://example.com/favicon.ico'
```

### 方法三：apple-touch-icon（通常更高清）

```bash
curl -o logo.png 'https://example.com/apple-touch-icon.png'
```

### 注意事项
- 下载后用 `file logo.png` 检查是否是真实图片还是 HTML 页面
- `.svg` 文件用 `.svg` 后缀，`.ico` 文件用 `.png` 后缀（Hugo 会直接引用，浏览器兼容性更好）
- 太小（<500B）的图标可能在页面上显示模糊

## 本地预览

```bash
hugo server --port 1313
# 访问 http://localhost:1313/nav/
```

## 构建与部署

推送 `main` → GitHub Actions 构建 Hugo → 输出到 `gh-pages` 分支 → 主仓库 `SixingWang2025.github.io` 拉取到 `/nav/` 路径。

```bash
# 本地构建
hugo --gc

# 提交
git add data/ static/ public/
git commit -m "更新导航"
git push
```

## 定制清单

- `layouts/` — 修复新版 Hugo 兼容性的侧栏/头部模板覆盖
- `data/webstack.yml` — 个性化导航数据
- `config.toml` — 自定义 Logo、页脚版权、一言服务、天气 API
- `static/assets/images/logos/` — 211 个站点图标（已清理未引用旧文件）
