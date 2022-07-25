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
    
# Groups 

    ┌─[✗]─[amul@Hacker]─[~]
    └──╼ $ cat /etc/group
    root:x:0:
    daemon:x:1:
    centos:x:1001:
    thor:x:1002:
    amul:x:1000:

    # hum apne ubuntu me group name ke folderme sare groups milegene root ka group milega fir aese bhot sare uske alava bhi jab hum user create krte hai
    tb same name ka bhi groups create ho jaat hai jese aap upr dekh skte ho thor wala user banaya tha pr uska group bhi ban gya ab humare company me 
    bhot sare department honge toh acchi baat hai naa hum perticular users ko unke groups me rkhe 10 users accounting manage krte hai toh unke accounts
    groups bana do fir us group me 10 users add kr do ab unko utna hi access do jitna dena chahaiye thik wesa sales ke liye 
    
# Create Group

    ┌─[✗]─[amul@Hacker]─[~]
    └──╼ $sudo groupadd admins
    # 'groupadd' command group add hoga aur group name de do 
    
    ┌─[✗]─[amul@Hacker]─[~]
    └──╼ $cat /etc/group | grep admins
    admins:x:1003:
    # humne wapis group me check kia pehle admins nhi tha par ab hau mtlb add ho gya sahi se
    
# Delete Group
    
    ┌─[amul@Hacker]─[~]
    └──╼ $sudo groupdel admins
    
    ┌─[amul@Hacker]─[~]
    └──╼ $cat /etc/group | grep admins
     ┌─[✗]─[amul@Hacker]─[~]
    └──╼ $
    # pehle admins tha pr abhi nhi hai kuch output hi nhi aaya 
   
# How to add users in group 

-- Pehle hum dekh lete hai ki humare user konse konse group me hai toh niche check kia mene amul user aur centos user jo filhal unke hi name ke group
ke alawa kisi group me nhi hai...

    ┌─[amul@Hacker]─[~]
    └──╼ $groups amul
    amul : amul
    # amul user amul group me hai 
    
    ┌─[amul@Hacker]─[~]
    └──╼ $groups centos
    centos : centos
    # centos user centos group me hai 
    
-- Ab hum in dono users ko Tech group me add krenge uske pehle Tech group add kr loon 

    ┌─[amul@Hacker]─[~]             
    └──╼ $ sudo groupadd Tech 
    # Tech group add ho chuka 
    
-- Command : >> sudo usermod -g group-name username <<
    
    ┌─[amul@Hacker]─[~]
    └──╼ $ sudo usermod -aG Tech amul                     
    
    # usermod = ye ek functon hai jisme users ke sath bhot kuch manage kr skte hai 
      -aG     = -a means append aur G mans Group isse hum -a -G bhi likh sktee the "sudo usermod -a -G Tech amul" pr mene sath kia taki easy ho
      Tech    = group name define kro ki kis group me kis user ko add krna hai toh Tech group me toh ynha Tech 
      amul    = aur Tech group me amul user ko add krna hai toh last me amul 
                    
    ┌─[amul@Hacker]─[~]
    └──╼ $ sudo usermod -aG Tech centos
    # same as above sare function pata hi hai 
    
-- Let's check ki ye dono users Tech ke group ko belong krte hai ya nhi 

    ┌─[amul@Hacker]─[~]
    └──╼ $groups amul
    amul : amul Tech
    ┌─[amul@Hacker]─[~]
    └──╼ $groups centos
    centos : centos Tech

    # See results pehle sirf amul user amul group me tha ab amul group ke saath saath Tech wale group ko bhi belong krta hai thik wesa centos ke liye

# Rename user's name 

-- Mere pass already thor name ka user created tha ab woh office me nhi rha pr aur ek band aa gya uska name tha hulk toh me ab naya user create kr lo hulk name ka yaa fir thor toh ab hai nhi toh thor ka name hi change kr deta hoon me to uske liye dekho aage ke steps

    ┌─[amul@Hacker]─[~]
    └──╼ $sudo usermod -d /home/hulk thor -m  
    # usermod   = users manage krega ye function
      -d        = new login directory jo bhi naya user hai uska name ka mene directory bana dia new user create kie bina
      thor -m   = kis user ka name change kr dena th woh name aur sath -m  mtlb move jo bhi pehle thor ka ab hul ka ho jayega 
      
    ┌─[amul@Hacker]─[~]
    └──╼ $sudo usermod -l hulk thor 
    # -l hulk    = hum new login set kr rhe ab hulk ka ki us user ko ab hum aese login kr paaye su - hulk like this
      thor       = bas thor ka tha pehle login ab uske alawa new login hoga hulk ke name se ab me check krunga login let's see

-- Dekhiar ab niche humne hulk se login kia aur ho bhi gya fir uske baad check kia hom directory usme bhi hulk hi dikh rha aur thor ka kahi kuch bhi nhi 
   thats means ki humne naya user create nhi kia bas rename kr dia aur sb naya jesa ho gya 
    
    ┌─[amul@Hacker]─[~]
    └──╼ $su - hulk
    Password: 
    hulk@Hacker:~$ ls -l  /home/
    drwxr-x--- 28 amul   amul   4096 Jul 25 11:36 amul
    drwxr-x---  6 centos centos 4096 Jul 21 20:47 centos
    drwxr-x---  3 hulk   thor   4096 Jul 24 18:37 hulk

# Remove Users from Group

-- sudo gpasswd -d username group_remove  
    
    ┌─[amul@Hacker]─[~]
    └──╼ $groups centos
    centos : centos Tech
    # abhi centos user Tech group ko belong krta hai 
    
    ┌─[amul@Hacker]─[~]
    └──╼ $sudo gpasswd -d centos Tech
    Removing user centos from group Tech
    # -d     = delete
      centos = user name centos hai  
      Tech   = group name Tech hai 
      muje centos user ko Tech group se delete krna hai...
    
    ┌─[amul@Hacker]─[~]
    └──╼ $groups centos
    centos : centos
    # ab centos user Tech ka hissa nhi hai 
    
### Finally all clear for users and groups now we go ahed for password policies

   
  
    
    
    
    
    
    
