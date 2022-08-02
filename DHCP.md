# Setting up a DHCP server for serving IP addresses
    sudo apt install isc-dhcp-server
    
    systemctl status isc-dhcp-server 
    # ye wala status filhal aapko disable dikhayega mera mtlb ki failed dikhayega 
    
    sudo systemctl stop isc-dhcp-server
    # fir stop kr do kyun ki hum ab isme config krenge 
    
    sudo systemctl stop isc-dhcp-server6
    sudo systemctl disable isc-dhcp-server6
    # haan ipv6 toh abhi stop hi kr do kyun ki hum sb toh ipv4 me kr rhe hai filhal 
    
> sudo cat /etc/dhcp/dhcpd.conf -- isme aapko dhcp ki bydefault config milegi jisse ab hum change kr ke apne hisab se krenge 
    
    sudo mv /etc/dhcp/dhcpd.conf /etc/dhcp/dhcpd.conf.orig 
    #isliye me pehle uska copy le leta hoon taaki kuch gadbad ho toh woh as it is rhe
    
> Ab hum open krenge nano /etc/dhcp/dhcpd.conf aur isme kuch config krenge

    default-lease-time 43200;                       / 43200 seconds hai mtlb 12 ghnta hua toh kisi bhi user ko ip milne ke baad 12 ghnta tk rhega  
    max-lease-time 86400;                           / 86400 seconds mtlb hau ki 24 ghnta agar kisi ko ip assign hua hai toh max to max 24 ghta rhe
    option subnet-mask 255.255.255.0;               / jo bhi user ko ip milega uska bydefault mask yahi set ho jayega
    option broadcast-address 192.168.1.255;         / fir jo bhi user ko ip milega usse hum keh rhe hai ki broadcast id yhi rahega
    option domain-name "local.lan";                 / fir ye hua ki domain-name mtlb ki mera usrname hau amul toh uska mtlb ye hua ki amul local.lan ho jayega
    authoritative;                                  / ye ek term hotu haijo hume deni hoti hai uske dusri bi ek term hoti hai ki unauthortatvi jisse abhi hum pdhenge nhi par aage dekhenge
    subnet 192.168.1.0 netmask 255.255.255.0        / hum ynha par apna network block dikha rhe hai ki isse k ander mera dhcp run kr rha hai 
    {                                               / 
        range 192.168.1.100 192.168.1.240;          / aur is block ke ander muje konse ip apne user ko dene hai wh define kro 
        option routers 192.168.1.1;                 / fir network devices ko me konsa doonga woh set kro jese router switches like this
        option domain-name-servers 192.168.1.1;     / aur mera domain-name server ka ip mera router ka hi gateway hai like this 
    } 
    
> sudo nano /etc/default/isc-dhcp-server  << isse open krna hoga aur usme interface define krna hoga ki muje is interface par set krna hai janha mere saare user connectd honge
> usme muje > INTERFACESv4="" < aesa dekhne ko milega bas muje fir isme mera apna exit interface set krna hai > INTERFACESv4="eth2" < like this

> ab sb done hua dekhte hai aage ka hum 

    sudo systemctl start isc-dhcp-server 
    # ab start kro ab dekho ho jayega active dikhega
    sudo systemctl status isc-dhcp-server 
    
> ab toh app apne user me jaakr windows ho to obtain with ip address automatically kro aur ip mil jayega fir ubuntu ho toh usme aap dhclient eth1 kr do mtlb aapka jo bhi eth2 eth3 anything mil jayega 

> ab aapko dekhna hai ki kitne logo ko mila hai ip aur konse users ko mila hai woh sb ip lease information milegi apko 

    /var/lib/dhcp/dhcpd.leases
    
    # isme aapko sb dikhega user ka name fir kya ip milega hai us user ko aur uska kitna time bacha woh ip assign wala sb kuch 
    
    
