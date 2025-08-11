## The LEGENDARY Linux Command Cheat Sheet (DevOps & Cloud Focus) 🚀

Ee guide, commands ni vaati purpose batti categories ga divide chestundi. **Prathi command ki most important options kooda add chesam.**

-----

### 1\. The Absolute Basics (Navigation & Creation) 🗺️

* **`pwd`** (Present Working Directory): Nuvvu current ga ఏ directory lo unnavo cheptundi.

  * **DevOps Use:** Automation scripts lo, correct path lo unnamo ledo confirm cheskovadaniki.

* **`ls`** (List): Current location lo unna files and folders list chupistundi.

  * **Most Common Options:**
    * `-l`: **L**ong listing format (permissions, owner, size, date chupistundi).
    * `-a`: **A**ll files (hidden files `.`, `..` tho saha chupistundi).
    * `-h`: **H**uman-readable sizes (`1K`, `2M`, `3G` laaga).
    * `-t`: **T**ime prakaaram sort cheyi (newest first).
    * `-r`: **R**everse order lo sort cheyi.

    <!-- end list -->

    ```bash
    ls -lha # anni options kalipi vaadadam
    ```

  * **DevOps Use:** Directory contents chudadaniki, permissions check cheyadaniki.

* **`cd`** (Change Directory): Vere directory ki velladaniki.

  * **Most Common Options:**
    * `cd ..`: Parent directory ki vellu.
    * `cd ~` or `cd`: Nee home directory ki vellu.
    * `cd -`: Last time unna directory ki vellu (chala useful shortcut).

* **`mkdir`** (Make Directory): Kotha empty folder create cheyyataniki.

  * **Most Common Options:**
    * `-p`: **P**arent directories lekapothe, vaatini kooda create cheyi.

    <!-- end list -->

    ```bash
    mkdir -p project/src/main # project and src folders lekapoina, create chestundi
    ```

* **`touch`**: Kotha empty file create cheyyataniki.

* **`stat`**: File gurinchi detailed info (size, permissions, timestamps) chupistundi.

-----

### 2\. File & Directory Operations (The Daily Toolkit) 🛠️

* **`cp`** (Copy): Files or folders ni copy cheyyataniki.

  * **Most Common Options:**
    * `-r`: **R**ecursive (folder and daani lopalivi anni copy cheyi).
    * `-v`: **V**erbose (em copy avutundo screen meeda chupinchu).
    * `-p`: **P**reserve (permissions, owner, timestamps lantiవి alane unchu).

* **`mv`** (Move): Files or folders ni move cheyadaniki or rename cheyadaniki.

  * **Most Common Options:**
    * `-v`: **V**erbose (em move avutundo chupinchu).
    * `-i`: **I**nteractive (overwrite chese mundu adugu).

* **`rm`** (Remove): Files or folders ni **permanently** delete cheyyataniki.

  * **Most Common Options:**
    * `-r`: **R**ecursive (folder and lopalivi anni delete cheyi).
    * `-f`: **F**orce (confirmation adagakunda, force ga delete cheyi).
    * `-i`: **I**nteractive (prathi file ki mundu adugu).

-----

### 3\. Viewing & Reading Files (The Inspector's Toolkit) 🕵️

* **`cat`**: Chinna file content ni display cheyyataniki.

* **`less`**: Pedda files ni scroll chesi chudataniki (large files ki best).

* **`head` / `tail`**: File lo first (`head`) or last (`tail`) lines chudataniki.

  * **Most Common Options:**
    * `-n <number>`: Enni lines chudalo cheppu (e.g., `tail -n 50`).
    * `-f`: **F**ollow (real-time lo log file ki add ayye kotha lines ni chupistu undu - SUPER IMPORTANT for logs).

* **`wc`** (Word Count): File lo unna lines, words, characters ni count chestundi.

  * **Most Common Options:**
    * `-l`: **L**ines matrame count cheyi.
    * `-w`: **W**ords matrame count cheyi.
    * `-c`: **C**haracters matrame count cheyi.

-----

### 4\. Searching & Filtering (The Detective's Toolkit) 🔍

* **`find`**: Files/folders ni search cheyyataniki.

  * **Most Common Options:**
    * `-name "*.log"`: Peru prakaaram search cheyi.
    * `-type f`: Type (**f**ile) prakaaram search cheyi (`d` for directory).
    * `-user <username>`: Owner prakaaram search cheyi.
    * `-mtime -7`: **M**odified **time** (last 7 days lo) prakaaram search cheyi.
    * `-exec <command> {} \;`: Find chesina prathi file meeda oka command run cheyi.

* **`grep`**: File lo or command output lo oka specific word (pattern) kosam search cheyyataniki.

  * **Most Common Options:**
    * `-r`: **R**ecursive (folder lopala unna anni files lo vethuku).
    * `-i`: **I**gnore case (case-sensitive kaakunda vethuku).
    * `-v`: In**v**ert match (aa word leni lines ni chupinchu).
    * `-n`: Line **n**umber tho saha chupinchu.

