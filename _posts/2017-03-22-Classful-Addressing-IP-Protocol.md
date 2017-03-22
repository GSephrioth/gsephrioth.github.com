---
layout: post
title:  "Classful Addressing"
image: ''
date:   2017-03-22 13:15:00
comments: true
description: 'Definition of classful addressing with its advantages and dis advantages'
series: TCP/IP
---

<h1 style="color:grey">IP Address(CLassful Addressing)</h1>

<h4 style="text-align:center">An IP address is a 32-bit address.</h4>

The identifier used in the network layer of the implement model to identify each device connected to the Internet is called <label style="color:red">Internet address</label> or <label style="color:red">IP address </label>

In <label style="color:red">Binary notation</label> the IP address is displayed as 32-bits. 

In <label style="color:red">Dotted-decimal notation</label> Internet addresses are written in decimal form with a dot separating the Bytes.

In classful addressing the address space is divided into five classes: A, B, C, D, and E.

<img src="/assets/img/having-fun/IPaddress.jpg">

When the address is given in dotted decimal notation, then we need to look at the first byte to determine the class of the address.

Addresses in A, B, and C are for <label style="color:red">universal communication</label> from one source to one destination. Addresses on class D are for <label style="color:red"> multicast communication </label>, from one source to a group of destination. Addresses in class E are <label style="color:red">reserved </label> for future use.

An IP addresses in classes A, B and C is divided into <label style="color:red">Net-id </label>and <label style="color:red"> Host ID </label>

* Class A: 1 Byte defines Net-id and 3 Bytes defines Host ID.
* Class B: 2 Byte defines Net-id and 2 Bytes defines Host ID.
* Class C: 3 Byte defines Net-id and 1 Bytes defines Host ID.

* <b>Class A</b> is divided into 128 blocks with each block having a different Net-id, and 2^24 unique IP addresses. The first covers address from <label style="color:red">0.0.0.0 to 0.255.255.255</label>, the 2nd block from <label style="color:red">1.0.0.0 to 1.255.255.255</label>, etc. Class A addresses were designed for large organization with a large number of hosts or routers attached to their network, Or it will be wasted.

* <b>Class B</b> is divided into (191-127)*256=16384 blocks with each block having a different Net-id, and 2^16 unique IP addresses. The first covers address from <label style="color:red">128.0.0.0 to 128.0.255.255</label> with Net-id <label style="color:red">128.0</label>, the Last block from <label style="color:red">191.255.0.0 to 191.255.255.255</label>, with Net-id <label style="color:red">191.255</label> , etc. Class A addresses were designed for mid-size organization with Tens of thousands of hosts or routers.

* <b>Class C</b> is divided into 2097152 blocks with each block having a different Net-id, and 2^8 unique IP addresses. The first covers address from <label style="color:red">192.0.0.0 to 192.0.0.255</label>, the last block from <label style="color:red">223.255.255.0 to 223.255.255.255</label>, etc. Class A addresses were designed for large organization with a large number of hosts or routers attached to their network, Or it will be wasted.

<h4 style="text-align:center">Net-id is part of Network Address</h4>

'Net-id + All 0s' is the Network address.

The network address is an address that defines the network itself. It can not be assigned to a host or router.

A network address has several properties :

* A Host-id byte are 0s.
* A network address defines the network to the rest of the internet.
* The network address is the first address in the block.

The first address in the block defines the <label style="color:red">Network Address</label> these address is used by routers the outside the organization to route the packets destined to this network.

IP addresses are designed with <label style="color:red">two levels of hierarchy(层次结构)</label>. A position of a 32-bit address indicates the network(Net id) and a portion indicates the host(Host id) in the network.

Often the network needs to be divided into several <label style="color:red">subnetworks(subnets)</label>, with each subnetwork having its own <label style="color:red">subnetwork address</label>. When we divide a network into several subnets we have three levels of hierarchy.

Adding subnetwork creates an intermediate level of hierarchy in the IP address. Now we have 3 levels: site, subnet, host.

