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

I hope that all made sense, I just wanted to touch on the basics I will be be covering IP addressing in several other lessons.
