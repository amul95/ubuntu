# Samba 

> jese hum windows me apna FTP server create krte the thik wesa agar muje ubuntu me krna ho toh aur woh bhi apne ubuntu server me taaki jo users hai woh aaceess kr paaye mene file server ko aurf data ko copy kr sake fir store kr sake anything 

> A Samba file server enables file sharing across different operating systems over a network. It lets you access your desktop files from a laptop and share files with Windows and macOS users.

# Installing Samba

    sudo apt update
    sudo apt install samba
    
    
    whereis samba
    # iska output kyaa aana chahiye woh niche likha hai 
    
    Output : aesa dikhega whereis samba likhoge toh
    samba: /usr/sbin/samba /usr/lib/samba /etc/samba /usr/share/samba /usr/share/man/man7/samba.7.gz /usr/share/man/man8/samba.8.gz
    
    
# Setting up Samba

> muje kyaa share krna hai sb users ke liye ?? so me ek folder create kr leta hoon jisk name 'sambashare' par aaplog apne hisab se rakh skte ho name...
> jo mene folder create kia hoga usse hum share karenge sb ke liye aur usme sb chize store krenge taaki jab bhi hm chahe usko access krke usme se le ske
  
    mkdir /home/amul/sambashare/
    # mene folder create home me amul user me 

> ab humne folder toh create kr dia par ab samba me bhi mention bhi krna padega ye folder tb bhi sb log usse use kr payenge 

    sudo nano /etc/samba/smb.conf
    # ye rhi samba ka confing file isse open kro apne nano yaa vim editor me 
    
    [sambashare]
    comment = Samba on Ubuntu
    path = /home/username/sambashare
    read only = no
    browsable = yes
    
    # comment = jo dena chahe de de
    # path    = jis bhi folder ko hume share krna hai woh path 
    # ready only = ynha baat hui permissino ki 
    # browsable   = agar hume users windows wale hai fir ubuntu wale hai toh ubntntu me bhi smb access kr ke file isliye yes 
    
> Configuration toh done ab service ko restart kar do 

    sudo service smbd restart
    
    sudo ufw allow samba
    # de hi dena ye command 
    
# Setting up User Accounts and Connecting to Share
> ab koi user ye file server use krna chahega toh woh ip likhega uske baad usse credencials bhi puche jaayenge na kyun ki jo humara server ka login hai usse thodi woh open hoga hum username mention krna padega agar sb log woh username daalenge jo humne menstion kia tb hi open hoga 

    sudo smbpasswd -a amul
    # mera system me username amul hai means me amul user hoon isliye mene mera name dia aap bi apne username daalna 
    # aur haan server par jo user created hai woh hi username dalna hai uske alwa baaki sb open krne ke liye woh same username hi dalenge apna nhi daal skte aur open bhi nhi hoga usse 
  
# Client-SIde
> aap bas same network me hone chahiye aur upr ke saare steps clear hone chahiye server side ab hum dekhenge is file server ko apne side kese hum access krte hai 

--- if Ubuntu user

