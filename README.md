# orangesai.com

橘子 / Leo Feng 的个人主页。纯静态，无构建步骤，GitHub Pages 托管。

```
index.html           整站（改这个）
404.html             自定义 404
avatar.svg           头像（圆角版，页面里用这个）
favicon.svg          站点图标（同 avatar.svg）
favicon-32.png       favicon 回退 32×32
favicon-192.png      favicon 回退 192×192
favicon-512.png      大图标 512×512
apple-touch-icon.png iOS 添加到主屏 180×180
og.png               分享卡片 1200×630
robots.txt           爬虫规则
sitemap.xml          站点地图
llms.txt             给 AI 搜索/answer engine 看的摘要
CNAME                orangesai.com
.nojekyll            原样发布，不走 Jekyll
```

## 改内容

所有内容都在 `index.html`，样式是内联在 `<head>` 里的 CSS，没有依赖、没有 web font。

加一个作品：往对应 `<ul class="list">` 里加一条

```html
<li>
  <div class="item"><a class="name" href="https://example.com">名字</a><span class="meta">分类</span></div>
  <p>一句话说明。</p>
</li>
```

改了内容记得同步 `sitemap.xml` 的 `<lastmod>`。推到 `main`，30 秒左右生效。

## SEO 结构

- `<title>` / `description` 里同时带中文名、英文名、网名和身份
- JSON-LD `@graph`：`Person` + `WebSite`，`alternateName` 收所有别名，`sameAs` 串起所有平台账号（这是让搜索引擎把各个平台认成同一个人的关键）
- `og:*` / `twitter:*` + `og.png`，分享出去有卡片
- `llms.txt`：给 ChatGPT/Perplexity 这类答案引擎的自我介绍

新增平台账号时，务必同时加进 JSON-LD 的 `sameAs` 和页面的「联系」区。

## DNS（Cloudflare）

| 类型  | 名称             | 内容                   | 代理     |
|-------|------------------|------------------------|----------|
| CNAME | `orangesai.com`  | `orange2ai.github.io`  | DNS only |
| CNAME | `www`            | `orangesai.com`        | DNS only |

代理保持**关闭**（灰云），GitHub 才能给自定义域名签发和续期 Let's Encrypt 证书。之后想开 CF 代理，先把 SSL/TLS 模式改成 **Full (strict)**。
