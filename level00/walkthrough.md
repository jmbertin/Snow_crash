##### 1 - We search for files who belongs to user and group flag00

``find / -user flag00 -group flag00 2>/dev/null``
>/usr/sbin/john
>/rofs/usr/sbin/john

``cat /usr/sbin/john``
> cdiiddwpgswtgt

``cat /rofs/usr/sbin/john``
>cdiiddwpgswtgt

-----

##### 2 - Decrypt the token
Trying to decrypt here https://www.dcode.fr/identification-chiffrement
Interesting results by "chiffre affine" & "disque chiffrant" & "Cesar" (crypt by +15 or -11) !
> nottoohardhere

-----

##### 3 - Getting the flag
``su flag00``
``password: nottoohardhere``

``getflag``
> Check flag.Here is your token : **x24ti5gi3x0ol2eh4esiuxias**

