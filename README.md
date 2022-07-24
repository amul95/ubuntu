# Learn Linux

-- short me mene topics sb smjaye hue hai aapko asani rhaegi sajmne me toh shuru krte hai...

# Head & Tail Command for Logs 

-- humne logs kyaa hote hai ye jaana hai aaj tak mtlb ki ki system jo process krti hai uski logs hote hi hai bas hume usse dekhna hota hai uske path me jaa kar jese ki windows se event logger hota hai usse open krke pata chelga ki is windows systrm kis time kyaa hua hai thik wesa linux me bhi hota hai uske logs store hote hai " /var/logs/syslog " toh hume ye pata chal gya chlo ab hume ye dikkt hogi ki hum jab bhi ye open krenge toh bhot saare logs hume dikhenge ho skta hai 500 yaa 1000 yaa fir 20k logs ho skte hai toh hume thodi sare logs ki zarurt hai hme toh logs tb dekhene hote hai jab kuch issue ho jb koi service sahi se work naa kre aur hume usa error kyaa hai usse kaha issue ho rha hai woh sb find krne ka logs dekhte hai ki hum smj paaye isliye maan lo humne koi service start ki aur woh nhi hui toh hum turnt logs check krenge zaahir si baat hai ki woh sb niche hi honge mtlb latest wale logs toh niche hi honge naa jese 1st log 1 number se start hua that means ki niche uske baad saare naye wale niche hi honge toh muje sirf perticular service ka dekhna hai maan lo toh me grep krke bhi dekh skta hoon aur gar wesa nhi krta hoon head laga kar dekh skta hoon tail laga kar dekh skta hoon 


Head bole toh upr ka aur tail bole toh niche kaa ab head aur tail me hum logs ka output sirf 10 line ka milega hum head use kre syslog dekhenge toh upr ke 10 line dikhenge yaa upr ke 10 logs jo starting me hai aur hm tail laga kar logs dekhenge toh hum last wale logs dikhenge 10 logs
ab command kese dena 

      ┌─[✗]─[amul@Hacker]─[~]
      └──╼ $ sudo head /var/log/syslog
      
      Jul 24 12:11:59 Hacker systemd[1]: logrotate.service: Deactivated successfully.
      Jul 24 12:11:59 Hacker systemd[1]: Finished Rotate log files.
      Jul 24 12:11:59 Hacker systemd[1]: Startup finished in 4.814s (firmware) + 6.018s (loader) + 7.755s (kernel) + 1min 12.878s (userspace) = 1min           31.466s.
      Jul 24 12:11:59 Hacker systemd[1]: logrotate.service: Consumed 2.002s CPU time.
      Jul 24 12:11:59 Hacker gnome-session[4602]: libEGL warning: DRI2: failed to authenticate
      Jul 24 12:11:59 Hacker wpa_supplicant[784]: wlp3s0: CTRL-EVENT-SIGNAL-CHANGE above=0 signal=19 noise=-94 txrate=135000
      Jul 24 12:11:59 Hacker gnome-session[4580]: gnome-session-check-accelerated: GLES Helper exited with code 512
      Jul 24 12:11:59 Hacker gnome-session[4579]: gnome-session-binary[4579]: GLib-GIO-CRITICAL: g_bus_get_sync: assertion 'error == NULL || *error ==         NULL' failed     
      Jul 24 12:11:59 Hacker gnome-session[4579]: gnome-session-binary[4579]: GLib-GIO-CRITICAL: g_bus_get_sync: assertion 'error == NULL || *error == 
      NULL' failed
      Jul 24 12:11:59 Hacker gnome-session-binary[4579]: GLib-GIO-CRITICAL: g_bus_get_sync: assertion 'error == NULL || *error == NULL' failed
      
      ┌─[amul@Hacker]─[~]
      └──╼ $ sudo head /var/log/syslog | wc -l
      10
      
