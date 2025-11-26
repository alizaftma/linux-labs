# Linux Labs

Collection of Linux practice labs covering file management, permissions, logging, text processing, user management, and shell scripting.

## Labs

1. **Lab 1: Organizing Project Files on a Linux System**
- Structure project files using Linux commands: create directories and files, copy and move files, and verify the layout.

2. **Lab 2: Organize Records with Wildcards and Links**  
- Directory structure creation, file search, wildcards, soft & hard links.

3. **Lab 3: Secure Project Files with Permissions and Ownership**  
- File permissions, ownership, chmod, chown.

4. **Lab 4: Create a Log File Using Redirects and Tee Command**  
- Redirect output, append logs, handle errors, use `tee`.

5. **Lab 5: Create a Text Filtering and Search Workflow**  
- `cat`, `head`, `tail`, `less`, `grep`, `cut`.

6. **Lab 6: Develop a File Handling and Processing Pipeline**  
- Organize files, extract and summarize data, `awk`, `sort`, `uniq`.

7. **Lab 7: Manage Team Accounts and Enforce Password Policies**  
- Check users, groups, passwords, and login activity.

8. **Lab 8: Create a System Health and Monitoring Report**  
- Monitor processes, disk, memory, logs, and system usage.

9. **Lab 9: Develop a Menu-Driven Utility with Shell Scripting**  
- Shell script menu, loops, case, logging actions.

10. **Lab 10: Network Troubleshooting Toolkit**
- Build a lightweight toolkit to check network connectivity and inspect sockets.
- Tasks include setting up a workspace, checking HTTP reachability, saving TCP/UDP socket snapshots, and recording results in a report.
- Useful commands: `mkdir`, `curl`, `host`, `ss`, `head`.

11. **Lab 11: File Transfer and Synchronization**
- Create a simple console to download, copy, and synchronize files.
- Tasks include setting up workspace and sample files, downloading a webpage, copying files locally, and mirroring folders.
- Useful commands: `mkdir`, `echo`, `wget`, `scp`, `cp`.

12. **Lab 12: Network Diagnostics and Configuration Console**
- Run basic network checks for identity, routing, connectivity, and DNS resolution.
- Tasks include recording hostname/IP, saving routing tables, checking HTTP reachability, and capturing active sockets.
- Useful commands: `hostname`, `ip`, `cat`, `curl`, `getent`.

13. **Lab 13: Admin Console for Logs, Traffic, and Processes**
- Monitor system logs, network traffic, and active processes.
- Tasks include reading SSH logs, checking DNS and HTTP reachability, snapshotting processes, and safely adjusting process priority.
- Useful commands: `journalctl`, `getent`, `curl`, `ps`, `top`, `sleep`, `renice`.

14. **Lab 14: Disk Console for Storage and Backups**
- Inspect storage usage, mounts, and create simple file backups.
- Tasks include checking disk usage, saving mount info and fstab preview, creating a sample file, backing it up, and verifying hashes.
- Useful commands: `df`, `du`, `cat`, `head`, `dd`, `sha256sum`.


**Note:** All labs store snapshots in a `snapshots` folder and maintain a `report.txt` to summarize key results, making them easy to reuse for quick system checks.

## Usage

- Each lab contains step-by-step instructions and example commands.  
- Run commands in a Linux terminal.  
- For labs with scripts, make files executable with `chmod +x filename` and run with `./filename`.
