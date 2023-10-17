##### 1 - We display the content of /etc/passwd
``cat /etc/passwd``
> flag01:42hDRfypTqqnw:3001:3001::/home/flag/flag01:/bin/bash

We see the flag01 is readable but crypted

---

##### 2 - Decrypt the password
Run Kali WM
Paste the content in a new file "passwd"
Use John the Ripper 1.9.0 : ``john passwd``


>Using default input encoding: UTF-8
Loaded 1 password hash (descrypt, traditional crypt(3) [DES 256/256 AVX2])
Will run 2 OpenMP threads
Proceeding with single, rules:Single
Press 'q' or Ctrl-C to abort, almost any other key for status
Almost done: Processing the remaining buffered candidate passwords, if any.
Proceeding with wordlist:/usr/share/john/password.lst
abcdefg          (flag01)
1g 0:00:00:00 DONE 2/3 (2023-05-28 06:10) 12.50g/s 163250p/s 163250c/s 163250C/s 123456..Herman1
Use the "--show" option to display all of the cracked passwords reliably
Session completed.

-----

##### 3 - Getting the flag
``su flag01``
``password: abcdefg``

``getflag``
> Check flag.Here is your token : **f2av5il02puano7naaf6adaaf**
