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
 1. I've use virtualbox [official site to download virtualbox](https://www.virtualbox.org/wiki/Linux_Downloads)
 2. create a GNU/linux machine with *debian 10* oprating system virtual machine and clone a instance from that and name the first machine **internet** and 
other machine **no-internet**   


  set the **internet** two network interfaces  
1.Host-only Adapter    
![image](https://github.com/ArmanTaheriGhaleTaki/diginext-devops-bootcamp/assets/88885103/a4e0b87c-c90b-4977-b45f-0eecce946d29)       
2.Bridged Adapter   
![image](https://github.com/ArmanTaheriGhaleTaki/diginext-devops-bootcamp/assets/88885103/316afb0b-f4ae-4c18-8eac-7e1b7abab3fd)    

  set the **no-internet** a Host-only Adapter network interface
  ![image](https://github.com/ArmanTaheriGhaleTaki/diginext-devops-bootcamp/assets/88885103/4fdc251e-e200-47d0-90fc-2a9639b38cfa)   
  

