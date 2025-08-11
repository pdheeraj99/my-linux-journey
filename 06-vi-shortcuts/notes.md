## VI Editor Shortcuts: The Pro Gamer's Guide ✍️⚡

**Analogy:** `vi` anedi oka **Video Game** 🎮 laantidi. Daaniki three modes untayi.

### **VI Editor Modes**

* **Normal Mode (The Game World 🗺️):**
    * Idi default mode. Ikkada nuvvu character ni move chesinattu, cursor ni move chestaru (`h,j,k,l`). Special actions (`dd`, `yy`) chestaru. Ikkada text type cheyaleru.

* **Insert Mode (The Chat Box ⌨️):**
    * `i` press chesi ee mode loki vastav. Ippudu nuvvu em type cheste, adi screen meeda kanipistundi.
    * `Esc` press chesi, malli Game World (Normal Mode) loki vellipothav.

* **Command Mode (The Main Menu 💾):**
    * Normal mode lo undi `:` (colon) press cheste ee mode loki vastav. Ikkada "Save Game" (`:w`), "Quit Game" (`:q`) lanti commands istav.

---

### Basic Navigation (Moving Your Character) 🗺️
*(Ee commands anni Normal Mode lo pani chestayi)*

* `h` – **Left** ki vellu ⬅️
* `l` – **Right** ki vellu ➡️
* `j` – **Down** (kinda) ki vellu ⬇️
* `k` – **Up** (paina) ki vellu ⬆️
* `0` – Line **starting** ki vellu
* `^` – Line lo unna **first character** daggarki vellu
* `$` – Line **ending** ki vellu
* `w` – Next **word** ki jump cheyi
* `b` – Mundu unna **word** ki jump cheyi
* `gg` – File **starting** ki vellipo (double tap `g`)
* `G` – File **ending** ki vellipo
* `:n` – `n` ane **line number** ki vellu (e.g., `:100` ante 100th line ki)

---

### Insert Mode Shortcuts (Entering the Chat Box) ⌨️

* `i` – Cursor ki **mundu** nunchi type cheyi (**i**nsert)
* `I` – Current line **starting** nunchi type cheyi
* `a` – Cursor **tarvata** nunchi type cheyi (**a**ppend)
* `A` – Current line **ending** nunchi type cheyi
* `o` – Cursor unna line **kinda** kotha line open cheyi
* `O` – Cursor unna line **paina** kotha line open cheyi
* `Esc` – Chat box close chesi, **Normal Mode** ki vellipo

---

### Editing Text (Attacks & Power-ups) ✂️📋🩹
*(Ee commands anni Normal Mode lo pani chestayi)*

* `x` – Cursor daggara unna **character** ni delete cheyi
* `dw` – Oka **word** ni delete cheyi (**d**elete **w**ord)
* `dd` – Current **line** antha delete cheyi (double tap `d`)
* `D` or `d$` – Cursor nunchi line **ending** varaku delete cheyi
* `u` – Last action ni **undo** cheyi
* `Ctrl + r` – **Redo** cheyi
* `yy` – Current **line** antha copy cheyi (**y**ank)
* `yw` – Oka **word** ni copy cheyi (**y**ank **w**ord)
* `p` – Cursor **tarvata** paste cheyi
* `P` – Cursor **mundu** paste cheyi

---

### Search and Replace (Finding Enemies & Magic Spells) 🔍✨
*(Ee commands Command Mode lo pani chestayi)*

* `/pattern` – Munduki `pattern` kosam **search** cheyi
* `?pattern` – Venakki `pattern` kosam **search** cheyi
* `n` – Last search ni **munduki** repeat cheyi
* `N` – Last search ni **venakki** repeat cheyi
* `:%s/old/new/g` – **Magic Spell:** Motham file lo, `old` ane prathi padam బదులుగా `new` ane padam pettu.
* `:s/old/new/g` – **Mini-Spell:** Current line lo matrame replace cheyi.

---

### Working with Multiple Files (Managing Game Levels) 📁
*(Ee commands Command Mode lo pani chestayi)*

* `:e filename` – Kotha file ni **open** cheyi (**e**dit)
* `:w` – File ni **save** cheyi (**w**rite)
* `:wq` – **Save chesi quit** avvu
* `:q!` – **Changes save cheyakunda**, balavanthamga quit avvu
* `:split filename` – Screen ni **horizontally** split cheyi
* `:vsplit filename` – Screen ni **vertically** split cheyi
* `Ctrl + w + w` – Split screens madhya switch avvu