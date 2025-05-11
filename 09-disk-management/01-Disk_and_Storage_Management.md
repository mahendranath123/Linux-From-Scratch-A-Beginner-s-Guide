# 💽 Linux Disk and Storage Management Guide

## 📖 Introduction
Managing disks and storage efficiently is crucial for system performance and stability. Linux provides powerful commands to monitor, partition, format, mount, and manage disk storage.

🔹 **Key Features Covered:**
- 🖥️ Disk information viewing
- ✂️ Partition management
- 📌 Mounting/unmounting
- 🔄 Logical Volume Management (LVM)
- 🔄 Swap space management

## 📋 Command Cheat Sheet

```bash
# Quick Reference Table
```

| Category | Command | Description | Example |
|----------|---------|-------------|---------|
| 🔍 Viewing Disk Info | `lsblk` | Display block devices | `lsblk -o NAME,SIZE,TYPE,MOUNTPOINT` |
|  | `fdisk -l` | List disk partitions | `fdisk -l /dev/sda` |
|  | `blkid` | Show UUIDs of devices | `blkid /dev/sda1` |
|  | `df -h` | Check disk space usage | `df -h /home` |
|  | `du -sh` | Show directory size | `du -sh /var/log` |
## ✂️ Partition Management

### 🛠️ Basic Partition Operations
```bash
# List available disks
lsblk

# Create partition table (MBR/GPT)
fdisk /dev/sdX
parted /dev/sdX  # For GPT disks

# Format partitions
mkfs.ext4 /dev/sdX1  # ext4 filesystem
mkfs.xfs /dev/sdX1   # XFS filesystem
```
## 📌 Mounting and Unmounting

### 🔗 Mount Operations
```bash
# Temporary mount
mount /dev/sdX1 /mnt

# Permanent mount (add to /etc/fstab)
UUID=$(blkid -s UUID -o value /dev/sdX1)
echo "UUID=$UUID /mnt ext4 defaults 0 2" | sudo tee -a /etc/fstab

# Unmount safely
umount /mnt

# Remount as read-write
mount -o remount,rw /mnt
```
## 🔄 Logical Volume Management (LVM)

### 🏗️ LVM Setup Guide
```bash
# Initialize physical volume
pvcreate /dev/sdX

# Create volume group
vgcreate vg_name /dev/sdX

# Create logical volume (10GB)
lvcreate -L 10G -n lv_name vg_name

# Format and mount
mkfs.ext4 /dev/vg_name/lv_name
mount /dev/vg_name/lv_name /mnt

# Extend LV (add 5GB)
lvextend -L +5G /dev/vg_name/lv_name
resize2fs /dev/vg_name/lv_name
```
## 🔄 Swap Management

### ⚡ Swap Operations
```bash
# Create swap
mkswap /dev/sdX

# Enable swap
swapon /dev/sdX
swapon --show  # Verify

# Disable swap
swapoff /dev/sdX

# Add swap permanently
echo "/dev/sdX none swap sw 0 0" | sudo tee -a /etc/fstab
```
Viewing Disk Information
## 🔍 Viewing Disk Information

### 📌 Using lsblk
```bash
lsblk  # List all block devices
```
### 🗂️ Using fdisk
```bash
fdisk -l  # View partition details
```
### 📊 Using df
```bash
df -h  # Check available disk space
```
### 📂 Using du
```bash
du -sh /var/log  # Find directory size
```
## ✂️ Partition Management

### 🛠️ Creating a Partition with fdisk
```bash
fdisk /dev/sdX  # Interactive partition creation
```

### 🔧 Formatting a Partition
```bash
mkfs.ext4 /dev/sdX1  # Format as ext4
mkfs.xfs /dev/sdX1   # Format as XFS
```
## 📌 Mounting and Unmounting

### 🔗 Mount a Partition
```bash
mount /dev/sdX1 /mnt
```

### 🔓 Unmount a Partition
```bash
umount /mnt
```

### 🔄 Remount a Partition
```bash
mount -o remount,rw /mnt
```
## 🔄 Logical Volume Management (LVM)

### 🏗️ Create a Physical Volume
```bash
pvcreate /dev/sdX
```

### 🧩 Create a Volume Group
```bash
vgcreate vg_name /dev/sdX
```

### 📦 Create a Logical Volume
```bash
lvcreate -L 10G -n lv_name vg_name
```

### 🔧 Format and Mount the Logical Volume
```bash
mkfs.ext4 /dev/vg_name/lv_name
mount /dev/vg_name/lv_name /mnt
```
## 🔄 Swap Management

### 🛠️ Create a Swap Partition
```bash
mkswap /dev/sdX
```

### ⚡ Enable Swap
```bash
swapon /dev/sdX
```

### ⏹️ Disable Swap
```bash
swapoff /dev/sdX
```