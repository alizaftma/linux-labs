# **Lab 11: File Transfer and Synchronization Toolkit**

## **This lab teaches how to create a simple toolkit to download, copy, and synchronize files using only user-level tools. Everything is kept in your home folder so it is easy to manage.**

### **Task 1: Setup Workspace and Sample Data**

Create a folder structure and a sample file for testing. <br>

```
mkdir -p ~/transfer_lab/{incoming,outgoing,mirror}
echo "sample file for transfer lab" > ~/transfer_lab/outgoing/sample.txt
ls -l ~/transfer_lab/
ls -l ~/transfer_lab/outgoing/
```
Explanation: <br>
```mkdir -p ~/transfer_lab/{incoming,outgoing,mirror}``` <br>
Creates transfer_lab with three subfolders: incoming, outgoing, and mirror. -p avoids errors if folders already exist.<br>

```echo "sample file for transfer lab" > ~/transfer_lab/outgoing/sample.txt``` <br>
Writes some text into a new file called sample.txt in the outgoing folder. <br>

```ls -l ~/transfer_lab/``` <br>
Lists the folders inside transfer_lab with details. <br>

```ls -l ~/transfer_lab/outgoing/``` <br>
Lists the files inside outgoing with details. <br>

### **Task 2: Download a File into Incoming Folder**
Grab a sample webpage to practice moving files.<br>

```
wget -O ~/transfer_lab/incoming/web.html http://example.com
ls -l ~/transfer_lab/incoming/
```
Explanation: <br>
```wget -O ~/transfer_lab/incoming/web.html http://example.com```
Downloads a webpage from the internet and saves it as web.html in the incoming folder. <br>

```ls -l ~/transfer_lab/incoming/```<br>
Lists files in incoming to confirm the download. <br>

### **Task 3: Copy Files Securely**
Copy files locally using the same command normally used for remote copying. <br>
```
scp ~/transfer_lab/incoming/web.html ~/transfer_lab/outgoing/web_copy.html
scp ~/transfer_lab/outgoing/sample.txt ~/transfer_lab/outgoing/sample_copy.txt
ls -l ~/transfer_lab/outgoing/
```
Explanation: <br>
```scp ~/transfer_lab/incoming/web.html ~/transfer_lab/outgoing/web_copy.html``` <br>
Copies web.html from incoming to outgoing as web_copy.html. scp is usually used for remote copying but works locally too. <br>

```scp ~/transfer_lab/outgoing/sample.txt ~/transfer_lab/outgoing/sample_copy.txt```<br>
Makes a copy of sample.txt inside outgoing as sample_copy.txt. <br>

```ls -l ~/transfer_lab/outgoing/```<br>
Shows the files in outgoing to confirm copies. <br>

### **Task 4: Synchronize Folders**
Keep a mirror of outgoing in mirror and update it with changes. <br>
```
cp -r ~/transfer_lab/outgoing ~/transfer_lab/mirror
cp -u ~/transfer_lab/outgoing/* ~/transfer_lab/mirror/
echo "additional line appended to demonstrate update." >> ~/transfer_lab/mirror/sample.txt
ls -R ~/transfer_lab/mirror/
```
Explanation: <br>
```cp -r ~/transfer_lab/outgoing ~/transfer_lab/mirror``` <br>
Copies the entire outgoing folder into mirror recursively. <br>

```cp -u ~/transfer_lab/outgoing/* ~/transfer_lab/mirror/```<br>
Updates files in mirror only if they are newer than the existing ones. <br>

```echo "additional line appended to demonstrate update." >> ~/transfer_lab/mirror/sample.txt```<br>
Adds a line to a file in mirror to show updates are possible.<br>

ls -R ~/transfer_lab/mirror/
Lists all files in mirror and its subfolders recursively.
