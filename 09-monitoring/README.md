## 📊 **The Ultimate Guide to Linux System Monitoring**

*Ee guide lo, manam tools ni avi monitor chese resource (CPU, Memory, etc.) prakaaram divide chesam.*

-----

### 1\. Live Dashboards 🖥️ (Real-time Overview)

*System health ni oka single screen lo, live ga chudadaniki vaade primary tools.*

#### **`top`** & **`htop`**

  * **Purpose:** System resources (CPU, Memory) and processes ni **live** ga monitor cheyadaniki. `htop` install cheskunte, inka colorful and user-friendly ga untundi.
  * **Common "Power-ups" (Interactive Shortcuts in `top`):**
      * `P` (Shift+p): **P**CPU usage prakaaram sort cheyi.
      * `M` (Shift+m): **M**emory usage prakaaram sort cheyi.
      * `k`: Oka process ni **k**ill cheyadaniki.
      * `u`: Oka specific **u**ser process ni filter cheyi.
      * `q`: **Q**uit.
  * **Real-World Usage:**
    ```bash
    # System health ni live ga chudadaniki (htop is recommended)
    # First install it: sudo yum install htop
    htop
    ```

#### **`watch`**

  * **Purpose:** Oka command ni prathi `n` seconds ki repeat chesi, output lo changes ni live ga chupistundi.
  * **Common "Power-ups" (Options):**
      * `-n <seconds>`: **N**umber of seconds interval set cheyi.
  * **Real-World Usage:**
    ```bash
    # Prathi 2 seconds ki, memory usage lo changes ni chudu
    watch -n 2 'free -h'
    ```

-----

### 2\. CPU Monitoring 🧠

*System brain (CPU) entha busy ga undi, daani details ento teluskovadaniki.*

#### **`uptime`**

  * **Purpose:** System entha sepu nunchi **up** and running lo undi, entha **load** (rush) undi anedi cheptundi.
  * **Real-World Usage:**
    ```bash
    uptime
    # Output: 10:29 up 5 days, 1 user, load average: 0.05, 0.10, 0.15
    # Meaning: Last 1, 5, and 15 minutes lo average load entha undo chudochu.
    ```

#### **`nproc`** & **`lscpu`**

  * **Purpose:** System yokka CPU details teluskovadaniki.
  * **Real-World Usage:**
    ```bash
    # System lo enni CPU cores unnayo quick ga chudu
    nproc

    # CPU gurinchi full details (Architecture, Model name, etc.) telusko
    lscpu
    ```

-----

### 3\. Memory Monitoring 🐏

*System lo entha RAM and Swap vaadutunnaro teluskovadaniki.*

#### **`free`**

  * **Purpose:** System yokka **RAM (Memory)** and **Swap** space usage ni chupistundi.
  * **Common "Power-ups" (Options):**
      * `-h`: **H**uman-readable format (`GB`, `MB` lo).
      * `-m`: **M**egaBytes lo chupinchu.
      * `-s N`: Prathi **N** seconds ki update chesi chupinchu.
  * **Real-World Usage:**
    ```bash
    # Easy ga ardham ayye format lo memory usage chudu
    free -h
    ```

-----

### 4\. Disk & Storage Monitoring 💾

*System lo entha storage undi, evaru ekkuva vaadutunnaro teluskovadaniki.*

#### **`df`** (Disk Free)

  * **Purpose:** Anni mounted filesystems (drives) lo entha **disk space** undi anedi chupistundi.
  * **Common "Power-ups" (Options):**
      * `-h`: **H**uman-readable format.
      * `-T`: Filesystem **T**ype ni kooda chupinchu (e.g., `xfs`, `ext4`).
      * `-i`: **I**node usage.
  * **Real-World Usage:**
    ```bash
    # Anni drives and vaati types tho saha, easy format lo chudu
    df -hT
    ```

#### **`du`** (Disk Usage)

  * **Purpose:** Oka specific folder or file entha **disk space** teskuntundo chupistundi.
  * **Common "Power-ups" (Options):**
      * `-h`: **H**uman-readable format.
      * `-s`: **S**ummary (motham folder yokka total size matrame chupinchu).
      * `--max-depth=N`: Entha **depth** varaku velli chupinchalo cheppu.
  * **Real-World Usage:**
    ```bash
    # /var/log folder yokka total size ento chudu
    du -sh /var/log

    # Current directory lo unna prathi sub-folder entha size o chudu
    du -h --max-depth=1 .
    ```

