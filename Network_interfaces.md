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
