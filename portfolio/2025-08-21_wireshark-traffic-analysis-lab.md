# Wireshark Traffic Analysis – Identification & Navigation

**Date:** 2025-08-21
**Objective:** Analyze, identify, and describe network traffic PCAPs through Wireshark.

**Environment:** TryHackMe – “Wireshark: Traffic Analysis” room  
**Tools Used:** Wireshark


# Processes
# 1. Filtered for the total of the "TCP Connect" scans
   - "tcp.flags.syn==1 and tcp.flags.ack==0 and tcp.window_size > 1024"
     ## BREAKDOWN
     - **"tcp.flags.syn==1"** Means to filter for TCP packets that have the "SYN" flag set
     - **"tcp.flags.ack==0"** Means to filter for TCP packets that doesn't have the ACK flag set

<img width="1400" height="792" alt="image" src="https://github.com/user-attachments/assets/2ea35778-9568-4764-97c5-6fac96fe980c" />


# 2. Figuring out which nmap scan (TCP, SYN, UDP) type was used to scan port 80
   - "tcp.port == 80"
     ## BREAKDOWN
     - Filtering for the port equaling to 80 (HTTP) will show all traffic communication utilizing that specific port
     - As shown in the image, the nmap scan signature is using a TCP connect scan and **shutting down the connection shortly after**
     - A closed TCP port would provide (SYN> , <RST, ACK)
<img width="1400" height="271" alt="image" src="https://github.com/user-attachments/assets/3138e453-5834-468c-aa0e-e1cbcc2f3e46" />


# 3. Discovering the total ammount of UDP scans that resulted in a "Closed port" message
   - "icmp.type==3 and icmp.code==3"
     ## BREAKDOWN
     - "icmp.type==3" would mean to show results where the **destination is unreachable**
     - While using "type==3", "code==3" means "Port unreachable", meaning that the application / service at the specific UDP port isn't listening
     - **If a UDP port is closed**, most hosts respond with a type 3, code 3 message

<img width="1400" height="792" alt="image" src="https://github.com/user-attachments/assets/a63576cc-02fa-4c5b-ab8d-5ac2ce17c83c" />



    

## Findings
- Source IP: `203[.]0[.]113[.]55`
- Repeated connection attempts over port 22.

## Outcome
Successfully detected brute-force behavior; adjusted IDS thresholds to reduce noise.

## Lessons Learned
Improved understanding of TCP flags and connection patterns in attack scenarios.
