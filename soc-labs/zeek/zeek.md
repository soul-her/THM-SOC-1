Zeek (formerly Bro) is an open-source and commercial passive 
Network Monitoring tool (traffic analysis framework) developed by Lawrence Berkeley Labs.
Zeek differs from known monitoring and IDS/IPS tools by providing a wide range of detailed 
logs ready to investigate both for forensics and data analysis actions. Currently, Zeek provides 
50+ logs in 7 categories.

Main Zeek command line parameters are explained below;
Parameter	Description
-r	 Reading option, read/process a pcap file.
-C	 Ignoring checksum errors.
-v	 Version information.
zeekctl	ZeekControl module.

Category
	Command Purpose and Usage 
	Category
	Command Purpose and Usage 
Basics
	

View the command history:
ubuntu@ubuntu$ history

Execute the 10th command in history:
ubuntu@ubuntu$ !10

Execute the previous command:
ubuntu@ubuntu$ !!
	Read File	


Read sample.txt file:
ubuntu@ubuntu$ cat sample.txt

Read the first 10 lines of the file:
ubuntu@ubuntu$ head sample.txt

Read the last 10 lines of the file:
ubuntu@ubuntu$ tail sample.txt

Find
&
Filter
	


Cut the 1st field:
ubuntu@ubuntu$ cat test.txt | cut -f 1

Cut the 1st column:
ubuntu@ubuntu$ cat test.txt | cut -c1

Filter specific keywords:
ubuntu@ubuntu$ cat test.txt | grep 'keywords'

Sort outputs alphabetically:
ubuntu@ubuntu$ cat test.txt | sort

Sort outputs numerically:
ubuntu@ubuntu$ cat test.txt | sort -n

Eliminate duplicate lines:
ubuntu@ubuntu$ cat test.txt | uniq

Count line numbers:
ubuntu@ubuntu$ cat test.txt | wc -l

Show line numbers
ubuntu@ubuntu$ cat test.txt | nl
	Advanced
	


Print line 11:
ubuntu@ubuntu$ cat test.txt | sed -n '11p'

Print lines between 10-15:
ubuntu@ubuntu$ cat test.txt | sed -n '10,15p'

Print lines below 11:
ubuntu@ubuntu$ cat test.txt | awk 'NR < 11 {print $0}'

Print line 11:
ubuntu@ubuntu$ cat test.txt | awk 'NR == 11 {print $0}'
Special	
Filter specific fields of Zeek logs:
ubuntu@ubuntu$ cat signatures.log | zeek-cut uid src_addr dst_addr
Use Case	Description

sort | uniq
	Remove duplicate values.

sort | uniq -c 
	Remove duplicates and count the number of occurrences for each value.

sort -nr
	Sort values numerically and recursively.

rev
	Reverse string characters.

cut -f 1
	Cut field 1.

cut -d '.' -f 1-2
	Split the string on every dot and print keep the first two fields.

grep -v 'test'
	Display lines that  don't match the "test" string.

grep -v -e 'test1' -e 'test2'
	Display lines that don't match one or both "test1" and "test2" strings.

file  
	View file information.

grep -rin Testvalue1 * | column -t | less -S
	Search the "Testvalue1" string everywhere, organise column spaces and view the output with less.

(snort1.png)
in here as we go and check the host name 

An alert triggered: "Anomalous DNS Activity".

The case was assigned to you. Inspect the PCAP and retrieve the artefacts to confirm this alert is a true positive. 
Investigate the dns-tunneling.pcap file. Investigate the dns.log file. What is the number of DNS records linked to the IPv6 address?

ubuntu@ip-10-201-20-104:~/Desktop/Exercise-Files/anomalous-dns$ ls -al
