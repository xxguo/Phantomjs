

###  使用Phantomjs 抓取js渲染的页面 
你当然要有Phantomjs，废话！（Linux下最好用supervisord守护，必须保持抓取的时候Phantomjs一直处于开启状态）
用项目路径下的phantomjs_fetcher.js启动：phantomjs phantomjs_fetcher.js [port]
安装tornado依赖（使用了tornado的httpclient模块）

```
from tornado_fetcher import Fetcher

# 创建一个爬虫
>>> fetcher=Fetcher(
    user_agent='phantomjs', # 模拟浏览器的User-Agent
    phantomjs_proxy='http://localhost:12306', # phantomjs的地址
    poolsize=10, # 最大的httpclient数量
    async=False # 同步还是异步
    )
# 开始连接Phantomjs的代理，可以渲染JS！
>>> fetcher.phantomjs_fetch(url)
# 渲染成功后执行额外的JS脚本（注意用function包起来！）
>>> fetcher.phantomjs_fetch(url, js_script='function(){setTimeout("window.scrollTo(0,100000)}", 1000)')

```

## 时间仓促，功能和代码都比较简陋，以后有时间再改进。喜欢的在github上给个star。感谢！
