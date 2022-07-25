# What is SUDO

-- sudo hume bhot zarut padi hai jab bhi hume kuch install krna hai update krna hai anything par haan agr aap root user nhi ho toh aap ko sudo chahiye hi
   chahiye mtlb ki me agar root user nhi hoon aur fir bhi muje kuch install krna hai aur update krna hai toh hume sudo command use krna padefa tb hi ho 
   payega par jab hum new user create krke sudo apt-get update likhte hai yaa fir kuch install krna chahte hai toh ek error show hota hai

-- Error-name : hulk is not in the sudoers file.  This incident will be reported.

![image](https://user-images.githubusercontent.com/38901699/180760702-1f6a6856-935f-4e9e-901d-27c62fe6161a.png)

# Method - 1

-- Ab find krte hai iska solution

    sudo usermod -aG sudo hulk
    
    # hum hulk user ko sudo ke group me add kr denge taaki sudo wale jo bhi access hai woh ye user kr payega fir aap niche image dekho ki woh hulk user
      ab update kr paa rha hai 

![image](https://user-images.githubusercontent.com/38901699/180761545-71843b86-fd24-4ba9-9cf0-294af9636a3e.png)

# Method - 2

-- user ko sudo group me daal kar bhi hume solution mil gya aur dusra method-2 ab dekho 

    ┌─[amul@Hacker]─[~]
    └──╼ $sudo visudo 
    
    # agar aap root user ho to sidha visudo type krke enter kro aur agar aap sudo user bhi hai toh mene jese dia hai woh command use kro...
    # hum visudo command use krke usme user hulk ko add krenge apne root ke samne jese likha hua hau ALL:ALL wala thik wesa hulk ke samne likh do 
      jesa aapko niche image me dekh kar pata chlega fir CTRL+O kr ke save kr do. 
    # uske baad wapis hum hulk user ka login krke sudo apt update likhenge tb bhi toh work krega ye aache se mene check kr lia...

![image](https://user-images.githubusercontent.com/38901699/180763760-5943e74a-8277-4003-8f01-9fc4ede4d114.png)
 
# Sudo deep-dive 

-- Humne hulk user ko sudo wala access toh de dia par kahi humne kuch galti toh nhi ki naa kyun ki woh user ab sb kr skta ho jo ek root user kr skta hai 
   kisi service ko start stop krna disable krna hai fir server ko reboot yaa poweroff anything toh hum iske liye kya krenge.
   
-- me sudo wala access dena chahta hoon par sirf apt update krke kaa apne choice ke hisab se toh me kese krunga dekhiae niche 

    ┌─[✗]─[amul@Hacker]─[~]
    └──╼ $sudo visudo 
    # visudo me wapis jaakr aapko kuch changes krne hai niche image me dekh skte ho 
    
![image](https://user-images.githubusercontent.com/38901699/180773196-c2be321b-e3ae-4add-a7a5-e46553f1b518.png)

    ┌─[root@Hacker]─[/etc]
    └──╼ #cat sudoers | grep hulk
    hulk	ALL=(ALL:ALL) /usr/bin/apt
    
    # See humne grep krke dekha ki humne kya changes kie 
    # usr/bin/apt = hulk user sirf sudo command use krke apt wala hi use kr payega
    # sudo apt update & sudo apt install like janah par b apt command use hoga sif whi us kr payega hulk user 

![image](https://user-images.githubusercontent.com/38901699/180776342-bc887037-d8e7-4050-b47d-e72c1f869cb7.png)

-- upar image me dekh skte ho ki right side me mene suders file me hulk ke samne konsa acccess dia hai yes visudo me jaakr jo edit kia tha use thoda 
   changes kia mene hulk user ko sirf mene apt use krna ka permission dia hai isliye woh sirf woh hi use kr paayega uske alwa woh kahi pr bhi kuch b
   use krega sudo command lagakr kuch nhi hoga aap upr images me dekh skto 
   
![image](https://user-images.githubusercontent.com/38901699/180778014-77171f3f-e016-4723-941b-4ff00e644947.png)

-- see ab mene hulk user ko sirf chage wala information dekhne ka access dia isliye sirf woh chage wala command hi use kr payega sudo ke saath par
   woh ab apt update yaa upgrade bhi nhi kar paayega
  
### Aap path dekar kisi bhi command ko use krna aur use naa kare  ke liye user ko manage kar skte ho jese mene kai hai mene bas do example die hai but aap aur bhi de skte hai apne hisab se

   
   
   
 
