# cdn
小文件js img js json等cdn加速

只放小文件



# 境外 
## jsdelivr
```
https://cdn.jsdelivr.net/gh/joyanhui/cdn@main/README.md
https://fastly.jsdelivr.net/gh/joyanhui/cdn@main/README.md
```
## github
```
https://raw.githubusercontent.com/joyanhui/cdn/main/README.md
https://ghproxy.net/https://raw.githubusercontent.com/joyanhui/cdn/main/README.md
```
## cf
```
https://joyanhui-github-cdn.kkdysite.workers.dev/README.md
https://gh.cf-cdn.eu.org/README.md
```

# 境内cdn
```
https://cdn.leiyanhui.com/README.md

http://cdn.leiyanhui.com/gh/joyanhui/cdn@main/README.md
https://cdn.leiyanhui.com/gh/joyanhui/cdn@main/README.md
```
## 环境配置
### 域名解析
默认：gh.cf-cdn.eu.org 境内：cdn
### 缓存规则
全部文件缓存30天，更新文件手动更新

## cf works
```
addEventListener("fetch", event => {
  event.respondWith(handleRequest(event.request))
})

async function handleRequest(request) {
  // Cloudflare Workers 分配的域名
  cf_worker_host = "joyanhui-github-cdn.kkdysite.workers.dev";
  // 自定义的域名1
  origin_host1 = "cdn.leiyanhui.com";
  // 自定义的域名2
  origin_host2 = "gh.cf-cdn.eu.org";
  // GitHub 仓库文件地址
  github_host = "raw.githubusercontent.com/joyanhui/cdn/main";
  // 替换 N 次以同时兼容 Worker 来源和域名来源
  url = request.url.replace(cf_worker_host, github_host).replace(origin_host1, github_host).replace(origin_host2, github_host);
  return fetch(url);
}
```

