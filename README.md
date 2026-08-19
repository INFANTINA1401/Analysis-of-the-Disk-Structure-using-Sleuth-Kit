# Analysis-of-the-Disk-Structure-using-Sleuth-Kit
## AIM:
To analyze the disk structure of a given disk image using Sleuth Kit tools in Kali Linux.

## REQUIREMENTS
- **Operating System**: Windows 10/11 or Kali Linux
- **Tools**:  
  - [The Sleuth Kit for Windows](https://sleuthkit.org/)  
  - Optional GUI: [Autopsy Forensic Browser](https://www.autopsy.com/)
- **Test Data**: Disk image file (`disk.dd`, `disk.img`, `.E01`)

## ARCHITECTURE DIAGRAM
```mermaid
flowchart TD
    A[Disk Image / Physical Disk] --> B[mmls - Partition Analysis]
    B --> C[fsstat - File System Metadata]
    C --> D[fls - File Listing]
    D --> E[icat - File Recovery]
    E --> F[Recovered Data / Metadata Report]
```
## DESIGN STEPS:
### Step 1:
- Obtain or create a disk image file (e.g., disk.dd) to analyze.
- Open the terminal in Kali Linux.

### Step 2:
Use Sleuth Kit tools like:
 - mmls → Examine the partition layout.
 - fsstat → View file system details.
 - fls → Get file listing.
 - icat → Recover files using inode numbers.
### Step 3:
Interpret the output to understand:
 - Partition table layout
 - File system metadata (block size, creation time, etc.)
 - Deleted and allocated files
 - Inode-based file recovery

## PROGRAM:
Sleuth Kit Disk Analysis Commands
### Partition Analysis
```bash
mmls disk.dd
```
### File System Metadata
```bash
fsstat -o 2048 disk.dd
```
### File Listing
```bash
fls -o 2048 disk.dd
```
### File Recovery
```bash
icat -o 2048 disk.dd 4 > recovered_file.txt
```
- Recovers the file associated with inode 4.
## SAMPLE WORKFLOW (Windows)
```bash
# Step 1: View partitions
mmls.exe C:\forensics\disk.dd

# Step 2: View file system details
fsstat.exe -o 2048 C:\forensics\disk.dd

# Step 3: List files
fls.exe -r -o 2048 C:\forensics\disk.dd

# Step 4: Recover a file
icat.exe -o 2048 C:\forensics\disk.dd 6 > C:\forensics\image.jpg
```
## OUTPUT:
Disk Structure Analysis Results

<img width="667" height="104" alt="image" src="https://github.com/user-attachments/assets/5dfc05e4-a0c8-4783-9b20-d5329328b06f" />
<img width="1248" height="732" alt="image" src="https://github.com/user-attachments/assets/7b083af9-06d5-427a-9d3d-ec27739a6fd5" />
<img width="486" height="81" alt="image" src="https://github.com/user-attachments/assets/e06e4d3c-375f-48a8-9e17-565d846edf98" />
<img width="924" height="374" alt="image" src="https://github.com/user-attachments/assets/b2a0f29f-5d86-413b-99dd-d0281bc5d0de" />
<img width="567" height="131" alt="image" src="https://github.com/user-attachments/assets/411e1c16-3f30-445e-b650-96a517997e63" />




## RESULT:
The analysis was performed successfully using Sleuth Kit, and the disk structure was understood in detail.
