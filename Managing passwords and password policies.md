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
   
    
# Setting a password policy

    
    
 
