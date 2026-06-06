# 🚀 AWS EC2 + EBS Persistent Storage Project
live Demo--https://irfanpasha05.github.io/aws-ec2-ebs-persistent-storage/
## 📌 Project Overview

This project demonstrates how to create, attach, mount, and configure an Amazon EBS volume on an AWS EC2 Ubuntu instance. The EBS volume was configured for persistent storage using `/etc/fstab` and verified after a system reboot.

---

## 🏗️ Architecture

```text
+----------------------+
|      AWS EC2         |
|    Ubuntu Server     |
+----------+-----------+
           |
           |
           v
+----------------------+
|      EBS Volume      |
|       10 GB          |
|     Mounted at       |
|       /data          |
+----------+-----------+
           |
           |
           v
+----------------------+
|      demo.txt        |
| Persistent Data      |
+----------------------+
```

---

## 🎯 Objectives

- Launch an EC2 Ubuntu instance
- Create and attach an EBS volume
- Format the EBS volume
- Mount the volume to Linux
- Configure automatic mounting using `/etc/fstab`
- Verify data persistence after reboot
- Troubleshoot mount issues

---

## 🛠️ Technologies Used

- AWS EC2
- AWS EBS
- Ubuntu Linux
- SSH
- Linux Filesystem (ext4)
- Git & GitHub

---

## 📋 Commands Used

```bash
lsblk

sudo mkfs.ext4 /dev/nvme1n1

sudo mkdir /data

sudo mount /dev/nvme1n1 /data

echo "Irfan EBS Persistence Project" | sudo tee /data/demo.txt

sudo blkid

sudo nano /etc/fstab

sudo mount -a

sudo reboot

df -h

cat /data/demo.txt
```

---

## 🔍 Troubleshooting

### Issue

EBS volume was not mounting automatically after reboot.

### Root Cause

Incorrect UUID was configured in `/etc/fstab`.

### Resolution

Verified UUID using:

```bash
sudo blkid
lsblk -f
```

Updated the correct UUID and verified successful automatic mounting after reboot.

---

## ✅ Final Verification

After reboot:

```bash
df -h
```

Output confirmed:

```text
/dev/nvme1n1 mounted on /data
```

Data verification:

```bash
cat /data/demo.txt
```

Output:

```text
Irfan EBS Persistence Project
```

---

## 📚 Key Learnings

- AWS EBS volume management
- Linux storage administration
- Filesystem creation and mounting
- Persistent storage configuration
- Troubleshooting Linux mount issues
- AWS infrastructure management

---

## 👨‍💻 Author

**Irfan Pasha**

- GitHub: https://github.com/IrfanPasha05
- Portfolio: https://irfanpasha05.github.io/my-portfolio/

---
⭐ If you found this project useful, please give it a star!
