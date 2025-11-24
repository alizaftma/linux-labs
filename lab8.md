# **Lab 8: Create a System Health and Monitoring Report**

## **Overview**
This lab creates a basic system health and monitoring report. It covers process management, resource monitoring, and log review. The steps reflect common administrative tasks used to assess system performance and identify recent activity.

### **Task 1: Manage and Monitor Processes**
Manage foreground and background processes and examine runtime activity. Adjust process priority to observe scheduling behavior. <br>
Commands used: `bg`, `fg`, `jobs`, `ps`, `nice` <br>
Explanation: <br>
 `jobs` lists background and stopped tasks. <br>
 `bg` resumes a task in the background. <br>
 `fg` brings a task to the foreground. <br>
 `ps` displays running processes. <br>
 `nice` starts a process with modified priority.

### **Task 2: Create a System Health and Monitoring Report**
Check current system resource usage. <br>
Commands: <br>
`df` <br>
`free` <br>
`top` <br>

Explanation: <br>
 `df` shows disk usage and available space. <br>
 `free` displays memory and swap usage. <br>
 `top` provides real-time CPU, process, and memory statistics. <br>

### **Task 3: Review System Log Files**
Inspect recent system activity by examining log files. <br>
Commands: <br>
```ls /var/log``` <br>
```head /var/log/<logfile>``` <br>
```tail /var/log/<logfile>``` <br>
```less /var/log/<logfile>``` <br>

Explanation: <br>
 ```ls /var/log``` lists available logs. <br>
 ```head``` shows the beginning of a log. <br>
 ```tail``` shows the most recent entries. <br>
 ```less``` allows scrolling through large log files.

### **Task 4: Summarize System Health Information**
Review system usage and login activity. <br>
Commands: <br>
```who``` <br>
```w``` <br>
```last``` <br>

Explanation: <br>
 ```who``` shows logged-in users. <br>
 ```w``` shows active sessions and resource usage per session. <br>
 ```last``` displays login history.
