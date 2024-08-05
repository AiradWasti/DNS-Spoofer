<h1>DNS Spoofer</h1>


<h2>Description</h2>
This Python script sets up a packet manipulation tool using the netfilterqueue and scapy libraries. It binds to NFQUEUE with queue number 0, allowing the interception and modification of network packets. The process_packet function processes each packet, decoding its payload and checking for DNS response layers. If a DNS response is detected and it matches the domain "arh.bg.ac.rs", the response is modified to redirect to the IP address "10.0.0.224". The del_fields function is used to delete specific IP and UDP fields to ensure the packet is reassembled correctly. The modified packet is then reinjected into the network stack. The script continuously runs, processing and modifying packets as specified.
<br />


<h2>Languages and Utilities Used</h2>

- <b>Python</b> 

<h2>Environments Used </h2>

- <b>Kali Linux</b>

<h2>Program walk-through:</h2>

<p align="center">
I made a spoofed Facebook login page redirect hosted on my machines IP address: <br/>
<img src="https://imgur.com/QLSTkhm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
You must run the following commands before running the script:  <br/>
<p align="left">
  - Flushes (deletes) all rules in the iptables chains, essentially clearing any existing firewall rules.  <br/>
  - Inserts a rule at the top of the FORWARD chain to send all forwarded packets to NFQUEUE with queue number 0 for user-space processing.  <br/>
  - Inserts a rule at the top of the OUTPUT chain to send all outgoing packets to NFQUEUE with queue number 0 for user-space processing.  <br/>
  - Inserts a rule at the top of the INPUT chain to send all incoming packets to NFQUEUE with queue number 0 for user-space processing.  <br/>
<p align="center">
<img src="https://imgur.com/HDLjbjJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<p align="center">
The script is ready to run:  <br/>
<img src="https://imgur.com/s7CJ4Zd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<p align="center">  
The DNS spoofer redirects this website:  <br/>
<img src="https://imgur.com/gY9Pk0E.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<p align="center">
When a user goes to "arh.bg.ac.rs", they get redirected to the spoofed facebook page instead:  <br/>
<img src="https://imgur.com/7raE98q.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