Dekha humne ki upr ke starting ke hume logs dikhe aur woh sirf 10 ab hum tail use karenge 

      ┌─[amul@Hacker]─[~]
      └──╼ $sudo tail /var/log/syslog
      Jul 24 16:29:22 Hacker wpa_supplicant[784]: wlp3s0: CTRL-EVENT-SIGNAL-CHANGE above=0 signal=-22 noise=-94 txrate=1000
      Jul 24 16:29:22 Hacker wpa_supplicant[784]: wlp3s0: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-21 noise=-94 txrate=1000
      Jul 24 16:29:22 Hacker wpa_supplicant[784]: wlp3s0: CTRL-EVENT-SIGNAL-CHANGE above=0 signal=-21 noise=-94 txrate=121500
      Jul 24 16:29:22 Hacker wpa_supplicant[784]: wlp3s0: CTRL-EVENT-SIGNAL-CHANGE above=0 signal=-21 noise=-94 txrate=121500
      Jul 24 16:29:22 Hacker wpa_supplicant[784]: wlp3s0: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-21 noise=-94 txrate=121500
      Jul 24 16:29:22 Hacker wpa_supplicant[784]: wlp3s0: CTRL-EVENT-SIGNAL-CHANGE above=0 signal=-21 noise=-94 txrate=121500
      Jul 24 16:29:22 Hacker wpa_supplicant[784]: wlp3s0: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-21 noise=-94 txrate=121500
      Jul 24 16:29:22 Hacker wpa_supplicant[784]: wlp3s0: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-21 noise=-94 txrate=121500
      Jul 24 16:29:22 Hacker wpa_supplicant[784]: wlp3s0: CTRL-EVENT-SIGNAL-CHANGE above=0 signal=-21 noise=-94 txrate=121500
      Jul 24 16:29:22 Hacker wpa_supplicant[784]: wlp3s0: CTRL-EVENT-SIGNAL-CHANGE above=0 signal=-21 noise=-94 txrate=121500
      
      ┌─[amul@Hacker]─[~]
      └──╼ $sudo tail /var/log/syslog | wc -l
      10

See, head mtlb logs me jo upar honge woh 10 count krke aayenge aur tail me niche wale latest yaa last wale 10 logs dikhenge ap upr dono ka diff dekh hi skte ho...


Mere me logs dekho total 12812 hai lines ke hai ab me pura open toh krunga nhi aur sirf cat command use krunga fir bhi muje sare hi show honge issliye zarurt pada head & tail ka ki kum dikhenge aur apna kaam ho jayega ab aur bhi kuch hai aage dekhenge

      ┌─[✗]─[amul@Hacker]─[~]
      └──╼ $sudo cat /var/log/syslog | wc -l
      12812
      
Ab muje aesa chahiye ki me sirf selected service ka logs dekhu muje dekhna hai ssh kaa toh me kya krunga pehle jb muje head & tail ka kuch ni pata me command type krunga ye wala 

      sudo cat /var/log/syslog | grep ssh
      # aur isse muje shy ssh wale logs dikh bhi jaayege pr ye pure 12k logs ke ander total ssh wale dikhayega pr muje toh abhi ke latest dekhne hai 
        toh me kya krunga 
        
      sudo tail /var/log/syslog | grep ssh 
      # ye command type krunga hai naa pr isse kuch hasil nhi hoga output blank hi aayega
      
      # aesa isliye kyun ki mene tail likha mtlb ki niche wale 10 logs aur usme bhi mene grep ssh likha toh mtlb ye hua ki woh check krega ki 
      niche ke total 10 logs me ssh hai toh hi output do wrna blank par kyaa ye sahi baat hai itne sare logs hai kahin kuch miss ho gya toh isliye 
      hum thda advcanced command lagayenge 
      
      sudo cat /var/log/syslog | grep ssh | tail 
      # yes finally ye command work krega humne isse ye kaha ki logs me jao sare kesare 12k logs me ssh wale logs find kro aur sirf jo last ho ssh
      wale logs woh hi output me do mtlb ki jab ssh ko logs khtm ho chuke ho toh woh last wale 10 show krega not ki abhi jo logs me niche 10 honge woh 
      
      sudo cat /var/log/syslog | grep ssh | head
      # hume sirf upr ke chahiye mtlb jab bhi ye ssh ke log start hue ho tb se lekar total 10 logs hi chahiye 
      
