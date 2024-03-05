# Operation on Directories
**Create:**
```bash
mkdir <directory-name>
```
**Delete**
```bash
rmdir <directory-name>
# non-empty directory
rm -r <directory-name>
```
**Change:**
```bash
cd <directory-name>
```
**List:** (list all files and directories in the current directory)
```bash
ls
# including hidden files
ls -a
```
**Copy:**
```bash
cp <source> <destination>
# Example: copy file to another directory
cp file.txt destination
# or copy directory to another directory
cp -r folder all-folders
```
**Move:**
```bash
mv <source> <destination>
# Example: move file to another directory
mv file.txt destination
# or move directory to another directory
mv folder all-folders 
```
**Rename:**
```bash
mv <old-name> <new-name>
# Example: rename file
mv old-name.txt new-name.txt
# or rename directory
mv old-name new-name
```
**Find:**
```bash
find <directory> -name <file-name>
# Example: find file in the current directory
find . -name file.txt
# or find file in the specific directory
find /home/user -name file.txt
# find all files with specific extension
find . -name "*.md"
```


