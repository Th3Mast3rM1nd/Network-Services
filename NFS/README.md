
# NFS (Network File System )

NFS is  a file system mechanism that can store and retrieve data from multiple disks and directories through a shared network and runs on Port 111 (TCP and UDP) and 2049 (TCP and UDP) for the NFS server.

* ***NFS Enumeration***

```shell
nmap -sS -sT -sV -A -p- ip # port 111,2049
```
<pre id="fence-code-2" class="fence-code has-commands">
<code>
111/tcp   open  rpcbind  2-4 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100000  2,3,4        111/tcp   rpcbind
|   100000  2,3,4        111/udp   rpcbind
|   100000  3,4          111/tcp6  rpcbind
|   100000  3,4          111/udp6  rpcbind
|   100003  3           2049/udp   nfs
|   100003  3           2049/udp6  nfs
|   100003  3,4         2049/tcp   nfs
|   100003  3,4         2049/tcp6  nfs
|   100005  1,2,3      36700/udp   mountd
|   100005  1,2,3      46793/tcp6  mountd
|   100005  1,2,3      50563/tcp   mountd
|   100005  1,2,3      53078/udp6  mountd
|   100021  1,3,4      36915/udp6  nlockmgr
|   100021  1,3,4      37445/tcp6  nlockmgr
|   100021  1,3,4      41605/tcp   nlockmgr
|   100021  1,3,4      50321/udp   nlockmgr
|   100227  3           2049/tcp   nfs_acl
|   100227  3           2049/tcp6  nfs_acl
|   100227  3           2049/udp   nfs_acl
|_  100227  3           2049/udp6  nfs_acl
2049/tcp  open  nfs_acl  3 (RPC #100227)
33945/tcp open  mountd   1-3 (RPC #100005)
41605/tcp open  nlockmgr 1-4 (RPC #100021)
44371/tcp open  mountd   1-3 (RPC #100005)
50563/tcp open  mountd   1-3 (RPC #100005)
</code>
</pre>
* ***List the NFS Shares***
<pre id="fence-code-2" class="fence-code has-commands">
<code>
┌──(mastermind㉿mastermind)-[~]
└─$ showmount -e 127.0.0.1
</code>
</pre>
* ***mount the sahres***
<pre id="fence-code-2" class="fence-code has-commands">
<code>
sudo mount -t nfs 127.0.0.1:/sharename ./nfs-folder -nolock
</code>
</pre>
