# /etc Folder lo DevOps ki Important Files

---

## 1. **/etc/passwd**

- **Purpose**: System lo unna prati user ki details (username, UID, GID, home directory, shell) ikada untayi.
- **DevOps Use**: User management, permissions, automation scripts lo user checks.
- **Command**:

  ```bash
  cat /etc/passwd
  ```

  (User list chudataniki)

---

## 2. **/etc/shadow**

- **Purpose**: User passwords (encrypted ga) and password expiry info ikada untadi. Only root ki access.
- **DevOps Use**: Security audits, password policies.
- **Command**:

  ```bash
  sudo cat /etc/shadow
  ```

  (Root access tho chudali)

---

## 3. **/etc/group**

- **Purpose**: System lo groups and vati members list ikada untadi.
- **DevOps Use**: Group-based permissions, automation scripts lo group checks.
- **Command**:

  ```bash
  cat /etc/group
  ```

---

## 4. **/etc/sudoers**

- **Purpose**: Evaru sudo (root permissions) use cheyyalo decide cheyyadaniki.
- **DevOps Use**: Secure privilege escalation, automation scripts ki limited root access.
- **Command**:

  ```bash
  sudo visudo
  ```

  (Edit cheyyali ante visudo use cheyyali, direct edit cheyyakandi)

---

## 5. **/etc/hosts**

- **Purpose**: Hostname to IP mapping manual ga cheyyadaniki.
- **DevOps Use**: Local DNS override, testing, static mapping.
- **Command**:

  ```bash
  cat /etc/hosts
  sudo nano /etc/hosts
  ```

---

## 6. **/etc/resolv.conf**

- **Purpose**: DNS servers list ikada untadi.
- **DevOps Use**: Custom DNS set cheyyali ante, network troubleshooting.
- **Command**:

  ```bash
  cat /etc/resolv.conf
  sudo nano /etc/resolv.conf
  ```

---

## 7. **/etc/fstab**

- **Purpose**: System boot appudu mount avvalsina disks, partitions, NFS shares list.
- **DevOps Use**: Storage automation, EBS/EFS mount cheyyali ante.
- **Command**:

  ```bash
  cat /etc/fstab
  sudo nano /etc/fstab
  ```

---

## 8. **/etc/ssh/sshd_config**

- **Purpose**: SSH server configuration (port, root login, key auth, etc).
- **DevOps Use**: Secure remote access, automation, security hardening.
- **Command**:

  ```bash
  cat /etc/ssh/sshd_config
  sudo nano /etc/ssh/sshd_config
  sudo systemctl restart sshd
  ```

---

## 9. **/etc/sysctl.conf**

- **Purpose**: Kernel parameters (network tuning, file limits, etc).
- **DevOps Use**: Performance tuning, security hardening.
- **Command**:

  ```bash
  cat /etc/sysctl.conf
  sudo nano /etc/sysctl.conf
  sudo sysctl -p
  ```

---

## 10. **/etc/crontab** & **/etc/cron.* (daily, hourly, weekly, monthly)**

- **Purpose**: Scheduled automation tasks (cron jobs).
- **DevOps Use**: Backups, monitoring, periodic scripts.
- **Command**:

  ```bash
  cat /etc/crontab
  sudo nano /etc/crontab
  ls /etc/cron.daily/
  ```

---

## 11. **/etc/nsswitch.conf**

- **Purpose**: System info (users, hosts, etc) resolution order (files, DNS, LDAP, etc).
- **DevOps Use**: Customizing lookup order for performance/security.
- **Command**:

  ```bash
  cat /etc/nsswitch.conf
  ```

---

## 12. **/etc/network/interfaces** (Debian/Ubuntu) / **/etc/sysconfig/network-scripts/** (RHEL/CentOS)

- **Purpose**: Network interface configuration.
- **DevOps Use**: Static IP, bonding, VLANs, cloud networking.
- **Command**:

  ```bash
  cat /etc/network/interfaces
  sudo nano /etc/network/interfaces
  ```

---

## 13. **/etc/systemd/system/** (and **/etc/init.d/**)

- **Purpose**: Service (daemon) management, custom service unit files.
- **DevOps Use**: Service automation, custom deployments.
- **Command**:

  ```bash
  ls /etc/systemd/system/
  sudo systemctl status <service>
  sudo systemctl edit <service>
  ```

---

## 14. **/etc/pam.d/**

- **Purpose**: Authentication modules configuration.
- **DevOps Use**: Custom login/auth policies, MFA integration.
- **Command**:

  ```bash
  ls /etc/pam.d/
  cat /etc/pam.d/sshd
  ```

---

## 15. **/etc/selinux/config**

- **Purpose**: SELinux security mode (enforcing, permissive, disabled).
- **DevOps Use**: Security hardening, compliance.
- **Command**:

  ```bash
  cat /etc/selinux/config
  sudo nano /etc/selinux/config
  ```

---

## 16. **/etc/audit/audit.rules**

