# **Lab 2: Organizing Records with Wildcards and Links**

## **Purpose**
Practice file-searching, pattern matching, file-type inspection, and link creation. Improve navigation and access within large Linux file sets.

### **Task 1: Set Up the Project Structure**
Create the base working environment. <br>
```mkdir -p ~/SearchLab/docs ~/SearchLab/reports ~/SearchLab/images``` <br>
```touch ~/SearchLab/docs/notes.txt``` <br>
```touch ~/SearchLab/reports/summary.log``` <br>
```touch ~/SearchLab/images/photo.jpg```

Explanation:
This establishes a directory tree with representative files. The structure is used for search tests and link operations.

### **Task 2: Locate Files with find**
Search within the project directory using filename patterns. <br>
```find ~/SearchLab -name "*.txt"``` <br>
```find ~/SearchLab -name "summary.log"```

Explanation: <br>
find scans directories recursively. `-name` filters results by pattern. This is the standard method for locating files when their locations are unknown.

### **Task 3: Use Wildcards for Quick Matching**
Navigate into each directory and list files using shell globbing. <br>
```cd ~/SearchLab/docs``` <br>
```ls *.txt```

```cd ~/SearchLab/reports``` <br>
```ls *.log```

```cd ~/SearchLab/images``` <br>
```ls p*```

Explanation: <br>
Wildcards provide fast filtering without recursion. *.ext matches by extension. p* matches by prefix. Useful when the directory is known and only patterns matter.

### **Task 4: Inspect File Types and Create Links**
Check detailed file information and practice creating hard and soft links. <br>
```ls -l ~/SearchLab``` <br>
```ln -s /home/afatima/SearchLab/docs/notes.txt ~/notes.txt``` <br>
```ln /home/afatima/SearchLab/reports/summary.log ~/summary.log``` <br>

Explanation: <br>
```ls -l``` shows file types, permissions, and link counts. <br>
Soft links act as pointers to another file’s path. <br>
Hard links create an additional directory entry referencing the same underlying data.