The router outside the organization route the packet based on the network address. The router inside the organization routes the packet based on the subnet address.

<h1 style="color:grey"> The mask </h1>

The 32-bit number called the mask is the routing key.

A default mask is a 32-bit binary number that gives the network address when "anded" with an address in the block

<h4 style="text-align:center"> "anded" means logical "AND" </h4>

<img src="/assets/img/having-fun/IPmask.jpg">

## how does default mask works
1. The router looks at the first byte of the address to find the class. It is class B
2. The default mask for class B is 255.255.0.0. The router ANDs this mask with the address to get 190.240.0.0.
3. The router looks in its routing table to find out how to route the packet to this destination. 

<h1 style="color:grey">Subnetwork</h1>

## how does subnet mask works
The number of is in a subnet mask '1's more than the number of '1's in the corresponding default mask.

<img src="/assets/img/having-fun/subnetMask.jpg">

1. The router must know the mask. We assume it is /19.
2. The router applies the mask to the address, 190.240.33.91.  The subnet address is 190.240.32.0. 19 = 8+8+3 => Mask is 255.255.224.0.
3. The router looks in its routing table find out how to route the packet to this destination.

The default mask creates the network address.
The subnet mask creates the subnet address.

Today we use only use contiguous masks(连续的掩码) (a run of 1s followed by a run of 0s)

Given the IP address we can find the subnet address the same way we found the network address. We applying the mask to the address.

The number of subnetworks can be found by counting the extra 1s that are added to the default mask to make the subnet mask. For example, if the number of extra 1s is 3, the number of subnets is 2^3 = 8.

two addresses in each subnet are added to the list of special addresses. The first address in each subnet is the subnet address the last address is reserved for broadcast in side the subnet.

<h1 style="color:grey">Supernetwork</h1>

Using the first byte to decide the class of the network, make the mask shorter to create a supernetwork mask.

The notation 195.14.192.3/24 shows a class C address, with a default mask. But the address 195.14.192.3/21 shows a supernetwork of class C address, with the mask 255.255.248.0, which combined by 2^3 = 8 class C networks.
<img src="/assets/img/having-fun/supernetMask.jpg">

<h1 style="color:grey">multi-homed devices</h1>

<img src="/assets/img/having-fun/multihomedDevices.jpg">

A computer that is connected to different networks is called a multi-homed computer and will have more than one address.

An Internet address defines the connection of a device to a specific network. The movement of a computer from one network to another means that its IP address must be changed.

<h1 style="color:grey">Special Addresses</h1>

<img src="/assets/img/having-fun/specialAddresses.jpg">

* Network Address: The first address in the block defines the network address. (Net-id: Specific + Host-id: All 0s)

* Direct Broadcast Address: If the Host-id is all 1s, the address is called a direct broadcast address. It is used by a router to send a packet to all hosts in this specific network. All hosts will accept a packet having this type of destination address. (Net-id: Specific + Host-id: All 1s)

* Limited Broadcast Address: An address with all 1s for the Net-id and the Host id defines a broadcast address in the current network. A host that wants to send a message to every others. Host can use this address as a destination address in an IP packet. A router will block a packet having this type of address to confirm the broadcasting to the local network. (Net-id and Host-id: All 1s)

* Loopback Address: The IP address with the first byte 127 is used for the loopback address, which is an address to test software on a machine. When this address is used, the packet never leaves the machine. It simply returns to the protocol software. (Net-id and Host-id: 127.X.Y.Z)

* Private Address: Addresses in the private space are not allocated to any specific organization and anyone may use these addresses without approval from a regional Internet registry. However, IP packets addressed from them cannot be transmitted through the public Internet, and so if such a private network needs to connect to the Internet, it must do so via a network address translator (NAT) gateway, or a proxy server.

<img src="/assets/img/having-fun/privateAddresses.jpg">

Communication in the Internet can be achieved using <label style="color:red">Unicast, Multicast or Broadcast</label> addresses. No Broadcasting is allowed at the global Internet.
* Unicast: one to one
* Multicast: one to many
* Broadcast: one to all
