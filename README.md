# Networking-Fundamentals

When you put in something like DuckDuckgo.com on your computer it will talk to something called a DNS server.That's a domain name system server. The DNS server is responsible for providing the IP address that corresponds to that domain name.the DNS server has a zone file and that zone file tells the computer that DuckDuckgo.com has an IP address of 52.149.246.39

The reason that we need the IP address is because that's the address on the network.Whether it's an internal network or the Internet, computers have an address that's an IP address,and all of the network devices that are on the Internet or your internal network know how to send information and route information to that endpoint.

An IP address is made up of four parts and those parts are separated by dots and they include a network and host ID.


The network ID is a part of the IP address starting from the left that identifies the specific network on which the device is located. On a typical home network, where a device has the IP address 192.168.1.34, the 192.168.1 part of the address will be the network ID. It’s custom to fill in the missing final part with a zero, so we might say that the network ID of the device is 192.168.1.0.

The host ID is the part of the IP address not taken up by the network ID. It identifies a specific device (in the TCP/IP world, we call devices “hosts”) on that network. Continuing our example of the IP address 192.168.1.34, the host ID would be 34—the host’s unique ID on the 192.168.1.0 network.

IPv4 addresses are 32-bit addresses. Each byte, or 8-bit segment of the address, is divided by a period and typically expressed as a number 0–255. Even though these numbers are typically expressed in decimal to aid in human comprehension, each segment is usually referred to as an octet to express the fact that it is a representation of 8 bits.

The lowest value in each octet is a 0, and the highest value is 255.

We can also express this in binary to get a better idea of how the four octets will look. We will separate each 4 bits by a space for readability and replace the dots with dashes:

![ID](/pics/id3.png)

Computers work with the binary format, but we humans find it much easier to work with the decimal format. Still, knowing that the addresses are actually binary numbers will help us understand why some things surrounding IP addresses work the way they do.

We can use this table here
![id](/pics/id5.png)

The bit on the left here is known as the most significant bit, and it has a value of 128.
On the right, we have the least significant bit and that has a value of one.
So if our binary octet was all ones, then we'd have 255 and if it was all zeros, we'd have zero.
So add up 128 plus 64 plus 32 plus 16 plus eight plus four plus two plus one, you'll get 255.

Now if you add up 128 plus 64 you'll get 192.

![ID](/pics/id1.png)

Now, the way that we understand which portions are the network and which are the host is through something called a subnet mask.

On most simple networks (like the ones in homes or small businesses), you’ll see subnet masks like 255.255.255.0, where all four numbers are either 255 or 0. The position of the changes from 255 to 0 indicate the division between the network and host ID. The 255s “mask out” the network ID from the equation.

![ID](/pics/id2.png)

<span style="color:red">Note: The basic subnet masks we’re describing here are known as default subnet masks. Things get more complicated than this on bigger networks. People often use custom subnet masks (where the position of the break between zeros and ones shifts within an octet) to create multiple subnets on the same network.</span>

The idea of subnetting is to take a portion of the host space of an address, and use it as an additional networking specification to divide the address space again.

For instance, a netmask of 255.255.255.0

```
1111 1111 - 1111 1111 - 1111 1111 - 0000 0000
```
This adds up to 24 ones, or /24

Refer to the CIDR Subnet Table to find the CIDR equivalent of a decimal subnet mask.

![subnet](/pics/id4.png)

Now we also have several classes of IP address and the most commonly used are Class A, Class B, and Class C.And then we often subdivide these to get different networks within them.

Here is a translation table that defines the addresses based on their leading bits:

![id](/pics/id6.png)



A quick overview of the OSI model
-------

If you have different pieces of software and hardware they all have to be able to talk to each other and interact to make your network go. So the OSI 7 layer model is seven distinct functions that a network must do.You can think of it as a universal language for networking.

![osi](/image/1.png)

The Physical Layer
-------
It defines how data is transmitted, so in other words, what states represents binary 1's or binary 0's.
Here's an example: RJ45 connectors are used in Ethernet and you would plug an RJ45 connector into the Network Interface Card of a PC, the standards associated with an RJ45 interface are different to other interfaces such as a V35 connection which is used in some WAN implementations.
So we've got things like coaxial cable, fiber cables, wireless connections, Ethernet ports.
The Physical Layer is often the easiest layer to identify because it's focused on physical devices with physical cabling.
Here are some Layer 1 problems to watch out for:
Defunct cables, for example damaged wires or broken connectors
Broken hardware network devices, for example damaged circuits
Stuff being unplugged

If there are issues in Layer 1, anything beyond Layer 1 will not function properly.

The Data Link Layer
-------------
At this layer, we have frames being sent over the network.Framing is a function of the data link layer. It provides a way for a sender to transmit a set of bits that are meaningful to the receiver.
After creating frames, Data link layer adds physical addresses (MAC address) of sender and/or receiver in the header of each frame.
Data link layer provides the mechanism of error control in which it detects and retransmits damaged or lost frames.The data rate must be constant on both sides else the data may get corrupted.

Network Layer
---

The network layer protocols determine which route is suitable from source to destination. This function of network layer is known as **routing**. In order to identify each device on internetwork uniquely, network layer defines an addressing scheme. The sender & receiver’s IP address are placed in the header by network layer. Such an address distinguishes each device uniquely and universally.
Segment in Network layer is referred as Packet.

Transport Layer
------

Transport layer provides services to application layer and takes services from network layer. The data in the transport layer is referred to as Segments. It is responsible for the End to End Delivery of the complete message. The transport layer also provides the acknowledgement of the successful data transmission and re-transmits the data if an error is found.

Transport Layer reads the port number from its header and forwards the Data which it has received to the respective application. It also performs sequencing and reassembling of the segmented data.
Transport layer receives the formatted data from the upper layers, performs Segmentation and also implements Flow & Error control to ensure proper data transmission. It also adds Source and Destination port number in its header and forwards the segmented data to the Network Layer.

Session Layer
-----

This layer is responsible for establishment of connection, maintenance of sessions, authentication and also ensures security.
The functions of the session layer are :

**Session establishment, maintenance and termination**: The layer allows the two processes to establish, use and terminate a connection.

**Synchronization**: This layer allows a process to add checkpoints which are considered as synchronization points into the data. These synchronization point help to identify the error so that the data is re-synchronized properly, and ends of the messages are not cut prematurely and data loss is avoided.

**Dialog Controller** : The session layer allows two systems to start communication with each other in half-duplex or full-duplex.


Presentation Layer
----

Presentation layer is also called the Translation layer.The data from the application layer is extracted here and manipulated as per the required format to transmit over the network.
The functions of the presentation layer are :

**Translation** : For example, ASCII to EBCDIC.

**Encryption/ Decryption** : Data encryption translates the data into another form or code. The encrypted data is known as the cipher text and the decrypted data is known as plain text. A key value is used for encrypting as well as decrypting data.

**Compression**: Reduces the number of bits that need to be transmitted on the network.

Application Layer
----

Application layer interacts with an application program, which is the highest level of OSI model. The application layer is the OSI layer, which is closest to the end-user. It means OSI application layer allows users to interact with other software application.

Application layer interacts with software applications to implement a communicating component. The interpretation of data by the application program is always outside the scope of the OSI model.

Example of the application layer is an application such as file transfer, email, remote login, etc.

Protocols Supported at Various Levels
-----

![level](/image/2.png)

Differences between OSI & TCP/IP
----

![diff](/image/3.png)


I hope that all made sense, I just wanted to touch on the basics I will be be covering IP addressing in several other lessons.
