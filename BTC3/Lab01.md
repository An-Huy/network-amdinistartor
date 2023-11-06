
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
R-UTC(config-if)#ip add 99.100.31.1 255.255.255.0
R-UTC(config-if)#ipv6 add A1B3:4E1C::1/64
R-UTC(config-if)#no shut

R-UTC(config-if)#int f0/1
R-UTC(config-if)#ip add 32.154.23.129 255.255.255.128
R-UTC(config-if)#ipv6 add 2DCF:A001::1/64
R-UTC(config-if)#no shut
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