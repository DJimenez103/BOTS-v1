<h2>Description</h2>
Project consists of an APT(Advanced Persistent Threat) Scenario in which an Organization has been defaced. Our goal is to investigate the threat.
<br />


<h2>Languages and Utilities Used</h2>

- <b>Splunk</b> 
- <b>CyberDefenders</b>

<h2>Environments Used </h2>

- <b>Windows 11</b>
- <b>Ubuntu Desktop</b>
- <b>Splunk</b>
<h2>Program walk-through:</h2>

<p align="center">

 <br/>
<img src="https://imgur.com/QEtK51X.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br/>
<img src="https://imgur.com/YSbpY9p.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
By looking at the number of events by “src_ip” that are communicating with “imreallynotbatman.com”, it is safe to determine 40.80.148.42 is the likely IP address. 
<br />
<img src="https://imgur.com/SaS4d4I.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<img src="https://imgur.com/FGdwpII.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
By searching the index and filtering to find data associated with the source type and the source ID, we can look into our destination headers and find the Vulnerability Scanner.
<img src="https://imgur.com/sFXXu0p.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://imgur.com/GekFPP1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://imgur.com/UqasaqX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
A simple "http.url" value search will give us the contact management system
<br />
<img src="https://imgur.com/mBjD8ZY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<img src="https://imgur.com/Eh2ofbk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Searching the "src_headers" values will reveal the name of the file that defaced "imreallynotbatman.com"
<img src="https://imgur.com/EOQJGdB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<img src="https://imgur.com/qsEfYqF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Investigating an event in the "src_headers", the fully qualified domain name (FQDN) associated with this attack is revealed.
<img src="https://imgur.com/ul6oux5.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://imgur.com/jdH8d9x.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
From the previous questions, we know that the IP address “40.80.148.12” conducted a web vulnerability scanning, and “23.22.63.114” hosted the file that defaced the victim’s website.
<img src="https://imgur.com/hCCWWaG.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://imgur.com/8TGlrxg.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
A "whoxy.com search of “Po1s0n1vy APT” yeilds results that point to a person named Lillian Rose
<img src="https://imgur.com/KKxhOKu.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Upon Further investigation of the name "Lillian Rose" we discovered the email associated.
<img src="https://imgur.com/nYRp3Y3.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://imgur.com/K4YCoAR.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
By investigating the IP address of the attacker's domain which we figured out previously in question 6, we see the amount of brute force attacks conducted.
<br />
<img src="https://imgur.com/hkI8TU2.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 
<img src="https://imgur.com/GJ7Hqo1.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
By investigating the "src_ip" that is scanning for vulnerabilities, we can also look for any files by "filename" index within that source IP to find the executable
<br />
<img src="https://imgur.com/Kopt9Ed.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Here, we can see that there are 2 executables, 3791.exe is a more suspicious file upon further investigation
<br />
<img src="https://imgur.com/2aY66sR.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://imgur.com/WTBl1R8.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Now we can investigate the Command Line of the executable to find the Hash we are looking for
<br />
<img src="https://imgur.com/RJ6PFn2.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://imgur.com/hD0ySEH.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Using Virustotal, we can identify domains related to the IP of the host which is "23.22.63.114"
<br />
<img src="https://imgur.com/OEPxm5N.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br ?>
Further investigation of "MirandaTateScreensaver.scr.exe" we can find the SHA256 hash.
<br />
<img src="https://imgur.com/Ao6DZHr.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://imgur.com/XgyNLnR.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Investigating the hash even further will give us the special hex code.
<br />
<img src="https://imgur.com/WXcVzO4.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://imgur.com/vr9qrS8.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Back on Splunk, creating a table to show the "src_ip" password using the "dest_ip" also using the "post"method on the url "/joomla/administrator/index.php" will display the first bruteforce password used.
<br />
<img src="https://imgur.com/LP1e6PL.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://imgur.com/6aaz5hg.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Again creating a table to show the "src_ip" password, we narrow the events down to show the number of coldplay songs that have 6 digits that have been used as a password.
<br />
<img src="https://imgur.com/smygT11.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://imgur.com/63Pe1jO.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Using these commands gives us a count of occurrences a password was used to authenticate.
<br />
<img src="https://imgur.com/LIxeGwm.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Based on answer to Q16
<br />
<img src="https://imgur.com/C2CipzP.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://imgur.com/owTVDPJ.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Using the transaction function, we can group the events where the password "batman" was used.
<br />
<img src="https://imgur.com/N5SnmqJ.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
We can see in the duration field the amount of seconds between the brute force password scan identified the correct password and the compromised login.
<br />
<img src="https://imgur.com/byN15aV.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://imgur.com/znRIWuG.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
A simple stats sum count search using both IPs and the joomla administrator index guves us the count of the unique passwords used in the brute force attack.
<br />
<img src="https://imgur.com/xskeEXW.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://imgur.com/45umyPj.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Based on the number of events related to workstation “we8105desk”, it is safe to say 192.168.250.100 is most likely the IP address associated with host "we8105desk"
<br />
<img src="https://imgur.com/OjD79ev.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://imgur.com/8yeV0pw.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
A simple "cerber" search with Suricata as the source type will help us analyze which suricata signatures were alerted the fewest number of times. Upon further analysis of the "alert.signature_id" field, we can see that 2816783 was the signature ID value.
<br />
<img src="https://imgur.com/k2CzyIU.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://imgur.com/kBhHQ9n.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://imgur.com/bcu4Dym.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://imgur.com/Itz4U9R.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
While investigating the Windowd log, I found a suspicious event in the command line log.
<br />
<img src="https://imgur.com/BVvlIPo.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://imgur.com/Zm81q4N.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Investigating the suspicious event, we used the "eval" command and the "len" function to count the length of characters.
<br />
<img src="https://imgur.com/zfG1KXh.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://imgur.com/syTAAlP.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Using this formula will show us the windows registry log and break it down to show us the registry entry value specific to USB devices.
<br />
<img src="https://imgur.com/sy6HF2W.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Upon investigating the "data" field, we can see that MIRANDA.PRI is the USB key.
<br />
<img src="https://imgur.com/Kgu8KFX.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://imgur.com/ck4DwVC.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
We need to investigate the IP address of the workstation to get the Destination IP of the file server.
<br />
<img src="https://imgur.com/x6xTlOj.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
It is likely the destination IP of the file server is 192.168.250.20.
<br />
<img src="https://imgur.com/ChIfUul.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://imgur.com/UmwBq4Y.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Using the formula we used in Q25 to analyze the vbs scripts, we can simply add the filename to find our answer in the Parent_Process_ID field
<br />
<img src="https://imgur.com/LZjpmUy.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://imgur.com/WSJQfjd.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://imgur.com/L5iHkJs.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Using Bob Smiths hostname, we can then query all text files within Bob Smiths directory.
<br />
<img src="https://imgur.com/eF4o50r.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://imgur.com/gcYDObg.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
We need to use a suspicious domain and in Question 25, we discovered “solidaritedeproximite.org” was indeed suspicious.
<br />
<img src="https://imgur.com/eEnhpL9.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Now we can investigate the "filename" field to find the file name.
<br />
<img src="https://imgur.com/Kg1ZAfI.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://imgur.com/FKgJhid.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://imgur.com/ZuYuD1k.png)" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
