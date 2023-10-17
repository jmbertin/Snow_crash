##### 1 - Analyze directory content
``ls -l``

>total 12
>----r--r-- 1 flag02 level02 8302 Aug 30  2015 level02.pcap

----

##### 2 - Download the pcap file
From a local terminal :
``-P 4242 level02@10.11.249.59:/home/user/level02/level02.pcap ~/Desktop/``

----

##### 3 - Analyze packets with Wireshark

Packet 43 says :
``password``

We concatenate the fallowing packets PUSH/ACK with size 1 :
``ft_wandr, del, del, del, N, D, R, e, l, del, L, 0, L, cr (carriage return)``

Result :
``ft_waNDReL0L``

----

##### 4 - Getting the flag
``su flag02``
``password: ft_waNDReL0L``

``getflag``
> Check flag.Here is your token : **kooda2puivaav1idi4f57q8iq**
