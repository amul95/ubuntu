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
 

