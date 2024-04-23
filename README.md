# Session Hijacking with MITM Attack

## Description
This project focuses on understanding and demonstrating the vulnerability of session security in network communications. A Man-in-the-Middle-Attack refers to a scenrio where an attacker intercepts communication between two parties, such as user and a server, without their knowledge. By exploiting this vulnerability the attacker can eavesdrop on the communication, manipulate data, or even impersonate one of the parties.

Session hijacking refers to an attack in which an attacker seizes control of a valid TCP communication session between two computers. This project aims to provide insights into how session hijacking occurs by implementing MITM attack in a controlled environment.

## Process
Let's open the Linux terminal in root user with the following command 
```
sudo su
```
Now we need to enable IP forwarding on the linux machine. This can be done with the following command
```
echo 1 > /proc/sys/net/ipv4/ip_forward
```
Here's what each part of the command does:
1. `echo 1` this command simple outputs the number 1. But as we also spcified the redirection operator `>` it redirects the output of the command on the left-hand side to the file specified on its right hand side.
2. `/proc/sys/net/ipv4/ip_forward` is the path to a file in the linux filesystem. And `/proc` is a virtual filesystem that provides access to kernel data structures and system information. Within `/proc/sys/net/ipv4/` there is a file called `ip_forward`. And this file controls whether IP forwarding is enabled or disabled.
3. This command sets the value of `/proc/sys/net/ipv4/ip_forward` to 1, which enables IP forwarding. IP forwarding is a feature that allows a linux system to act as a router by forwarding packets between network interfaces. When IP forwarding is enabled, the system will process incoming packets and decide whether to forward them to another network interface based on its routing table.