- **Purpose**: Auditd rules for system event logging.
- **DevOps Use**: Security compliance, incident response.
- **Command**:

  ```bash
  cat /etc/audit/audit.rules
  ```

---

## 17. **/etc/logrotate.conf** & **/etc/logrotate.d/**

- **Purpose**: Log file rotation and management.
- **DevOps Use**: Prevent disk full, log management automation.
- **Command**:

  ```bash
  cat /etc/logrotate.conf
  ls /etc/logrotate.d/
  ```

---

## 18. **/etc/yum.repos.d/** (RHEL/CentOS) / **/etc/apt/** (Debian/Ubuntu)

- **Purpose**: Package repository configuration.
- **DevOps Use**: Custom repo setup, package automation.
- **Command**:

  ```bash
  ls /etc/yum.repos.d/
  cat /etc/yum.repos.d/*.repo
  ```

---

## 19. **/etc/hostname**

- **Purpose**: System hostname.
- **DevOps Use**: Host identification, automation scripts.
- **Command**:

  ```bash
  cat /etc/hostname
  sudo hostnamectl set-hostname <newname>
  ```

---

## 20. **/etc/os-release**

- **Purpose**: OS version info.
- **DevOps Use**: Automation scripts lo OS detection.
- **Command**:

  ```bash
  cat /etc/os-release
  ```

---

# General Commands for Viewing & Editing

- **cat**: File ni chudataniki
- **less/more**: Page by page chudataniki
- **nano/vim**: Edit cheyyataniki (sudo use cheyyali)
- **cp**: Backup ki

  ```bash
  sudo cp /etc/filename /etc/filename.bak
  ```

- **grep**: Search cheyyataniki

  ```bash
  grep "pattern" /etc/filename
  ```

---

# Security Best Practices

- **Backup chesi edit cheyyandi**: Always backup before editing.
- **sudo use cheyyandi**: Most files root permissions lo untayi.
- **visudo for sudoers**: Direct ga edit cheyyakandi, visudo use cheyyandi.
- **Logs and cron jobs**: Automation ki logs maintain cheyyandi.

---

# Summary Table

| File/Folder                | Purpose/Use Case                        | Command Example                  |
|----------------------------|-----------------------------------------|----------------------------------|
| /etc/passwd                | User info                               | cat /etc/passwd                  |
| /etc/shadow                | Passwords (encrypted)                   | sudo cat /etc/shadow             |
| /etc/group                 | Groups info                             | cat /etc/group                   |
| /etc/sudoers               | Sudo permissions                        | sudo visudo                      |
| /etc/hosts                 | Hostname-IP mapping                     | sudo nano /etc/hosts             |
| /etc/resolv.conf           | DNS servers                             | sudo nano /etc/resolv.conf       |
| /etc/fstab                 | Mount points                            | sudo nano /etc/fstab             |
| /etc/ssh/sshd_config       | SSH server config                       | sudo nano /etc/ssh/sshd_config   |
| /etc/sysctl.conf           | Kernel params                           | sudo nano /etc/sysctl.conf       |
| /etc/crontab               | System cron jobs                        | sudo nano /etc/crontab           |
| /etc/nsswitch.conf         | Lookup order                            | cat /etc/nsswitch.conf           |
| /etc/network/interfaces    | Network config (Debian)                 | sudo nano /etc/network/interfaces|
| /etc/systemd/system/       | Custom service units                    | sudo systemctl edit <service>    |
| /etc/pam.d/                | Auth modules                            | cat /etc/pam.d/sshd              |
| /etc/selinux/config        | SELinux mode                            | sudo nano /etc/selinux/config    |
| /etc/audit/audit.rules     | Audit rules                             | cat /etc/audit/audit.rules       |
| /etc/logrotate.conf        | Log rotation                            | cat /etc/logrotate.conf          |
| /etc/yum.repos.d/          | Package repos (RHEL)                    | ls /etc/yum.repos.d/             |
| /etc/hostname              | Hostname                                | sudo hostnamectl set-hostname    |
| /etc/os-release            | OS info                                 | cat /etc/os-release              |

---

# /etc Important Files Cheat Sheet

| File/Folder         | Purpose                  | Command Example           | Notes                        |
|---------------------|--------------------------|---------------------------|------------------------------|
| /etc/passwd         | User info                | cat /etc/passwd           | User list, never edit directly|
| /etc/shadow         | Passwords (encrypted)    | sudo cat /etc/shadow      | Root only, password policies |
| /etc/sudoers        | Sudo permissions         | sudo visudo               | Always use visudo to edit    |
| /etc/hosts          | Hostname-IP mapping      | sudo nano /etc/hosts      | Local DNS override           |
| /etc/ssh/sshd_config| SSH server config        | sudo nano /etc/ssh/sshd_config | Restart sshd after edit |

**Mawa, ee notes chalu, DevOps lo /etc folder lo important files, vati use cases, and commands clear ga untayi. Inka doubts unte, specific file or use case adugu, in-depth explain chestha!**  
