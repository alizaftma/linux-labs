# **Lab 10: Simple Network Troubleshooting Toolkit**

## **This lab shows how to create a small network testing toolkit in your home folder. You will run quick checks to see if websites are reachable, inspect sockets, and confirm SSH configuration. Everything is saved in your `net_lab` folder so you can review it later.**

### **Task 1: Setup Workspace and HTTP Reachability Check**
Create a folder for your lab and a file to store notes. Then check if a website responds. <br>
```
mkdir -p ~/net_lab
echo "==initial reachability check==" >> ~/net_lab/report.txt
curl -sI https://example.com >> ~/net_lab/report.txt
curl -s -o /dev/null -w "%{http_code}\n" https://example.com >> ~/net_lab/report.txt
host example.com >> ~/net_lab/report.txt
ls -l ~/net_lab/report.txt
```
Explanation of each command: <br>
```mkdir -p ~/net_lab``` <br>
Makes a folder called net_lab in your home folder. If it already exists, nothing breaks. <br>
```echo "==initial reachability check==" >> ~/net_lab/report.txt```<br>
Writes a label in report.txt for notes. If the file doesn’t exist, it is created. <br>
```curl -sI https://example.com >> ~/net_lab/report.txt``` <br>
Asks the website for headers only (quick hello). Saves output to report.txt. <br>
```curl -s -o /dev/null -w "%{http_code}\n" https://example.com >> ~/net_lab/report.txt``` <br>
Requests the website but ignores the page. Saves only the status code (like 200) to report.txt. <br>
```host example.com >> ~/net_lab/report.txt``` <br>
Looks up the website’s IP address and adds it to report.txt. <br>
```ls -l ~/net_lab/report.txt``` <br>
Shows details about your report file, including size and permissions. <br>

### **Task 2: Capture TCP/UDP Socket Snapshot**
Save a snapshot of all network sockets and add the first 20 lines to your report. <br>
```
ss -tuna > ~/net_lab/ss.out && ss -uana >> ~/net_lab/ss.out
head -n 20 ~/net_lab/ss.out >> ~/net_lab/report.txt
```
Explanation: <br>
```ss -tuna > ~/net_lab/ss.out && ss -uana >> ~/net_lab/ss.out```
Saves all TCP and UDP socket info into ss.out. -tuna lists TCP/UDP sockets with addresses and states. <br>
```head -n 20 ~/net_lab/ss.out >> ~/net_lab/report.txt``` <br>
Adds only the first 20 lines of the snapshot to report.txt to keep it short. <br>

### **Task 3: Check External Reachability with curl**
Test outbound connectivity, save headers, status code, and timing. <br>
```
curl -sI https://example.com > ~/net_lab/headers.txt
curl -s -o /dev/null -w "%{http_code}\n" https://example.com > ~/net_lab/curl_status.txt
curl -s -o /dev/null -w "%{time_total}\n" https://example.com > ~/net_lab/curl_timing.txt
echo "status: $(cat ~/net_lab/curl_status.txt)" >> ~/net_lab/report.txt
```
Explanation: <br>
```curl -sI https://example.com > ~/net_lab/headers.txt```<br>
Requests headers only and saves them to headers.txt. <br>
```curl -s -o /dev/null -w "%{http_code}\n" https://example.com > ~/net_lab/curl_status.txt``` <br>
Ignores the page content, saves just the HTTP status code to curl_status.txt. <br>
```curl -s -o /dev/null -w "%{time_total}\n" https://example.com > ~/net_lab/curl_timing.txt``` <br>
Measures total time for the request and saves it to curl_timing.txt. <br>
```echo "status: $(cat ~/net_lab/curl_status.txt)" >> ~/net_lab/report.txt``` <br>
Reads the status code and appends it to your main report file. <br>

### **Task 4: Confirm SSH Client and Capture Config**
Check SSH client version and save a snapshot of its settings.
```
ssh -v 2>&1 | head -n 1 >> ~/net_lab/report.txt
ssh -G localhost > ~/net_lab/ssh_config.txt
```
Explanation: <br>
```ssh -v 2>&1 | head -n 1 >> ~/net_lab/report.txt``` <br>
Runs SSH in verbose mode. Captures the first line (version info) and appends it to report.txt. <br>
```ssh -G localhost > ~/net_lab/ssh_config.txt``` <br>
Prints the full SSH configuration as if connecting to localhost, without actually connecting. Saves it to ssh_config.txt.
