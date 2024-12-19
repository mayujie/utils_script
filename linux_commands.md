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
Download imagenet & extract
```bash
cd /path/ImageNet21K && wget https://image-net.org/data/imagenet21k_resized.tar.gz && 
tar -xvzf imagenet21k_resized.tar.gz

cd /nas/datasets/vision/ImageNet21K && wget https://image-net.org/data/winter21_whole.tar.gz && 
tar -xvzf winter21_whole.tar.gz
```

```bash
cd /path/data/ && zip -r lip_super_proc.zip images masks
# -r 是递归选项，表示将 train 文件夹及其所有子文件夹和内容一并压缩
# lip_super_proc.zip 是压缩后的文件名，压缩结果会保存为这个文件。
# images 和 masks 是待压缩的文件夹名称。
```

## Read, write, COPY
copy and archive means preserve the attributes

`cp -a /path/masks/. /path_target/masks/ `

Remove dir & unzip extract

`cd /path/data && rm -r valid train test && unzip '*.zip'`

