|                 Command                 |           Function              |
-----------------------------------------------------------------------------
`ls`   (-force  , -recurse , -filter)     |  List current files and folders / hidden / subfiles+folders / get specific files 
`ls 'path' -recurse -filter *.exe `       |  list specific files using filter
`get-help ls`  (-full , -examples..)      |  know more about command like ls
`pwd`                                     |  print working directory
`cd`                                      |  Change directory                
`cd 'c:\users\mega store\.m2'`            |  absolute path
`cd ..`                                   |  relative path  one step for backward
`cd ..\.m2`                               |  one step to backward then go to 
`cd ~\.android`                           |  telda refer to home directory 
`#cd + tab`                               |  reuse last usage of cd 
`mkdir 'folder name' `                    |  make folde in the current directory 
`history` or use `arrow`                  |  List Used Commands   
`tab`                                     |  autocomplete
`cp *.pdf 'paste to specific path'`       |  use wildcard to copy all files with the same extension to specific folder , copy must be from working directory   
`*_document.pdf    *file*.pdf`            |  another examples of wildcard
`-recurse -verbose`                       |  copy folders + files , confirming message
`mv 'file name' 'new file name'`          |  rename file
`mv 'file' 'path'` -force                 |  move the file to another directory , force to move the file even if it is read only
`mv *_documents.txt 'path'`               |  use wildcard to speed up the process
`rm 'file name'` -force                   |  permenant deletion , force for delete even if file has protection
`rm 'folder name'` -recurse               |  delete directory + its files must use -recurse
`cat 'file name'`                         |  show the content of the file , efficient for small files 
`cat 'file name' -Head 10`                |  to show first lines , must write number not like python :) 
`cat 'file name' -tail 10`                |  to show last lines  , must write number 
`more 'file name'`                        |  show the content of the file in parts , efficient for large files (enter,space,q) , memory efficient
`winget search 'name of the program'`     |  to search for the program before installation to make sure of the program name
`winget install / uninstall 'name'`       |  to speed up and skip all silly process of manual installation process 
`start notepad++ 'file name'`             |  open this file with notepad++ 
`get-alias ls`                            |  get the original command  
`sls word 'file.txt'`                     |  get the lines that have this word , line number , file name 
`sls word '*.txt'`                        |  get the lines that have this word , line number , file name
`echo word > file.txt`                    |  clear the whole content , writes this new word only (Overwrite)
`echo word >> file.txt`                   |  keep the current content , adds the word to the end (Append)
process in windows(3 types of streams     |  stdin, stdout,stderr) pipe(|) example for stdout , stdin
`cat file.txt | sls nada`                 |  displays only the lines from the file that contain nada
`cat file.txt | sls st > file2.txt`       |  move the output to the file2.txt
`rm secure_folder 2> file.txt`            |  error will be saved in file.txt
`rm secure_folder 2> $null`               |  silence error , will not appear on terminal screen $null is a black hole
`ni -Path 'path' -ItemType 'file' -Value 'hello ndod' -force`       |  to make file or folder 'new item'
`get-localuser`                           |  show users 
`get-localgroup`                          |  show groups 
`get-localgroupmember 'group name'`       |  show members of specific group 
`$PSVersionTable.PSVersion`               |  version of the powershell
`net`                                     |  change password , add users , remove users , modify users info
`net user nada *`                         |  change password in hide (run as admin)
`net user nada /logonpasswordchg:yes`     |  the user must change his password after login to the system
`net user sarah nnnnn /add                | create new user with password nnnn 
= net user sarah * /add`                  | create new user with hidden password
`net user sarah * /comment:"title" /add`  | create new user with hidden password and description
`New-LocalUser -Name "sarah" -Description "HR Manager" -Password (Read-Host "Enter Password" -AsSecureString)` |   AsSecureString like * in net 
`net user sarah /del                      |  delete user sarah 
= remove-localuser sarah`                 |  delete user sarah 
`Set-LocalUser`                           |  modify data for user already exists

















