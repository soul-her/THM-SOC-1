# 🛡️ Snort IDS/IPS Writeup

## SCENARIO 1 — Detecting and Blocking a Brute-Force Attack

There’s an ongoing brute-force attack on your company’s system.  
As the cybersecurity specialist, it’s your responsibility to protect the company’s privacy.  
We’ll use **Snort** to observe the network traffic, identify the anomaly, and create a rule to stop the attack.

---

### Step 1: Observe Network Traffic

Run Snort in verbose mode to capture and log packets:

```bash
sudo snort -dev -l .

After running Snort for a short period, press Ctrl + C to stop the capture.
Then, list the directory to verify that the log file was created:

ls

Step 2: Analyze the Captured Packets

View the contents of the log file to inspect network activity:

sudo snort -r snort.log.1758627467

During analysis, we notice suspicious repeated connections targeting port 22 (SSH):

sudo snort -r snort.log.1758627467 "port 22"

Or filter the log for clearer visibility:

sudo snort -r snort.log.1758627467 | grep ":22"

Here, the red-marked section indicates multiple attempts to connect through port 22, suggesting a brute-force SSH attack.

The suspicious traffic shows repeated attempts from:

10.10.140.29:22 -> 10.10.245.36:46610

Step 3: Create a Snort Rule to Block the Attack

Now that we’ve identified the attacker, let’s edit the Snort local rules file:

sudo mousepad /etc/snort/rules/local.rules

Add the following rule:

drop tcp any any <> any 22 (msg:"SSH Brute Force Attack Prevented - Packet Dropped"; sid:100001; rev:1)

This rule drops any TCP traffic targeting port 22, effectively blocking brute-force attempts.
Step 4: Run Snort in Inline Mode

To enforce the new rule, run Snort in inline mode:

sudo snort -Q --daq afpacket -i eth0:eth1 -dev -c /etc/snort/snort.conf -A full -l .

Snort will now monitor and drop packets that match your rule, preventing further SSH brute-force attacks.
SCENARIO 2 — Detecting and Blocking a Reverse Shell Connection

After securing SSH, your team wants to perform a quick scan to investigate suspicious outbound traffic that might indicate a reverse shell.
Step 1: Capture Outbound Traffic

Run Snort again to capture network packets:

sudo snort -dev -l .

After capturing for a bit, stop it using Ctrl + C, and then inspect the log.
Step 2: Analyze the Log for Suspicious Ports

We’ll analyze the logs to look for traffic on unusual ports (e.g., 4444 — often used by reverse shells):

sudo snort -r snort.log.1758629770 | grep ":4444"

Port 4444 appears in the traffic — confirming potential reverse shell activity.
Step 3: Create a Rule to Block the Reverse Shell

Let’s edit our Snort rules again:

sudo mousepad /etc/snort/rules/local.rules

Add this rule:

reject tcp any 4444 <> any any (msg:"Reverse Shell Prevented - Packet Dropped"; sid:100002; rev:1)

This rule rejects any TCP traffic associated with port 4444, effectively blocking reverse shell connections.
Step 4: Apply and Verify the Rule

Run Snort in inline mode again to enforce all current rules:

sudo snort -Q --daq afpacket -i eth0:eth1 -dev -c /etc/snort/snort.conf -A full -l .

If configured correctly, Snort will reject malicious packets attempting to communicate over port 4444.
✅ Summary
Scenario	Threat	Port	Action	Rule Type	Status
1	SSH Brute Force	22	Dropped	drop	✅ Prevented
2	Reverse Shell	4444	Rejected	reject	✅ Prevented
🧠 Key Takeaways

    Snort is a powerful tool for both Intrusion Detection (IDS) and Intrusion Prevention (IPS).

    Regularly inspecting captured traffic helps uncover attack patterns.

    Writing custom rules tailors Snort’s protection to specific threats.

    Running Snort in inline mode (-Q) ensures real-time packet blocking.

📸 Screenshots

All images used:

    snortc1.png — Initial traffic capture

    snortc2.png — SSH brute-force evidence

    snortc3.png — Reverse shell detection