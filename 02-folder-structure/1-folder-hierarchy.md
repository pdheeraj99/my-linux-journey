# Understanding the Folder Structure

### Explanation of System Directories

### **Symbolic Links (Less Significant)**
| Directory | Description |
|-----------|-------------|
| `/sbin -> /usr/sbin` | Administrative commands kosam unna system binaries (`/usr/sbin` ki link chesi untundi). |
| `/bin -> /usr/bin` | Avsaramaina user binaries (`/usr/bin` ki link chesi untundi). |
| `/lib -> /usr/lib` | Shared libraries mariyu kernel modules (`/usr/lib` ki link chesi untundi). |

### **Important System Directories**
| Directory | Description |
|-----------|-------------|
| `/boot` | System boot avvadaniki avasaramaina files ni store chestundi (containers lo idi relevant kaadu). |
| `/usr` | User install chesina chala varaku applications mariyu libraries ni kaligi untundi. |
| `/var` | Regular ga maarutune logs, caches, mariyu temporary files ni store chestundi. |
| `/etc` | System configuration files ni store chestundi. |

### **User & Application-Specific Directories**
| Directory | Description |
|-----------|-------------|
| `/home` | User home directories kosam default location. |
| `/opt` | Optional third-party software ni install cheyadaniki use chestaru. |
| `/srv` | Web servers lanti services kosam data ni hold chestundi (containers lo idi takkuvaga use chestaru). |
| `/root` | Root user yokka home directory. |

### **Temporary & Volatile Directories**
| Directory | Description |
|-----------|-------------|
| `/tmp` | Temporary files (reboot cheste clear avutayi). |
| `/run` | Processes yokka runtime data ni hold chestundi. |
| `/proc` | Process mariyu system information kosam virtual filesystem. |
| `/sys` | Hardware mariyu kernel information kosam virtual filesystem. |
| `/dev` | Device files ni kaligi untundi (e.g., `/dev/null`, `/dev/sda`). |

### **Mount Points**
| Directory | Description |
|-----------|-------------|
| `/mnt` | External filesystems kosam temporary mount point. |
| `/media` | Removable media (USB, CDs) kosam mount point. |
| `/data` | Windows nundi meeru mount chesina volume (`C:/ubuntu-data`). |