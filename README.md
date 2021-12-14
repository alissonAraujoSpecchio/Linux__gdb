# Linux__gdb
How to use gdb to debug core dump files

Install gdb
```
sudo apt install gdb
```

On ubuntu, you can get the core dump file in /var/core, copy it to another folder
```
mkdir ~/c_dump
cp /var/core/core-1639489100-mme-20091.tgz ~/c_dump/
cd ~/c_dump
```

Now uncompress the file, twice, uncompress the tgz format and then the gz format
```
tar -xvzf core-1639489100-mme-20091.tgz
gunzip core-1639489100-mme-20091.gz
```

Then run gdb passing the file extracted
```
$ gdb -c core-1639489100-mme-20091
GNU gdb (Ubuntu 9.2-0ubuntu1~20.04) 9.2
Copyright (C) 2020 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
Type "show copying" and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
    <http://www.gnu.org/software/gdb/documentation/>.

For help, type "help".
Type "apropos word" to search for commands related to "word".
[New LWP 20091]
[New LWP 20092]
[New LWP 20093]
[New LWP 20094]
Core was generated by `/usr/local/bin/mme -c /var/opt/magma/tmp/mme.conf -s /var/opt/magma/tmp/spgw.co'.
Program terminated with signal SIGILL, Illegal instruction.
#0  0x0000557de850531c in ?? ()
[Current thread is 1 (LWP 20091)]
(gdb)
```

Ther type bt to see the back tracing
```
(gdb) bt
#0  0x0000557de850531c in ?? ()
#1  0x000060200000f880 in ?? ()
#2  0x0000557de850525d in ?? ()
#3  0x0000557de916fea0 in ?? ()
#4  0x0000557de84209e1 in ?? ()
#5  0x00007ffe67c17180 in ?? ()
#6  0x00007ffe67c17198 in ?? ()
#7  0x00007ffe67c17180 in ?? ()
#8  0x0000557de8421ded in ?? ()
#9  0x0000000000001a90 in ?? ()
#10 0x0000000000000000 in ?? ()
```

