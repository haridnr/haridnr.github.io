---
layout: post
title: Big Endian vs Little Endian
---

Data is represented as bits of 0's and 1's on computers and these bits are used to store and manipulate data on computers. Most systems work with chunks of 8 bits called as a byte.

When we say that the int data type needs 4 bytes, this means that 4 * 8 (1-byte) = 32 bits are used to represent that integer number in the system.

For example,

Lets take a number such as 255. 

It's binary representation is as follows - 
00000000 00000000 00000000 11111111

In Hexadecimal form - 
0 0 0 ff

The following program prints how the bytes are stored for the integer 255 on a particular system

{% gist ce08525b0688092dd52b %}

If you are running a little endian machine the output will be ff 0 0 0. This is because the bits are stored in the reverse order. Little endian as in the least signification byte which in this case 'ff' is stored in the most significant byte position.

Whereas on a big endian machine the bytes are stored in the normal way we think of the bytes - 00 00 00 ff.

Intel architectures typically use little endian format while PowerPC and SPARC are examples of machines which use big endian format.

These are some of the situations where the endianess of the system becomes important - 

1. Date transfer over the network - If the bytes from a little endian machine are sent over the network to a big endian machine and the receiving machine reads the data without reversing the bytes then this could cause problems. Eg - 255 (ff 0 0 0) on a little endian system will be read as 1044480 (ff 0 0 0) on a big endian system.

To avoid such problems data is send over the network always in big endian format. In C there are set of functions which enable conversion from the system byte order to the network order [htons](http://linux.die.net/man/3/htons).


2. Assemby code - The byte ordering of Various integers in assembly code could be represented based on the endianess of the system which generates the code.




