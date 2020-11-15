# SS Server Setup

## <font color=blue>关于加密方法的背景资料</font>
### 重点：
- 推荐加密方式：aes-256-gcm，chacha20-ietf-poly1305（排名分先后）
- 推荐的混淆obfs：http，tls（排名分先后）
- SSR反而有更明显流量特征
### 链接：
- 当前网络环境，SS及SSR该怎么配置协议混淆才是最佳
https://shadowsocksrr.blogspot.com/2019/04/ssssr.html
- Shadowsocks是如何被检测和封锁的，兼谈ss配置策略
https://pincong.rocks/article/12173

## <font color=blue>搭建云</font>
- AWS：薅羊毛，Amazon AWS免费使用一年，详细教程说明
https://www.luofan.net/post/105.html
- Google Cloud：薅羊毛，Google Cloud免费使用一年以及详细教程说明
https://www.luofan.net/post/112.html
- Vultr：薅羊毛Vultr，比Google云亚马逊云都要优惠实在
https://www.luofan.net/post/1150.html

## <font color=blue>部署SS/SSR</font>
- 采用docker部署c语言版ss（维护较好）
https://hub.docker.com/r/teddysun/shadowsocks-libev/
- 采用docker部署ssr
https://hub.docker.com/r/teddysun/shadowsocks-r