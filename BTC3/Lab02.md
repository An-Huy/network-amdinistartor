
NOTE: 
+ dấu >: mode user 
+ dấu #: mode 
+ config: config mode

1. đặt tên cho router
```
Router>en
Router#conf t
Router(config)#hostname R-UTC
```

2. Add IP cho port
```
R-UTC(config)#int f0/0
R-UTC(config-if)#ip add 55.14.92.1 255.255.255.0
R-UTC(config-if)#ipv6 add 24BB:7A1::1/64
R-UTC(config-if)#no shut
R-UTC(config-if)#
R-UTC(config-if)#int f0/1
R-UTC(config-if)#ip add 212.96.8.253 255.255.255.252
R-UTC(config-if)#ipv6 add 2FF2:B52::1/64
R-UTC(config-if)#
R-UTC(config-if)#no shut
```

```
R-UTC2(config)#int f0/0
R-UTC2(config-if)#ip add 74.54.33.129 255.255.255.128
R-UTC2(config-if)#ipv6 add 2DCF:4A6::1/64
R-UTC2(config-if)#no shut
R-UTC2(config-if)#
R-UTC2(config-if)#int f0/1
R-UTC2(config-if)#ip add 212.96.8.254 255.255.255.252
R-UTC2(config-if)#ipv6 add 2FF2:B52::2/64
R-UTC2(config-if)#no shut
```

enable ipv6 unicat-routing and cef
```
R-UTC(config)#ipv6 unicast-routing 
R-UTC(config)#ipv6 cef
```

Lưu ý: Save config
```
R-UTC#wr
```
3. Add ip cho Server và PC như trong hình
4. Add route như trong hướng dẫn 