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

Next<br/>

This command stops network managers then kill interfering processes left <br/>
**Note:** It is very important to kill the network managers before putting a card in monitor mode!

```console
sudo airmon-ng check kill
```
<img src="https://user-images.githubusercontent.com/76158313/234449446-9f423ee1-9aa5-4c76-98e7-22fc6bfd1433.png" width=480px/>

Now we start *monitoring mode* on our card :
```console
$ sudo airmon-ng start wlan0
```
<img src="https://user-images.githubusercontent.com/76158313/234451442-6df2b332-5c57-4671-a124-d4fde763a6f6.png" width=480px/>

Next<br/>

```console
sudo aireplay-ng -9 wlan0mon
```

So we have to use the ``wlan0mon`` interface to see all the access points around us and what is being done in these different access points.We see " **injection is working** " and we have the access points that are displayed. We are interested in the access point "TECNO SPARK 6 Air" and you see that each access point operates in a specific channel. For us it is ``channel 13``.

<img src="https://user-images.githubusercontent.com/76158313/234453484-04e230eb-e75b-4e12-bec0-84a2d5c67c05.png" width=480px/>

Next <br/>
```console
sudo aireplay-ng -9 wlan0mon
sudo airodump-ng -c 13 --bssid 76:C7:DA:D8:1A:AD -w group8 wlan0mon
```
Here we will copy the ``bssid`` which is the ``Mac address`` of our access point and we will execute the airodum-ng command with the precise parameters as follows: in the terminal, it will generate traffic at the access point location  

While the packets are going through, when someone is going to connect. And we'll see that it will have change, we'll see a **handshake** that confirms that there is a client that wanted to connect to our access point.

Finally,<br/>
```console
sudo aircrack-ng -w /usr/share/metasploit-framework/data/wordlists/password.lst group8-01.cap
```
And now we will use the ``aircrack`` command that allows us to crack the password that relies on a file that contains a set of predefined passwords to retrieve the password entered. After validating, we see the password appear in the dictionnary ``password`` which is not very **huge**.


