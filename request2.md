# 需求文档

上一个情况修复完成后，执行
```shell
sudo ./daemon/owl -i wlp0s20f3 -c 44                                                                           ─╯
              .oOXWMMMMWXOx:
         .oOOOx:'''''''''''':OOOx:
      oXOo'      ........      ':OXx.
           .oOOO''''''''''OOOo.
        oXOo'                'oOO:
             :oOOOOXXXXOOOOo:.
          oXO:'            ':OXo
              .:xOXXXXXXOx:.
          .xXMMMMMMMMMMMMMMMMXx.
  'XWWWWWWMMMMMMMMMMMMMMMMMMMMMMWWWWWWX'
    oWMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMWo
     OMMMMMMWWMMMMMMMMMMMMMMWWWMMMMMO
    OMMWx'      'xWMMMMWx'      'oXMMO
   :MW:            oMMx            'WM:
   XM'    .xOOo.    :o     .xOOo.    WX
   WX    :MMMMMX          :MMMMMX    xW
   XW    'WMMMMX   .xx.   'WMMMWX    XX
   'Wx    'xWMx'   OMMO    'xWMx'   xM'
    'XX:           'XX'           :XX'
      'xXOx:..................:xXWx'
         'xXMMMMMMMMMMMMMMMMMMWO'

            Open Wireless Link

            https://owlink.org

20:13:53 ERROR: Error while receiving via netlink: Operation not supported
20:13:53 WARN : Active monitor mode not supported, falling back to plain monitor mode
20:13:53 INFO : Set plain monitor mode successfully
20:13:53 INFO : WLAN device: wlp0s20f3 (addr f4:ce:23:c9:32:95)
20:13:53 INFO : Host device: awdl0
20:13:53 WARN : Cannot inject frames on channel 44 [5220 MHz], try setting a regulatory domain (`iw reg set <CC>`) or using a different channel (6, 49, or 149)
20:14:19 ERROR: unable to inject packet (send: Resource temporarily unavailable)
20:14:19 ERROR: unable to inject packet (send: Resource temporarily unavailable)
20:14:19 ERROR: unable to inject packet (send: Resource temporarily unavailable)
20:14:19 ERROR: unable to inject packet (send: Resource temporarily unavailable)
20:14:19 ERROR: unable to inject packet (send: Resource temporarily unavailable)
20:14:19 ERROR: unable to inject packet (send: Resource temporarily unavailable)
```

查看ip a
```shell
ip a        
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: wlp0s20f3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether f4:ce:23:c9:32:95 brd ff:ff:ff:ff:ff:ff
    inet 10.9.239.29/24 brd 10.9.239.255 scope global dynamic noprefixroute wlp0s20f3
       valid_lft 1795sec preferred_lft 1795sec
    inet6 fe80::d2e0:f1e6:b823:a4ae/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: awdl0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1450 qdisc fq_codel state UNKNOWN group default qlen 1000
    link/ether f4:ce:23:c9:32:95 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::f6ce:23ff:fec9:3295/64 scope link 
       valid_lft forever preferred_lft forever

```

确实有了awdl接口

目前的报错问题如何解决？