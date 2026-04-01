# 需求文档

这是一个owl工具，核心功能是在Linux上模拟实现了awdl协议，但是目前在Ubuntu22.04执行出现如下问题

iw dev输出
```shell
phy#0
	Unnamed/non-netdev interface
		wdev 0x2
		addr f4:ce:23:c9:32:96
		type P2P-device
	Interface wlp0s20f3
		ifindex 2
		wdev 0x1
		addr f4:ce:23:c9:32:95
		ssid Tencent-GuestWiFi
		type managed
		channel 44 (5220 MHz), width: 40 MHz, center1: 5230 MHz
		txpower 22.00 dBm
		multicast TXQ:
			qsz-byt	qsz-pkt	flows	drops	marks	overlmt	hashcol	tx-bytes	tx-packets
			0	0	0	0	0	0	0	0		0

```


于是我便执行命令
```shell
sudo owl -i wlp0s20f3 -c 44 
```

输出如下
```shell
20:01:00 ERROR: Error while receiving via netlink: Operation not supported
20:01:00 ERROR: Could not put device in monitor mode: wlp0s20f3
20:01:00 ERROR: could not initialize core
```

分析问题，并解决问题，使得旧的owl可以是配现在的Linux版本