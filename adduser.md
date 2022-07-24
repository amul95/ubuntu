# How to add users in Linux with # USERADD

    ┌─[✗]─[amul@Hacker]─[/home]
    └──╼ $ sudo useradd -d /home/thanos -m thanos
    
    useradd         = means user add krna hai 
    -d              = home directory create kr do user ke name se 
    /home/thanos    = path dia mene ki thik aesa hi bana na 
    -m thanos       = mene -m flag mention kia taaki jab create ho toh is name se ho aur issi name se directory bane 
    
    Fir hum check karenge ki bana yaa ya nahi..
    
    ┌─[amul@Hacker]─[/home]
    └──╼ $sudo cat /etc/passwd
    # ye command use krke aap dekh skte ho
    
    ┌─[amul@Hacker]─[/home]
    └──╼ $ls -l /home/
    total 12
    drwxr-x--- 28 amul   amul   4096 Jul 24 17:41 amul
    drwxr-x---  6 centos centos 4096 Jul 21 20:47 centos
    drwxr-x---  2 thanos thanos 4096 Jul 24 17:44 thanos

    # hum dekh skte hai ki thanos user ban gya ab dekhete hai ki passwd kese set karte hai uspr 
    
    ┌─[amul@Hacker]─[/home]
    └──╼ $sudo passwd thanos
    New password:  
    Retype new password: 
    passwd: password updated successfully

    # ab ye dekhte hai ki $HOME directory ka mtlb kya tha agar hume login krenge is user ko terminal toh kesa show krega 
    
    ┌─[✗]─[amul@Hacker]─[/home]
    └──╼ $ su - thanos              //jo bhi username tha usko su - kr ke login kia fir passwd dia  
    
    Password: 
    $ 
    $ ls
    $ pwd
    /home/thanos
    $ 

    # aap dekh skte ho ki kya diffrence hai agar me simple adduser krta tha toh woh $HOME directory wala jesa nhi dikhta tha uske next chapter padhte hai 
    
    
# How to add users in Linux with # ADDUSER
    
    ┌─[amul@Hacker]─[/etc/pam.d]
    └──╼ $ sudo adduser iron-man
    
    Adding user `iron-man' ...
    Adding new group `iron-man' (1003) ...
    Adding new user `iron-man' (1003) with group `iron-man' ...
    Creating home directory `/home/iron-man' ...
    Copying files from `/etc/skel' ...
    New password: 
    Retype new password: 
    passwd: password updated successfully
    Changing the user information for iron-man
    Enter the new value, or press ENTER for the default
        Full Name []: Iron-Man
        Room Number []: 10
        Work Phone []: 7802839450
        Home Phone []: 5354492
        Other []: 
    Is the information correct? [Y/n] Y
    
    ┌─[amul@Hacker]─[/home]
    └──╼ $sudo cat /etc/passwd
    # ye command use krke aap dekh skte ho
    
    ┌─[amul@Hacker]─[/etc/pam.d]
    └──╼ $ls -l /home/
    total 16
    drwxr-x--- 28 amul     amul     4096 Jul 24 17:41 amul
    drwxr-x---  6 centos   centos   4096 Jul 21 20:47 centos
    drwxr-x---  2 iron-man iron-man 4096 Jul 24 18:01 iron-man
    drwxr-x---  3 thanos   thanos   4096 Jul 24 17:48 thanos

    # Humne dekha upr ki kitna simple command se ye user create hua aur home me bhi dekha ki yes create ho chuka hai 
      passwd set krna same method hai sudo passwd iron-man toh New passwod krke prompt hoga bas user create 
      

# How to Remove Users

     ┌─[✗]─[amul@Hacker]─[/home]
     └──╼ $ sudo deluser thanos
     # sirf ye command use krne thanos user delete toh ho jayega par uska jo folder bana hua hoga /home directory me woh nhi delete hoga
       isliye dusra method hai niche wala...


    ┌─[✗]─[amul@Hacker]─[/home]
    └──╼ $ sudo deluser --remove-home thanos
    
    Looking for files to backup/remove ...
    Removing files ...
    Removing user `thanos' ...
    Warning: group `thanos' has no more members.
    Done.

    # Finally ye wala command jo hai woh user ko toh remove krega hi upr se jo folder bana hoga usse bhi delete kr dega toh humare liye
      best hai.
    
        
    
