# Bypass GFW—SSH

# 0. 


# 1. vps安装install V2ray/Trojan/Xray…

> 生成原生Ip原理: （开启IPV6）
vps 安装v2ray，  设置代理绕过GFW。 此时只有ipv4地址，cloudflare 可以检测到你不在美国，

套Warp，此时会生成ipv6地址，即所谓的原生ip。warp也是cf开发的，cloudflare会检测你在美国。即用魔法打败魔法。
> 

[new-pac/自建ssr服务器教程.md at master · Alvin9999/new-pac · GitHub](https://github.com/Alvin9999/new-pac/blob/master/%E8%87%AA%E5%BB%BAssr%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%95%99%E7%A8%8B.md)

ssh登陆vps，输入

```bash
source <(curl -sL https://multi.netlify.app/v2ray.sh) --zh

```

After install v2ray  successfully!

1. input: v2ray, 

修改传输方式5  ：websocket 
修改TLS ：开启， 获取SSL证书
输入提前解析好的域名： vv02.garyhou.top

到这一步，ipv4解锁


导入vmess地址到代理客户端,   每次调整代理配置，重启v2ray客户端

- shadowsocket手动配置
    
    请输入要设置的ShadowsocksR账号 密码
    (默认: [doub.io](http://doub.io/)):root
    
    ——————————————————————————————
    密码 : root
    ——————————————————————————————
    
    nano /root/.acme.sh/vv11.garryhou.xyz_ecc/vv11.garryhou.xyz.cer
    
    nano /root/.acme.sh/vv11.garryhou.xyz_ecc/vv11.garryhou.xyz.key
    
    ShadowsocksR账号 配置信息：
    
    I  P	    : 45.77.211.156
    端口	    : 2333
    密码	    : root
    加密	    : aes-256-cfb
    协议	    : auth_sha1_v4_compatible
    混淆	    : plain
    设备数限制 : 0(无限)
    单线程限速 : 0 KB/S
    端口总限速 : 0 KB/S
    SS    链接 : ss://YWVzLTI1Ni1jZmI6cm9vdEA0NS43Ny4yMTEuMTU2OjIzMzM
    SS  二维码 : http://doub.pw/qr/qr.php?text=ss://YWVzLTI1Ni1jZmI6cm9vdEA0NS43Ny4yMTEuMTU2OjIzMzM
    SSR   链接 : ssr://NDUuNzcuMjExLjE1NjoyMzMzOmF1dGhfc2hhMV92NDphZXMtMjU2LWNmYjpwbGFpbjpjbTl2ZEE
    SSR 二维码 : http://doub.pw/qr/qr.php?text=ssr://NDUuNzcuMjExLjE1NjoyMzMzOmF1dGhfc2hhMV92NDphZXMtMjU2LWNmYjpwbGFpbjpjbTl2ZEE
    
    提示:
    在浏览器中，打开二维码链接，就可以看到二维码图片。
    协议和混淆后面的[ _compatible ]，指的是 兼容原版协议/混淆。
    

记得打开端口防火墙



# 2.Install Warp 解锁IPv6

ssh登陆，输入

```bash
wget -N https://gitlab.com/fscarmen/warp/-/raw/main/menu.sh && bash menu.sh d
一直默认

 11. WARP 解锁 Netflix 等流媒体专业一键(支持多平台、多方式和 TG 通知) 
 Choose: 11


```

 输入telegram bot token, 
 ### how to apply?
 open your telegram,   search ' BotFather'
 input'/help/'  '/newbot/
 format like this:6549138388:AAG9kzWJBxe2lCv9jnFyu0wraoA8JmgqK0A

### input your account userid, how to find ?
  search'userinfobot'   input'/start/
  you will get you id like: 5816788429


 warp b (升级内核、开启BBR及DD)
 warp a (更换账户为 Free，WARP+ 或 Teams)
 warp p (刷WARP+流量)
 warp v (同步脚本至最新版本)
 warp r (WARP Linux Client 开关)
 warp 4/6 (WARP IPv4/IPv6 单栈)
 warp d (WARP 双栈)
 warp c (安装 WARP Linux Client，开启 Socks5 代理模式)
 warp l (安装 WARP Linux Client，开启 WARP 模式)
 warp i (更换支持 Netflix 的IP)
 warp e (安装 Iptables + dnsmasq + ipset 解决方案)
 warp w (安装 WireProxy 解决方案)
 warp y (WireProxy socks5 开关)
 warp s 4/6/d (优先级: IPv4 / IPv6 / VPS default)
```

# 3.  安装BBR流量加速

```bash
wget -N --no-check-certificate "https://raw.githubusercontent.com/chiakge/Linux-NetSpeed/master/tcp.sh"

chmod +x tcp.sh

./tcp.sh
```

以安装暴力BBR魔改版加速为例，我们先安装对应的内核，输入数字1

内核安装完成后，输入y进行重启，重启才能让内核生效

重启完成后，输入数字6来启动暴力BBR魔改版加速

再次输入 ./tcp.sh  check

 当前状态: 已安装 BBR 加速内核 , BBR启动成功

 请输入数字 [0-11]:

[我用了bbr plus]