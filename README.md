# NpingSnort

Use Snort to Detect Packets with Flags Set by Nping

In this lab I set flags in a data packet using nping and wrote a snort rule to alert it for threats.  
There are 8 possible flags can be set in a tcp packet: CWR, ECN, URG, ACK, PSH, RST, SYN, and FIN. CWR (Congestion Window Reduced):  Set by an ECN-Capable sender when it reduces its congestion window (due to a retransmit timeout, a fast retransmit or in response to an ECN notification. URG (Urgent): Segment is urgent and the urgent pointer field carries valid information.

I started first ran Dos command nping --flags CWR, URG --tcp -p 80 scanme.nmap.org. This command sends tcp packets to scanme.nmap.org, the flags CWR and URG are set in the packets.
 <img width="851" height="305" alt="image" src="https://github.com/user-attachments/assets/56b96c63-7fb5-4646-a9d5-c147122312f4" />


I then verified the flags in the packets by starting Wireshark to capture packets then run the Dos command, and after it is done, stop the capture. I could see the CWR and URG flags in TCP layer, from Wireshark.
 <img width="568" height="436" alt="image" src="https://github.com/user-attachments/assets/441025e2-d843-4f5a-b095-da3d87c30f4e" />

Then I saved the packets from Wireshark as nping_data in my snort\bin folder.
 <img width="527" height="467" alt="image" src="https://github.com/user-attachments/assets/73fb7845-1912-445c-9e82-20acc44533e0" />


Using note pad I then wrote a snort rule to detect these packets with flags CWR and URG set.
 <img width="827" height="92" alt="image" src="https://github.com/user-attachments/assets/cae41c1b-60f5-4e9e-ab95-d9bf84276df3" />


I then ran the Dos command dir to make sure the rule.txt file is in snot\bin folder.
 <img width="491" height="444" alt="image" src="https://github.com/user-attachments/assets/ca485406-287e-4188-9c7b-0b69df72de32" />


I ran snort to check the results. 
 <img width="710" height="632" alt="image" src="https://github.com/user-attachments/assets/cfe59fc9-61f9-447d-96d4-ea23215033f0" />


From snort\bin\log, opened the alert.ids on notepad and several packets are detected.
 <img width="492" height="463" alt="image" src="https://github.com/user-attachments/assets/e94da583-4a31-440f-aba0-8cb5b7db4149" />


I’m going to do the same thing but this time im going to set the flags PSH and RST in the packets to the same target.
<img width="867" height="267" alt="image" src="https://github.com/user-attachments/assets/7cf8956e-5c93-46ac-85ea-29020c973dfe" />

 
Set the flags using nping then wrote the snort rule ad produced the rules from the alert.ids 
 <img width="703" height="702" alt="image" src="https://github.com/user-attachments/assets/69763544-f525-40b9-8e20-1b351fdd663d" />
<img width="555" height="513" alt="image" src="https://github.com/user-attachments/assets/e11fd8ec-63af-40f5-8f55-a942d1624835" />
<img width="547" height="479" alt="image" src="https://github.com/user-attachments/assets/a3d124e6-779f-4274-8a62-45fa27ec8597" />

 
 


