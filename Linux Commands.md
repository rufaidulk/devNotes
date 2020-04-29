# Linux Commands
## ls -l
- run : `ls -l /etc/hosts`  , output : **-rw-r--r-- 1 root root 337 Oct  4 11:31 /etc/hosts**
- first character: shows file type
  - - : regular file
  - b : block special file
  - c : character special file
  - d : directory
  - l : symbolic link
  - n : network file
  - p : FIFO
  - s : socket
- Next 9 characters are showing the file permissions. first 3 for user, next 3 for group and last 3 for others.
  - r : read
  - w : write
  - x : execute
  - s : setgid bit
  - t : sticky bit
- Next character shows the number of hard links to the file , here it is 1
- Next 2 fields shows the file owner and group, here both are root.
- Next fields are size of file, last modification timestamp, file name. use **-h** for size human readable format
---
- **-a** for hidden files
- --sort for sorting  , default alphabetical order.
  - --sort=exension or -X
  - --sort=size or -S
  - --sort=time or -t
  - --sort=version or -v
  - for reverse order -r
# chown 
- change user/group ownership of file, directory or symbolic link
- **`chown [OPTIONS] USER[:GROUP] FILE(s)`**
- **USER** is the user name or the user ID (UID) of the new owner. **GROUP** is the name of the new group or the group ID (GID). **FILE(s)** is the name of one or more files, directories or links. Numeric IDs should be prefixed with the **+** symbol.
- **USER** - If only the user is specified, the specified user will become the owner of the given files, the group ownership is not changed.
- **USER:** - When the username is followed by a colon **:**, and the group name is not given, the user will become the owner of the files, and the files group ownership is changed to user’s login group.
- **USER:GROUP** - If both the user and the group are specified (with no space betwen them), the user ownership of the files is changed to the given user and the group ownership is changed to the given group.
- **:GROUP** - If the User is omitted and the group is prefixed with a colon **:**, only the group ownership of the files is changed to the given group.
- **:** If only a colon **:** is given, without specifying the user and the group, no change is made.
- By default, on success, chown doesn’t produce any output and returns zero.
---
- change the owning group of a file named f**ile1** to **www-data**: `chown :www-data file1`
- change the ownership of a file named **file1** to a new owner named **linuxize** and group **users:** `chown linuxize:users file1`
- change the ownership of a file named f**ile1** to a new owner named **linuxize** :`chown linuxize file1`
# chmod
### Effect of Permissions on Files

![Image](/home/rufaidulk/Documents/medley/resources/SyyzInQK8_H1ub-w8FL.png)
### Effect of Permissions on Directories (Folders)

![Image](/home/rufaidulk/Documents/medley/resources/SyyzInQK8_Sy8mWv8FI.png)
- syntax : **chmod [OPTIONS] MODE FILE...**
- Numeric values :
  - r - 4
  - w - 2
  - x - 1
  - no permission - 0
- The permissions number of a specific user class is represented by the sum of the values of the permissions for that group.
- To find out the file’s permissions in numeric mode simply calculate the totals for all users classes. For example, to give read, write and execute permission to the file’s owner, read and execute permissions to the file’s group and only read permissions to all other users you would do the following:
  - Owner: rwx=4+2+1=7
  - Group: r-x=4+0+1=5
  - Others: r-x=4+0+0=4
- for changing in numeric mode : **`chmode 754 filename/dirname`**
- For recursive , effects all files and directories under a given directory : **`chmod -R 754 directory`**
