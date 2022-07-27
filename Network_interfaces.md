# Managing network interfaces

 > How to interface up & down


	┌─[amul@Hacker]─[~]
	└──╼ $ip address show
	
	# isse aapko pata chlega ki kitne interfaces hai
	
	┌─[amul@Hacker]─[~]
	└──╼ $ip a
	
	# ye b command se check kar skte ho apne ip address
	
 > Now, ab jis bhi interface ko DOWN krna hai yaa UP krna hai uske liye pehle uska name dekh lo aese kuch names dikhegene apko..[enp2so]-[wlp3s0]-[eth0]-      [eth1] like this toh abhi mere laptop me wifi connected hai mocha ka toh us interface ka name hai "wlp3s0" ab muje issedown karna hai 

	┌─[amul@Hacker]─[~]
	└──╼ $sudo ip link set wlp3s0 down
 	
	# ab wifi wala interface down hogya hoga aur internet access nhi kr paunga
	# me wapis ip address show command use krunga toh usme muje wlp3s0 state down dikhayega 
	
	┌─[amul@Hacker]─[~]
	└──╼ $sudo ip link set wlp3s0 up
	
	# Ab isse up bhi kr lete hai chlo 

> Agar aapke ubuntu me ifconfig command run hota hai jo "net-tools"  me aata hai jisse hum aese install kr skte hai "sudo apt install net-tools" fir uske baad ifconfig type kroge toh output milega jesa hum windows terminal me use krte the.
	
-- Yes, fir aap ifconfig command se bhi interface up & down kr skte hai...
	
	┌─[amul@Hacker]─[~]
	└──╼ $sudo ifconfig wlp3s0 down
	
	┌─[amul@Hacker]─[~]
	└──╼ $ping google.com
	ping: google.com: Temporary failure in name resolution
	
	┌─[✗]─[amul@Hacker]─[~]
	└──╼ $sudo ifconfig wlp3s0 up
	
	┌─[amul@Hacker]─[~]
	└──╼ $ping google.com
	PING google.com (142.250.77.46) 56(84) bytes of data.
	64 bytes from bom07s26-in-f14.1e100.net (142.250.77.46): icmp_seq=1 ttl=116 time=26.7 ms
 
# Assigning static IP addresses

> iske liye hume jaana padega netplan me jisse hum config kar ke apne hisab se ip add de skte hai uske alwa bhi hum dhcp on rkha hai toh on rkh skte hai yaa off rkhna hai toh off bhi thik wesa agar koi department ho toh us hisab se rkh skte hai aur jab ye sara config ho jaye toh hume woh work karane ke liye sudo netplan apply command bhi dena padega uske bad hi hai work karega aur usko apply krne ke baad kuch error naa aaye toh smj lo ki sb sahi ho jayega 

		







# Planning your IP address scheme

> hume office me humara ek planing krna hoga jisme hum ye decide kr paaye ki kis department ko kitne IP dene hai ab maan lo meri office choti hai toh me kese devide krunga mere ip address like me abhi network le rha hoon /24 ka means 254 total IP address milegange muje ab dekho mene niche kese deivde kia hai.	
	
	Network: 192.168.1.0/24 
	# ye mera network hai jo mene define kia ki ye mera network hai aur sara kuch mera /24 ke under hai kind of network i'd

	Network equipment: 192.168.1.1 - 192.168.1.10 
	# fir mere jo bhi router switches yaa wireless point ye sb mera network ka equipment hua mtlb ye sb device ko iske under apna ip doong 1 se 10 ke bich me
	
	Servers: 192.168.1.11 - 192.168.1.99 
	#fir mere company me jo mere servers hai un sb ka ip range me daal doonga 11 se 99 tk mtlb jo bhi server new create karunga uska ip address 11 se 99 ke bich me rhega

	DHCP: 192.168.1.100 - 192.168.1.240 
	# fir me apna DHCP server baaunga toh jo bhi dhcp ke through connect hoga usko ip milega 100 se 240 ke bich me 

	Reservations: 192.168.1.241 - 192.168.1.254 
	# aur jo mere pass bache hua ip address honge usse me  rkhunga reserved taaki koi ussse use nhi kar paye 

> Note : mene dhcp me range dia hai uske alwa baaki sb jo hai range hai woh mene as a refrence di hai kyun ki woh sb toh me khud static dunnga jo mera server ka hoga router ka hoga sb pr jo mere compnay ke users honge woh sidha dhcp se ip le lenge 

