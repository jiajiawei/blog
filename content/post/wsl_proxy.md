---
title: "pwsh和wsl中使用代理上网"
date: 2022-09-14T23:50:34+08:00
draft: false
---

工作原因偶尔科学上网,但是命令行需要专门配置下才能走代理

我用的 **v2rayN**, 默认端口号用掉4个: 10808,10809,10810,10811

## **pwsh** 中使用代理

```pwsh
$env:HTTP_PROXY = "http://localhost:10809"
$env:HTTPS_PROXY = "http://localhost:10809"
```

可以参照 [pwsh_profile](../pwsh_profile) 配置为命令, 使用时直接 `proxy` 开启, 不需要的话就 `noproxy` 关闭


## **wsl** 中使用代理

因为 **wsl** 有自己的网卡,所以使用的是后面两个端口号, 另外需要开启配置:

![](../wsl_proxy/v2rayN_config.png)

1. `vi ~/.zshrc`
2. 粘贴代码:
```zsh
export hostip=$(cat /etc/resolv.conf |grep -oP '(?<=nameserver\ ).*')
alias proxy='export https_proxy="http://${hostip}:10811";export http_proxy="http://${hostip}:10811";export all_proxy="socks5://${hostip}:10810";'
alias noproxy='export https_proxy=""; export http_proxy=""; unset all_proxy'
```
3. `source ~/.zshrc`
4. 跟 **pwsh** 中使用一样, `proxy` 开启, `noproxy` 关闭