**Name     :** Sruthi R

**Company  :** CODTECH IT SOLUTIONS

**Domain   :** Cybersecurity and Ethical Hacking

**ID no    :** CT08DS7399

**Duration :** Aug - Sept 2024

**Mentor   :** Neela Santhosh Kumar


## OVERVIEW OF THE PROJECT

### PROJECT : VULNERABILITY SCANNING TOOL

## OBJECTIVE

The objective of this program is to perform a comprehensive vulnerability scan on a target system (IP address or domain). It automates the following security checks:

**Port Scanning:** It uses nmap to perform a SYN scan to identify all open ports on the target system.

**SSL/TLS Scanning:** It utilizes sslscan to check the SSL/TLS configuration on the target, ensuring encryption protocols are secure and correctly configured.

**Outdated Software and Vulnerability Scanning:** It leverages nmap with the -sV and --script=vuln flags to check for outdated software versions and known vulnerabilities. The program is intended to be a simple and automated way for a security analyst or administrator to assess the security posture of a target by identifying exposed ports, misconfigured SSL/TLS settings, and vulnerable software.


## Key Activities

**Port Scanning:** The program uses the nmap tool with the -sS (SYN scan) and -p- options to perform a full scan of all TCP ports on the target system. This identifies open or closed ports, which can indicate potential points of entry for an attacker.

**SSL/TLS Scanning:** The program leverages sslscan to analyze the SSL/TLS configuration of the target. This activity checks for weak or outdated encryption protocols and ciphers to ensure that the target is not vulnerable to SSL/TLS attacks.

**Outdated Software and Vulnerability Scanning:** Using nmap with the -sV option, the program detects versions of services running on the target. With the --script=vuln flag, it scans for known vulnerabilities related to those services, helping to identify outdated software that could be exploited.

**Automation of the Vulnerability Scan Process:** The program automates the entire vulnerability scanning process, running all three checks (port scan, SSL scan, and software vulnerability scan) in sequence on the provided target. It outputs the results of each step, providing the user with a comprehensive overview of potential security risks.
These activities enable the user to assess the security posture of the target system efficiently.

## Technologies Used

**Python:** The program is written in Python and uses Python's subprocess module to execute external commands, integrating powerful system tools for network and security scanning.

**Kali Linux:** Kali Linux, is a common environment for security-related tools and scripts. The tool can be designed to run efficiently in a Linux terminal, taking advantage of the scripting capabilities and security tools available in Kali Linux.This task is done in kali linux.

**nmap (Network Mapper):** A widely used open-source tool for network discovery and security auditing. In this program:

-sS performs a SYN scan to detect open ports.

-p- scans all TCP ports (0–65535).

-sV detects versions of services running on the target.

--script=vuln runs vulnerability detection scripts for known vulnerabilities.

**sslscan:** A tool for testing SSL/TLS services on a target. It reports on supported ciphers, protocols, and other SSL/TLS configuration details, helping identify weak or misconfigured encryption settings.

**Command-line Execution:** The program uses the command-line tools nmap and sslscan by invoking them through Python's subprocess.run() method, allowing seamless integration of external system commands with Python.

These technologies combine to automate a multi-layered security scan, providing a comprehensive evaluation of the target system’s security.


## Implementation

**Setup the Python Script:** Start by creating a Python script file (e.g., vulnerability_scan.py) and use the shebang line to make the script executable in Linux environments.

#!/usr/bin/env python3

Import the subprocess module to allow Python to execute external commands like nmap and sslscan.

import subprocess

**Define the Functions:** Implement three key functions that call specific security tools to perform different types of scans on the target system.

**Port Scanning:** This function invokes nmap with a SYN scan (-sS) to check all TCP ports (-p-) on the target.

def scan_ports(target):
    print(f"Scanning open ports on {target}...")
    subprocess.run(['nmap', '-sS', '-p-', target])
    
**SSL/TLS Configuration Scanning:** This function uses sslscan to check the SSL/TLS settings on the target. This is useful to identify weak encryption settings or insecure SSL/TLS protocols.

def scan_ssl(target):
    print(f"Scanning SSL/TLS configurations on {target}...")
    subprocess.run(['sslscan', target])

**Outdated Software and Vulnerability Scanning:** This function calls nmap with the -sV flag to detect the version of services running on the target, and it uses --script=vuln to run vulnerability checks for known issues in outdated software.

def scan_outdated_software(target):
    print(f"Checking for outdated software on {target}...")
    subprocess.run(['nmap', '-sV', '--script=vuln', target])

**Run the Full Scan:** The run_scan function coordinates the three scanning activities. It calls the port scan, SSL scan, and software vulnerability scan functions sequentially, with printed output to indicate progress.

def run_scan(target):
    print(f"Starting vulnerability scan on {target}...\n")
    
    scan_ports(target)
    print("\n")
    
    scan_ssl(target)
    print("\n")
    
    scan_outdated_software(target)
    print("\n")
    
    print(f"Vulnerability scan on {target} completed.")

**Input and Execution:** Finally, use a conditional block (if __name__ == "__main__":) to ensure the script runs only when it is executed directly (not imported as a module). The program asks the user to input the target (IP address or domain) and then runs the complete scan on that target.

if __name__ == "__main__":
    target = input("Enter the target IP or domain: ")
    run_scan(target)

**Make the Script Executable (Optional):** If you're on a Linux environment, make the script executable by running the following command in the terminal:

chmod +x vulnerability_scan.py

**Run the Program:** Execute the script from the command line:

./vulnerability_scan.py

**Output:**

As the program runs, it will: 
Print information about the scanning process.

Call the external tools (nmap and sslscan).

Provide results for each scan (port scan, SSL scan, and vulnerability scan).

This is how the program is implemented. It automates the process of performing a basic vulnerability scan using widely adopted security tools like nmap and sslscan.

## How it works?

This Python program automates the process of running security vulnerability scans on a target system (specified by an IP address or domain) using command-line tools like nmap and sslscan. Here’s a step-by-step breakdown of how it works:

**User Input:** The program starts by prompting the user to input the target IP address or domain name

target = input("Enter the target IP or domain: ")

**Running the Vulnerability Scan:** Once the user enters the target, the program calls the run_scan function, which initiates three different security checks on the target:
>Port Scanning
>SSL/TLS Configuration Scanning
>Outdated Software and Vulnerability Scanning

run_scan(target)

**Port Scanning:** The scan_ports function runs an nmap scan with the SYN scan option (-sS), which is a stealthy scan to detect open TCP ports. The -p- option ensures that all ports from 0 to 65535 are scanned.

subprocess.run(['nmap', '-sS', '-p-', target])

**Output:** The program displays the status of all open ports on the target, which could indicate potential attack entry points.

**SSL/TLS Configuration Scanning:** The scan_ssl function uses the sslscan tool to examine the SSL/TLS configurations of the target. It checks for weak encryption algorithms, outdated protocols, or insecure settings.

subprocess.run(['sslscan', target])

**Output:** This step detects outdated or vulnerable software versions and displays known vulnerabilities associated with them.

**Sequential Execution:**

The program runs these three scans in sequence: 
> Port scan to identify open ports.
>SSL/TLS scan to check for encryption issues.
>Vulnerability scan to detect outdated software and known vulnerabilities.

After each scan, the program prints the results and proceeds to the next step.

**Completion Message:** Once all three scans are completed, the program prints a message indicating that the full vulnerability scan is done. This program is a simple, automated way to conduct basic security assessments on a given target, identifying misconfigurations, outdated software, and exposed ports.

## Conclusion




    




         



