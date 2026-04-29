 Linux System Administration & Core CLI Ops
Comprehensive guide for:
 File & Directory Management
(ls, cd, mkdir, touch, cp, mv, rm, cat, nano, grep, pipe |)

 User & Access Control
(useradd, usermod, userdel, passwd, sudo, /etc/passwd, /etc/shadow)

 Permissions & Ownership
(chmod, chown, chgrp, SUID, SGID, Sticky Bit)

|                 Command                 |           Function              |
----------------------------------------------------------------------------- flag 
`command--Help = man command`               | know more about commands but man more detailed
`ls ~/Documents`                            | list all files/subdirectories in documents folder 
`ls --help = man ls`                        | get more about ls command
`ls -lh /home/nada/Downloads`               | displays a detailed, vertical list of files including permissions, owners, and sizes in human-readable format
`ls -a /Documents`                          | list all files , subdirectories + hidden(starting with . )
`cd ../Desktop`                             | one step to back (Parent) then enter to another directory(Desktop)
`mkdir 'folder name'`                       | create new directory in current directory 
`touch 'file name.txt'`                     | create new file in current directory
`nano 'file name'`                          | to create file then you will write what you want then ctrl+o for save , ctrl+x for exit  or show + edit file if already exist
`history`                                   | for show , use the last command one more time
`ctrl+R`                                    | for search , one more ctrl+R to see one more matched in history not in file for file we use "less command"
`cp -recursive 'folder name' 'paste to'`    | copy directory with its files 
`cp 'file name' 'paste to'`                 | copy file 
`cp *.png ~/Documents`                      | copy using wildcard
`mv 'file name' 'new file name'`            | rename the file 
`mv 'file name' 'directory'`                | move file to another directory 
`mv *_documents.txt 'destination path'`     | moving use wildcard
`rm -r 'folder name'`                       | remove directory with its files
`rm 'file name'`                            | remove file 
`cat 'file name'`                           | show the content without editing
`head 'file name'`                          | show the first 10 rows by default      head -n 15 'file name'
`tail 'file name'`                          | show the last  10 rows by default      tail -n 15 'file name'
`less 'file name'`                          | less in linux = more in windows    up,down,g(to first row),G(to last row),/word(search),q(quit)  ****very important command
`grep -i word 'file name'`                  | search about word in file whatever the letters capital/small (ignore case)
`grep -i word *.txt`                        | search about word in many files (wildcard)    
`ls /home 2> /dev/null`                     | /dev/null = $null in windows
`ls -la /etc | grep bluetooth`              | use pipe to combine two commands in one line || list only rows in etc file that contain 'bluetooth' word
** --Help , history , more , (less , grep) in linux --> so important commands
`sudo` (super user do)                      | like run as admin in powershell (UAC)
`sudo -l`                                   | to know what permissions I have
`sudo cat /etc/sudoers`                     | show who has access to use sudo must type sudo even if I have permissions of root 
`sudo su -`                                 | switch account to root to do multiple commands with root permissions then 'exit command' to retrieve to my previous account
`sudo su - username`                        | switch account to specific user    
`cat /etc/group`                            | view group members            groupname:password:groupid:members
`cat /etc/passwd`                           | view users + system users in our machine     username:password:UID:GID:comment:home_directory:shell
shell : `/bin/bash/`                        | normal user can open the terminal and write the commands 
        `/bin/false/` = `/usr/sbin/nologin/`| this user prevented to open the terminal
`usermod` = set-localuser in powershell     | modify user account
`sudo usermod -s /usr/sbin/nologin username`| -s (shell) to prevent user from opening the terminal
`sudo usermod -L username`                  | -l (lock)  to lock his account temprorary 
`sudo usermod -U username`                  | -u (unlock) to open the account
`sudo usermod -aG sudo username`            | -ag (append group to prevent deletion of data tha already exist) to add user to specific group
`passwd`                                    | change my own password
`sudo passwd user`                          | create or change the password
`/etc/shadow`                               | stores encrypted passwords (Scrambled) only root can access it 
`sudo passwd -e 'username'`                 | force someone to change his password in next login "make the current one expired"
`sudo useradd -m nada`                      | create a new user , -m (to make to her home directory /home/nada)
`sudo passwd nada`                          | to set the initial password , then sudo passwd -e 'username to force her to change her password 
`sudo userdel -r nada`                      | delete the user and its files 
`cat /etc/passwd | grep nada`               | to get nada's account 
`ls -l 'path'`                              | we use -l to see the file permissions on this file
ex: -rwxrw-r-- 1 nada cool_group 0 oct 9 17:48 path of this file
first 10 bits are the permissions of this file 
first bit --> - refers to this is a file , d refers to directory
1st  trio  --> rwx refers to the permissions of the owner    (read , write , execute)
2nd  trio  --> rw- refers to the members of the group permissions (read , write)
3rd  trio  --> r-- refers to all other users      (read only)  
r = 4 , w = 2 , x = 1 , - = 0              permission of this file 764
`chmod`                                     | change permissions
`chmod u+x 'file'`                          | grant execute permission to owner u --> owner , x --> execute 
`chmod u-x 'file'`                          | revoke execute permission 
`chmod ugo+r 'file'`                        | grant owner , group of members , others read permission (symbolic format)
`chmod 754 'file'`                          | (numeric format)
`sudo chown sarah 'file'`                   | change the owner of the file
`sudo chgrp 'newgroup' 'file'`              | change the group that the file belongs to
`sudo chmod u+s 'file'`                     | lets a normal user run the passwd program as if they were the Root (Admin)   s=4
`sudo chmod g+s 'file'`                     | s (set group id SGID)  s=2
`sudo chmod +t 'folder'`                    | everyone can add or modify files but root/owner only can delete t=1
