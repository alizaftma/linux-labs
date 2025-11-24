# **Lab 2: Organizing Records with Wildcards and Links**

## **Purpose**
Practice file-searching, pattern matching, file-type inspection, and link creation. Improve navigation and access within large Linux file sets.

### **Task 1: Set Up the Project Structure**
Create the base working environment.
```mkdir -p ~/SearchLab/docs ~/SearchLab/reports ~/SearchLab/images```
```touch ~/SearchLab/docs/notes.txt```
```touch ~/SearchLab/reports/summary.log```
```touch ~/SearchLab/images/photo.jpg```

Explanation:
This establishes a directory tree with representative files. The structure is used for search tests and link operations.

### **Task 2: Locate Files with find**
Search within the project directory using filename patterns.
```find ~/SearchLab -name "*.txt"```
```find ~/SearchLab -name "summary.log"```

Explanation:
find scans directories recursively. `-name` filters results by pattern. This is the standard method for locating files when their locations are unknown.

### **Task 3: Use Wildcards for Quick Matching**
Navigate into each directory and list files using shell globbing.
```cd ~/SearchLab/docs```
```ls *.txt```

```cd ~/SearchLab/reports```
```ls *.log```

```cd ~/SearchLab/images```
```ls p*```

Explanation:
Wildcards provide fast filtering without recursion. *.ext matches by extension. p* matches by prefix. Useful when the directory is known and only patterns matter.

### **Task 4: Inspect File Types and Create Links**
Check detailed file information and practice creating hard and soft links.
```ls -l ~/SearchLab```
```ln -s /home/afatima/SearchLab/docs/notes.txt ~/notes.txt```
```ln /home/afatima/SearchLab/reports/summary.log ~/summary.log```

Explanation:
```ls -l``` shows file types, permissions, and link counts.
Soft links act as pointers to another file’s path.
Hard links create an additional directory entry referencing the same underlying data.
