##### 1 - Searching clue

No clue found.

----

##### 2 - Attacking the getflag binary

Downloading the binary
``scp -P 4242 level14@10.11.249.59:/bin/getflag ~/Desktop/``

Decompile with ghidra and find this in main

>else if (_Var6 == 0xbc5) {
>	pcVar4 = (char *)ft_des("boe]!ai0FB@.:|L6l@A?>qJ}I");
>	fputs(pcVar4,__stream);
>}
>else {
>	if (_Var6 != 0xbc6) goto LAB_08048e06;
>	pcVar4 = (char *)ft_des("g <t61:|4_|!@IF.-62FH&G~DCK/Ekrvvdwz?v|");
>	fputs(pcVar4,__stream);
>}

We understand that all the token are inside the main, in their coded form. On the **Else if** we see that is the coded form of previous level, so we take the next one ``g <t61:|4_|!@IF.-62FH&G~DCK/Ekrvvdwz?v|`` and try to uncode it with our previous script.

----

##### 3 - Getting the flag
``./gcc main.c``
``./a.out``
>your token is 7QiHafiNa3HVozsaXkawuYrTstxbpABHD8CPnHJ

``su flag14``
Password: ``7QiHafiNa3HVozsaXkawuYrTstxbpABHD8CPnHJ``
>Congratulation. Type getflag to get the key and send it to me the owner of this livecd :)

``getflag``
>Check flag.Here is your token : **7QiHafiNa3HVozsaXkawuYrTstxbpABHD8CPnHJ**
