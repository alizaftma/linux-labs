# **Lab 3: Securing Project Files with Permissions and Ownership**

## **Purpose** 
Apply Linux permission and ownership controls to protect sensitive project files. Set up a controlled environment, adjust permissions, modify ownership, and enforce strict access rules.

### **Task 1: Set Up the Test Environment**
Create a dedicated directory and a sample sensitive file. <br>
```mkdir ~/secure_lab```
```touch ~/secure_lab/report.txt```

Explanation: <br>
 This directory isolates the file used for permission and ownership testing. `report.txt` represents a restricted document.

### **Task 2: Modify File Permissions**
Adjust access rights for the owner, group, and others. <br>
```chmod u+rw ~/secure_lab/report.txt``` <br>
```chmod g+r ~/secure_lab/report.txt``` <br>
```chmod o= ~/secure_lab/report.txt```

Explanation: <br>
 `u` refers to the file owner, `g` to the group, and `o` to all others. <br>
 The commands allow the owner to read/write, give the group read-only access, and remove all permissions for others.

### **Task 3: Work with Ownership**
Inspect and adjust file ownership. <br>
```ls -l ~/secure_lab/report.txt```
```chown :$(id -gn) ~/secure_lab/report.txt```

Explanation: <br>
 `ls -l` displays the current owner and group. <br>
 `chown :group` file changes the group ownership. `$(id -gn)` retrieves the user’s default group.

### **Task 4: Apply Strict Permission Rules**
Enforce owner-only access. <br>
```chmod 600 ~/secure_lab/report.txt```
```ls -l ~/secure_lab/report.txt```

Explanation: <br>
 `600` sets read/write for the owner and denies all access to group and others. <br>
 The final `ls -l` confirms that the file is secured according to strict access requirements.
