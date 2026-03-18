copy 'file name' 'new file name'  copy the file and paste it in the same directory but with another name        /y   /v 
robocopy /e /zb /mt:8 /copyall /log /tee /r:3 /w:5
gpupdate --> update the policies 
gpupdate /target:computer /force --> to update policies on my computer even if applied before
gpupdate /target:user /force --> to update policies on my computer even if applied before
gpresult /r --> show what policies applyed on my device 
gpresult /user sgc/professor /v
** (memory type) --> GUI : 
                      task manager > performance > memory 
                 --> CLI :
                     Get-CimInstance -ClassName Win32_PhysicalMemoryArray  (my computer cababilities , Motherboard capacity (Max RAM & Total Slots))
                     Get-CimInstance -ClassName Win32_PhysicalMemory | Select-Object DeviceLocator, Capacity, Speed (current memory)
** (Check RAM Generation (DDR)) --> GUI:
                                    Task Manager > Performance > Memory
                                         check 'Speed': 
                                           - 1600MHz or less = DDR3
                                           - 2133MHz to 3200MHz = DDR4
                                           - 4800MHz+ = DDR5
                                --> CLI:
                                   `Get-CimInstance -ClassName Win32_PhysicalMemory | Select-Object SMBIOSMemoryType`
                                                    - Code 24 = DDR3
                                                    - Code 26 = DDR4 
                                                    - Code 30/34 = DDR5


