# **Lab 13: Admin Console for Logs, Traffic, and Processes**

### **This lab teaches how to build a small admin console to monitor logs, network activity, and active processes. Everything is saved in your home folder with snapshots and a short report, so you can reuse it anytime.**


### **Task 1: Create Workspace and Blank Report**

Set up folders and a blank report file.

```
mkdir -p "$HOME/Admin_Console/snapshots"
: > "$HOME/Admin_Console/report.txt"
ls -la "$HOME/Admin_Console"
```
Explanation:<br>

```mkdir -p "$HOME/Admin_Console/snapshots"```<br>
Creates a main folder Admin_Console with a snapshots subfolder. -p prevents errors if folders already exist.

```: > "$HOME/Admin_Console/report.txt"```<br>
Creates an empty report.txt or clears it if it exists.

```ls -la "$HOME/Admin_Console"```<br>
Lists all files and folders inside Admin_Console with details.

### **Task 2: Read Key Logs and Develop a Summary**
Check SSH logs and save a short summary.

```
journalctl -u ssh.service | head -n 40 > "$HOME/Admin_Console/snapshots/auth_head.txt"
journalctl -u ssh.service | tail -n 40 > "$HOME/Admin_Console/snapshots/auth_tail.txt"
cat "$HOME/Admin_Console/snapshots/auth_head.txt" >> "$HOME/Admin_Console/report.txt"
cat "$HOME/Admin_Console/snapshots/auth_tail.txt" >> "$HOME/Admin_Console/report.txt"
```
Explanation:

```journalctl -u ssh.service | head -n 40 > ...```<br>
Saves the first 40 lines of SSH logs to auth_head.txt.

```journalctl -u ssh.service | tail -n 40 > ...```<br>
Saves the last 40 lines to auth_tail.txt.

```cat ... >> report.txt```<br>
Appends the snapshots into the main report.

### **Task 3: Check DNS, Remote IP, and HTTP Reachability**
Resolve hostnames, fetch headers, and record website status.

```
getent hosts example.com > "$HOME/Admin_Console/snapshots/dns.txt"
curl -sI https://example.com > "$HOME/Admin_Console/snapshots/example_headers.txt"
echo $(curl -s -o /dev/null -w '%{http_code}' https://example.com) >> "$HOME/Admin_Console/report.txt"
curl -s --connect-timeout 10 -o /dev/null -w "remote_ip: %{remote_ip}\n" https://example.com >> "$HOME/Admin_Console/report.txt"
```
Explanation:

```getent hosts example.com > dns.txt```<br>
Resolves example.com to IP and saves it.

```curl -sI https://example.com > example_headers.txt```<br>
Fetches only headers and saves them.

```echo $(curl -s -o /dev/null -w '%{http_code}' ...) >> report.txt```<br>
Saves the HTTP status code (like 200) into the report.

```curl -s --connect-timeout 10 -o /dev/null -w "remote_ip: %{remote_ip}\n" ... >> report.txt```<br>
Captures the remote IP of the server and appends to report.

### **Task 4: Inspect Processes and Demo Safe Priority Change**
Snapshot active processes and adjust priority safely on a test process.

```
ps aux --sort=-%cpu | head -n 20 > "$HOME/Admin_Console/snapshots/ps_top.txt"
top -b -n 1 | head -n 20 > "$HOME/Admin_Console/snapshots/top.txt"
sleep 300 &
BG_PID=$!
echo "started test sleep in background with PID $BG_PID" >> "$HOME/Admin_Console/report.txt"
renice +10 -p "$BG_PID"
echo "reniced PID $BG_PID to +10" >> "$HOME/Admin_Console/report.txt"
echo "current process snapshot and priority adjustments recorded." >> "$HOME/Admin_Console/report.txt"
ps -o pid,ppid,ni,cmd -p "$BG_PID" >> "$HOME/Admin_Console/report.txt"
```
Explanation:

```ps aux --sort=-%cpu | head -n 20 > ps_top.txt```<br>
Saves top 20 CPU-consuming processes to a snapshot.

```top -b -n 1 | head -n 20 > top.txt```<br>
Another snapshot of running processes.

```sleep 300 &```<br>
Starts a test background process that sleeps for 5 minutes.

```BG_PID=$!```<br>
Saves the PID of the background sleep process.

```echo "started test sleep..." >> report.txt```<br>
Logs the action in the report.

```renice +10 -p "$BG_PID"```<br>
Changes the priority of the test process safely.

```echo "reniced PID..." >> report.```<br>
Records the priority change.

```ps -o pid,ppid,ni,cmd -p "$BG_PID" >> report.txt```<br>
Adds a snapshot of the test process with its new priority to the report.