-----

### 5\. Text Processing (The Power User's Toolkit) ✍️

* **`awk`**: Text files lo columns extract/process cheyyataniki.
  * **Most Common Options:**
    * `-F <delimiter>`: Columns ni separate chese character enti anedi cheppu (e.g., `-F ':'`).
* **`sed`**: Files lo text ni search and replace cheyadaniki (stream editor).
  * **Most Common Options:**
    * `-i`: **I**n-place (original file lone changes cheseyi, screen meeda chupinchaku).
* **`xargs`**: Oru command output ni teskuni, veroka command ki input ga bulk ga pampistundi.
* **`diff`**: Rendu files madhya teda chupistundi.
  * **Most Common Options:**
    * `-u`: **U**nified format (clear ga, easy ga chudataniki).

-----

### 6\. Archiving & Transfer (Packaging & Shipping) 📦

* **`tar`**: Files/folders ni oka single file (`.tar` archive) la bundle cheyyataniki.
  * **Most Common Options:**
    * `c`: **C**reate an archive.
    * `x`: E**x**tract an archive.
    * `v`: **V**erbose (em jarugutundo chupinchu).
    * `f`: **F**ile (oka file tho pani cheyi).
    * `z`: G**z**ip compression tho pani cheyi.
    <!-- end list -->
    ```bash
    # Common Usage
    tar -czvf archive.tar.gz folder/ # Create
    tar -xzvf archive.tar.gz         # Extract
    ```

* **`ssh`** (Secure Shell): Vere server ki secure ga login avvadaniki.
  * **Most Common Options:**
    * `-i <key_file>`: **I**dentity file (private key) ni specify cheyi.
    * `-p <port_number>`: Default port (22) kaakunda vere **p**ort ki connect avvu.
* **`scp`** (Secure Copy): Files ni secure ga remote host ki copy cheyyataniki.
* **`rsync`**: Files/directories ni efficient ga sync cheyyataniki.
  * **Most Common Options:** ` -avz --delete `
* **`curl`**: URLs tho interact avvadaniki.
  * **Most Common Options:**
    * `-X <METHOD>`: Request method ni specify cheyi (e.g., `GET`, `POST`).
    * `-H <Header>`: Custom **h**eader pampu (e.g., `-H "Content-Type: application/json"`).
    * `-d <data>`: **D**ata pampu (POST request lo).
    * `-o <file>`: Output ni **o**utput file lo save cheyi.

-----

### 7\. Security & Permissions (The Bouncer's Toolkit) 🛡️

* **`chmod`**: File/directory permissions change cheyyataniki.
  * **Common Usage:**
    * `chmod 755 script.sh`: Numeric mode.
    * `chmod u+x script.sh`: Symbolic mode (**u**ser ki e**x**ecute add cheyi).
* **`chown`**: File/directory owner and group change cheyyataniki.
  * **Most Common Options:**
    * `-R`: **R**ecursive (folder lopala unna annitiki change cheyi).
* **`useradd` / `passwd`**: Kotha user ni create chesi, password set cheyadaniki.
  * **Most Common Options (`useradd`):**
    * `-m`: **M**ake home directory.
    * `-s <shell_path>`: User ki default **s**hell set cheyi (e.g., `-s /bin/bash`).
    * `-g <group>`: Primary **g**roup set cheyi.
    * `-G <groups>`: Secondary **G**roups set cheyi.

-----

### 8\. System Monitoring & Health Check (The Doctor's Toolkit) 🩺

* **`ps`**: Running processes ni chupistundi.
  * **Most Common Options:**
    * `aux`: (BSD style) Anni users vi, terminal control lenivi kooda, chupinchu.
    * `-ef`: (System V style) Anni processes ni full format lo chupinchu.
* **`top` / `htop`**: Real-time process and resource monitoring.
* **`df`**: Disk space usage chupistundi.
  * **Most Common Options:** `-h` (human-readable), `-i` (inodes).
* **`du`**: Oka specific directory entha space teskuntundo chupistundi.
  * **Most Common Options:** `-h` (human-readable), `-s` (summary).
* **`ss`**: Active network connections and listening ports chupistundi.
  * **Most Common Options:**
    * `-t`: **T**CP connections.
    * `-u`: **U**DP connections.
    * `-l`: **L**istening ports.
    * `-n`: **N**umeric (IPs, port numbers chupinchu, perlu kaadu).
    * `-p`: **P**rocesses (aa port ni use chestunna program chupinchu).
* **`ping`**: Network connectivity ni test cheyadaniki.
  * **Most Common Options:** `-c <count>`: Enni packets pampalo **c**ount cheppu.
* **`journalctl`**: Systemd services yokka logs chudataniki.
  * **Most Common Options:**
    * `-u <service>`: Oka specific **u**nit/service logs matrame chudu.
    * `-f`: **F**ollow (live logs).

-----

Idhe mawa mana **'Legendary Edition'** cheat sheet. Prathi command ki ippudu power-ups (options) kooda unnayi. Chusi ela anipinchindo cheppu\!
