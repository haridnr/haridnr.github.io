---
layout: page
title: Raymonds Token Based Algorithm
---

Raymonds Token Based Algorithm using SCTP protocol

About
-----

The Raymonds token based algorithm is used to enable synchronization of critical section requests in a distributed environment. In this algorithm, at any given moment of time only a single node in the distributed environment can have the token. And a process executing on each of these nodes cannot enter into their respective critical sections unless they have access to the token.

Implementation
--------------

The application executing on each of the nodes consists of 2 modules. The application module and system module, 

Application Module      System Module
Enter-CS ->
			Request token ->
			Once token arrives <-
			Give token to process <-
Execute CS
Leave CS 
Return token to system->

Multiple processes running on a set of nodes would generate critical section requests to it's underlying system module based on an exponential distribution. If the system module does not have the token, it would send messages to other nodes which have the token and retrieve the token so that, it's respective processes CS request can be satisfied.

The system module communicates with the rest of the nodes by using a spanning tree of the nodes in the network. SCTP protocol was used for communication in Java language.





