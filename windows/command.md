copy 'file name' 'new file name'  copy the file and paste it in the same directory but with another name        /y   /v 
robocopy /e /zb /mt:8 /copyall /log /tee /r:3 /w:5
gpupdate --> update the policies 
gpupdate /target:computer /force --> to update policies on my computer even if applied before
gpupdate /target:user /force --> to update policies on my computer even if applied before
gpresult /r --> show what policies applyed on my device 
gpresult /user sgc/professor /v


