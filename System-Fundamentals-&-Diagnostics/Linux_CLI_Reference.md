🐧 Linux System Administration & Core CLI Ops
Comprehensive guide for:
📂 File & Directory Management

(ls, cd, mkdir, rm, cp, mv, touch, chmod, chown)

🔐 User & Access Control

(useradd, usermod, passwd, sudo, groups, /etc/shadow)

⚙️ Process & Service Management

(ps, top, htop, systemctl, kill, bg/fg)

🛠️ Logging & Troubleshooting

(tail -f, journalctl, dmesg, uptime, df/du)

|                 Command                 |           Function              |
----------------------------------------------------------------------------- flag 
command--Help = man command               | know more about commands but man more detailed
ls ~/Documents                            | list all files/subdirectories in documents folder 
ls --help = man ls                        | get more about ls command
ls -lh /home/nada/Downloads               | displays a detailed, vertical list of files including permissions, owners, and sizes in human-readable format
ls -a /Documents                          | list all files , subdirectories + hidden(starting with . )
cd ../Desktop                             | one step to back (Parent) then enter to another directory(Desktop)
mkdir 'folder name'                       | create new directory in current directory 
touch 'file name.txt'                     | create new file in current directory
nano 'file name'                          | to create file then you will write what you want then ctrl+o for save , ctrl+x for exit  or show + edit file if already exist
history                                   | for show , use the last command one more time
ctrl+R                                    | for search , one more ctrl+R to see one more matched in history not in file for file we use "less command"
cp -recursive 'folder name' 'paste to'    | copy directory with its files 
cp 'file name' 'paste to'                 | copy file 
cp *.png ~/Documents                      | copy using wildcard
mv 'file name' 'new file name'            | rename the file 
mv 'file name' 'directory'                | move file to another directory 
mv *_documents.txt 'destination path'     | moving use wildcard
rm -r 'folder name'                       | remove directory with its files
rm 'file name'                            | remove file 
cat 'file name'                           | show the content without editing
head 'file name'                          | show the first 10 rows by default      head -n 15 'file name'
tail 'file name'                          | show the last  10 rows by default      tail -n 15 'file name'
less 'file name'                          | less in linux = more in windows    up,down,g(to first row),G(to last row),/word(search),q(quit)  ****very important command
grep -i word 'file name'                  | search about word in file whatever the letters capital/small (ignore case)
grep -i word *.txt | search about word in many files (wildcard)    
ls /home 2> /dev/null                     | /dev/null = $null in windows
ls -la /etc | grep bluetooth              | use pipe to combine two commands in one line || list only rows in etc file that contain 'bluetooth' word
** --Help , history , more , (less , grep) in linux --> so important commands
sudo(super user do)                       | like run as admin in powershell (UAC)
sudo -l                                   | to know what permissions I have
sudo cat /etc/sudoers                     | show who has access to use sudo must type sudo even if I have permissions of root 

























