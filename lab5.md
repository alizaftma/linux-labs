# **Lab 5: Text Filtering and Search Workflow**

## **Purpose**
Build a basic workflow for filtering and searching text data. Create files, examine their contents, and apply common text-processing commands to extract information.

### **Task 1: Create and Prepare Files**
Set up a workspace and generate sample text files. <br>
```mkdir text_lab``` <br>
```echo "this is the first line" > text_lab/sample.txt``` <br>
```echo "this is the second line" >> text_lab/sample.txt```

```cp text_lab/sample.txt text_lab/sample.txt1``` <br>
```cp text_lab/sample.txt text_lab/sample.txt2```

Explanation: <br>
 `mkdir` creates the working directory. <br>
 `echo` writes text; `>` creates or overwrites a file; `>>` appends. <br>
 `cp` duplicates the file so you can test filtering across multiple inputs.

### **Task 2: Display and Explore File Content**
View files in different ways. <br>
```cat text_lab/sample.txt``` <br>
```head -n 10 text_lab/sample.txt``` <br>
```tail -n 10 text_lab/sample.txt``` <br>
```less text_lab/sample.txt``` <br>

Explanation: <br>
 `cat` shows the whole file. <br>
 `head` prints the first lines. <br>
 `tail` prints the last lines. <br>
 `less` allows scrolling; press `q` to exit.

### **Task 3: Filter and Extract Text**
Search for patterns and extract specific fields. <br>
```grep "the" text_lab/*.txt``` <br>
```grep -E "error|warning" text_lab/*.txt``` <br>
```cut -d',' -f1,3 text_lab/sample.txt```

Explanation: <br>
 ```grep finds lines matching a word.``` <br>
 ```grep -E``` enables extended patterns for multiple matches. <br>
 `cut` extracts fields using a delimiter (`,` here). Useful when processing structured or CSV-like data.

### **Task 4: Combine Filters into a Workflow**
Search across files and count matching lines. <br>
```cat text_lab/*.txt | grep -i "the" | wc -l```

Explanation: <br>
 `cat` outputs all text from the files. <br>
 `grep -i` performs a case-insensitive search for “the”. <br>
 `wc -l` counts how many lines matched, completing a simple text-analysis pipeline.
