# backuppc-sandbox

backuppc server(ubuntu)
client(centos)
~~~~

vagrant@lampstack-03:~$ sudo apt-get update && sudo apt-get install backuppc -y
~~~~
~~~~
select the “Local only” option
leave the Sytem mail name as “lampstack-01.local”
Select “apache2” to configure Apache for use with BackupPC
~~~~
~~~~
BackupPC can be managed through its web interface:                                                                                                                            
http://lampstack-01.local/backuppc/

a web user named 'backuppc' with 'AqTDJbpK' as password has been created. You can change this password by running 'htpasswd /etc/backuppc/htpasswd backuppc'.


browse
http://192.168.1.120/backuppc/
~~~~
~~~~
vagrant@lampstack-01:~$ sudo su - backuppc
backuppc@lampstack-01:~$ ssh-keygen

You now have a private and public key on your backup server. You need to transfer the public key to the root user on each client machine you wish to access.
backuppc@lampstack-01:~$ ssh-copy-id root@lampstack-02

~~~~
smoke tests
~~~~
Access the Web Interface
Next, click “Add”. Fill in the client machine’s IP address. For user, add “vagrant”

Configure Transfer Settings
Click on the “Xfer” tab on the top of the page. Under “XferMethod”, select “rsync”.
Under “RsyncShareName”, select the path you would like to back up.

Run a Manual Backup
select you client from the “Hosts” drop-down menu in the upper-left corner.
Click “Start Full Backup” under the “User Actions” section.

backuppc@lampstack-01:~$ ls -l /var/lib/backuppc/pc/lampstack-02/
total 24
drwxr-x--- 3 backuppc backuppc 4096 Feb 17 23:29 0
-rw-r----- 1 backuppc backuppc   82 Feb 17 23:29 backups
-rw-r----- 1 backuppc backuppc   74 Feb 17 23:29 backups.old
-rw-r----- 1 backuppc backuppc    0 Feb 17 23:12 LOCK
-rw-r----- 1 backuppc backuppc  555 Feb 17 23:29 LOG.022020
-rw-r----- 1 backuppc backuppc  465 Feb 17 23:29 XferLOG.0.z
-rw-r----- 1 backuppc backuppc  350 Feb 17 23:21 XferLOG.bad.z.old

backuppc@lampstack-01:~$ ls -l /var/lib/backuppc/pc/lampstack-02/backups
-rw-r----- 1 backuppc backuppc 82 Feb 17 23:29 /var/lib/backuppc/pc/lampstack-02/backups

~~~~
~~~~

BackupPC is a high-performance, enterprise-grade system for backing up Linux, Windows and macOS PCs and laptops to a server's disk
https://github.com/backuppc/backuppc

~~~~
