# 🐧 **Introduction to Process Management**
Process ante enti?  
Process ante oka running program. Prathi process ki unique number untundi, daani **PID (Process ID)** antaru. Prathi process ki parent process untundi. Ee guide lo manam processlu ni choodadam, control cheyyadam, manage cheyyadam ela cheyyalo nerchukuntam.

---

# 👀 **Choodatam: Processes ni ela chudali? (Viewing Processes)**

| Command | Ardham (Explanation) | Common Options |
|---------|----------------------|---------------|
| `ps aux` | System lo run avuthunna anni processlu ni chupistundi. | `-u <user>` (user processlu), `-C <name>` (process name), `-o <fields>` (custom columns), `-p <PID>` (specific PID) |
| `ps -ef` | Anni processlu ni full format lo chupistundi. | `-f` (full), `-e` (all), `-l` (long), `-j` (jobs format) |
| `ps -u username` | Oka user run chestunna processlu ni chupistundi. |  |
| `ps -C processname` | Process peru tho vetakadaniki. |  |
| `ps -eo pid,ppid,user,cmd,%mem,%cpu --sort=-%mem` | Memory ekkuva vadina processlu sort cheyyadam. |  |
| `pstree -p` | Processlu ni tree laaga, parent-child relation tho chupistundi, PID tho. |  |
| `pgrep processname` | Process peru tho PID number isthundi. | `-u <user>` (user filter), `-l` (name tho), `-f` (full command line) |
| `pidof processname` | Process ki PID number direct ga isthundi. |  |
| `jobs -l` | Current shell lo background jobs list chupistundi, PID tho. |  |
| `lsof -p PID` | A process open chesina files ni chupistundi. | `-i` (network), `-u <user>` (user filter) |
| `ps -ef | grep processname` | Process peru tho filter cheyyataniki. |  |

---

# 🔍 **Vetakadam: Specific Process ni Ela Vetakali? (Finding a Process)**

- **By Name:**  
  `ps -C processname`  
  `pgrep processname`  
  `pidof processname`  
  `ps -ef | grep processname`
- **By User:**  
  `ps -u username`  
  `pgrep -u username`
- **By Custom Filter:**  
  `ps -eo pid,ppid,user,cmd | grep pattern`

---

# 🚦 **Niyantrinchadam: Processes ni ఆపడం & కొనసాగించడం (Controlling Processes)**

| Command | Ardham (Explanation) | Common Options |
|---------|----------------------|---------------|
| `kill PID` | Process ni soft ga close cheyadaniki (SIGTERM). | `-15` (default, soft), `-1` (SIGHUP), `-2` (SIGINT) |
| `kill -9 PID` | Process ni force ga (balavantam ga) aapadaniki (SIGKILL). |  |
| `pkill processname` | Process peru tho anni processlu ni close cheyadaniki. | `-u <user>`, `-f` (full cmd), `-9` (force) |
| `killall processname` | Peru tho anni processlu ni terminate cheyadaniki. | `-9` (force), `-u <user>` |
| `pkill -9 processname` | Peru tho anni processlu ni force ga terminate cheyadaniki. |  |
| `kill -STOP PID` | Process ni temporary ga pause cheyadaniki. |  |
| `kill -CONT PID` | Pause chesina process ni malli continue cheyadaniki. |  |
| `CTRL+C` | Foreground lo run avuthunna process ni terminate cheyadaniki. |  |
| `xargs kill` | Multiple PIDs ni oka sarlu kill cheyadaniki. |  |

**Examples:**
```bash
kill -15 1234         # Soft kill
kill -9 1234          # Force kill
pkill -u appuser      # User processlu anni kill
killall -9 python3    # All python3 processes force kill
ps aux | grep java | awk '{print $2}' | xargs kill
```

---

# 🏃‍♂️💨 **Background & Foreground lo Nadapadam (Job Control & Management)**

| Command | Ardham (Explanation) |
|---------|----------------------|
| `command &` | Command ni background lo run cheyadaniki. |
| `nohup command &` | Terminal close chesina kuda process run avvadam kosam. |
| `jobs -l` | Background jobs list chudataniki, PID tho. |
| `Ctrl + Z` | Foreground process ni pause cheyadaniki (suspend cheyyadam). |
| `bg %jobnumber` | Pause chesina job ni background lo continue cheyadaniki. |
| `fg %jobnumber` | Background job ni malli foreground lo techukodaniki. |

**Pro Tips:**
- `disown` – Background job ni shell nunchi detach cheyyadam (logout ayina kuda run avutundi).
- `screen` / `tmux` – Persistent sessions ki, especially for long-running jobs.

---

# 🥇🥈🥉 **Pradhanyata: Process Priority ni Ela Set Cheyyali? (Process Priority & Scheduling)**

| Command | Ardham (Explanation) | Options/Examples |
|---------|----------------------|------------------|
| `nice -n 10 command` | Command ni takkuva priority tho start cheyadaniki (1 to 19, ekkuva number ante takkuva priority). | `nice -n 19 myscript.sh` |
| `renice -n -5 -p PID` | Already run avuthunna process priority ni penchadaniki (negative value ante ekkuva priority, root user matrame cheyyagaladu). | `renice -n -10 -p 1234` |
| `renice -n 10 -p PID` | Process priority ni thaggadaniki (positive value ante takkuva priority). |  |
| `top` | NI (nice) column lo process priority chudachu. |  |

**Advanced:**
- `chrt` – Real-time scheduling class set cheyyadam (rare, but for performance tuning).

---

# 📊 **Live ga Monitor Cheyadam (Live & Historical Monitoring)**

