No notes available. Contribute notes based on [this](https://www.youtube.com/watch?v=PbMT53jaUaU&list=PL2kSRH_DmWVZp_cu6MMPWkgYh7GZVFS6i&index=6) video now!
# File System
## Type Characteristics

| Symbol  | Type Characteristic |  description |
| ------------- | ------------- |-----------|
| d | directory  | collection of files|
| l |  link | link to a directory of file |
| - | file  | stream of data |
| c | character |a character device which passes/shares data char by char|
| b |  block | a block device transfer data in big size of blocks |
| p | pipe |transfer one process input to another process output|
| s |  socket |same as a pipe but handles more than one process |

### Common commands
```
ls -l /dev
```
## Filesystem Hierarchy
* / -> root directory
* /bin -> contains essential & ready to run binaries
* /boot -> contains bootloader files
* /dev -> contains device files
* /etc -> contains configuration files
* /home -> home directory
* /lib -> contains libraries
* /mnt -> temp mounted FS
* /opt -> optional software packages
* /proc -> process info
* /root -> home directory for root
* /sbin -> system binaries which are run by the root
## Journaling
Used to repair any inconsistencies that occur as the result of an improper shutdown of the computer
Suppose you were copying a file, if the system then also we can able to identify the currupt file by using *journaling*.

## Desktop file types
|Destop file types| Description|
|---|---|
| ext 4 | latest & standard choice of file system which support disk space of 1exabyte of file sixe 16 TB|
| Btrfs| Butter/Better file system and it is not stable than other|
| XFS |  high performance journaling file system generally good for servers|
| NTFS & FAT| windows file system|
| HFS | MAC file system |

To check filesystem of linux :-
```
df -T
```
We can create multiple partitions in any disk and each parttion act as an individual **block device**.And each block system can act as different filesystem.

## Nodes and innodes
Nodes tables are just like dtabase to manage files .In this table each file or directory has innode and contains the information about the file.

### Partition Table
To check how a disk is partitioned.
THere are two main parttion schemes
* MBR -> Mast er Boot Record  
* GRT -> GUID partition table
## MBR
  It is a traditional partition table ,supports the disk upto *2TB*. WHich has linmitations of 4 parts only known as *primary partitions*. Out of these 4 we can create one extended partition & in that can create multiple logical partitions same as creating primary partitions.
 
 ### GPT
 
 This is new standard each partition has globally unique ID(GUID) and usually used with UEFI based looting .
 
 ## Filesystem Structure
 
 FS is part of an organized collection of files &  directives. It's like a database to manage files.
 
 FS has 4 major components
 
 *  Bootblock
 *  SuperBlock
 *  Innode table
 *  Data Blocks

# Inode
   Inode, short of index node tables are just like database to manage files in this table  each file or directory has inode & it generally describes all the info about file. Contains everything execpt for file & it's  name , also contains pointers to datablocks of file.
  When file system is created ,some space for the innodes is also allocated as well.
 ```
 df -i
 ```
This is the command to check how many innodes are availabele.

```
ls -li
```
This is the command to check inodes number.
### How do inodes work and locate file
![Untitled Diagram drawio (1)](https://user-images.githubusercontent.com/120579608/234055609-51a0d8d1-0e67-4e1c-9091-71c7c2c48f18.png)
Innode points to the actual data block of file in the file system. Each and every innode contains 15 pointers.When a file is created on a file system, the file system allocates a new inode and stores the file's metadata in the inode data structure. The file system also allocates the necessary data blocks to store the file's contents and links them to the inode by storing their addresses in the inode's data block pointers.
