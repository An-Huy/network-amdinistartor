

NOTE: 
+ dấu >: mode user 
+ dấu #: mode 
+ config: config mode

1. đặt tên switch và password 
```
Switch>en
Switch#conf t
Switch(config)#hostname UTC-SW

# notice that name of the switch has changed 
UTC-SW(config)#enable secret UTC@123
```

2. tạo vlan và gán port vào vlan
a. tạo vlan 3,5,7
```
UTC-SW(config)#vlan 3
UTC-SW(config-vlan)#name SinhVienUTC
UTC-SW(config-vlan)#vlan 5
UTC-SW(config-vlan)#name GiaoVienUTC
UTC-SW(config-vlan)#vlan 7
UTC-SW(config-vlan)#name HanhChinhUTC
```
![](https://github.com/An-Huy/network-amdinistartor/blob/main/vlan-trunking/Lab_images/1.png)

b. gán port vào các vlan 3,5,7; chỉnh lại speed và duplex full
```
# vlan 3
UTC-SW(config)#int range f0/3,f0/5,f0/7,f0/9
UTC-SW(config-if-range)#switchport mode access 
UTC-SW(config-if-range)#switchport acc vlan 3
UTC-SW(config-if-range)#speed 100
UTC-SW(config-if-range)#duplex full

# vlan 5
UTC-SW(config-if-range)#int range f0/4,f0/6,f0/8,f0/10
UTC-SW(config-if-range)#switchport mode access
UTC-SW(config-if-range)#switchport access vlan 5
UTC-SW(config-if-range)#speed 100
UTC-SW(config-if-range)#duplex full

# vlan 7
UTC-SW(config-if-range)#int range f0/11-f0/18
UTC-SW(config-if-range)#switchport mode access
UTC-SW(config-if-range)#switchport access vlan 7
UTC-SW(config-if-range)#speed 100
UTC-SW(config-if-range)#duplex full
```

# Kết quả khi show vlan và int status
```
UTC-SW#show vlan
```
![](https://github.com/An-Huy/network-amdinistartor/blob/main/vlan-trunking/Lab_images/2.png)

```
UTC-SW#show int status 
```
![](https://github.com/An-Huy/network-amdinistartor/blob/main/vlan-trunking/Lab_images/3.png)

c. tạo trunking và chỉnh lại speed và duplex full
```
UTC-SW(config-if)#int g0/1
UTC-SW(config-if)#switchport mode trunk
UTC-SW(config-if)#speed 1000
UTC-SW(config-if)#duplex full
```
![](https://github.com/An-Huy/network-amdinistartor/blob/main/vlan-trunking/Lab_images/4.png)

```
UTC-SW(config-if)#int g0/2
UTC-SW(config-if)#switchport mode trunk
UTC-SW(config-if)#switchport trunk allowed vlan 5,7
UTC-SW(config-if)#speed 1000
UTC-SW(config-if)#duplex full
```
![](https://github.com/An-Huy/network-amdinistartor/blob/main/vlan-trunking/Lab_images/5.png)