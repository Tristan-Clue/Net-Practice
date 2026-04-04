*This project has been created as part of the 42 curriculum by mjoon-yu.*

# Net-Practice
The Basics of Networking - The 42 Way

To note:
- Computer Networking
- IP Addresses
- Routers
- Switches
- Gateways
- TCP/IP Addressing
- Configurating small-scale networks
- Subnet Mask
- Default Gateway

Requirements:

## Description
- Project presentation
- Goals
- Brief Overview
> Mentions of network concepts studied, such as: TCP/IP Addressing, subnet mask,
default gateway, routers and switches, OSI layers, etc.

## Instructions
- Compilations/Installations/Execution
> How to run the training interface, export configuration, submission requirements

## Resource
- References to topic (Video, documentation, etc...)
- How AI was used and specify which tasks and part was used

> Submission details must include the 10 exported configuration files for each level

### Network
A group of connected devices that can communicate with each other. Devices can include and not limited to: Desktop, Phones, Printers, Switches, Routers, etc...<br>
A well known network would be the **Local Area Network (LAN)**, which is a network of devices that are connected in a local area, like your home or a cafe. Above that we have something called a **Wide Area Network (WAN)**, which is a network of many LANs, which covers large distances.<br>
These networks are connected in many ways ranging fromshort distance (Bluetooth, Ethernet), medium (Fiber Optics, Microwave), to far (Leased Lines, Satellite links).<br>

### Types of Network
Wired (Server):
>
Wired (Internet):
>
Wireless (Wi-Fi):
>
Wireless (Satellite):
>

### Network Devices
- Switch: 
> A hardware device that connects multiple devices together. It uses MAC addressing to identify where the data packets should go to.
- Router: 
> A device that routes traffic between networks, like your home network to the Internet.

### OSI Model
A conceptual model that divides network communication and interoperability into 7 abstract layers. It provides a standardized model that enables different applications, computer systems and networks to communicate.<br>
The modern Internet doesn't strictly follow the OSI Model anymore (ditched for a simpler Internet protocol suite), but it is still used as reference for troubleshooting network problems.

> For example, when someone says, "It's a layer 3 issue.", it would mean there's a problem like a network configuration. Or maybe a layer 1 issue, which would mean the physical layer like maybe the cable is loose or the switch broke.

They layers are ordered in descending order by how the data travels:
> 7. Application layer: SMTP, FTP, Telnet
> 6. Presentation layer: Format Data, Encryption
> 5. Session layer: Start & Stop Sessions
> 4. Transport layer: TCP, UDP, Port Numbers
> 3. Network layer: IP Address, Routers
> 2. Data Link layer: MAC Address, Switches
> 1. Physical layer: Cable, Network Interface Cards, Hubs


Nowadays, people use a more simpler Internet protocol suite called:
### TCP/IP
The Transmission Control Protocol/Internet Protocol model, a more practical model that is being used to this day. It has 5 layers instead of 7:
> 1. Application Layer: SMTP, FTP, HTTP
> 2. Transport Layer: TCP, IDP -> Segment
> 3. Network Layer: IP, Routers -> Packet
> 4. Data Link Layer: Ethernet, Switches -> Frame
> 5. Hardware Layer: Cables, Nic

Information is added by each layer as it goes down the model, before it gets sent to where it needs to go according to the headers that the layers provide. This is called encapsulation.<br>
TCP is a reliable when it comes to sending and receiving data, as it creates a stable and reliable connection when it transfer data. Which makes it possible to recover half loaded websites or corrupted documents. TCP does through acknowledgements, sequencing, and checksums.<br>
It uses something called three-way handshake, where the sender sends a signal (SYN) for synchronization. The receiver will then reply that signal with an acknowledgement (SYN-ACK). Finally, the sender sends their own acknowledgement (ACK) to the receiver, completing the open TCP connection. This is also used to close the TCP connection.<br>
Next, sequencing, TCP assigns number to segments so that the receiver can identify and organize the segments in order it's meant to be in.<br>
Checksum is used to make sure the packet is transmitted fully without problems through matching the checksum. If it's mismatched, the receiver would discard of the packet.<br>

