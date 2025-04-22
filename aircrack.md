**Aim:** To study Wi-Fi network security tool **Aircrack-ng** tool in KALI LINUX.

**Learning Objective:** To understand Wi-Fi network security tool Aircrack-ng in KALI LINUX.

**Theory:**
Aircrack-ng is a tool that comes pre-installed in Kali Linux and is used for Wi-Fi network security and hacking. Aircrack is an **all in one packet sniffer** , **WEP** and **WPA/WPA2 cracker** , **analysing tool** and **a hash capturing tool**. It is a tool used for Wi-Fi hacking. It helps in capturing the package and reading the hashes out of them and even cracking those hashes by various attacks like dictionary attacks. It supports almost all the latest wireless interfaces. It mainly focuses on 4 areas:

- **Monitoring** : Captures cap, packet, or hash files.
- **Attacking** : Performs deauthentication or creates fake access points
- **Testing** : Checking the wifi cards or driver capabilities
- **Cracking** : Various security standards like WEP or WPA PSK.

**Working with aircrack-ng**
To list all network interfaces.

```shell
sudo airmon-ng
```

This command will return all the network interfaces available or connected to the system.

**1.** Stopping the desired network interface.

```shell
sudo airmon-ng stop wlan0mon
```

To stop a network interface, enter the above command and replace “ **wlan0** ” with the desired network interface.

**2.** Starting a network interface at a specific channel.

```shell
sudo airmon-ng start wlan0 10
```

To start a network interface at a specific channel enter the above command and replace “ **wlan0** ” with the desired network interface and 10 with the desired channel name.

**3.** Collecting authentication handshake

```shell
sudo airodump-ng -c 10 --bssid 00:15:5D:9C: 44:00 -w psk wlan
```

To collect the authentication handshake, enter the above command in terminal and replace “ **wlan0** ” with
the desired network interface and 10 with the desired channel name and _bssid_ with the _bssid_ of the wifi.

**4.** Cracking the captured handshake file by means of a wordlist

```shell
sudo aircrack-ng -w wordlist psk\*.cap
```

**To run a brute force attack and to crack the password enter the above command in the terminal and replace “wordlist” with the desired wordlist to be used and “wpa.cap” with the desired handshake filename.**

**5.** To get the help section of the tool

```shell
sudo aircrack-ng –help
```

**6.** To display the # of CPUs and SIMD support

```shell
sudo aircrack-ng –u
```

**Learning Outcome:** Performed Wi-Fi network security tool Aircrack-ng in KALI LINUX.
