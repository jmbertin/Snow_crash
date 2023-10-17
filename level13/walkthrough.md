##### 1 - Analyze the binary
``./level13``
>UID 1000 started us but we we expect 4242

``strings level13``
>UID %d started us but we we expect %d
>boe]!ai0FB@.:|L6l@A?>qJ}I
>your token is %s

----

##### 2 - Downloading and decompiling binary

Downloading
``scp -P 4242 level13@10.11.249.58:/home/user/level13/level13 ~/Desktop/``

Decompiling with ghidra and found main who calls ft_des function (see original_code.c)

----

##### 3 - Reverse ingeneering the code to make a decoder
We clean the code :
- add includes
- modify var types
- remove if condition in main

We compile the program (see exploit.c)
``gcc main.c``

----

##### 4 - Getting the flag

``./a.out``
>your token is **2A31L79asukciNyi8uppkEuSx**
