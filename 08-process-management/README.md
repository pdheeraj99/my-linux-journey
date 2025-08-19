### 📜 **Introduction to Process Management**
*Process ante oka running program.* Prati program ki oka unique number untundi, daanine **PID (Process ID)** antaru. Ee commands tho manam ee processes ni control cheyochu.

### 👀 **Choodatam: Processes ni ela chudali? (Viewing Processes)**
Running lo unna processes ni chudataniki ee commands vadandi.

- `ps aux`
  - *System lo run avuthunna **anni** processes ni chupistundi.* (Shows **all** running processes on the system).
- `ps -ef`
  - *Idi kuda `ps aux` laantide, inko popular format lo chupistundi.* (Similar to `ps aux`, shows processes in a different popular format).
- `ps -u username`
  - *Oka particular **user** run chestunna processes ni chupistundi.* (Shows processes for a specific user).
- `pstree`
  - *Processes ni oka **tree laaga**, parent-child relationship tho chupistundi. Chala easy ga ardham avuthundi.* (Shows processes in a visual tree format).

### 🔍 **Vetakadam: Specific process ni ela vetakali? (Finding a Process)**
Oka particular process gurinchi telusukovali ante:

- `ps -C processname`
  - ***Process peru tho** vetakadaniki.* (To find a process by its name).
- `pgrep processname`
  - *Process peru isthe, daani **PID number** isthundi.* (Give the process name, it returns the PID).
- `pidof processname`
  - *Idi kuda `pgrep` laantide, direct ga **PID** isthundi.* (Similar to `pgrep`, directly gives the PID).

### 🚦 **Niyantrinchadam: Processes ni ఆపడం & కొనసాగించడం (Controlling Processes)**
Processes ni aapataniki (stop/kill) and malli continue cheyataniki.

- `kill PID`
  - *Process ni **soft ga** close cheyadaniki. Deeniki Process ID kavali.* (To gently terminate a process).
- `pkill processname`
  - ***Process peru tho** close cheyadaniki.* (To kill a process by its name).
- `killall processname`
  - *Idi kuda `pkill` laantide, peru tho **anni instances ni** close chestundi.* (Similar to pkill, kills all instances with that name).
- `kill -9 PID`
  - *Process ni **balavantham ga** (forcefully) aapadaniki. Idi data loss cheyochu, jagratha!* (To force kill a process. Be careful!).
- `kill -STOP PID`
  - *Running process ni **appatiki pause** cheyadaniki.* (To pause a running process).
- `kill -CONT PID`
  - ***Pause chesina process ni** malli continue cheyadaniki.* (To resume a paused process).

### 🏃♂️💨 **Background & Foreground lo Nadapadam (Running Processes)**
Commands ni terminal block cheyakunda background lo run cheyadaniki.

- `command &`
  - *Command ni **background lo** run cheyadaniki.* (To run a command in the background).
- `nohup command &`
  - ***Terminal close chesina kuda**, background lo command run avuthune undataniki.* (To keep a command running even after closing the terminal).
- `jobs`
  - ***Background lo** run avuthunna commands (jobs) list chudataniki.* (To list background jobs).
- `Ctrl + Z`
  - *Appudu run avuthunna process ni **pause chesi, background ki** pampadaniki.* (To suspend the current foreground process).
- `fg %jobnumber`
  - *Background job ni malli **munduki (foreground)** techukodaniki.* (To bring a job to the foreground).
- `bg %jobnumber`
  - ***Pause chesina job ni** background lo continue cheyadaniki.* (To resume a suspended job in the background).

### 🥇🥈🥉 **Pradhanyata: E-Process ki entha importance ivvali? (Process Priority)**
CPU e-process ki ekkuva importance ivvalo cheppadaniki.

- `nice -n 10 command`
  - *Oka command ni **takkuva priority** tho start cheyadaniki (value 1 to 19).* (To start a command with lower priority).
- `renice -n -5 -p PID`
  - *Already run avuthunna process **priority ni marchadaniki**. Negative value (-1 to -20) isthe **ekkuva priority** (root user matrame cheyagalaru).* (To change the priority of a running process).

### 📊 **Live ga Monitor Cheyadam (Live Monitoring)**
System load ni, processes ni live ga chudataniki.

- `top`
  - *System lo run avuthunna processes ni **live ga chudataniki** oka dashboard.* (Interactive process viewer).
  - Shortcuts: `k` to kill, `r` to renice, `q` to quit.
- `htop`
  - *`top` kanna **better, colorful, and user-friendly** tool. Mouse kuda use cheyochu. Install chesukovali.* (A more user-friendly viewer).

### ⚙️ **System Services (Daemons) ni Manage cheyadam**
System boot ayinappudu start ayye background services (daemons).

- `systemctl list-units --type=service`
  - *System lo unna **anni services** (daemons) list chudataniki.* (List all system daemons/services).
- `systemctl start service-name`
  - *Service ni **start** cheyadaniki.* (To start a service).
- `systemctl stop service-name`
  - *Service ni **stop** cheyadaniki.* (To stop a service).
- `systemctl status service-name`
  - *Service **status** (running, stopped, failed) telusukodaniki.* (To check the status of a service).
- `systemctl restart service-name`
  - *Service ni **stop chesi malli start** cheyadaniki.* (To restart a service).
- `systemctl enable service-name`
  - *System start ayinappudu, service **automatic ga start** avadaniki.* (To enable a service to start on boot).

### ✅ **Mugimpu (Conclusion)**
Process management Linux system administration lo chala mukhyam. Ee commands tho meeru Linux lo processes ni chala easy ga manage cheyagalaru. Practice chesthu undandi