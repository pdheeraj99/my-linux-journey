# /sbin Folder lo DevOps + Cloud Ki Important Commands – Priority-wise Detailed Guide

**Telugu lo explanation tho, DevOps, Cloud, Automation, and Interview ki one-stop reference!**

---

## ⭐⭐⭐ HIGH PRIORITY (Must Know – Daily DevOps/Cloud Work)

### **Networking & System Management**

#### **ip**

- **Purpose:** Modern network configuration (IP, routes, interfaces, etc).
- **Usage:**

  ```bash
  sudo ip addr                # All interfaces chudataniki
  sudo ip link set eth0 up    # Interface enable cheyyataniki
  sudo ip route               # Routing table chudataniki
  ```

- **DevOps Use:** Cloud VMs, Kubernetes networking, automation scripts lo network setup.

#### **ifconfig**

- **Purpose:** Legacy network interface configuration.
- **Usage:**

  ```bash
  sudo ifconfig               # All interfaces
  sudo ifconfig eth0 up       # Interface enable
  ```

- **Note:** Modern systems lo `ip` command prefer cheyyali, but legacy systems lo inka use chestaru.

#### **route**

- **Purpose:** Routing table view/change.
- **Usage:**

  ```bash
  sudo route -n
  sudo route add default gw 192.168.1.1
  ```

- **Note:** `ip route` tho kuda chudavachu.

#### **iptables** (if present)

- **Purpose:** Firewall rules configuration.
- **Usage:**

  ```bash
  sudo iptables -L
  sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
  ```

- **DevOps Use:** Security automation, cloud firewall hardening.

#### **systemctl**

- **Purpose:** Service management (start, stop, enable, status).
- **Usage:**

  ```bash
  sudo systemctl status nginx
  sudo systemctl restart docker
  sudo systemctl enable jenkins
  ```

- **DevOps Use:** All cloud, container, CI/CD, and automation workflows.

#### **fdisk**

- **Purpose:** Disk partitioning (create, delete, modify partitions).
- **Usage:**

  ```bash
  sudo fdisk -l
  sudo fdisk /dev/xvdf
  ```

- **Cloud Use:** AWS EBS, Azure disks attach chesinappudu.

#### **mkfs, mkfs.ext4, mkfs.xfs, mkfs.vfat, mkfs.fat, mkfs.msdos, mkfs.minix, mkfs.cramfs**

- **Purpose:** Filesystem create cheyyadam (formatting).
- **Usage:**

  ```bash
  sudo mkfs.ext4 /dev/xvdf1
  sudo mkfs.xfs /dev/xvdf1
  ```

- **DevOps Use:** New storage volumes, persistent volumes for containers.

#### **fsck, fsck.ext4, fsck.xfs, fsck.vfat, fsck.fat, fsck.msdos, fsck.minix, fsck.cramfs**

- **Purpose:** Filesystem check & repair.
- **Usage:**

  ```bash
  sudo fsck /dev/xvdf1
  ```

- **Use:** Disk errors, boot issues, data corruption fix cheyyali ante.

#### **mount, umount**

- **Purpose:** Filesystem mount/unmount.
- **Usage:**

  ```bash
  sudo mount /dev/xvdf1 /mnt
  sudo umount /mnt
  ```

- **DevOps Use:** Cloud storage, EBS/EFS, NFS, container volumes.

#### **useradd, userdel, usermod, groupadd, groupdel, groupmod, passwd**

- **Purpose:** User/group create, delete, modify, password set.
- **Usage:**

  ```bash
  sudo useradd devuser
  sudo passwd devuser
  sudo usermod -aG docker devuser
  sudo groupadd devops
  ```

- **DevOps Use:** Automation scripts, onboarding, security.

#### **visudo**

- **Purpose:** Safe sudoers file edit.
- **Usage:**

  ```bash
  sudo visudo
  ```

- **Note:** Sudo permissions automation, security best practice.

#### **shutdown, reboot, poweroff**

- **Purpose:** System shutdown/reboot/poweroff.
- **Usage:**

  ```bash
  sudo shutdown -h now
  sudo reboot
  sudo poweroff
  ```

#### **sysctl**

