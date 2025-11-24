# **Lab 6: File Handling and Processing Pipeline**

## **Purpose**
Build a lightweight, repeatable workflow for managing and processing text-based project files. Set up a workspace, organize raw inputs, apply transformations, and generate summary reports.

### **Task 1: Create the Workspace and Seed Data**
Set up the main directory and create initial input files. <br>
```mkdir pipeline_lab``` <br>
```cd pipeline_lab/``` <br>
```mkdir raw```

```cd raw``` <br>
```touch Data1.txt``` <br>
```touch Data2.txt``` <br>

Explanation: <br>
 `pipeline_lab` is the project workspace. <br>
 `raw` stores all unprocessed input files. <br>
 `touch` creates the two seed files; populate them manually using `echo`, `vi`, or any editor.

### **Task 2: Manage and Organize Files**
Combine raw inputs, produce backups, and rename files. <br>
```cd ~/pipeline_lab``` <br>
```mkdir processed```

```cat ~/pipeline_lab/raw/Data1.txt ~/pipeline_lab/raw/Data2.txt > ~/pipeline_lab/processed/Merged.txt``` <br>
```cp ~/pipeline_lab/processed/Merged.txt ~/pipeline_lab/processed/Merged_backup.txt``` <br>
```mv ~/pipeline_lab/processed/Merged_backup.txt ~/pipeline_lab/processed/Backup_merged.txt``` <br>

```mv ~/pipeline_lab/raw/Data2.txt ~/pipeline_lab/raw/Data_2.txt```

Explanation: <br>
 `cat` merges input files into a single dataset. <br>
 `cp` creates a backup of the merged file. <br>
 `mv` renames files—used for both backups and reorganizing raw inputs. <br>
 The processed directory keeps transformed output separate from raw data.

### **Task 3: Filter and Extract Data**
Generate focused reports from the merged dataset. <br>
```mkdir -p ~/pipeline_lab/reports```

```awk '$1=="apple"{counts[$1]+=$2} END {print counts["apple"], "apple"}' ~/pipeline_lab/processed/Merged.txt | sort -nr > ~/pipeline_lab/reports/apple.txt```

```awk '$1 ~ /^[A-Za-z]+$/ {print $1}' ~/pipeline_lab/processed/Merged.txt > ~/pipeline_lab/reports/items.txt```

```sort ~/pipeline_lab/reports/items.txt | uniq -c > ~/pipeline_lab/reports/items_count.txt```

```wc -l ~/pipeline_lab/processed/Merged.txt > ~/pipeline_lab/processed/line_count.txt```

Explanation: <br>
 `awk` filters rows, matches specific fruits, and performs arithmetic on associated values. <br>
 `sort` and `uniq -c` count distinct items. <br>
 `wc -l` records total dataset size. <br>
 The reports directory stores all derived outputs.

### **Task 4: Build the End-to-End Processing Pipeline**
Process the merged file, aggregate totals per fruit, and produce a summary report. <br>
```awk '$1 ~ /^[A-Za-z]+$/ {counts[$1]+=$2} END {for (fruit in counts) print counts[fruit], fruit}' ~/pipeline_lab/processed/Merged.txt | /usr/bin/sort -nr > ~/pipeline_lab/reports/summary.txt```

Explanation: <br>
 `awk` validates rows, sums numeric values by fruit, and prints aggregated results. <br>
 `sort -nr` orders totals in descending order. <br>
 The output becomes `summary.txt`, the final report for the pipeline.

This structure creates a reusable file-processing workflow suitable for scaled or automated data tasks.
