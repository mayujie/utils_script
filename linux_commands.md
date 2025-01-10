# Linux commands

Useful Docker image

`docker pull ubuntu/python:3.8-20.04_stable`

## Download & extract

Download and unzip extract
```bash
wget --version && cd /path/data && 
wget -i RAW_SIDD_URLs.txt -P /path/target_dir/ && 
cd /path/target_dir/ | unzip '*-*' -d /path/target_dir_new
```
Extracts files 
```bash
# Extracts all the files and folders inside zip file into a new named folder
unzip Imagenet32_val.zip -d ./verify_val

# Extract rar file, The x option stands for "extract with full path".
# extracted while preserving their directory structure
unrar x tracking.part01.rar /path/to/extract/
```

Download imagenet & extract
```bash
cd /path/ImageNet21K && wget https://image-net.org/data/imagenet21k_resized.tar.gz && 
tar -xvzf imagenet21k_resized.tar.gz

cd /nas/datasets/vision/ImageNet21K && wget https://image-net.org/data/winter21_whole.tar.gz && 
tar -xvzf winter21_whole.tar.gz
```

compress to zip
```bash
cd /path/data/ && zip -r lip_super_proc.zip images masks
# -r 是递归选项，表示将 train 文件夹及其所有子文件夹和内容一并压缩
# lip_super_proc.zip 是压缩后的文件名，压缩结果会保存为这个文件。
# images 和 masks 是待压缩的文件夹名称。
```

7z to compress
```bash
# x : eXtract files with full paths
sudo apt update && sudo apt install p7zip-full p7zip-rar && 
7z x detection_train_data.zip
```

for-loop extraction use 7z
```bash
# This command is a Bash for-loop that automates the extraction of all .zip files in the current directory using the 7z utility.
for z in *.zip; do 7z x "$z" ; done
```

zip to recover
```bash
# This command is used to fix or attempt to recover a potentially corrupt or incomplete ZIP archive.
# -F   fix zipfile (-FF try harder)
zip -F detection_train_data.zip --out detection_train_data_full.zip
zip -FF detection_train_data.zip --out detection_train_data_cp.zip
```

## Read, write, COPY
copy and archive means preserve the attributes

`cp -a /path/masks/. /path_target/masks/ `

Remove dir & unzip extract

`cd /path/data && rm -r valid train test && unzip '*.zip'`

move files
```bash
mv -v /path/segment_training_data/*.zip /target_path/zip_back_up/segment_training/
```

## access server via SSH related

### sshpass
A utility to automate password-based SSH authentication without requiring interactive password input.
```bash
sshpass -p 'password' ssh user@host
```

### openssh-client
Provides the client-side tools for SSH (Secure Shell) communication.

Includes commands like ssh, scp, and sftp.
```bash
ssh user@host
scp file.txt user@host:/path/to/destination
sftp user@host
```
### rsync
A powerful file synchronization and transfer tool.

Efficiently syncs files and directories between local and remote locations, transferring only the changes.
```bash
rsync -avz local_dir/ user@host:/remote_dir/
rsync -av --delete /source_dir/ /backup_dir/
```
### Combined Use Cases:
```bash
sshpass -p 'password' rsync -avz /local_dir/ user@remote_host:/remote_dir/
```

## Search files
The command searches for files with the .list extension in the specified directory and its subdirectories.
```bash
find /path/keywords_data_hxc/data4 -type f -name '*.list'
```

## Others
set pod to sleep
```bash
command: "export PYTHONPATH=$PYTHONPATH:$(pwd) && sleep 9999999999"
```

The command du -sh * is used to display the disk usage of files and directories in the current directory in a human-readable format.
```bash
# du Stands for Disk Usage.
#-s Stands for summary.
#-h human-readable.
#* A wildcard that matches all files and directories in the current directory.
du -sh *
```
pass output string password to next command, 
```bash
# sudo -S Runs the following command with superuser privileges.
# The -S option allows the password to be read from the standard input (in this case, provided by the echo command).
# Executes the string inside the single quotes as a shell command.
echo 'password' | sudo -S sh -c 'apt update && apt install -y p7zip-full p7zip-rar && 7z x archive.zip'
```
