# task
1. Use any kind of virtualization that you desire.
2. Create a “host-only” network.
3. Create any kind of network which has Internet access through an interface of your host.
4. To test the access to another network:
a. Create a VM with 2 interfaces; one to access internet and another as host-only = Machine A
b. Create another VM with host-only network = Machine B
c. Grant internet access from A to B
5. Create a VPN server or Proxy server:
a. This VPN or proxy server MUST be usable through cli for package managers like apt or yum
## answer 
I've use virtualbox [official site to download virtualbox](https://www.virtualbox.org/wiki/Linux_Downloads)   
create a GNU/linux machine with *debian 10* oprating system virtual machine and clone a instance from that and name the first machine **Machine A** and 
other machine **Machine B**   


  set the **Machine A** two network interfaces  
1.Host-only Adapter    
![image](https://github.com/ArmanTaheriGhaleTaki/diginext-devops-bootcamp/assets/88885103/a4e0b87c-c90b-4977-b45f-0eecce946d29)       
2.Bridged Adapter   
![image](https://github.com/ArmanTaheriGhaleTaki/diginext-devops-bootcamp/assets/88885103/316afb0b-f4ae-4c18-8eac-7e1b7abab3fd)    

  set the **Machine B** a Host-only Adapter network interface
  ![image](https://github.com/ArmanTaheriGhaleTaki/diginext-devops-bootcamp/assets/88885103/4fdc251e-e200-47d0-90fc-2a9639b38cfa)   
 after running the machines every thing is ok but if you run 
 ```
 ip a 
 ``` 
 in **Machine A** you will se the following output    
 ![image](https://github.com/ArmanTaheriGhaleTaki/diginext-devops-bootcamp/assets/88885103/39ebd15f-1b67-4217-ad29-698b1f15de43)   
 enp0s8 interface is down and this interface has internet acsses to be able to up this network interface you have to edit the   
 ``` 
 vim /etc/network/interfaces 
 ```
 and add this config  
 
 ``` # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug enp0s3
iface enp0s3 inet dhcp

allow-hotplug enp0s8 
iface enp0s8 inet dhcp
```

and after that up the internet interface  
``` 
ifup enp0s8
```
![image](https://github.com/ArmanTaheriGhaleTaki/diginext-devops-bootcamp/assets/88885103/6f09bf3f-e78b-424a-a989-6daa7a01c141)

set the machine to be able to route the packets between its interfaces 
```
echo 1 > /proc/sys/net/ipv4/ip_forward
``` 
and with iptables route the incomming packets to the ineternet
```
iptables -t nat -A POSTROUTING -o enp0s8 -j MASQUERADE 
```
in the **Machine B** 
use this command to change the defaulte gateway 
```
ip route add default via 192.168.56.106
```
and it's done
you can verify that by ping the google in **Machine B**
```
ping google.com
```
or 
``` 
curl google.com
```

