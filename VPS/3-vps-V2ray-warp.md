# Bypass GFW—SSH

# 0. 

```bash
#dependency broken
sudo apt --fix-broken install
sudo apt update
sudo apt upgrade
sudo apt install wireguard-tools
```

# 1. vps安装install V2ray/Trojan/Xray…

> ***原理: vps 安装v2ray，  设置代理绕过GFW。 此时只有ipv4地址，cloudflare 可以检测到你不在美国，所以需要套Warp，此时会生成ipv6地址，即所谓的原生ip。warp也是cf开发的，cloudflare会检测你在美国。即用魔法打败魔法。***
> 

[new-pac/自建ssr服务器教程.md at master · Alvin9999/new-pac · GitHub](https://github.com/Alvin9999/new-pac/blob/master/%E8%87%AA%E5%BB%BAssr%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%95%99%E7%A8%8B.md)

ssh登陆vps，输入

```bash
source <(curl -sL https://multi.netlify.app/v2ray.sh) --zh

# if you's using superuser not root user, use this:
sudo bash -c "$(curl -sL https://multi.netlify.app/v2ray.sh)"


#八合一脚本
wget -P /root -N --no-check-certificate "https://raw.githubusercontent.com/mack-a/v2ray-agent/master/install.sh" && chmod 700 /root/install.sh && /root/install.sh
```

install v2ray  successfully!

1. input: v2ray,  choose 3change setting 
2.  transportation  

选择传输方式5      ：websocket 

输入提前解析好的域名： vv02.garyhou.top


在开启输入v2ray 选择TLS 6 开启

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

centos

```bash
sudo firewall-cmd --zone=public --add-port=27302/tcp --permanent
#This command adds a permanent rule to allow incoming TCP traffic on port 1935.
sudo firewall-cmd --zone=public --add-port=22/tcp --add-port=443/tcp --permanent
#Reload the firewall configuration again to apply the changes:
sudo firewall-cmd --zone=public --add-port=3000/tcp --add-port=8000/tcp --permanent --ipv6
sudo firewall-cmd --reload
#Verify that port 1935 is open by running the following command:

sudo firewall-cmd --zone=public --list-ports
```

# 2.Install Warp 解锁IPv6

[fscarmen/warp: WARP one-click script. Add an IPv4, IPv6 or dual-stack CloudFlare WARP network interface and Socks5 proxy for VPS. 一键脚本 (github.com)](https://github.com/fscarmen/warp)

ssh登陆，输入

```bash
wget -N https://gitlab.com/fscarmen/warp/-/raw/main/menu.sh && bash menu.sh d

```

```bash
SERVER6-VPS88:~# bash warp-go.sh 

 Language:
 1.English (default) 
 2.简体中文 

 Choose: 1
 Checking VPS infomation... 
 This project is designed to add WARP network interface for VPS, using warp-go core, using various interfaces of CloudFlare-WARP, integrated wireguard-go, can completely replace WGCF. Save Hong Kong, Toronto and other VPS, can also get WARP IP. Thanks again @CoiaPrant and his team. Project address: https://gitlab.com/ProjectWARP/warp-go/-/tree/master/ 
======================================================================================================================

 Version: 1.1.4
 New features: 1. Docking the warp-go official account pool api; 2. Change non-global from ipv4 only to dualstacks; 3. Fix the bug that the native IPv6 cannot login when using dualstacks; 4. Update the Best-enpoint app; 5. Change ip api
 System infomation:
         Operating System: Ubuntu 20.04.6 LTS
         Kernel: 5.4.0-29-generic
         Architecture: amd64v3
         Virtualization: lxc 
         IPv4: 194.146.26.238  Turkey  Kaan Girgin 
         IPv6: 2a0f:b701:856:ca71::1  Turkey  Kaan Girgin 
         WARP network interface is not turned on 

======================================================================================================================

1. 为 原生双栈 添加 WARP IPv4 网络接口 (bash menu.sh 4) 
 2.  为 原生双栈 添加 WARP IPv6 网络接口 (bash menu.sh 6) 
 3.  为 原生双栈 添加 WARP 双栈网络接口 (bash menu.sh d) 
 4.  打开 WARP (warp o) 
 5.  安装 CloudFlare Client 并设置为 Proxy 模式 (bash menu.sh c) 
 6.  更换支持 Netflix 的 IP (warp i) 
 7.  永久关闭 WARP 网络接口，并删除 WARP、 Linux Client 和 WireProxy (warp u) 
 8.  刷 WARP+ 流量 (warp p) 
 9.  升级内核、安装BBR、DD脚本 (warp b) 
 10. 同步最新版本 (warp v) 
 11. WARP 解锁 Netflix 等流媒体专业一键(支持多平台、多方式和 TG 通知) 
 12. 安装 iptable + dnsmasq + ipset，让 WARP IPv4 only 接管流媒体流量 (不适用于 IPv6 only VPS) (bash menu.sh e) 
 13. 安装 wireproxy，让 WARP 在本地创建一个 socks5 代理 (bash menu.sh w) 
 14. 安装 CloudFlare Client 并设置为 WARP 模式 (bash menu.sh l)

 Choose: 11

 Is there a WARP+ or Teams account?
 1. WARP+
 2. Teams
 3. Use free account (default) 

 Choose: 

 Step 1/3: Install dependencies... 

 Maximum 5 attempts to registe WARP free account... 
 Try 1 

 Step 2/3: Install warp-go... 

 Step 3/3: Best MTU and Endpoint found. 

已成功获取 WARP 网络 

==============================================================

 IPv4: 45.77.211.156 美国  The Constant Company 
 IPv6: 2a09:bac5:cad3:154b::21f:1a 美国  Cloudflare Warp 
 恭喜！WARP 已开启，总耗时:30秒， 脚本当天运行次数:8552，累计运行次数:5267166 
 IPv6 优先 

==============================================================

 再次运行用 warp [option] [lisence]，如
 
 warp h (帮助菜单）
 warp n (获取 WARP IP)
 warp o (临时warp开关)
 warp u (卸载 WARP 网络接口和 Socks5 Client)
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

[我用了bbr plus]