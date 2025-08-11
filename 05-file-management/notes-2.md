### **File and Directory Management 📂**

  * **`ls`** (List)

      * **Purpose:** Current location lo unna files and folders list chupistundi.
      * **Common "Power-ups":**
          * `-l`: **L**ong listing format (full details).
          * `-a`: **A**ll files (hidden files `.`, `..` tho saha).
          * `-h`: **H**uman-readable sizes (`1K`, `2M`).
      * **Real-World Usage:**
        ```bash
        # Full details, human-readable sizes, and hidden files chudu
        ls -lha
        ```

  * **`cd`** (Change Directory)

      * **Purpose:** Vere directory ki velladaniki.
      * **Real-World Usage:**
        ```bash
        cd /var/log      # Go to the log directory
        cd ..            # Go one level up (parent directory)
        cd ~             # Go to your home directory
        cd -             # Go to the last directory you were in
        ```

  * **`pwd`** (Present Working Directory)

      * **Purpose:** Nuvvu current ga ఏ directory lo unnavo cheptundi.
      * **Real-World Usage:**
        ```bash
        pwd
        # Output: /home/ec2-user
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

  * **`rmdir`** (Remove Directory)

      * **Purpose:** **Only empty directories** ni remove chestundi.
      * **Real-World Usage:**
        ```bash
        # 'backups' ane folder empty ga unte, delete cheyi
        rmdir backups
        ```

  * **`rm`** (Remove)

      * **Purpose:** Files or folders ni **permanently** delete cheyyataniki.
      * **Common "Power-ups":**
          * `-r`: **R**ecursive (folder and lopalivi anni delete cheyi).
          * `-f`: **F**orce (confirmation adagakunda, force ga delete cheyi).
          * `-i`: **I**nteractive (prathi file ki mundu adugu).
      * **Real-World Usage:**
        ```bash
        # Safe ga delete cheyi, prathi saari adugutundi
        rm -i old_file.txt

        # Folder ni, lopalivi anni, force ga delete cheyi (JAAGRATHA!)
        rm -rf /tmp/old_project/
        ```

  * **`cp`** (Copy)

      * **Purpose:** Files or folders ni copy cheyyataniki.
      * **Common "Power-ups":**
          * `-r`: **R**ecursive (folder and daani lopalivi anni copy cheyi).
          * `-v`: **V**erbose (em copy avutundo screen meeda chupinchu).
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
        mv old_name.log new_name.log

        # Process chesina file ni 'archive' folder loki move cheyi
        mv data.csv processed/
        ```

-----

### **File Viewing and Editing ✍️**

  * **`cat`** (Concatenate)

      * **Purpose:** Chinna file content ni display cheyyataniki.
      * **Real-World Usage:**
        ```bash
        # System hostname ento chudu
        cat /etc/hostname
        ```

  * **`tac`** (cat reversed)

      * **Purpose:** File content ni reverse order lo (last line first) chupistundi.
      * **Real-World Usage:**
        ```bash
        # Log file lo last entry first kanapadela chudu
        tac application.log
        ```

  * **`less`**

      * **Purpose:** Pedda files ni easy ga, page by page, scroll chestu chudataniki (idi best tool).
      * **Real-World Usage:**
        ```bash
        # Pedda log file ni scroll chestu chudu (press 'q' to exit)
        less /var/log/messages
        ```

  * **`more`**

      * **Purpose:** `less` lantiది, kani forward matrame scroll avvachu (older version).
      * **Real-World Usage:**
        ```bash
        # Simple ga file ni page by page chudu
        more long_file.txt
        ```

  * **`head`**

      * **Purpose:** File lo unna first lines ni chupistundi.
      * **Common "Power-ups":**
          * `-n <number>`: Enni lines chudalo cheppu.
      * **Real-World Usage:**
        ```bash
        # CSV file lo header and first 5 data rows chudu
        head -n 6 data.csv
        ```

  * **`tail`**

      * **Purpose:** File lo unna last lines ni chupistundi.
      * **Common "Power-ups":**
          * `-n <number>`: Enni lines chudalo cheppu.
          * `-f`: **F**ollow (real-time lo file ki add ayye kotha lines ni chupistu undu).
      * **Real-World Usage:**
        ```bash
        # Application deploy avutunnapudu, log file ni live ga monitor cheyi
        tail -f /var/log/my_app.log
        ```

  * **`nano`**

      * **Purpose:** Simple, beginner-friendly text editor open cheyyataniki.
      * **Real-World Usage:**
        ```bash
        # Quick ga hosts file lo entry add cheyi (Ctrl+O to Save, Ctrl+X to Exit)
        sudo nano /etc/hosts
        ```

  * **`vi`** (or `vim`)

      * **Purpose:** Powerful, professional text editor open cheyyataniki.
      * **Real-World Usage:**
        ```bash
        # Script or config file ni edit cheyi (i for Insert, Esc for Normal, :wq to save & quit)
        vi my_script.sh
        ```

  * **`echo` with `>` & `>>`**

      * **Purpose:** File lo text ni create cheyadaniki or add cheyadaniki.
      * **Power-ups:**
          * `>` (Overwrite): File lo unna paatha content ni **motham teesi**, kotha content raayi.
          * `>>` (Append): File lo unna paatha content ki **last lo**, kotha content ni add cheyi.
      * **Real-World Usage:**
        ```bash
        # Script lo oka temporary config file create cheyi
        echo "STATUS=SUCCESS" > /tmp/status.txt

        # Log file ki oka custom message add cheyi
        echo "[INFO] Manual check done at $(date)" >> /var/log/manual_checks.log
        ```