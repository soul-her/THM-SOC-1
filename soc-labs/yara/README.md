# 🕵️‍♂️ YARA, LOKI, and Valhalla – Lab Write-Up  

## 🔹 Introduction  
This lab explores **YARA**, **Cuckoo Sandbox**, **Python PE**, **LOKI**, and **Valhalla**, which are tools commonly used in **malware analysis** and **threat hunting**. These tools help analysts classify malware, detect Indicators of Compromise (IOCs), and automate scanning tasks.  

---

## 🔹 Key Concepts  

### YARA  
YARA is a tool aimed at (but not limited to) helping malware researchers to **identify and classify malware samples**.  

- **Base-16 numbering system:** YARA can detect values in **hexadecimal**.  
- **Strings in applications:** Yes, `"Enter your Name"` would be detected as a **string** (Yay).  

Every YARA command requires two arguments:  
1. The rule file we create.  
2. The file, directory, or process ID to scan.  

---

### Cuckoo Sandbox  
Cuckoo Sandbox is an **automated malware analysis environment**. It allows researchers to safely run suspicious files inside a sandbox and capture system behavior.  

---

### Python PE  
Python’s **PE module** allows creation of YARA rules from the various sections and elements of a **Windows Portable Executable (PE) structure**. This makes it easier to target malware families based on their PE headers.  

---

### LOKI  
**LOKI** is a free and open-source **IOC scanner** created by Florian Roth.  

Detection is based on 4 methods:  
1. **File Name IOC Check**  
2. **YARA Rule Check**  
3. **Hash Check**  
4. **C2 Back Connect Check**  

📸 Example scan (lab screenshot):  

![YARA Example Detection](

print("YARA Example Detection: images/yara_file1.png")

---

### Valhalla  
**Valhalla** is an **online YARA rule feed** created and hosted by **Nextron-Systems** (also Florian Roth). It provides a constantly updated set of high-quality YARA rules for malware detection and threat hunting.  

---

## 🔹 Hands-On Practice  

### Writing a Simple YARA Rule  
Example rule to detect the string `"malicious"` in a file:  
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