Abhi tak hm dekhe ki humne lagatar 10 ki baat ki hme sirf ouput me 10 hi milte hai pr ab hm apne hisab numbers bhi change kar skte hai 

      ┌─[amul@Hacker]─[~]
      └──╼ $sudo head -n 5 /var/log/syslog
      
      Jul 24 12:11:59 Hacker systemd[1]: logrotate.service: Deactivated successfully.
      Jul 24 12:11:59 Hacker systemd[1]: Finished Rotate log files.
      Jul 24 12:11:59 Hacker systemd[1]: Startup finished in 4.814s (firmware) + 6.018s (loader) + 7.755s (kernel) + 1min 12.878s (userspace) = 1min 
       31.466s.
      Jul 24 12:11:59 Hacker systemd[1]: logrotate.service: Consumed 2.002s CPU time.
      Jul 24 12:11:59 Hacker gnome-session[4602]: libEGL warning: DRI2: failed to authenticate
      
      ┌─[amul@Hacker]─[~]
      └──╼ $sudo tail -n 5 /var/log/syslog
      
      Jul 24 16:46:43 Hacker wpa_supplicant[784]: wlp3s0: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-22 noise=-94 txrate=1000
      Jul 24 16:46:43 Hacker wpa_supplicant[784]: wlp3s0: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-22 noise=-94 txrate=1000
      Jul 24 16:46:43 Hacker wpa_supplicant[784]: wlp3s0: CTRL-EVENT-SIGNAL-CHANGE above=0 signal=-22 noise=-94 txrate=1000
      Jul 24 16:46:43 Hacker wpa_supplicant[784]: wlp3s0: CTRL-EVENT-SIGNAL-CHANGE above=0 signal=-22 noise=-94 txrate=1000
      Jul 24 16:46:43 Hacker wpa_supplicant[784]: wlp3s0: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-22 noise=-94 txrate=65000

-- Finally dekhe aap mene "-n" use kia hai that means ki muje bas 5 hi logs dikhenge chahe hum head ya tail use kre hume sirf number define krna hai utne hi logs hume dikhenge aap 5 ki jgh 50 bhi likh skte ho 


# Follow Logs

- Ye zaruri hai aur kamal ka bhi " -f " means follow bas itna fitt kr lo 

sb se pehle 2 terminal open kr lo ubuntu me aur ek terminal me ye command type kro 
  
     ┌─[amul@Hacker]─[~]
     └──╼ $ sudo tail -f /var/log/syslog
     # ye commnd dekar is terminal ko chor do aur dusre terminal maan lo aap ssh service ko restart kr lo 
     
     ┌─[✗]─[amul@Hacker]─[~]
     └──╼ $ systemctl restart ssh 
     # ab jo pehle wale terminal me mene f wala command use kia tail ke aage toh woh monitor kr rha hoga aur woh tail mtlb niche wale latest logs ke liye 
     toh hm jb bhi kuch karenge uska output hme sidha woh dusre terminal me show krega ki ssh restart hua fir connect hua etc...
     
     ┌─[amul@Hacker]─[~]
     └──╼ $ sudo tail -f /var/log/auth.log
     # auth.log start kia mtlb jab bhi kahin user n password wala login hoga toh ye logs me store hoga chahe me ssh se login try kru yaa fir apne user
     ko switch kru toh woh sb is log me store hoga aur hm montir kr skte hai ek terminal me -f wala command de kar dusre kisi terminal me jaakr 
     apne user ka login kro su - centos yaa su - amul toh woh logs me show krega aacha centos aur amul ye dono mere user hai aapke alag ho skte hai 
     
Jab bhi aap "-f" wala command do tb us terminal me 5 ya 10 bar enter kr dena taaki hume jo logs dikhe woh alag se ho already jo monitor ho rhe hai uske 
uske sath na chle jaaye..



    

        
