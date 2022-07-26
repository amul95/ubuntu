# Backing up and restoring Debian packages

> The " dpkg " command allows us to export and import a list of packages to install.

-- Backup my all installed pacakges
      
      ┌─[amul@Hacker]─[~]
      └──╼ $dpkg --get-selections > packages.list
      # dpkg command mere system me abhi jitne bhi packages installed hai
        uska backup le lega aur pacakges.list name ki file store kr lega 
      
      ┌─[amul@Hacker]─[~]
      └──╼ $ls
      # fir ls krke check kia yes packages.list file create ho chuki hai.
      
      ansible    Downloads       packages.list  Sync       Videos
      code.txt   gnome-terminal  Pictures       syslog
      Desktop    Music           Public         Templates
      Documents  number.txt      snap           Test
      
      Let's check ki uske ander kese humare sare packages dikhte hai
      
      ┌─[amul@Hacker]─[~]
      └──╼ $cat packages.list 
      accountsservice					install
      acl						          install
      acpi-support					  install
      acpid						        install
      adduser						      install
      
      # mene cat command use krke check kia ki packages.list me kyaa hai 
        aap dekh skte ho ki packages ke name hai aur install hai means woh 
        abhi sare pacakges mere me installed hai ye mtlb hua...par kya ye toh
        4-5 hi hai kyaa mere system me itne hi hai???
      
      ┌─[amul@Hacker]─[~]
      └──╼ $cat packages.list | wc -l
      1917
      
      # nahi nahi total 1917 packages hai pr pura ka pura print nhi kr skta
        me ynaa isliye example dia toh toal 1917 hai mere packges 
        
      Note: ab mene backup le lia jab bhi muje naye server ki zarut hogi
            toh muje wapis sb theek se chalane ke liye jo bhi zarrut hog
            woh muje ab is backup se mil jaayega 
            
-- Restoring my all installed pacakges

> Ye sb me new system me use krunga jab bhi muje zarurt pade aur mera old system work naa kre sahi se tab
    
> We'll need to ensure we have the dselect package installed. The dselect package provides us with additional features when managing Debian packages. Its finer points are beyond the scope of this chapter, but specific to our current goal, we can use it to restore packages from our exported list. At your shell prompt, type which dselect and you should see output similar to the following:
  
    which dselect 
    
    # check kr lo ki apke system me dselect package install hai ya nhi 
      maan lo nhi hai toh ab hum install krenge 
      
    
    sudo apt install dselect
    # yes install kr lo 
    
    which dselect 
    
    # wapis check kro ye command use krke toh output aesa milega
    ┌─[amul@Hacker]─[/usr/bin]
    └──╼ $which dselect
    /usr/bin/dselect

> Ab janah meri packages.list wali file store hai na toh wnha jaakar fir ye command run kro
 
    ┌─[amul@Hacker]─[~]
    └──╼ $sudo dpkg --set-selections < packages.list
    
    # --set-selections = me kuch select kr rha hoon 
    # < packages.list  = aur select jo kr rha hon woh hai packages.list wali file 
  
    ┌─[amul@Hacker]─[~]
    └──╼ $sudo apt-get dselect-upgrade
    # deselect-upgrade = means ki mene jo upr selcet kia usse upgrade kr lo
    
    Note: Finally fir muje ye command run kr dena hai ab jitne bhi mere packages.list
          me hai woh sb naye wale system me install ho jayenge aur update bhi...


> Niche pics dekh skte ho aap jisse aapko pata chalega ki real me kesa lagta hai.

![image](https://user-images.githubusercontent.com/38901699/180937839-f72b9a03-5fde-462e-8012-aff1e8723e12.png)

> Conclusion : hum aese kare kahin par bhi apna system wapis sahi kar skte hai.
      
      
  
  
  