### UDP
User Datagram Protocol, an unreliable way to transfer data compared to TCP. It doesn't have any error handling, sequencing, or reliability like TCP.<br>
Why UDP? Although UDP doesn't have the reliability as TCP, it is low latency, making it fast, which is needed for live, real-time connection, like gaming, streaming, voice calls, and so on.<br>

### Port Numbers
Port number is used to identify a specific process or service on a device, distinguishing traffic on a single IP address. It routes the data to the appropriate application in the device. It is part of the Transport Layer.<br>
Common port numbers would be SSH (22), HTTP (80), HTTPS (443), etc...<br>
These usually come right after the IP address separated by a colon, eg. 121.353.x.12:80<br>
> 0-1023 are well know port numbers
> 1024-49151 are registered port numbers
> 49152-65535 are dynamically assign port numbers, which are randomly generated for the local services on that address.

### What is an IP Address?
**I**nternet **P**rotocol Address 
is a unique numeric label assigned to each device connected to a computer network that uses the Internet Protocol for communication. It serves two main functions: identification and location addressing.<br>
There are two IP versions, IPV4 and IPV6:
> IPV4 addresses uses 32-bit format composed of 4 octets, values ranging from 0-255, separated by dots. Example below:
>> `192.168.0.1`
> IPV6 addresses uses a 128-bit format that are designed to support up to trillions of new devices, as IPV4 is slowly running out.

But for now we will be dealing with IPV4.

##### Subnet
Along with the IP Address, there is another set of 4 octets, which are called subnet masks. They are used to identify the network portion and the host portion of each IP Addresses.<br>
Subnet masks works by turning on the bits of the mask to indicate the network portion of the IP Address, for example:

> IP Address: 192.168.2.4
> Subnet Mask: 255.255.255.0
>> First three octets are network portion as the subnet mask bits are turned on

How it works is that the network portion indicates whether devices shares the same network. The host portion indicates the device in the network.<br>
So if there's two sets of IP Addresses that has the same network portion, would indicate they share the same network.<br><br>

> IPV4 are split to 5 classes as below:
>> Class A - For networks with large number of hosts
>> Public IP Range: 1.0.0.0 to 126.255.255.255
>> Private IP Range: 10.0.0.0 to 10.255.255.255
>> Special IP Range: 127.0.0.1 to 127.255.255.255
>> Subnet Mask: 255.0.0.0 (8 bits)
>> Number of Networks: 126
>> Number of Hosts per network: 16,777,214
> Class A IP address range are typically used byb ISP (Internet Service Providers) and large corporations.

>> Class B - For medium to large sized networks
>> Public IP Range: 128.0.0.0 to 191.255.255.255
>> Private IP Range: 172.16.0.0 to 172.31.255.255
>> Subnet Mask: 255.255.0.0 (16 bits)
>> Number of Networks: 16,382
>> Number of Hosts per Network: 65,534
> Class B IP Address range are used by universities and medium-sized businesses

>> Class C - Used in small local are networks (LANs)
>> Public IP Range: 192.0.0.0 to 223.255.255.255
>> Private IP Range: 192.168.0.0 to 192.168.255.255
>> Subnet Mask: 255.255.255.0 (24 bits)
>> Number of Networks: 2,097,150
>> Number of Hosts per Network: 254
> Class C IP Address range are used by small businesses and home networks<br>

> There is also Class D and E, which are used for multicasting and research purposes respectively.<br>

Private IP Addresses are addresses that are used within the local network. These addresses are non-routable on the internet, and are assigned by the network router to your particular device. Since these IPs are only used within the same network, the addresses can be reused then hence, not needing to exhaust public IPs.

