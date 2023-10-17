##### 1 - Analyze directory content
``ls -l``

>total 12
>-rwsr-sr-x 1 flag09 level09 7640 Mar  5  2016 level09
>----r--r-- 1 flag09 level09   26 Mar  5  2016 token

##### 2 - Analyze token content
``cat token``
> f4kmm6p|=�p�n��DB�Du{��

##### 3 - Analyze binarie behaviour
./level09 aaaaa
> abcde

We see that each char of the input is incremented by his index

##### 4 - Reverse the process in the token file
``scp -P 4242 level09@10.11.249.59:/home/user/level09/token ~/Desktop/``

``chmod 777 token``

We make a python script to reverse the process :
````
import ctypes

def reverse_process(token):
    result = ""
    for i in range(len(token)):
        result += chr(ctypes.c_ubyte(token[i] - i).value)
    return result

with open("token", "rb") as file:
    token = file.read()

print(reverse_process(token))
````
``python3 decrypt.py``
>f3iji1ju5yuevaus41q1afiuqñ

We remove last char (\n !)

Token is : **f3iji1ju5yuevaus41q1afiuq**

-----

##### 5 - Getting the flag
``su flag09``
``password: f3iji1ju5yuevaus41q1afiuq``

``getflag``
> **s5cAJpM8ev6XHw998pRWG728z**
