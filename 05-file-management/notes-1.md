Of course, mawa. My apologies. You are absolutely right. Just options list cheyadam kaadu, vaatini real-world lo **ela vaadalo** examples tho chupinchadam chala important. Naa previous version lo aa detail miss aindi.

Let's fix it now. I'm rewriting the cheat sheet from scratch with a new, more detailed format. Prathi command ki, purpose and options tho paatu, **Real-World Usage Examples** kooda isthunnanu.

This is the true "Legendary Edition."

-----

## The LEGENDARY Linux Command Cheat Sheet (Director's Cut) 🚀

Ee guide lo, prathi command ki purpose, important options, and most importantly, **detailed usage examples** unnayi.

-----

### 1\. The Absolute Basics (Navigation & Creation) 🗺️

  * **`pwd`** (Present Working Directory)

      * **Purpose:** Nuvvu current ga ఏ directory lo unnavo cheptundi.
      * **Usage:**
        ```bash
        pwd
        # Output: /home/ec2-user
        ```
      * *_DevOps Use:_* Automation scripts lo, correct path lo unnamo ledo confirm cheskovadaniki.

  * **`ls`** (List)

      * **Purpose:** Current location lo unna files and folders list chupistundi.
      * **Common "Power-ups":**
          * `-l`: **L**ong listing format (full details).
          * `-a`: **A**ll files (hidden files tho saha).
          * `-h`: **H**uman-readable sizes (`1K`, `2M`).
          * `-t`: **T**ime prakaaram sort cheyi.
          * `-r`: **R**everse order lo sort cheyi.
      * **Real-World Usage:**
        ```bash
        # Full details, human-readable sizes, and hidden files chudu
        ls -lha

        # Time prakaaram (newest last), reverse chesi chupinchu (newest first)
        ls -ltr
        ```
      * *_DevOps Use:_* Directory contents chudadaniki, permissions check cheyadaniki.

  * **`cd`** (Change Directory)

      * **Purpose:** Vere directory ki velladaniki.
      * **Real-World Usage:**
        ```bash
        cd /var/log      # Go to the log directory
        cd ..            # Go one level up
        cd ~             # Go to your home directory
        cd -             # Go to the last directory you were in
        ```

  * **`mkdir`** (Make Directory)

      * **Purpose:** Kotha empty folder create cheyyataniki.
      * **Common "Power-ups":**
          * `-p`: **P**arent directories lekapothe, vaatini kooda create cheyi.
      * **Real-World Usage:**
        ```bash
        # Nested directories ni okate saari create cheyi
        mkdir -p my_project/logs/archive
        ```

  * **`touch`**

      * **Purpose:** Kotha empty file create cheyyataniki or existing file timestamp ni update cheyadaniki.
      * **Real-World Usage:**
        ```bash
        # Script kosam kotha file create cheyi
        touch deploy_script.sh
        ```

  * **`echo` with `>` & `>>`**

      * **Purpose:** File lo text ni create cheyadaniki.
      * **Power-ups:** `>` (Overwrite), `>>` (Append).
      * **Real-World Usage:**
        ```bash
        # Kotha file create chesi, content raayi (overwrite)
        echo "Server is healthy" > status.txt

        # Existing file ki kotha line add cheyi (append)
        echo "INFO: Deployment started." >> deployment.log
        ```

-----

### 2\. File & Directory Operations (The Daily Toolkit) 🛠️

  * **`cp`** (Copy)

      * **Purpose:** Files or folders ni copy cheyyataniki.
      * **Common "Power-ups":** `-r` (Recursive), `-v` (Verbose), `-p` (Preserve).
      * **Real-World Usage:**
        ```bash
        # Config file ni edit chese mundu, backup tesko
        sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak

        # Folder ni, daani content tho saha, verbose ga copy cheyi
        cp -rv my_app/ backup_app/
        ```

  * **`mv`** (Move)

      * **Purpose:** Files or folders ni move cheyadaniki or rename cheyadaniki.
      * **Real-World Usage:**
        ```bash
        # File ni rename cheyi
        mv old_name.txt new_name.txt

        # Process chesina log file ni archive folder loki move cheyi
        mv access.log archives/access_2025_08_11.log
        ```

  * **`rm`** (Remove)

      * **Purpose:** Files or folders ni **permanently** delete cheyyataniki.
      * **Common "Power-ups":** `-r` (Recursive), `-f` (Force), `-i` (Interactive).
      * **Real-World Usage:**
        ```bash
        # Safe ga delete cheyi, prathi saari adugutundi
        rm -i old_file.txt

        # Folder ni, lopalivi anni, force ga delete cheyi (JAAGRATHA!)
        rm -rf /tmp/old_project/
        ```

