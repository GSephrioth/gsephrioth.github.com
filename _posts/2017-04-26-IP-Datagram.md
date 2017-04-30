---
layout: post
title:  "IP Datagram"
image: ''
date:   2017-04-04 10:00:00
comments: true
description: 'Description on IP datagram'
series: Notes
---
<h1 style="color:grey">The IP datagram</h1>

IP is an unreliable and connectionless datagram protocol. The best effort delivery service IP does is its......

Packets in the IP layer are called datagrams. A datagram is a variable length packet consisting of two parts: Header and Data. 

The Header is 20 to 60 bytes in length and contains information essential to routing and delivery.

<img src="/assets/img/TCP-IP/Figure8.2.png">

<h4 style="text-align:center">IP header format</h4>
- Version
This 4-bit field defines the version of the IP protocol

- Header Length(HLEN): 
This 4-bit field defines the total length of the datagram header in 4 byte times.

```
	length of header = header length * 4
	must be between 5-15
```

- Differentiated services(DS): 

<img src="/assets/img/TCP-IP/Figure8.3.png">
<img src="/assets/img/TCP-IP/Table8.1.png">

Service type:
The first 3-bits are called precedence bits. 
The 4-bits are called TOS bits. 
The last bit is not used.

2. Precedence bits: 
It is a 3-bit subfield ranging from 000 to 111. The precedence defines the priority of the datagram in issues such as congestion.

3. Type of service (TOS) bits: 
We have 5 different types of service resolved by application programs.

4. Interactive activities
- Activities requiring immediate attention.
- Activities requiring immediate response need min delay.
- Activities that send bulk data requiring max throughput.(吞吐量)
- Management activities need max reliability.
- Background activities need min cost.

5. Differentiated services
In this interpretation, the first 6-bits make up the codepoint subfield and the last 2-bits are not used.
The codepoint subfield can be used into different ways.
When the 3 right bits are 0s, The 3 left most bits are interpreted the same as the precedence bits in the service type interpretation. The precedence defines 8-level priority of the datagram
When the right most bits are not all 0s, the 6-bits define services based on the priority assignment by the internet or local authority.

- Total length: 
This is a 16-bit field that defines the total length(Header + data) of the IP datagram in bytes. Since the field is 16 bits, the total length of the IP datagram is limited to 2^16 =  65536 bytes, of which 20-40 bytes are the header add the rest is data.

- Time to live(TTL): 
Today this field is mostly used to control the max number of hops visited by the datagram. When a source host sends the datagram, it stores a number in this field each router that processes the datagram decreases this number by one. If this value is zero the router discards the datagram.

- Protocol: 
This 8-bit field defines the high level protocol that uses the services of the IP layer.

<img src="/assets/img/TCP-IP/Table8.4.png">

- Header checksum: 
This used for error detection

- Source IP address

- Destination IP address

- Options: 
This field can be used to request special treatment for the packet. It consists of a series of entries, each responding to a requested option.

1. The Record route option traces the route of a packet.
2. The Timestamp option: Each router stores the time at which it routed the packet.
3. The strict route option allows the sender to specify the router to be taken by storing a sequence of IP address in the options field. ? what if one router is down? 
4. The loose source router option does not provide the exact route but does provide at list of routers through which the packet must travel. ? how to make sure?

- Maximum Transfer Unit(MTU)
Maximum length of data that can be encapsulated in a frame.
Each data unit layer protocol has maximum size of the data field. when a datagram is encapsulated in a frame, the total size of the datagram must be less than this maximum size.

The maximum length of the IP datagram is 65535 bytes. Transmission is very efficient if we use a protocol with an MTU of this size. However, for other physical networks, we must divide the datagram to make it possible to pass through these networks, which is called fragmentation.

> Fragmentation

- Identification
This 16-bits field identifies a datagram originating from the source to grantee uniqueness. The IP protocol uses a counter to label the datagrams the counter is initialized to a positive number, when the IP protocol sends a datagram it copies the current value of the counter to the identification field.

<img src="/assets/img/TCP-IP/Figure8.7.png">
- Flags
This is a 3-bit field. So the first bit is reserved.

The 2nd bit is called 'don`t fragment' bit, 1 means not allowed to fragment, if it can not be passed through any physical network, it will be discarded.

The 3rd bit is called 'more fragment' bit, 1 means the datagram is not the last fragment, there are more fragments after this one. 0 means the datagram is the last fragment or only fragment.

<img src="/assets/img/TCP-IP/Figure8.8.png">
- Fragmentation offset

This 13-bit field shows the relative position of this Fragment with respect to the whole datagram. It is the offset of the data in the original datagram measured in units of 8 bytes.

<label style="color: red;"> This process hosts or routers that fragment datagram introduce the size of each fragment so that the first byte number is divisible by 8.</label>

The final destination host can reassemble the original datagram from the fragments received using the following strategy:
1. The first fragment has an offset value of 0
2. Divide the length of the first fragment by 8. The second fragment has an offset value equal to that result.
3. Divide the total length of the first and second fragment by 8. The third fragment has an offset equal to that result.
4. COntinue this process.
5. The last fragment has the 'more fragment' bit ( AKA M bit) equal to 0.


First Byte = Offset Value * 8

Last Byte = First byte + Total length - HLEN * 4 - 1

> remember the '-1' of the last byte

