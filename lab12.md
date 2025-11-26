# **Lab 12: Network Diagnostics and Configuration Console**

### **This lab teaches how to build a small network console to check identity, routing, connectivity, and name resolution. Everything is kept in your home folder. Snapshots are saved into files, and a short report summarizes key results. By the end, you will have a reusable toolkit to quickly verify network status.**

### **Task 1: Create Workspace and Blank Report**

Set up folders and a blank report file for notes.

```
mkdir -p ~/net_console/snapshots
: > ~/net_console/report.txt
ls -l ~/net_console
```
Explanation: <br>

```mkdir -p ~/net_console/snapshots```<br>
Makes a net_console folder with a snapshots subfolder. -p ensures it won’t fail if folders exist. <br>

```: > ~/net_console/report.txt```<br>
Creates an empty report.txt file or clears it if it already exists.<br>

```ls -l ~/net_console```<br>
Lists the folders and files in net_console to confirm setup.<br>

### **Task 2: Record Local Identity and Routes**
Save your machine’s hostname, IP address, routing table, and DNS settings.<br>

```
echo "hostname: $(hostname)" >> ~/net_console/report.txt
echo "IP address: $(hostname -I 2>/dev/null || ip -o -4 addr show | awk '{print $4}')" >> ~/net_console/report.txt
cat /proc/net/route > ~/net_console/snapshots/route.txt
cat /etc/resolv.conf > ~/net_console/snapshots/resolv.conf
```

Explanation: <br>

```echo "hostname: $(hostname)" >> ~/net_console/report.txt```<br>
Adds your computer’s name to the report.<br>

```echo "IP address: $(hostname -I 2>/dev/null || ip -o -4 addr show | awk '{print $4}')" >> ~/net_console/report.txt```<br>
Adds your IP address. Tries hostname -I first; if it fails, uses ip command.<br>

```cat /proc/net/route > ~/net_console/snapshots/route.txt```<br>
Saves the kernel routing table to a snapshot file. <br>

```cat /etc/resolv.conf > ~/net_console/snapshots/resolv.conf```<br>
Saves DNS settings to a snapshot file.<br>

### **Task 3: Test Connectivity and HTTP Reachability**
Check if you can access a website and measure response time. <br>

```
curl -I https://example.com > ~/net_console/snapshots/example_header.txt
curl -s -o /dev/null -w "%{http_code}\n" https://example.com > ~/net_console/snapshots/example_status.txt
curl -s -o /dev/null -w "%{time_total}\n" https://example.com > ~/net_console/snapshots/example_timing.txt
echo "example.com: $(cat ~/net_console/snapshots/example_status.txt) $(cat ~/net_console/snapshots/example_timing.txt)s" >> ~/net_console/report.txt
```
Explanation: <br>

```curl -I https://example.com > ~/net_console/snapshots/example_header.txt```<br>
Requests headers only (quick “hello”) and saves them to a file. <br>

```curl -s -o /dev/null -w "%{http_code}\n" https://example.com > ~/net_console/snapshots/example_status.txt```<br>
Checks website status code (like 200) without saving the page.<br>

```curl -s -o /dev/null -w "%{time_total}\n" https://example.com > ~/net_console/snapshots/example_timing.txt```<br>
Measures total time for the request and saves it.<br>

```echo "example.com: $(cat ~/net_console/snapshots/example_status.txt) $(cat ~/net_console/snapshots/example_timing.txt)s" >> ~/net_console/report.txt```<br>
Adds a short summary line with status code and timing to the report.<br>

### **Task 4: Check Name Resolution and Open Sockets**
Verify DNS resolution and capture active TCP/UDP sockets.

```
getent hosts example.com > ~/net_console/snapshots/dns.txt
cat /proc/net/tcp > ~/net_console/snapshots/tcp.txt
cat /proc/net/udp > ~/net_console/snapshots/udp.txt
echo "tcp lines: $(wc -l < ~/net_console/snapshots/tcp.txt)" >> ~/net_console/report.txt
echo "udp lines: $(wc -l < ~/net_console/snapshots/udp.txt)" >> ~/net_console/report.txt
```
Explanation: <br>

```getent hosts example.com > ~/net_console/snapshots/dns.txt```<br>
Resolves the hostname to IP and saves it.<br>

```cat /proc/net/tcp > ~/net_console/snapshots/tcp.txt``` <br>
Saves current TCP socket table to a snapshot. <br>

```cat /proc/net/udp > ~/net_console/snapshots/udp.txt``` <br>
Saves current UDP socket table. <br>

```echo "tcp lines: $(wc -l < ~/net_console/snapshots/tcp.txt)" >> ~/net_console/report.txt```<br>
Counts TCP entries and adds to report.<br>

```echo "udp lines: $(wc -l < ~/net_console/snapshots/udp.txt)" >> ~/net_console/report.txt```<br>
Counts UDP entries and adds to report.