-----

### 5\. Network Monitoring 🌐

*Server bayata prapancham tho ela matladutundo teluskovadaniki.*

#### **`ip`** & **`ifconfig`**

  * **Purpose:** Network interfaces and IP addresses ni chudataniki. `ip` anedi modern and powerful.
  * **Real-World Usage:**
    ```bash
    # Anni network interfaces, vaati IP addresses tho chudu
    ip a
    ```

#### **`ping`**

  * **Purpose:** Vere server/website reachable ga unda leda ani test cheyadaniki.
  * **Common "Power-ups" (Options):**
      * `-c <count>`: Enni packets pampalo **c**ount cheppu.
  * **Real-World Usage:**
    ```bash
    # Google server ki 5 packets pampi, connectivity test cheyi
    ping -c 5 google.com
    ```

#### **`ss`** & **`netstat`**

  * **Purpose:** Active network connections and listening ports chupistundi. `ss` anedi modern and faster.
  * **Common "Power-ups" (Options):**
      * `-t`: **T**CP, `-u`: **U**DP, `-l`: **L**istening, `-n`: **N**umeric, `-p`: **P**rocess.
  * **Real-World Usage:**
    ```bash
    # System lo listen chestunna anni TCP/UDP ports ni, vaati process details tho chudu
    sudo ss -tulnp
    ```

#### **`nslookup`** & **`traceroute`**

  * **Purpose:** DNS and network path ni debug cheyadaniki.
  * **Real-World Usage:**
    ```bash
    # google.com yokka IP address ento kanukko
    nslookup google.com
    ```

-----

### 6\. Advanced Performance Tools (CPU, Memory, I/O) 📈

*Ee commands system performance ni inka deep ga, historical ga analyze cheyadaniki.*

#### **`vmstat`** (Virtual Memory Statistics)

  * **Purpose:** System performance (processes, memory, I/O, CPU) gurinchi oka detailed snapshot istundi.
  * **Real-World Usage:**
    ```bash
    # Prathi 2 seconds ki, 5 sarlu performance report ivvu
    vmstat 2 5
    ```

#### **`iostat`** (Input/Output Statistics)

  * **Purpose:** CPU and Disk I/O (entha read/write jarugutundi) stats ni chupistundi. (Might need `sudo yum install sysstat`).
  * **Real-World Usage:**
    ```bash
    # Prathi second ki, disk activity lo unna extended stats chudu
    iostat -dx 1
    ```

#### **`sar`** (System Activity Reporter)

  * **Purpose:** System performance data ni over time collect chesi, historical reports ivvadaniki.
  * **Real-World Usage:**
    ```bash
    # Prathi 5 seconds ki, 3 sarlu, CPU usage report ivvu
    sar -u 5 3
    ```

-----

### 7\. Log Monitoring 📜

*System lo jarigina important events and errors ni chudataniki.*

#### **`dmesg`**

  * **Purpose:** System boot ayinappudu and hardware related **kernel messages** ni chupistundi.
  * **Common "Power-ups" (Options):**
      * `-T`: **T**imestamps ni human-readable format lo chupinchu.
  * **Real-World Usage:**
    ```bash
    # Hardware or driver issues ni debug cheyadaniki, last 20 messages chudu
    dmesg -T | tail -n 20
    ```

#### **`journalctl`**

  * **Purpose:** Modern systemd-based systems lo, anni system and service **logs** ni chudataniki vaade main command.
  * **Common "Power-ups" (Options):**
      * `-u <service>`: Oka specific **u**nit/service logs matrame chudu.
      * `-f`: **F**ollow (live logs).
      * `--since "time"`: Oka specific time nunchi logs chudu.
  * **Real-World Usage:**
    ```bash
    # Nginx service logs ni live ga follow avvu
    journalctl -u nginx -f
    ```

#### **`tail -f`**

  * **Purpose:** Log files ni **live** ga chudataniki.
  * **Real-World Usage:**
    ```bash
    # Application log file ni live ga chudu
    tail -f /var/log/my_app.log
    ```