##### Binary
Just a quick rundown of what binary is about:<br>
> A base-2 numbering system which only uses two digits, 0 and 1, to represent data and instructions.

In IPV4, binary is used to indicate the IP address, as well as the network and the host portion through the subnet mask.<br>
So let's say a subnet mask of

> 255.0.0.0

from this, we know that the first 8 bits are turned on, which means the first octet of the IP address is the network portion.<br>

Alternatively, instead of using subnet mask, a CIDR notation can also be used to indicate the number of 1s in the mask, like /24 for 255.255.255.0 or /16 for 255.255.0.0.<br>
This is also useful to understand when we get to subnetting, which is the process of splitting a network to smaller logical networks called subnets.<br><br>
Subnets allow for devices to communicate efficiently, improving network performance, security, and manageability. It allows for isolated networks within a network, so that data will be contained and not shared to every single device in the network.<br>
Take a company as an example, it's given a single IP Address which is shared to hundreds of devices in the company, or even to different locations. Subnetting allows them to divide the network into smaller networks, allowing each department to have their separate subnet and containing communications within that subnet. Any inter-department traffic will be routed through a router.<br><br>

#### Why subnetting?
- It allocates the amount of IP needed for each department, no wastage of IP
- Traffic remains within each subnet, improving performance, no excessive broadcast
- Departments are logically isolated, improving security

##### How-to subnet?
To subnet, we manipulate the host portion of the address, network portion will remain as is. Let's say we divide a Class C network (192.168.5.0) into two parts:
- Subnet-1 will contain IP addresses 192.168.5.0 to 192.168.5.127 (In binary, the host part is from 0000 0000 to 0111 1111).
- Subnet-2 will contain IP addresses 192.168.5.128 to 192.168.5.255 (In binary, the post part is from 1000 0000 to 1111 1111)
> If you noticed, you'll realize that the leftmost bit of the host part is the indication of the subnet. Since that's the bit that will indicate the subnet id. The number of subnet is equivalent to 2 to the power of bits used for subnetting<br> i.e 2 bits used == 4 subnets, etc...
> Also one thing to note when it comes to subnetting, each subnets are required to waste 2 IP addresses, which is the first and the last allocated address (Subnet-1 192.168.5.0 and 192.168.5.127), these are used as the network ID and the broadcast address for the subnet.

#### Subnet Cheat Sheet
| Subnet Mask     | No. of Hosts | No. of Addr   | CIDR         | Subnet Mask     | No. of Hosts | No. of Addr   | CIDR         |
| :-------------: | :----------: | :-----------: | :----------: | :-------------: | :----------: | :-----------: | :----------: |
| 255.255.255.252 | 2            | 4             | /30          | 255.252.0.0     | 131,070      | 131,072       | /15          |
| 255.255.255.248 | 6            | 8             | /29          | 255.248.0.0     | 262,142      | 262,144       | /14          |
| 255.255.255.240 | 14           | 16            | /28          | 255.240.0.0     | 524,286      | 524,288       | /13          |
| 255.255.255.224 | 30           | 32            | /27          | 255.224.0.0     | 1,048,574    | 1,048,576     | /12          |
| 255.255.255.192 | 62           | 64            | /26          | 255.192.0.0     | 2,097,150    | 2,097,152     | /11          |
| 255.255.255.128 | 126          | 128           | /25          | 255.128.0.0     | 4,194,302    | 4,194,304     | /10          |
| 255.255.255.0   | 254          | 256           | /24          | 255.0.0.0       | 8,388,606    | 8,388,608     | /9           |
| 255.255.254.0   | 510          | 512           | /23          | 254.0.0.0       | 8,388,606    | 16,777,216    | /8           |
| 255.255.252.0   | 1,022        | 1,024         | /22          | 252.0.0.0       | 8,388,606    | 33,554,432    | /7           |
| 255.255.248.0   | 2,046        | 2,048         | /21          | 250.0.0.0       | 8,388,606    | 67,108,864    | /6           |
| 255.255.240.0   | 4,094        | 4,096         | /20          | 248.0.0.0       | 8,388,606    | 134,217,728   | /5           |
| 255.255.224.0   | 8,190        | 8,192         | /19          | 240.0.0.0       | 8,388,606    | 268,435,456   | /4           |
| 255.255.192.0   | 16,382       | 16,384        | /18          | 224.0.0.0       | 8,388,606    | 536,870,912   | /3           |
| 255.255.128.0   | 32,766       | 32,768        | /17          | 192.0.0.0       | 8,388,606    | 1,073,741,824 | /2           |
| 255.255.0.0     | 65,534       | 65,536        | /16          | 128.0.0.0       | 8,388,606    | 2,147,483,648 | /1           |
|                 |              |               |              | 0.0.0.0         | 8,388,606    | 4,294,967,296 | /0           |