- **Purpose:** Kernel parameters view/set.
- **Usage:**

  ```bash
  sudo sysctl -a
  sudo sysctl -w net.ipv4.ip_forward=1
  ```

- **DevOps Use:** Performance tuning, Kubernetes networking.

#### **logrotate**

- **Purpose:** Log file rotation automation.
- **Usage:**

  ```bash
  sudo logrotate /etc/logrotate.conf
  ```

- **DevOps Use:** Log management, disk full avoid cheyyali ante.

---

## ⭐⭐ MEDIUM PRIORITY (Sometimes Useful – Advanced/Specific)

### **Advanced Disk & Module Management**

#### **parted, cfdisk, sfdisk, gdisk, sgdisk**

- **Purpose:** Advanced disk partitioning (GPT, >2TB disks).
- **Usage:**

  ```bash
  sudo parted /dev/xvdf
  sudo cfdisk /dev/xvdf
  ```

#### **modprobe, insmod, rmmod, lsmod**

- **Purpose:** Kernel module load/unload/list.
- **Usage:**

  ```bash
  sudo modprobe overlay
  sudo rmmod overlay
  lsmod
  ```

#### **losetup**

- **Purpose:** Loop device setup (disk images).
- **Usage:**

  ```bash
  sudo losetup /dev/loop0 disk.img
  ```

#### **swapoff, swapon**

- **Purpose:** Swap enable/disable.
- **Usage:**

  ```bash
  swapon -s
  sudo swapoff -a
  sudo swapon /dev/xvdf2
  ```

### **SELinux & Security Management**

#### **restorecon, setenforce, getenforce, sestatus, semanage, semodule**

- **Purpose:** SELinux management.
- **Usage:**

  ```bash
  sestatus
  sudo setenforce 0
  sudo restorecon -R /var/www
  sudo semanage port -l
  ```

#### **auditctl, auditd, ausearch, aureport**

- **Purpose:** Audit framework management.
- **Usage:**

  ```bash
  sudo auditctl -l
  sudo ausearch -x sshd
  sudo aureport
  ```

#### **chkconfig, service**

- **Purpose:** SysV service enable/disable (older systems).
- **Usage:**

  ```bash
  sudo chkconfig --list
  sudo chkconfig httpd on
  sudo service nginx restart
  ```

#### **ethtool, mii-tool**

- **Purpose:** Network interface diagnostics.
- **Usage:**

  ```bash
  sudo ethtool eth0
  sudo mii-tool eth0
  ```

---

## ⭐ LOW PRIORITY (Rarely Used – Storage/Security Admins, Niche Use Cases)

#### **cryptsetup**

- **Purpose:** Disk encryption setup.
- **Usage:**

  ```bash
  sudo cryptsetup luksFormat /dev/xvdf1
  ```

#### **badblocks, debugfs, tune2fs, e2fsck, e2label, e2image, e2undo, e4defrag**

- **Purpose:** Advanced filesystem diagnostics/tuning.
- **Usage:**

  ```bash
  sudo badblocks /dev/xvdf1
  sudo tune2fs -l /dev/xvdf1
  sudo debugfs /dev/xvdf1
  ```

#### **nfs*, rpc*, showmount, exportfs**

- **Purpose:** NFS server/client management.
- **Usage:**

  ```bash
  sudo showmount -e
  sudo exportfs -a
  ```

#### **xfs*, mkfs.xfs, xfs_repair, xfs_quota, xfs_growfs, etc.**

- **Purpose:** XFS filesystem management.
- **Usage:**

  ```bash
  sudo mkfs.xfs /dev/xvdf1
  sudo xfs_repair /dev/xvdf1
  ```

#### **grub2-***  

- **Purpose:** Bootloader management.
- **Usage:**

  ```bash
  sudo grub2-mkconfig -o /boot/grub2/grub.cfg
  ```

---

## ❌ NEGLECT (No Need for DevOps/Cloud/Interview)

- **acpid, atd, atrun, dump-acct, dump-utmp, hwclock, rtcwake, plipconfig, slattach, tipc, tsig-keygen, unix_chkpwd, unix_update, validatetrans, zic, zramctl, ...**
  - *Purpose:* Legacy/hardware-specific, not needed for modern DevOps/cloud work.

---

