---
layout: post
title:  "Classless Addressing"
image: ''
date:   2017-03-22 13:15:00
comments: true
description: 'Definition of classful addressing with its advantages and dis advantages'
series: TCP/IP
---

<h1 style="color:grey"> Classless Addressing</h1>
In classless addressing <label style="color:red">variable-length blocks</label> are assigned that belong to no class. In this architecture, the entire address space (2^32 addresses) is divided into block of different sizes. 

## Rules:
1. The number of addresses in a block must be power of 2.
2. The first address must be evenly divisible by the number of addresses.
	eg. if the block contains 4 addresses. The first address must be divisible by 4. If a block contains 16 addresses, the first address must be divisible by 16.

<h4 style="text-align:center"> First address + number of addresses = Last address</h4>

Problem 1: which of the following can be the beginning address of a block that contains 16 addresses?
	a. 205.16.37.32  b. 190.16.42.44  c. 17.17.33.80  d. 123.45.24.52
	
When calculating the IP Address, first three bytes will multiply 256, 256^2, 256^3, which is always divisible by 16. So the 4th byte determines whether the IP address is divisible by 16.

We can infer that if the size of the block is no larger than 256, which is 2,4,8,16,32,64,128 and 256, we can always determine whether the first follows the rules above via looking at the 4th byte. (计算IP Address的大小时，前3个字节分别要乘上256，256^2，256^3，肯定都能被16整除，第4个字节是32也能被16整除，所以4个字节加起来可以被整除。
	所以，只要一个block包含少于256个地址，并且符合第一条规则，那么只需要看最后一个字节是否能被整除。)

十进制:Decimal System 
二进制:Binary System

We can regard the IP address as a base-256 counting System
(可以把IP视为256进制，每个Byte是一个数字。)

There are two methods that find the last address in the block:
- In the first method we add the number of addresses in the block to the first address.
- In the 2nd method we add the first address to the complement of the mask.

In <label style="color:red">classful addressing</label> when an address is given we can first find the class of the address. We can then apply the mask to find the beginning address and the range of addresses.

In <label style="color:red">classless addressing</label> when an address is given the block the address belongs to can not be found unless we have the mask. The 'N' after the slash defines the number of bits that are the same in every addresses in the block.

> How can we tell if the address is classful or classless??

<h4 style="text-align:center"> Classful addressing is a special case of classless addressing.</h4>

<h1 style="color:grey"> CIDR notation </h1>

As we know, in classless addressing, we need both the IP address and the Mask to determine a specific hop in the network.
We use CIDR notation to represent the IP address and the mask of the address.

<img src="/assets/img/having-fun/CIDRnotation.jpg">

If n=20, it means that 20 leftmost bits are identical in each addresses with 12 bits not the same.

The prefix is another name for the common part of the address range(similar to Net Id)
The suffix is the varying part.(similar to Host id) The suffix length is 32-n.
We can "AND" the mask and the address to find the first address.

In CIDR notation, the block grounded is defined by the first and the prefix length. For instance, the block is defined as 190.87.140.200/29.

In fixed-length subnetting, the number of subnets is a power of 2.

We can have subnetting with classless addressing. If the number of subnets is 'x'. The number of extra is in the prefix of 'log2(x)'.

We can dividing the subnet based on the number of subnets, which will influence the prefix, and addresses in each subnets, which will influence the suffix.

<h4 style="text-align:center">Remember First Address & Last Address is special</h4>

E.g.: Diving 11 blocks in the given network address 12.24.74.0/24
	00000000/26:0
	01000000/26:64
	10000000/27:128
	10100000/27:160
	11000000/28:192
	11010000/28:208
	11100000/28:224
	11110000/30:240
	11110100/30:244
	11111000/30:248
	11111100/30:252


