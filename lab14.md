# **Lab 14: Disk Console for Storage Monitoring and Simple Backups**

### **This lab teaches how to build a small console to check storage, inspect mounts, and make simple file backups. Everything is saved in your home folder with snapshots and a short report so you can reuse it anytime.**


### **Task 1: Create Workspace and Blank Report**

Set up folders and a blank report file.

```
mkdir -p "$HOME/Disk_Console/snapshots"
touch "$HOME/Disk_Console/report.txt"
ls -l "$HOME/Disk_Console"
```
Explanation:

```mkdir -p "$HOME/Disk_Console/snapshots"```<br>
Creates Disk_Console folder with a snapshots subfolder. -p ensures it won’t fail if folders exist.

```touch "$HOME/Disk_Console/report.txt"```<br>
Creates an empty report.txt file for notes.

```ls -l "$HOME/Disk_Console"```<br>
Lists the files and folders inside Disk_Console.

### **Task 2: Check Current Storage Usage**
Record disk usage and the size of your console folder.

```
df -h > "$HOME/Disk_Console/snapshots/df.txt"
du -sh "$HOME/Disk_Console" > "$HOME/Disk_Console/snapshots/du_console.txt"
echo "Saved disk outputs on $(date)" >> "$HOME/Disk_Console/report.txt"
ls -l "$HOME/Disk_Console/snapshots"
```
Explanation:

```df -h > df.txt``` <br>
Shows overall disk usage in human-readable form and saves it to df.txt.

```du -sh "$HOME/Disk_Console" > du_console.txt```<br>
Shows the size of Disk_Console folder and saves it.

```echo "Saved disk outputs on $(date)" >> report.txt```<br>
Adds a note with the current date to the report.

```ls -l snapshots```<br>
Lists all snapshot files to confirm.

### **Task 3: Inspect Mounts and fstab (Read-Only)**
Capture active mounts and preview the system’s static mount list.

```
cat /proc/mounts > "$HOME/Disk_Console/snapshots/mounts.txt"
head -n 20 /etc/fstab > "$HOME/Disk_Console/snapshots/fstab_head.txt"
echo "Captured active mounts and saved fstab preview on $(date)" >> "$HOME/Disk_Console/report.txt"
ls -l "$HOME/Disk_Console/snapshots"
```
Explanation:

```cat /proc/mounts > mounts.txt```<br>
Saves currently active mounts to a snapshot.

```head -n 20 /etc/fstab > fstab_head.txt```<br>
Saves the first 20 lines of fstab to preview system mount configuration.

```echo ... >> report.txt```<br>
Logs the capture in the report.

```ls -l snapshots```<br>
Lists snapshot files to verify.

### **Task 4: Make a Safe File Backup and Verify It**
Create a sample file, back it up, and check that both copies match.

```
echo "This is a sample file for backup verification." > "$HOME/Disk_Console/sample.txt"
dd if="$HOME/Disk_Console/sample.txt" of="$HOME/Disk_Console/snapshots/sample.backup" bs=4M conv=notrunc status=none
sha256sum "$HOME/Disk_Console/sample.txt" > "$HOME/Disk_Console/snapshots/sample_hashes.txt"
sha256sum "$HOME/Disk_Console/snapshots/sample.backup" >> "$HOME/Disk_Console/snapshots/sample_hashes.txt"
echo "Saved sample and backup hashes to $HOME/Disk_Console/snapshots/sample_hashes.txt" >> "$HOME/Disk_Console/report.txt"
ls -l "$HOME/Disk_Console/snapshots"
```
Explanation:

```echo ... > sample.txt```<br>
Creates a small sample file.

```dd if=sample.txt of=sample.backup bs=4M conv=notrunc status=none```<br>
Makes a raw copy of the sample file into the snapshots folder.

```sha256sum sample.txt > sample_hashes.txt```<br>
Calculates and saves the hash of the original file.

```sha256sum sample.backup >> sample_hashes.txt```<br>
Calculates the hash of the backup and appends it to the same file for verification.

```echo ... >> report.txt```<br>
Notes in the report that hashes were saved.

```ls -l snapshots```<br>
Confirms all snapshot files exist.
