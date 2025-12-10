

# 安全策略
## meta层设置
避免暴露本站的url 查询参数等敏感路径
 <meta name="referrer" content="strict-origin-when-cross-origin">
 阻止别人用 iframe 嵌套你的页面。
<meta http-equiv="X-Frame-Options" content="DENY">
## nginx层设置
location / {
    try_files $uri /index.html;

    # 安全 Header
    add_header Content-Security-Policy "default-src 'self'; script-src 'self'; style-src 'self' 'unsafe-inline'; img-src 'self' data:; font-src 'self';" always; 防 XSS、限制资源加载
    add_header X-Frame-Options "DENY" always; 阻止别人用 iframe 嵌套你的页面。 避免 点击劫持 攻击
    add_header Referrer-Policy "strict-origin-when-cross-origin" always; 避免暴露本站的url 查询参数等敏感路径
    add_header X-Content-Type-Options "nosniff" always; 防止攻击者把脚本伪装成图片或其他资源，从而绕过浏览器安全限制。
    # add_header Strict-Transport-Security "max-age=31536000; includeSubDomains" always; 强制浏览器使用 HTTPS 
}

# 首页优化
- 懒加载分包  /已实现
命中浏览器强缓存 加快首页响应
- **多站点按需加载资源**
多站点资源 打包只打包需要站点资源 避免混淆 / 待测试
- 首页加载
  渲染范围控制在一屏内 非关键资源延迟加载渲染
- 接口合并 减少接口请求。后端协调数据结构等
- 精灵图 ui合作
- 异步资源预加载
- 图片优化 /缓存
- 
