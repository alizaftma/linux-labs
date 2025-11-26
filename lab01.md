# **Lab 1: Organizing Project Files on a Linux System**

## Purpose
Demonstrate how to structure project files on a Linux system using basic file-system commands. Show directory creation, file creation, copying, moving, and verification.

### **Task 1: Create the Main Directory**
Create the root location for the project. <br>
 ```mkdir``` makes a directory. ```ls``` lists the contents of a location so you can confirm the result. <br>
```mkdir ~/project_lab``` <br>
```ls ~``` <br>


### **Task 2: Create Subdirectories**
Use ```mkdir -p``` with full paths to avoid errors and ensure directories are created exactly where intended.
```mkdir -p /home/afatima/project_lab/Docs``` <br>
```mkdir -p /home/afatima/project_lab/Report``` <br>
```mkdir -p /home/afatima/project_lab/Images``` <br>

```ls /home/afatima/project_lab```

Explanation: <br>
A structured layout keeps different file types separate. Using absolute paths removes ambiguity about where directories are placed.

### **Task 3: Create Sample Files**
Use ```touch``` to create empty files. This simulates real project assets. <br>
```touch /home/afatima/project_lab/Docs/notes.txt``` <br>
```touch /home/afatima/project_lab/Report/summary.txt``` <br>
```touch /home/afatima/project_lab/Images/photo.jpg``` <br>

```ls -l /home/afatima/project_lab/Docs``` <br>
```ls -l /home/afatima/project_lab/Report``` <br>
```ls -l /home/afatima/project_lab/Images``` <br>

Explanation: <br>
```touch``` creates a file if it doesn’t exist. ```ls -l``` shows file details (permissions, size, timestamps), confirming creation.

### **Task 4: Copy Files**
Use ```cp``` to duplicate files across directories. <br>
```cp /home/afatima/project_lab/Docs/notes.txt /home/afatima/project_lab/Report/notes.txt``` <br>
```cp /home/afatima/project_lab/Report/summary.txt /home/afatima/project_lab/Docs/summary.txt``` <br>

```ls /home/afatima/project_lab/Docs``` <br>
```ls /home/afatima/project_lab/Report``` <br>

Explanation: <br>
Copying is useful when multiple teams or folders need access to the same content. Each directory ends up with both files.

### **Task 5: Move and Rename Files**
Use ```mv``` to rename or relocate files. <br>
 ```tree``` shows the full hierarchical structure. <br>
```mv /home/afatima/project_lab/Images/photo.jpg /home/afatima/project_lab/Images/project_photo.jpg``` <br>
```tree /home/afatima/project_lab``` <br>

Explanation: <br>
```mv``` handles both moves and renames. ```tree``` gives a complete visual of the final layout, ensuring everything is in the correct place.
