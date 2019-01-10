## 如何在VPS中安装v2ray：

一、进入服务器后获得ROOT权限：
  ``` 
  sudo su
  ```
 二、在命令行服务器中使用以下命令来一键安装V2Ray：
```
bash <(curl -s -L https://233blog.com/v2ray.sh)
```   
或者
```
bash <(curl -s -L https://raw.githubusercontent.com/pqguanyinli/v2ray/master/install.sh)
```
如果提示 curl: command not found ，那是因为你的小鸡没装 Curl

ubuntu/debian 系统安装 Curl 方法: ```apt-get update -y && apt-get install curl -y```

centos 系统安装 Curl 方法: ```yum update -y && yum install curl -y```

安装好 curl 之后就能安装脚本了，此脚本可同时安装V2ray和Shadowsocks。

三、V2Ray 管理：

1、V2Ray管理  输入 v2ray

2、快速管理 V2Ray

v2ray info 查看 V2Ray 配置信息

v2ray config 修改 V2Ray 配置

v2ray link 生成 V2Ray 配置文件链接

v2ray infolink 生成 V2Ray 配置信息链接

v2ray qr 生成 V2Ray 配置二维码链接

v2ray ss 修改 Shadowsocks 配置

v2ray ssinfo 查看 Shadowsocks 配置信息

v2ray ssqr 生成 Shadowsocks 配置二维码链接

v2ray status 查看 V2Ray 运行状态

v2ray start 启动 V2Ray

v2ray stop 停止 V2Ray

v2ray restart 重启 V2Ray

v2ray log 查看 V2Ray 运行日志

v2ray update 更新 V2Ray

v2ray update.sh 更新 V2Ray 管理脚本

v2ray uninstall 卸载 V2Ray

3、优化 V2Ray

由于搬瓦工的系统已经启用 BBR 优化加速了，所以不需要再安装 BBR 优化了，如果你还是觉得网络比较慢的话，你可以尝试使用含有 mKCP 的传输协议，这个 mKCP的东东，简单一点说就像 Kcptun 一样加速，并且还能进行伪装 (可选)，但是由于 mKCP 是使用 UDP 协议的，也许运营商会限速得更加厉害，网络变得更加慢。但不管怎么样，你都可以随时尝试一下。

服务器输入 v2ray config 回车，然后选择 修改 V2Ray 传输协议，再接着选择 mKCP 相关的传输协议即可

如果你是使用其他商家的 VPS 并且是按照此教程流程来安装 V2Ray 的话，那么你可以输入 v2ray bbr 回车，然后选择安装 BBR 或者 锐速 来优化 V2Ray

只是还想再啰嗦一下，如果你是使用国际大厂的小鸡鸡，并且是按照此教程流程来安装 V2Ray 的话，请自行在安全组 (防火墙) 开放端口和 UDP 协议 (如果你要使用含
有 mKCP 的传输协议)

4、WebSocket + TLS

实现 WebSocket + TLS 超级无敌简单，前提是要拥有一个能正常解析的域名

服务器输入 v2ray config 回车，然后选择 修改 V2Ray 传输协议，再选择 WebSocket + TLS，即是输入 4，接着输入你的域名，然后我都懒得说了，脚本都那么简单明了，我还瞎BB干嘛…

哈哈…可能有不少人在折腾 V2Ray 实现 WS + TLS 的时候真的是搞到很蛋痛咯，有些人的教程可能说得不是很清楚，或者是直接忽略小白萌新这些亲爱的用户，嗯，小白们好好加油吧，请尽量多学一些基础知识，别总是做伸手党，对于毫无交集的陌生人，人家并没有任何义务要帮你的啊

偷偷跟你说…使用 WebSocket + TLS 会有断流的问题

多说一句，不要被某些人带节奏，WS + TLS 并不是 V2Ray 的神级配置，该墙还是会墙，墙你不需要理由

备注一下啦，这里我没写怎么教你注册域名啦，怎么解析域名啦，如果你真的想要使用 WebSocket + TLS，那就 自己谷歌摸索一下，其实好简单的啦！

我本人并没有在使用 WS + TLS (WebSocket + TLS)，我用 TCP，就是用一键脚本全程回车的那种懒人

5、HTTP/2

实现 HTTP/2 (h2) 也超级无敌简单，和 WebSocket + TLS 一样，也就是只要一个域名就够

服务器输入 v2ray config 回车，然后选择 修改 V2Ray 传输协议，再选择 HTTP/2，即是输入 16，然后………看上面的 WebSocket + TLS 的相关。

备注一下，HTTP/2 相比 WS + TLS (WebSocket + TLS) ，在浏览网页时有一些优势。速度是差不多的啦

6、mKCP

mKCP 这个东东其实就是 KCP 协议，反正你知道是能提速的就行，但是不保证都能提速，还能避免 TCP 阻断，但是也可以会被运营商 Qos.

使用方法：服务器输入 v2ray config 回车，然后选择 修改 V2Ray 传输协议，之后再选择 mKCP 相关的就行

7、搬瓦工 VPS 速度慢

由于本教程使用了 搬瓦工 VPS 做为教程的一部分，那么相信有些新接触 VPS 的同学可能会是按照教程使用了 搬瓦工 VPS 翻墙。

如果你觉得搬瓦工 VPS 速度慢，你可以尝试修改一下端口，服务器输入 v2ray config ，，然后选择 修改 V2Ray 端口 即可，建议使用常见的端口，比如说 443，当然，为了更加安全隐蔽，你可以直接尝试使用 WebSocket + TLS 或者 HTTP/2 协议，但是使用这两个协议对于没有接触过 域名 的同学相对来说会是比较困难的。

搬瓦工 VPS 速度慢的一个主要原因可能会是因为端口限速，如果你已经修改端口为 443，速度还是慢的话，我建议你尝试使用 mKCP 协议。

8、V2Ray 多用户

我写的这个 V2Ray 一键安装脚本目前不支持配置 多用户。也许以后会支持。

说着当然，如果你是大佬，配置 多用户 这种事，不是分分钟的事么？

9、查看配置 / 修改配置 / 端口 / 传输协议…… ？

请看上面的快速管理。。。或者直接输入 v2ray 回车，找到你想要执行的功能。

10、哪个传输协议好？

心中无杂念，用 TCP

ISP 常作怪，用 动态端口

小鸡速度不好，用 mKCP

处子之身，用 WS + TLS
 
四、配置windows客户端：

1，首先下载客户端

https://www.v2ray.com/ui_client/
 
2，上面解压出来是V2RayN.exe文件，这只是客户端，它要打开需要依赖环境。下载v2ray-windows-xx

https://github.com/v2ray/v2ray-core/releases/
 
3，服务器命令行输入 v2ray link 回车，你会得到 V2Ray 客户端配置文件 的链接，在浏览器中打开这个链接，然后点击 Download
 
4，找到服务器ip和alterID等信息，添加到v2ray客户端中.