# **Summary Table: /sbin Commands for DevOps/Cloud**

| Command(s)                | Purpose/Use Case                        | Priority   | Example Command                        |
|---------------------------|-----------------------------------------|------------|----------------------------------------|
| ip, ifconfig, route       | Network config/troubleshooting          | High       | ip addr, ifconfig eth0 up              |
| iptables                  | Firewall rules                          | High       | iptables -L                            |
| systemctl                 | Service mgmt (systemd)                  | High       | systemctl restart nginx                |
| fdisk, mkfs*, fsck*, mount| Disk/FS mgmt, cloud storage             | High       | fdisk -l, mkfs.ext4, fsck, mount       |
| useradd, userdel, group*  | User/group mgmt, automation             | High       | useradd dev, groupadd devops           |
| visudo                    | Sudoers safe edit                       | High       | visudo                                 |
| shutdown, reboot, poweroff| System power mgmt                       | High       | shutdown -r now, reboot                |
| sysctl                    | Kernel/network tuning                   | High       | sysctl -a, sysctl -w ...               |
| logrotate                 | Log mgmt/automation                     | High       | logrotate /etc/logrotate.conf          |
| parted, cfdisk, sfdisk    | Advanced partitioning                   | Medium     | parted /dev/xvdf                       |
| modprobe, insmod, rmmod   | Kernel modules                          | Medium     | modprobe overlay                       |
| losetup                   | Loop device mgmt                        | Medium     | losetup /dev/loop0 file.img            |
| swapoff, swapon           | Swap mgmt                               | Medium     | swapon -s, swapoff /dev/sda2           |
| restorecon, setenforce    | SELinux mgmt                            | Medium     | setenforce 0, sestatus                 |
| auditctl, auditd          | Audit framework                         | Medium     | auditctl -l                            |
| ethtool, mii-tool         | Network diagnostics                     | Medium     | ethtool eth0                           |
| chkconfig, service        | Legacy service mgmt                     | Medium     | chkconfig httpd on                     |
| cryptsetup                | Disk encryption                         | Low        | cryptsetup luksFormat /dev/xvdf1        |
| badblocks, debugfs, tune2fs| FS diagnostics/tuning                  | Low        | badblocks /dev/xvdf1                   |
| nfs*, rpc*, showmount     | NFS mgmt                                | Low        | showmount -e                           |
| xfs*                      | XFS FS mgmt                             | Low        | xfs_repair /dev/xvdf1                  |
| grub2-*                   | Bootloader mgmt                         | Low        | grub2-mkconfig -o /boot/grub2/grub.cfg |
| Others (acpid, atd, etc.) | Legacy/hardware-specific                | Neglect    | -                                      |

---

# **How to Use & Remember**

- **Cheat Sheet:** Top 10-15 commands, one-line purpose, and example.
- **Practice:** Use in cloud VMs, automation scripts, and troubleshooting labs.
- **README/Notes:** Maintain a markdown file with this table and short explanations.
- **Ignore the rest:** Unless you have a very specific hardware, legacy, or compliance use case, you can safely ignore the rest for DevOps/cloud work.

---

# **Practical DevOps/Cloud Use Cases**

- **Automation:** Use `useradd`, `groupadd`, `systemctl`, `logrotate`, `fdisk`, `mkfs`, `mount` in Ansible, shell scripts, or CI/CD pipelines for provisioning and configuration.
- **Networking:** `ip`, `ifconfig`, `route`, `ethtool` for network setup, troubleshooting, and automation.
- **Security:** `iptables` (if present), `visudo`, `auditctl`, `restorecon`, `setenforce` for firewall, sudo, audit, and SELinux automation.
- **Cloud Storage:** `fdisk`, `mkfs`, `fsck`, `mount`, `umount` for EBS/EFS/Block storage management in AWS, Azure, GCP.
- **Service Management:** `systemctl`, `chkconfig`, `service` for starting/stopping/enabling services in automation and troubleshooting.

---

**Mawa, ee notes ni /sbin folder ki one-stop DevOps/cloud reference laga use cheyyachu. High priority commands matrame deep ga practice cheyyandi, interviews lo kuda ee commands chala important! Inka specific command or use case meeda in-depth kavali ante, adugu!**
