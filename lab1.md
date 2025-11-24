# **Lab 1: Organizing Project Files on a Linux System**

## Purpose
Demonstrate how to structure project files on a Linux system using basic file-system commands. Show directory creation, file creation, copying, moving, and verification.

### **Task 1: Create the Main Directory**
Create the root location for the project.
 ```mkdir``` makes a directory. ```ls``` lists the contents of a location so you can confirm the result.
```mkdir ~/project_lab```
```ls ~```


### **Task 2: Create Subdirectories**
Use ```mkdir -p``` with full paths to avoid errors and ensure directories are created exactly where intended.
```mkdir -p /home/afatima/project_lab/Docs```
```mkdir -p /home/afatima/project_lab/Report```
```mkdir -p /home/afatima/project_lab/Images```

```ls /home/afatima/project_lab```

Explanation
 A structured layout keeps different file types separate. Using absolute paths removes ambiguity about where directories are placed.

### **Task 3: Create Sample Files**
Use ```touch``` to create empty files. This simulates real project assets.
```touch /home/afatima/project_lab/Docs/notes.txt```
```touch /home/afatima/project_lab/Report/summary.txt```
```touch /home/afatima/project_lab/Images/photo.jpg```

```ls -l /home/afatima/project_lab/Docs```
```ls -l /home/afatima/project_lab/Report```
```ls -l /home/afatima/project_lab/Images```

Explanation
 ```touch``` creates a file if it doesn’t exist. ```ls -l``` shows file details (permissions, size, timestamps), confirming creation.

### **Task 4: Copy Files**
Use ```cp``` to duplicate files across directories.
```cp /home/afatima/project_lab/Docs/notes.txt /home/afatima/project_lab/Report/notes.txt```
```cp /home/afatima/project_lab/Report/summary.txt /home/afatima/project_lab/Docs/summary.txt```

```ls /home/afatima/project_lab/Docs```
```ls /home/afatima/project_lab/Report```

Explanation
 Copying is useful when multiple teams or folders need access to the same content. Each directory ends up with both files.

### **Task 5: Move and Rename Files**
Use ```mv``` to rename or relocate files.
 ```tree``` shows the full hierarchical structure.
```mv /home/afatima/project_lab/Images/photo.jpg /home/afatima/project_lab/Images/project_photo.jpg```
```tree /home/afatima/project_lab```

Explanation
```mv``` handles both moves and renames. ```tree``` gives a complete visual of the final layout, ensuring everything is in the correct place.