| Command | Ardham (Explanation) | Options/Shortcuts |
|---------|----------------------|-------------------|
| `top` | System lo run avuthunna processlu ni live ga chudataniki. | `k` (kill), `r` (renice), `P` (CPU sort), `M` (memory sort), `u` (user filter), `q` (quit) |
| `htop` | top kanna better, colorful, user-friendly tool (install cheyyali). Mouse tho manage cheyyachu. | F9 (kill), F6 (sort), F3 (search), F2 (setup) |
| `free -h` | System memory usage chudataniki. |  |
| `df -h` | Disk space usage chudataniki. |  |
| `du -sh directory` | Oka directory size chudataniki. |  |
| `vmstat 1` | System performance stats prathi 1 sec ki. |  |
| `iostat` | CPU, disk I/O stats chudataniki. |  |
| `sar -u 5 5` | CPU usage stats every 5 sec, 5 times. |  |
| `watch -n 2 command` | Command ni prathi 2 seconds ki repeat chesi output chupistundi. |  |
| `tail -f /var/log/syslog` | Live ga log files chudataniki (troubleshooting ki useful). |  |

---

# ⚙️ **System Services (Daemons) ni Manage cheyadam**

| Command | Ardham (Explanation) | Options/Examples |
|---------|----------------------|------------------|
| `systemctl list-units --type=service` | System lo unna anni services (daemons) list chudataniki. |  |
| `systemctl status service-name` | Service status (running, stopped, failed) chudataniki. | `systemctl status nginx` |
| `systemctl start service-name` | Service ni start cheyadaniki. |  |
| `systemctl stop service-name` | Service ni stop cheyadaniki. |  |
| `systemctl restart service-name` | Service ni stop chesi malli start cheyadaniki. |  |
| `systemctl enable service-name` | System boot ayinappudu service automatic ga start avvadam kosam. |  |
| `systemctl disable service-name` | Service ni boot lo automatic ga start avvakunda cheyadaniki. |  |
| `systemctl reload service-name` | Service configuration changes apply cheyadaniki (without full restart). |  |
| `journalctl -u service-name -xe` | Service logs chudataniki (systemd). |  |

---

# 🌀 **Process States (Process yoka Sthitulu)**

| State | Ardham (Explanation) |
|-------|----------------------|
| **R (Running)** | Process panichesutondi. |
| **S (Sleeping)** | Process wait chestondi (input/resource kosam). |
| **D (Uninterruptible Sleep)** | Disk I/O kosam waiting, kill cheyalemu. |
| **T (Stopped)** | Process pause chesaru (Ctrl+Z valla, kill -STOP). |
| **Z (Zombie)** | Process ayipoyindi, kani parent ki status ivvaledu. |
| **Orphan** | Parent process ledu, system adopt chesindi. |

---

# 🧰 **Advanced & Troubleshooting Tools**

| Command | Ardham (Explanation) | Example |
|---------|----------------------|---------|
| `strace -p PID` | Process system calls trace cheyyadam (debugging ki). | `strace -p 1234` |
| `lsof -i :80` | Port 80 lo open unna processlu chudataniki. |  |
| `pgrep -f pattern` | Full command line lo pattern match cheyyadam. | `pgrep -f gunicorn` |
| `pkill -u username` | Oka user ki sambandhinchina processlu anni kill cheyyadam. |  |
| `ps -eo pid,ppid,user,cmd,%mem,%cpu --sort=-%cpu` | CPU ekkuva vadina processlu sort cheyyadam. |  |
| `dmesg | tail` | Kernel messages chudataniki. |  |
| `crontab -l` | Scheduled jobs list chudataniki. |  |

---

# 🛡️ **Best Practices (Manchi Acharalu)**

- **Monitor Regularly:** `top`, `htop`, `ps`, `vmstat`, `iostat` use cheyyandi system health kosam.
- **Graceful Termination:** First `kill` (SIGTERM) try cheyyandi, tarvata `kill -9` (SIGKILL) vadandi.
- **Critical Process Priority:** `nice` and `renice` tho important process ki ekkuva priority ivvandi.
- **Long Running Tasks:** `nohup`, `screen`, `tmux` vadandi, terminal close aina process run avvadam kosam.
- **Service Management:** Modern Linux lo `systemctl` vadandi services ni manage cheyyadaniki.
- **Automation:** Shell scripts, `cron`, `at` tho routine monitoring and process management automate cheyyandi.
- **Logs and Alerts:** `tail -f`, `journalctl`, and alerting tools tho abnormal process behavior ni monitor cheyyandi.
- **Resource Limits:** Production lo resource limits (ulimit, cgroups) set cheyyandi.
- **Security:** Only required users ki process control permissions ivvandi.
- **Documentation:** Prathi custom script or automation ki documentation maintain cheyyandi.

---

# 💡 **Pro Tips for DevOps Engineers**

- **Aliases:** Regular ga vadey commands ki aliases create cheyyandi (e.g., `alias psg='ps aux | grep'`).
- **Scripting:** Process checks, restarts, and alerts automate cheyyandi with shell scripts.
- **Integration:** Monitoring tools (Nagios, Zabbix, Prometheus, Grafana) integrate cheyyandi for enterprise scale.
- **Container Awareness:** Docker/Kubernetes lo process management ki `docker top`, `kubectl exec`, `kubectl logs` vadandi.
- **Log Rotation:** Log files size control ki logrotate configure cheyyandi.
- **Health Checks:** Service/process health ki custom health checks implement cheyyandi.

**Happy Linux DevOps Learning!** 🐧🚀  