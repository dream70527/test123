
• 我会放出，2个 666美元的 密钥  正好 1212美元  你们自己抢着用。不需要你们充值，不割你们[奸笑]
• 13:50准时放出！新人赶快根据配置教材配置好，

免费密钥2个：【凭本事抢】

bma_d33054c188ce93cb4c4cd7572e1b9b321fe7be15435eed18ea596c0b925f521d

bma_3a0ed0a25912c269976a4dbf1e16646d7f604934ff31e976b270fe3f07e56d58
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

- 预连接cdn地址 
  提前建立cdn 网络连接 DNS解析 tls握手 tcp连接
  <link rel="preconnect" href="https://cdn.xxx.com" crossorigin>
  
- 懒加载分包  /已实现
命中浏览器强缓存 加快首页响应
- **多站点按需加载资源**
多站点资源 打包只打包需要站点资源 避免混淆 / 待测试
- 首页加载
  渲染范围控制在一屏内 非关键组件延迟加载渲染
- 接口合并 减少接口请求。后端协调数据结构等
- 精灵图 ui合作
- 异步资源预加载
- 图片优化 /缓存
- 
