# **Lab 4: Creating Log Files with Redirects and tee**

## **Purpose**
Capture command output into log files, append additional data, separate error messages, and use pipelines with tee to view and save output simultaneously.

### **Task 1: Set Up the Workspace and Create an Empty Log**
Create a logging directory and start with a clean log file. <br>
```mkdir -p logs```
```> logs/log.txt```

Explanation: <br>
 `mkdir -p` ensures the directory exists. <br>
 `>` creates an empty file or clears an existing one. This prepares a fresh log.

### **Task 2: Record the Current Date and Disk Usage**
Overwrite the log with the current date, then append system disk usage. <br>
```date > logs/log.txt```
```df -h >> logs/log.txt```

Explanation: <br>
 `>` overwrites the file with the output of date. <br>
 `>>` appends the output of `df -h`, preserving the previous entry.

### **Task 3: Append Process Information and Capture Errors**
Append running process details while redirecting errors separately. <br>
```ps aux >> logs/log.txt 2> logs/errors.txt```

Explanation: <br>
 `ps aux` outputs all running processes. <br>
 `>>` appends normal output to log.txt. <br>
 `2>` directs error output (stderr) into `errors.txt`, keeping logs clean.

### **Task 4: Use a Pipeline and Save Output with tee**
View output on-screen while writing it to the log. <br>
```ls -l /var | grep log | tee -a logs/log.txt``` <br>

Explanation: <br>
 `|` pipes command output into another command. <br>
 `tee -a` displays the output and appends it to the log file. <br>
 This provides live visibility while still recording the result.
 
### **Task 5: Capture Both Output and Errors Together**
Redirect standard output and standard error into a single combined log. <br>
```ps aux &> logs/combined.log```

Explanation: <br>
 `&>` merges `stdout` and `stderr` into one file. <br>
 This produces a comprehensive log containing all output from the command.

Summary: <br>
The workflow creates a log directory, writes and appends command output, separates or merges error streams, and uses tee for simultaneous viewing and logging.