![image](https://user-images.githubusercontent.com/38901699/182024056-67262df8-5dc4-46f2-bbb4-1e36021a9508.png)

> is imsage aap dekhna niche Connect to server likha hai yes whi hume server ka ip likha hai aur enter krna hai ttoh hum server wala woh folder sambashare wala use kr payenge apni side se 

--- if mac user

> isme finder menu me joage toh Connect to server wala dikhega usme same ubuntu jesa likh do ip address aur foldername 

--- if window user

> isme bs window explore open kro aur upr addrss bar me likh do "\\10.0.0.14\sambashare" aur enter kro fir aapse puche user & password isme ap server me jo username amul dia tha woh amul likho aur password me jo set kia tha woh passwd likho 


Note : bhot easy hai samba aur usse hum as a mac user as a linux user aur as a window user bhi hai toh bhi hum ubuntu server ko access kr skte hai 
       access mtlb use samba file server ko access kr skte hai 
       
       
       
# Window side FTP

-- humne ubuntu me samba kiaa toh muje windows me ftp jo create kia tha woh yaad aa gya me bata deta hoob ek baar

Step:1 = control panel me jakar "Turn Windows feutures on or off" ye open kro 
Step:2 = fir windows features ka box open hoga usme Internet Information Services ko find karke usse expand kro usme FTP server hoga usse bhi expand kro aur uske under FTP Extensibilty aur FTP service dono ko tik kr do 
Step:3 = fir 'Administrativ Tools' open kro woh milega aapko Control Panel ke ander System & Security me administrative tools 
Step:4 = ussme fir dekho Internet information Services(IIS) Manager usse open kro 
Step:5 = ab usme Sites likha hua hoga expand kroge toh usse open kro aur right side panel me likha hoga Add FTP site usse click kr lo 
Step:6 = site ka name jo mann chhe do fir path puchega usme aap jo bhi folder ko share krna hai uska path de do 
step:7 = fir next kroge toh binding puchega toh jo current jo ip hai abhi windows me select kr lo aur port as it is rehne do 
Step:8 = niche ssl me 'No SSL' pr click kr do aur uaur Start FTP site automatically pr bhi click kr d then next 
Step:9 = fir authentication aayega usme Basic pr click krna 
Step:10 = Authorizatin me specified user ko select kr do niche user ka name mentions kr dena mera abhi windows me amul hai toh me amul likhung
Step:11 = Fir finish kr do 
Step:12 = ab firewall me jao aur Allow programs to communicate throgh windows firewall pr click kro use open krke usme FTP server ka line find kro aur uske samne dono me tick kr do fir enter


Note : ab mene amul user likha jo mere me already bana hua tha par new user create krkke use bhi usme mention kr skta hoon authorizarion rule me jaakr jo muje FTP site pr milega

ab maan lo mene payal user new create kia ab me us folder pr jaunga usme right click krunga fir properties me jaunga usme security tab ko click krunga fir usme Edit me jaunga Add pr click krunga aur Payal likhuda fir checknames krunga then enter 
aur usse me sb allow kr doonga mtlb ki tik kr doonga 

bas ab me as amul ke alwa payal aur uska passswd use krke bhi access kar skta hoon 


# Beyond Network

> ye sb jo hua woh to same network me hua par me kahu aur hoon uar muje apna FTP access kn hai yaa apna samba aaccss krna hai toh kya krunga 

> me apne router admin page par jaunga usme internet me jaakr security me jaunga port forwarding me niche image me dekh lo wese type krunga

![image](https://user-images.githubusercontent.com/38901699/182024980-59991a7e-374c-4500-8a59-b1f09434e9ae.png)

-- image me total do filed hai ek hi FTP ka jo mene windows me create kia aur dusra hai samba ka jo mene ubuntu server me banaya 

-- baaki sb toh smj  aa gya hoga kyun ki image me pata chal hi gya hoga fir bhi thoda clear kr doon 

Name : jo bhi service hai uska name asani rhega smjne me 
Protocol : TCP aayega mostly kyun ki FTP aur samba ye sb TCP ke under kaam krte hai 
Wan Connection : isme aapka jo inernet connection hoga woh show krega 
Wan Host IP address : isme dono me 0.0.0.0 hi rehne dena kun ki iska mtlb hai ALL mera DHCP hai public ip toh woh bdlta rhega static hota toh mention kr deta
                      pr dhcp hai toh badlt rhega aur 0.0.0.0 mtlb ALL hota hai 
LAN Host : ye important hai mtlb mera server ka ip janha pr FTP ya samba chala rha hoob 
           samba me mene ubuntu desktop ka ip dala jo muje local wala mila tha NAT kr ke 
           FTP me windows ka dla mene jo muje private ip mila hai NAT se
WAN Port : iske bina toh kuch hoga hi nhi 
           FTP ka 21 hai 
           Samba ka  hai 139 aur 445 
LAN Port : sare de do kyun ki risk kyun lena 

Note : ab hume kahin aur se use krna hai toh hm private IP nhi daal skte hai hume public ip dalna hoga abhi mera public ip hai '27.57.172.249'
       toh ab ye use krna hai muje ftp aur samba ke liye apne liye jese upr sb user me ftp://27.57.172.249 likhna hai ab pehle hum sirf ftp:10.0.0.14 aese private likhte hai toh chlta hai kyun ki tb hum same network me the 

# Sharing With Android Device

-- ab mera ubuntu OS hai usme mene samba share kiaa apna ek folder par me apne android me dekhna chahta hoon toh kese dekh paunga uske liye FTP use nhi kr skta kyun ki uska port 21 hai aur samba 139 aur 445 ha toh ab kyaa ???

-- simple hai x-plore  krke ek app download kr lo playstore se usme aap pehle FTP ka option use krte hai ab uske niche dekhna LAN wala option hoga usme aap apna server ip jo ubuntu ka hai aur jo user create kia hai woh daal do passwd bhi aur IP local daalna jab same network me ho aur aapko kahi aur se krna ho toh public daal dena uske liye kya krna hai upr hai hi,


