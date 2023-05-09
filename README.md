# sshrm
A tool to remove quickly all keys belonging to the specified host from a known_hosts file.

Usage : 
`sshrm hostname`
`sshrm ip_address`
`sshrm username@hostname`
`sshrm user@ip_address`

---------------------------------

When you use a lot of virtual machines, sometime when you connect with ssh, you have this WARNING : 

`@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the ED25519 key sent by the remote host is
SHA256:+wSlnErVnmqzZZ6agLhhHHMLZjUaAyHeVhQCvtapolE.
Please contact your system administrator.
Add correct host key in /home/adrien/.ssh/known_hosts to get rid of this message.
Offending ED25519 key in /home/adrien/.ssh/known_hosts:100
Host key for 192.168.21.111 has changed and you have requested strict checking.
Host key verification failed.`

The command i use is :

`ssh root@192.168.21.111` 

To quickly remove all the keys for 192.168.21.111 hostname, only add "rm" to ssh command : 

`ssh root@192.168.21.111` 

Automatically, all entries removed : 

`# Host 192.168.21.111 found: line 100
/home/adrien/.ssh/known_hosts updated.
Original contents retained as /home/adrien/.ssh/known_hosts.old`

You can invoke again the ssh command removing "rm" suffix to ssh 

`ssh root@192.168.21.111` 

And you can connect after accepting new fingerprint : 

`The authenticity of host '192.168.21.111 (192.168.21.111)' can't be established.
ED25519 key fingerprint is SHA256:+wSlnErVnmqzZZ6agLhhHHMLZjUaAyHeVhQCvtapolE.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '192.168.21.111' (ED25519) to the list of known hosts.
root@192.168.21.111's password: `
