# Viewing permissions
    
    ┌─[amul@Hacker]─[~]
    └──╼ $ls -l 
    total 360
    drwx------  5 amul amul   4096 Jul 22 17:16 ansible
    --wx-wx-wx  1 amul amul     27 Jul 18 16:11 code.txt
    drwxr-xr-x  2 amul amul   4096 Jul 22 16:59 Desktop
    drwxrwx---  2 amul amul   4096 Jul 19 16:54 Documents
    drwxr-xr-x  3 amul amul   4096 Jul 23 18:19 Downloads
    drwxrwxr-x  5 amul amul   4096 Jul 16 19:32 gnome-terminal
    drwxr-xr-x  2 amul amul   4096 Apr  8 01:25 Music
    -rw-rw-r--  1 amul amul     22 Jul 24 14:01 number.txt
    drwxrwx---  5 amul amul   4096 Jul 19 13:17 Pictures
    drwxr-xr-x  2 amul amul   4096 Apr  8 01:25 Public
    drwx------ 13 amul amul   4096 Jul 24 13:16 snap
    drwxr-xr-x  3 amul amul   4096 Jul 17 18:46 Sync
    -rw-r-----  1 amul amul 304667 Jul 24 12:30 syslog
    drwxr-xr-x  2 amul amul   4096 Apr  8 01:25 Templates
    drw-r--r--  2 amul amul   4096 Jul 18 12:19 Test
    drwxr-xr-x  3 amul amul   4096 Jul 13 19:26 Videos

![image](https://user-images.githubusercontent.com/38901699/180926297-b9394684-794f-4de3-b8d2-f71c3aee20a5.png)

![image](https://user-images.githubusercontent.com/38901699/180926424-576fe1a8-50a2-4eac-8135-cd932e236722.png)

![image](https://user-images.githubusercontent.com/38901699/180926636-f49c7f92-d0a5-421e-a59a-4e35e7c70c58.png)

    chmod u+rw <filename>: Mene user ko read aur write ka permission dia
    
    chmod g+r <filename>: Mene group ko read ka permission dia 
    
    chmod o-rw <filename>: Mene other me se read aur write ka permission hata dia 
    
    # "+" Plus means permission dena aur "-" Minus means permission hata dena 
    
# Permissions Numbers for easy to remember 

    Read: 4
    Write: 2
    Execute: 1
  
-- ab hum number denge sirf jo rwx ko represent krega like below:

    600: 6 kb hoga jab 4+2 hoga that menas Read(4)+Write(5)=6 is tarike se 
         user has read, and write also group & other has nothing... 
    # this is same as rw- --- ---
         
    740: User has read, write, and execute. Group has read. Other has nothing.
    # this is same as rwx r-- ---
    
    
    770: Both user and group have full access (read, write, and execute). Other has nothing.
    # this is same as rwx rwx ---
    
    777: Everyone has everything.
    # This is the same as -rwxrwxrwx.
    
# Changing the ownership of objects
> We can change user and group ownership of a file or directory with the " chown " command. 
    
      ┌─[amul@Hacker]─[~]
      └──╼ $ls -l number.txt 
      -rw-rw-r-- 1 amul amul 22 Jul 24 14:01 number.txt
      # number.txt ek file hai uska user amul hai aur group bhi amul hai 
      
      
      ┌─[amul@Hacker]─[~]
      └──╼ $sudo chown hulk number.txt 
      # muje ab amul user ko hata kar hulk user ko ownership de deni hai
      
      
      ┌─[amul@Hacker]─[~]
      └──╼ $ls -l number.txt 
      -rw-rw-r-- 1 hulk amul 22 Jul 24 14:01 number.txt
      # Finally wapis dekiae ab hulk ho gya ownership change kr di 
      
> Yes ab user ke saath group bhi change krenge 
      
      ┌─[amul@Hacker]─[~]
      └──╼ $ls -l number.txt 
      -rw-rw-r-- 1 hulk amul 22 Jul 24 14:01 number.txt
      # Ye toh hmne dekha hi ki user hulk ho gya muje ab amul group ko 
        hatakr hulk group me lana hai
      
      
      ┌─[amul@Hacker]─[~]
      └──╼ $sudo chown hulk:hulk number.txt
      # hulk user aur uske baad [ : ] double collom use krke group name type kro
      
      
      ┌─[amul@Hacker]─[~]
      └──╼ $ls -l number.txt 
      -rw-rw-r-- 1 hulk hulk 22 Jul 24 14:01 number.txt
      # Ab dekhiar user ke saath group bhi change....
      
> humne abhi user & group dono change agar me hulk group ki jagh centos group yaa fir jis bhi group me dalna chahta hoon muje us group ka name likha hai...

-- Dusra method hai sirf akele group ko change krne kaa with " chgrp " command.

    ┌─[amul@Hacker]─[~]
    └──╼ $sudo chgrp centos number.txt 
    # chgrp command ke baad jis bhi group me dalna woh grp_name likh do
    
    ┌─[amul@Hacker]─[~]
    └──╼ $ls -l number.txt 
    -rw-rw-r-- 1 hulk centos 22 Jul 24 14:01 number.txt
    # dekhie group changed...in one shot
    
    
        