#### Gateways
Gateway is a network device that connects two different networks. They manage the traffic for the data packets sent, acting as a "gate" to determine where the packets are routed to and so on.<br>
A default gateway can be described as a route for when the data packet's routing information is not found within the routing table for the device, i.e, the host not knowing where to send the data packets.<br>
The data packets would then be sent to the default gateway of that device.

#### Example of configuring a network
For a simple setup, let's say a small company that has 2 departments, IT and Account.
<br>
<blockquote>
    To separate the networks, we would need to split them into 2 subnets.<br>
    So given an IP of 178.245.12.0 (Class C network), we create a subnet mask of `255.255.255.128 or /25`.
    Giving 178.245.12.0 - 128.245.12.127 and 178.245.12.128 - 178.245.12.255
    Now, any devices that are connected to the network will be isolate to its own subnet. Data within the subnet will also be contained within the subnet and not share to the other subnet.
    <br>
    Now let's say we want to send information from one subnet to the other, we can't just send it since it's considered a "different" network.<br>
    To do this, we would need to setup a routing table on the host (the user device in this context), to route the data to it's respective subnet.
    > Sending data from 178.245.12.3 to 178.245.12.178
    > We set up a route on the host for data sent to 178.245.12.128/25, it sends to the router.
    > This way, when information from the host is sent to said network, it will be sent to the router as that's the designated route for it.
    >> Alternatively, if we want any data that is sent out to just send to the router, we can just use 0.0.0.0/0 or `default`. Which says "If unsure where destination, send to this route".
    >> This is needed to set up for both sides if we want to both sides to communicate with each other.
</blockquote>

Solutions for Net Practice Levels:
<details>
<summary>Level 1:</summary>
<img src="/src/levels/level-01.png">
- Just 2 sets of devices connected to each other. So configure the addresses to be in the same network for each pair.
</details>
<details>
<summary>Level 2:</summary>
<img src="/src/levels/level-02.png">
- Here we are introduced to **Subnet Mask**, so instead of just configuring the IP addresses to the same network, we must also make sure that the address is within the same subnet.
- So based of the given subnet mask, we just have to calculate which subnet it is in and configure the IP address of the respective device.
</details>
<details>
<summary>Level 3:</summary>
<img src="/src/levels/level-03.png">
</details>
<details>
<summary>Level 4:</summary>
<img src="/src/levels/level-04.png">
</details>
<details>
<summary>Level 5:</summary>
<img src="/src/levels/level-05.png">
</details>
<details>
<summary>Level 6:</summary>
<img src="/src/levels/level-06.png">
</details>
<details>
<summary>Level 7:</summary>
<img src="/src/levels/level-07.png">
</details>
<details>
<summary>Level 8:</summary>
<img src="/src/levels/level-08.png">
</details>
<details>
<summary>Level 9:</summary>
<img src="/src/levels/level-09.png">
</details>
<details>
<summary>Level 10:</summary>
<img src="/src/levels/level-10.png">
</details>
