# 🕵️‍♂️ YARA, LOKI, and Valhalla – Lab Write-Up  

## 🔹 Introduction  
This lab explores **YARA**, **Cuckoo Sandbox**, **Python PE**, **LOKI**, and **Valhalla**, which are powerful tools commonly used in **malware analysis** and **threat hunting**.  
They help analysts classify malware, detect Indicators of Compromise (IOCs), and automate scanning tasks to identify potential threats.

---

## 🔹 Key Concepts  

### 🧩 YARA  
**YARA** is a tool designed to help malware researchers **identify and classify malware samples** based on textual or binary patterns.  

**Core features:**  
- Supports pattern matching using the **Base-16 (hexadecimal)** numbering system.  
- Detects specific **strings** inside applications (e.g., `"Enter your Name"`).  
- Each YARA command requires two arguments:  
  1. The **rule file** to use.  
  2. The **file, directory, or process ID** to scan.  

---

### 🧪 Cuckoo Sandbox  
**Cuckoo Sandbox** is an **automated malware analysis environment**.  
It allows researchers to execute suspicious files safely inside an isolated virtual environment (sandbox) to observe behavior such as:  
- File system modifications  
- Network activity  
- Process creation  
- Registry changes  

---

### 🧱 Python PE  
The **Python PE module** enables the creation of YARA rules using metadata extracted from **Windows Portable Executable (PE)** files.  
This helps analysts target specific malware families based on:  
- Import tables  
- Section names  
- PE header characteristics  

---

### ⚔️ LOKI  
**LOKI** is a free and open-source **IOC scanner** developed by Florian Roth.  
It uses multiple detection techniques to identify potentially malicious files.  

**Detection methods:**  
1. **File Name IOC Check** – Detects suspicious filenames.  
2. **YARA Rule Check** – Matches file content with YARA rules.  
3. **Hash Check** – Compares file hashes against known IOCs.  
4. **C2 Backconnect Check** – Detects indicators of command-and-control (C2) communications.  

📸 Example scan result:  
![LOKI Scan Example](./yara_file1.png)

---

### ⚡ Valhalla  
**Valhalla** is an **online YARA rule feed** hosted by **Nextron Systems** (also founded by Florian Roth).  
It provides a constantly updated database of verified YARA rules for:  
- Threat hunting  
- Incident response  
- Malware classification  

---

## 🔹 Hands-On Practice  

### 🧠 Writing a Simple YARA Rule  
Below is an example YARA rule that detects the presence of the string `"malicious"` in any scanned file:  

```yara
rule DetectMaliciousString
{
    meta:
        author = "Fretshie Aranza"
        description = "Simple YARA rule to detect 'malicious'"
        date = "2025-09-02"

    strings:
        $a = "malicious"

    condition:
        $a
}

🧩 Explanation:

    meta: Describes metadata about the rule.

    strings: Lists the text or hex patterns to detect.

    condition: Specifies when to trigger the alert (in this case, when $a is found).

🧾 Running YARA

To test your YARA rule on a sample file:

yara DetectMaliciousString.yar sample.exe

If the rule matches, YARA will print the rule name in the terminal output.
🕵️‍♀️ LOKI and Valhalla in Action

Using LOKI, analysts can scan directories for known threats:

python loki.py --path /samples/

For Valhalla, analysts can retrieve the latest YARA feeds or search for specific threat families online to keep rulesets up to date.
🧩 Conclusion

This lab demonstrated how YARA, Cuckoo Sandbox, Python PE, LOKI, and Valhalla can be used together for effective malware analysis and threat detection.
By writing custom YARA rules, automating scans with LOKI, and leveraging Valhalla’s curated rule feeds, analysts can efficiently identify and classify malicious activity in any environment.