-----

### 3\. Viewing & Reading Files (The Inspector's Toolkit) 🕵️

  * **`cat` / `tac` / `less` / `more`**

      * **Purpose:** Files ni chudataniki. `less` anedi best for large files.
      * **Real-World Usage:**
        ```bash
        # Chinna config file ni chudu
        cat /etc/hostname

        # Pedda log file ni scroll chestu chudu (press 'q' to exit)
        less /var/log/messages
        ```

  * **`head` / `tail`**

      * **Purpose:** File lo first (`head`) or last (`tail`) lines chudataniki.
      * **Common "Power-ups":** `-n <number>`, `-f` (Follow).
      * **Real-World Usage:**
        ```bash
        # Log file lo last 100 lines chudu
        tail -n 100 /var/log/nginx/error.log

        # Deployment appudu, log file ni live ga monitor cheyi
        tail -f /var/log/my_app.log
        ```

-----

### 4\. Text Processing, Editing & Searching ✍️

  * **`vim` / `nano`**

      * **Purpose:** Text ni edit cheyadaniki. `vim` is powerful, `nano` is beginner-friendly.
      * **Real-World Usage:**
        ```bash
        # SSH config ni edit cheyi
        sudo vim /etc/ssh/sshd_config

        # Quick ga hosts file lo entry add cheyi
        sudo nano /etc/hosts
        ```

  * **`grep`**

      * **Purpose:** File lo or command output lo oka specific word (pattern) kosam search cheyyataniki.
      * **Common "Power-ups":** `-r` (Recursive), `-i` (Ignore case), `-v` (Invert match).
      * **Real-World Usage:**
        ```bash
        # Log file lo "error" ane padam unna anni lines chupinchu (case-insensitive)
        grep -i "error" /var/log/syslog

        # Nginx process run avutundo ledo chudu
        ps -ef | grep 'nginx'
        ```

  * **`sed`**

      * **Purpose:** Files lo text ni search and replace cheyadaniki.
      * **Common "Power-ups":** `-i` (**I**n-place - original file lone changes cheseyi).
      * **Real-World Usage:**
        ```bash
        # Config file lo, old IP ni kotha IP tho replace cheyi
        sed -i 's/192.168.1.10/10.0.0.50/g' /etc/my_app/config.conf
        ```

-----

### 5\. Archiving & Transfer (Packaging & Shipping) 📦

  * **`tar`**

      * **Purpose:** Files/folders ni oka single file (`.tar` archive) la bundle cheyyataniki.
      * **Common "Power-ups":** `c` (Create), `x` (Extract), `v` (Verbose), `f` (File), `z` (Gzip).
      * **Real-World Usage:**
        ```bash
        # 'my_project' folder ni compress chesi, oka backup file create cheyi
        tar -czvf my_project_backup.tar.gz my_project/

        # Backup file ni extract cheyi
        tar -xzvf my_project_backup.tar.gz
        ```

  * **`ssh`**

      * **Purpose:** Vere server ki secure ga login avvadaniki.
      * **Common "Power-ups":** `-i <key_file>`, `-p <port_number>`.
      * **Real-World Usage:**
        ```bash
        # Key file tho AWS EC2 instance ki connect avvu
        ssh -i my-aws-key.pem ec2-user@<public-ip-address>
        ```

  * **`rsync`**

      * **Purpose:** Files/directories ni efficient ga sync cheyyataniki.
      * **Real-World Usage:**
        ```bash
        # Local folder ni remote server tho sync cheyi (deployment kosam)
        rsync -avz my_website/ ec2-user@<ip>:/var/www/html/
        ```

-----

Ee version chudu mawa. Prathi command ki ippudu 'ela vaadali' ane section lo detailed examples unnayi. This should be much more useful for your practice. Let me know what you think of this "Director's Cut" version\!