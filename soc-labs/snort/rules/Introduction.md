Introduction

Intrusion Detection System (IDS)

IDS is a passive monitoring solution for detecting possible malicious activities/patterns, abnormal incidents, and policy violations.

Two main types of IDS
Network Intrusion Detection System (NIDS
Host-based Intrusion Detection System (HIDS) -

Intrusion Prevention System (IPS)

IPS is an active protecting solution for preventing possible malicious activities/patterns, abnormal incidents, and policy violations.

  There are four main types of IPS systems;

    Network Intrusion Prevention System (NIPS)
    Behaviour-based Intrusion Prevention System (Network Behaviour Analysis - NBA) 
    Wireless Intrusion Prevention System (WIPS)
    Host-based Intrusion Prevention System (HIPS)

    key concept
 SNORT is an open-source, rule-based Network Intrusion Detection and Prevention System (NIDS/NIPS). It was developed and still maintained by Martin Roesch, open-source contributors, and the Cisco Talos team. 

Capabilities of Snort;

    Live traffic analysis
    Attack and probe detection
    Packet loggingji
    Protocol analysis
    Real-time alerting
    Modules & plugins
    Pre-processors
    Cross-platform support! (Linux & Windows)

Parameter 	Description
-v 	Verbose. Display the TCP/IP output in the console.
-d 	Display the packet data (payload).
-e 	Display the link-layer (TCP/IP/UDP/ICMP) headers. 
-X 	Display the full packet details in HEX.
-i 	This parameter helps to define a specific network interface to listen/sniff. Once you have multiple interfaces, you can choose a specific interface to sniff.  
Parameter 	Description
-l 	

Logger mode, target log and alert output directory. Default output folder is /var/log/snort

The default action is to dump as tcpdump format in /var/log/snort
-K ASCII 	Log packets in ASCII format.
-r 	Reading option, read the dumped logs in Snort.
-n 	Specify the number of packets that will process/read. Snort will stop after reading the specified number of packets.

Parameter 	Description
-c 	

Defining the configuration file.
-T 	Testing the configuration file.
-N 	Disable logging.
-D 	Background mode.
-A Alert mode

    lab setup
ubuntu@ip-10-201-97-4:~/Desktop/Task-Exercises$ sudo ./traffic-generator.sh
- OS / Distro used:  ubuntu
- Tools installed:  snort  Version 2.9.7.0 
- Sample files or targets:  
    hands on practice

    ubuntu@ip-10-201-63-234:~/Desktop/Task-Exercises$ cd Exercise-Files
ubuntu@ip-10-201-63-234:~/Desktop/Task-Exercises/Exercise-Files$ ls
TASK-5  TASK-6  TASK-7  TASK-8  TASK-9
ubuntu@ip-10-201-63-234:~/Desktop/Task-Exercises/Exercise-Files$ cd TASK-6/
ubuntu@ip-10-201-63-234:~/Desktop/Task-Exercises/Exercise-Files/TASK-6$ sudo snort -dev -K ASCII -l

ran sudo ./traffic-generator.sh

cd 145.254.160.237
(supposed pic of traffic generated)
Read the "snort.log.1640048004" file with Snort; what is the referer of the 4th packet?
snort -r snort.log.1640048004 -n 4 -X

http://www.ethereal.com/development.html