# Locking and unlocking user accounts

    sudo passwd -l <username>
    # -l = locked >> user locked 
  
    sudo passwd -u <username>
    # -u = unlocked >> user unlocked
    
# Setting password expiration information

    sudo chage -l centos
    
    # chage     = change user password expiry information
    # -l        = --list Show account aging information. 
    # centos =  = kis user ka hume detail chahiye woh 
    
  ![image](https://user-images.githubusercontent.com/38901699/180714327-57c931c2-b838-4f4c-9d07-630a00e57b83.png)

    sudo chage -d 0 centos
    
    # '-d' means last_day mene ynha centos ko passwd change krne ke liye 0 set kia mtlb usse ab passwd change krna hoga kyun ki uske days khtm
      ho chuke hai woh same passwd rkhne ke ab usse change krna hoga 
    
    sudo chage -l centos
    
    # ab me wapis apni password wali info dekhunga toh likha hua hoga ki password must be changed today niche aap dekho 
    
  ![image](https://user-images.githubusercontent.com/38901699/180715897-76bd110d-1784-4b0c-8312-15bf2c852a1c.png)
      
    su - centos
    
    # jese hi ye run krunga toh normally me apna password daal kr login kr leta tha pr ab aesa nhi hoga dekho niche image 
    
  ![image](https://user-images.githubusercontent.com/38901699/180716418-1e31fcb4-52ae-46d6-9215-56980e4cbb7f.png)

    sudo chage -M 90 centos
    
    # -M = --max_days mltb maximum number of days toh user ko mene 
    # 90 = 90 days die hai ki woh tb tk uska jo bhi passwd hai woh valid rhega
    
    --- jese hi 90 din khtm hone aayenge mtlb jo bhi 90 din baad date aayegi use pehle ka ek din uska last day hoga aur current day bhi tb hi usse apna
    password change krna hoga au usse warning bhi di jayegi 
    
    sudo chage -m 0 centos
    
    # -m = --mindays hua mtlb mimimum kitne dino tak passwd change krna zaruri hoga agar me -m ke baad value 0 dal doon toh on the spot us user ka 
    password change hona chahiye mtlb ki woh user jab bhi wapis login krega usse new password dena padega

# In-Depth of CHAGE Command
![image](https://user-images.githubusercontent.com/38901699/189149494-00bc10e2-2efd-441c-8477-09c7aaf040df.png)
       
        Last password change					            : Jul 15, 2022
        # mene july 15 ko apna passwd change kiaa thaa toh bas ye show karega ki mene last passwd kab change kia tha
        
        Password expires					                : Sep 13, 2022
        # iska mtlb huaa ki aaj 8 sept huaa hai current date aur sep 13 ko mera expire ho jayega passwd itna smj aa gyaa aapko
        
        Password inactive					                : never
        # iska mtlb hai never kyun ki humne passwd abhi ta inactive nhi kiaa hai me kr bhi skta hoon uske baad kyaa hoga ki user ko passwd turnt change 
          krna hoga on the spot 
        
        Account expires						                : Jul 12, 2023
        # mera jo user hai amul woh account mera totaly expire bhi hoga uska date hai July 12 2023 me tab tak ye chlta rhega
        # aur account expire ho gya mtlb naa hi amul user work krega aur naa hi amul user ka passwd 
        
        Minimum number of days between password change		: 7
        # mene set kiaa huaa hai 7 days ki tab tak aapko apna passwd change krna hai 
        
        Maximum number of days between password change		: 60
        # 60 days mtlb dekho mene passwd change kiaa hai 15th july ko tab se 60 dino kaa gap hoga apna 13th Sept aur us beech hume passwd change kr lena           hai humara toh ye huaa humara maximum
        
        Number of days of warning before password expires	: 7
        # warning bole toh jab aap apna user login kroge screen pr toh aapko niche likha huaa aayega ki aap apna passwd change kro kyun ki humne time set 
          kia hai 7 din warning kaa jisse user apna us dino ko bich change kr le 
        
        Ab muje apna jo passwd change krna padega but muje nhi krna hai toh me kyaa krunga mere jo maximum days hai 60 usko me badhake kr dia hoon 120           days uska mtlb ab ho gya nov tak aese me khel skta hoon 
        
