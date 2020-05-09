# 使用 Github Actions 在线编译 NanoPi-R2s 固件

内核5.4.38    

# 佛系更新，通常在某s软件更新后

## 温情提醒
刷机请**不要**保留配置，任何因保留配置导致的问题不给予解决！

## 相关链接
Chuck预编译的版本: https://github.com/fanck0605/nanopi_r2s/releases

本项目发布于Action

本项目采用的源码: 

https://github.com/fanck0605/friendlywrt-lean

https://github.com/fanck0605/friendlywrt-kernel

## 说明
* ipv4: 192.168.2.1
* username: root
* password: password

## 特色
* 完美的 Flow Offload 支持，不与 PPPoE 冲突，降低 CPU 负载
* 使用 [coolsnowwolf/lede](https://github.com/coolsnowwolf/lede)，并 merge 了 [friendlyarm/friendlywrt](https://github.com/friendlyarm/friendlywrt)
    - 包含大部分 [coolsnowwolf/lede](https://github.com/coolsnowwolf/lede) 的特性（网络相关的内核功能已经正常啦！）
    - 可以支持 [friendlyarm/friendlywrt](https://github.com/friendlyarm/friendlywrt) 所支持的机型
* 开启了 [Full Cone Nat](https://github.com/Chion82/netfilter-full-cone-nat)，对游戏用户支持更佳
* 支持 IPv6，可以访问最新 IPv6 规范的互联网。
    - 需要关闭 *网络* -> *DHCP/DNS* -> *高级设置* -> *禁止解析 IPv6 DNS 记录*
    
精简到只有s**p

没有互换wan/lan

## 用法
1. Fork 到自己的账号下
2. 进入 Actions 界面，启用 Github Actions(**必须要先启用**)
3. 在 `config_rk3328` 文件中，自定义所需要的软件包
     - 比如需要 `luci-app-samba`， 那么只要在文件中添加一行 `CONFIG_PACKAGE_luci-app-samba=y`
     - 只需添加 `luci-app-samba` 即可，依赖会自动补全；请不要去自己添加任何多余组件，除非你知道自己在做什么。
4. 如需usb 网卡功能，解除 `#cat config_usb-net >> rk3328/configs/config_rk3328` 的注释即可
     - 未经测试不保证能用

## 注意
应用 friendlyelec 修改的 [patch](https://github.com/fanck0605/nanopi_r2s/raw/lean/patches/002-openwrt-apply-friendlywrt.patch)，需要的自行拿走

## 特别感谢（本项目的出现离不开以下项目）

尤其感谢Chuck大佬提供的项目源码，和Nanopi R2S Club群友的帮助，谢谢各位！

* [soffchen/NanoPi-R2S](https://github.com/soffchen/NanoPi-R2S)
* [klever1988/nanopi-openwrt](https://github.com/klever1988/nanopi-openwrt)
* [coolsnowwolf/lede](https://github.com/coolsnowwolf/lede)
* [friendlyarm/friendlywrt](https://github.com/friendlyarm/friendlywrt)

## 参考
* [使用Github的Actions功能在线编译NanoPi-R1S固件（包含H5和H3）](https://totoro.site/index.php/archives/70/)
* [skytotwo/NanoPi-R1S-Build-By-Actions](https://github.com/skytotwo/NanoPi-R1S-Build-By-Actions)
* [yangliu/NanoPi-R2S](https://github.com/yangliu/NanoPi-R2S)
* [maxming2333/NanoPi-R2S](https://github.com/maxming2333/NanoPi-R2S)
