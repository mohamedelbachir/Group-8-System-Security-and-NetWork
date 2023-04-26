# Group-8-System-Security-and-NetWork
Group 8 for course System Security and Network
## Table of contents
- [Wifi Attack](#wifi-attack)


## Requirements
- Os : **Kali Lunix** (for this pratice) , **Ubuntu** , other linux distribution

## Wifi Attack
📢JUST FOR EDUCATIONNAL PURPOSE📢
>**Prerequisites**<br/>
>We need to have *hostpot* (wifi name (**ssid**)) available in this case we just  put sample password (**1234567890**)


To start open your terminal and type the command bellow : 
```console
ifconfig
```

 or
 
 ```console
iwconfig
```
 
 > Those commands allow you to list all network interface available and to apply the attack we focus on *wlan0* interface (wireless network)
<img src="https://user-images.githubusercontent.com/76158313/234447153-edad29ae-5958-478a-a2ac-58d94f861164.png" width=480px/>

 ```console
sudo airmon-ng check kill
```
