# **Lab 7: Manage Team Accounts and Enforce Password Policies**

## **Overview**
This lab audits user accounts, groups, password information, login activity, and environment details in a restricted Linux environment. It demonstrates practical account-level security checks used in production systems.

### **Task 1: Examine Existing User and Group Information**
Review user identity, group membership, and system-wide account listings. <br>
Commands: <br>
`id afatima` <br>
`groups afatima`<br>
`cat /etc/passwd | head` <br>
`cat /etc/group | head` <br>

Explanation: <br>
 `id` shows UID, GID, and supplementary groups. <br>
 `groups` lists all groups assigned to the user. <br>
 `/etc/passwd` stores all user accounts. <br>
 `/etc/group` stores group definitions. <br>
 Using `head` limits the output.

### **Task 2: Review Password and Account Details**
Inspect account entries and verify the lab user’s record. <br>
Commands: <br>
```cat /etc/passwd``` <br>
```grep afatima /etc/passwd``` <br>
```ls -l /etc``` <br>

Explanation: <br>
 ```/etc/passwd``` shows username, UID, GID, home directory, and shell. <br>
 `grep` isolates the specific user entry. <br>
 `ls -l /etc` confirms access rights for system configuration files, including authentication-related components such as `passwd`, `shadow`, and `login.defs`. <br>

### **Task 3: Check User Access Rights and Environment Details**
Confirm identity, home directory, default shell, and account metadata. <br>
Commands: <br>
```whoami``` <br>
```echo $HOME``` <br>
```echo $SHELL``` <br>
```id```

Explanation: <br>
 `whoami` prints the effective user. <br>
 Environment variables reveal the user’s runtime context. <br>
 `id` verifies UID, GID, and group assignments. <br>

### **Task 4: Monitor User Activity**
Review current sessions and login history. <br>
Commands: <br>
```who``` <br>
```w``` <br>
```last -n 10```

Explanation: <br>
 `who` lists currently logged-in users. <br>
 `w` shows sessions plus system load and active processes. <br>
 `last` displays login history; limiting to 10 entries keeps output concise.
