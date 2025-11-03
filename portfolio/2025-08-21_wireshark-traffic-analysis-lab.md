# Title: Wireshark Traffic Analysis – Identification & Navigation

**Date:** 2025-08-21
**Objective:** Analyze, identify, and describe network traffic PCAPs through Wireshark.

**Environment:** TryHackMe – “Wireshark: Traffic Analysis” room  
**Tools Used:** Wireshark


## Processes
1. Filtered for the total of the "TCP Connect" scans
   - "tcp.flags.syn==1 and tcp.flags.ack==0 and tcp.window_size > 1024"
     # BREAKDOWN
     - **"tcp.flags.syn==1"** Means to filter for TCP packets that have the "SYN" flag set
     - **"tcp.flags.ack==0"** Means to filter for TCP packets that doesn't have the ACK flag set
2. 



## Findings
- Source IP: `203[.]0[.]113[.]55`
- Repeated connection attempts over port 22.

## Outcome
Successfully detected brute-force behavior; adjusted IDS thresholds to reduce noise.

## Lessons Learned
Improved understanding of TCP flags and connection patterns in attack scenarios.
