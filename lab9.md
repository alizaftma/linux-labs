# **Lab 9: Develop a Menu-Driven Utility with Shell Scripting**

## **Overview**
This lab builds a simple menu-driven shell script that performs basic system checks from one place. The work is organized inside a dedicated workspace to keep the project clean. The script evolves from a basic menu to a version that generates structured log entries.

### **Task 1: Create Your Workspace**
Set up the working directory and initial files. <br>
Commands: <br>
```mkdir -p ~/menu_lab``` <br>
```cd ~/menu_lab``` <br>
```echo '#!/bin/bash' > menu``` <br>
```touch actions.log``` <br>
```chmod +x menu``` <br>
```ls -l```

Explanation: <br>
 A directory is created to contain all script-related files. <br>
 A script file is initialized with a Bash shebang so the system treats it as an executable script. <br>
 A log file is created to record operations. <br>
 Execution permissions are added. <br>
 The directory contents are listed to verify the setup. <br>

### **Task 2: Add an Interactive Menu**
Implement a simple menu system using a loop and a case structure. Each option logs its activity. <br>
**Script:** <br>
```
while true; do
  echo "\nSelect an option:"
  echo "1) Show current directory"
  echo "2) List files"
  echo "3) Show date"
  echo "4) Show disk usage"
  echo "5) Exit"

  read -p "Choice: " choice

  case "$choice" in
    1)
      pwd >> ~/menu_lab/actions.log
      ;;
    2)
      ls -la >> ~/menu_lab/actions.log
      ;;
    3)
      date >> ~/menu_lab/actions.log
      ;;
    4)
      df -h >> ~/menu_lab/actions.log
      ;;
    5)
      echo "Exiting."
      break
      ;;
    *)
      echo "Invalid choice."
      ;;
  esac
done
```
Explanation: <br>
 A `while true` loop keeps the menu running until an exit option is selected. <br>
 `echo` displays menu options. <br>
 `read` captures the user’s choice. <br>
 The case statement defines the action for each menu option. <br>
 Each selected option appends information to actions.log for tracking.

### **Task 3: Rewrite the Script to Use Structured Log Entries**
Replace the append-style logging with a here-document that overwrites the log file with a structured report each time an option is chosen. <br>
Revised case block: <br>
```
case "$choice" in
  1)
    cat > ~/menu_lab/actions.log <<EOF
Date: $(date)
Choice: Show current directory
EOF
    ;;
  2)
    cat > ~/menu_lab/actions.log <<EOF
Date: $(date)
Choice: List files
EOF
    ;;
  3)
    cat > ~/menu_lab/actions.log <<EOF
Date: $(date)
Choice: Show date
EOF
    ;;
  4)
    cat > ~/menu_lab/actions.log <<EOF
Date: $(date)
Choice: Show disk usage
EOF
    ;;
esac
done
```

Explanation: <br>
 The earlier version appended output to the log. <br>
 The revised version overwrites the log using a here-document `(<<EOF)`. <br>
 Everything between `<<EOF` and `EOF` becomes the new content of actions.log. <br>
 Each choice produces a short structured entry containing a timestamp and the selected operation.

This structure creates a reusable, self-contained menu utility and demonstrates logging, looping, case handling, and here-document usage within shell scripts.
