# Session Hijacking with MITM Attack

## Description
This project focuses on understanding and demonstrating the vulnerability of session security in network communications. A Man-in-the-Middle-Attack refers to a scenrio where an attacker intercepts communication between two parties, such as user and a server, without their knowledge. By exploiting this vulnerability the attacker can eavesdrop on the communication, manipulate data, or even impersonate one of the parties.

Session hijacking refers to an attack in which an attacker seizes control of a valid TCP communication session between two computers. This project aims to provide insights into how session hijacking occurs by implementing MITM attack in a controlled environment.

## Process
Let's open the Linux terminal in root user with the following command. It is important to be in the root user, because the next command will not be executed if you aren't. Even if you execute it with a `sudo` in the beginning, it will say permission denied.
```
sudo su
```
****
Now we need to enable IP forwarding on the linux machine. This can be done with the following command
```
echo 1 > /proc/sys/net/ipv4/ip_forward
```
Here's what each part of the command does:
1. `echo 1` this command simple outputs the number 1. But as we also spcified the redirection operator `>` it redirects the output of the command on the left-hand side to the file specified on its right hand side.
2. `/proc/sys/net/ipv4/ip_forward` is the path to a file in the linux filesystem. And `/proc` is a virtual filesystem that provides access to kernel data structures and system information. Within `/proc/sys/net/ipv4/` there is a file called `ip_forward`. And this file controls whether IP forwarding is enabled or disabled.
3. This command sets the value of `/proc/sys/net/ipv4/ip_forward` to 1, which enables IP forwarding. IP forwarding is a feature that allows a linux system to act as a router by forwarding packets between network interfaces. When IP forwarding is enabled, the system will process incoming packets and decide whether to forward them to another network interface based on its routing table.
****
To know the router or gateway IP address execute this command.
```
route -n
```
Now we need to get the IP address of the target. Since this is project is for educational purposes, I will be using my own device. So the attacker system is my Kali Linux (running on VM) and the target system is my secondary device (running windows). Both are connected to the same network. So this becomes a LAN level attack.
****
Now we use a technique called ARP spoofing. This technique is used to intercept network traffic by impersonating another device on the network. Execute the following command for this.
```
arpspoof -t <routerip> <targetip>
```
Here in place of `<routerip` and `<targetip>` you need to add the real IP address. Once you have your target's IP address we can proceed with the next step.
> **Note** Let's see what this command does
> 1. `arpspoof` it is the command-line utility for ARP spoofing.
> 2. `-t` specifies a target or victim IP address you want to intercept or manipulate.

<div align="center">
  
![ezgif com-video-to-gif-converter](https://github.com/JaySeeram/Session_Hijacking_with_MITM_attack/assets/162781155/7a923c7d-9a4c-45d6-b8f1-f8ca49649e46)

</div>
