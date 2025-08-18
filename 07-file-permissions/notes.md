# File Permissions Management in Linux

## Introduction to File Permissions

Linux file permissions determine who can read, write, or execute files and directories. Each file and directory has three levels of permission:

- **Owner (User)**: The creator or assigned owner of the file.
- **Group**: Users belonging to the assigned group.
- **Others**: All other users on the system.

Permissions are represented as:
- **Read (`r` or `4`)** – View file contents (or list directory contents).
- **Write (`w` or `2`)** – Modify file contents (or add/delete files in a directory).
- **Execute (`x` or `1`)** – Run scripts or programs (or traverse/enter a directory).

To check file permissions, use:
```bash
ls -l filename
```
Output example:
```bash
-rwxr--r-- 1 user group 1234 Mar 28 10:00 myfile.sh
```
- The first character indicates the file type: `-` (regular file), `d` (directory), `l` (symlink), etc.
- The next nine characters are grouped in threes: user, group, others.

You can also use `stat filename` for detailed permission and ownership information.

---

## Understanding Permission Notation

| Symbolic | Octal | Meaning (per class)      |
|----------|-------|--------------------------|
| ---      | 0     | No permissions           |
| --x      | 1     | Execute                  |
| -w-      | 2     | Write                    |
| -wx      | 3     | Write, Execute           |
| r--      | 4     | Read                     |
| r-x      | 5     | Read, Execute            |
| rw-      | 6     | Read, Write              |
| rwx      | 7     | Read, Write, Execute     |

---

## File vs. Directory Permissions

- **Files:**
  - `r`: Read file contents.
  - `w`: Modify file contents.
  - `x`: Execute the file as a program or script.

- **Directories:**
  - `r`: List directory contents (filenames).
  - `w`: Create, delete, or rename files within the directory.
  - `x`: Enter the directory (`cd`), access file metadata, or open files if the name is known.

**Important Directory Behaviors:**
- To access a file, you must have execute permission on all parent directories, even if you have read permission on the file itself.
- If you have execute but not read permission on a directory, you can access files if you know their names, but cannot list the directory contents.
- If you have read but not execute permission, you can list the directory contents but cannot access any files or subdirectories within it .

---

## Changing Permissions with `chmod`

### Using Symbolic Mode

Modify permissions using symbols:
- Add (`+`), remove (`-`), or set (`=`) permissions.

Examples:
```bash
chmod u+x filename           # Add execute for user
chmod g-w filename           # Remove write for group
chmod o=r filename           # Set read-only for others
chmod u=rwx,g=rx,o= filename # Set full access for user, read/execute for group, and no access for others
chmod a+x filename           # Add execute for all (user, group, others)
```

### Using Numeric (Octal) Mode

Each permission has a value:
- Read (`4`), Write (`2`), Execute (`1`).

Examples:
```bash
chmod 755 filename  # User (rwx), Group (r-x), Others (r-x)
chmod 644 filename  # User (rw-), Group (r--), Others (r--)
chmod 700 filename  # User (rwx), No access for group/others
```

### Recursive Permission Changes

To apply permissions recursively to all files and subdirectories:
```bash
chmod -R 755 directory/
```
**Caution:** Use recursive changes carefully to avoid unintended permission exposure.

---

## Changing Ownership with `chown`

Modify file owner and group:
```bash
chown newuser filename            # Change owner
chown newuser:newgroup filename   # Change owner and group
chown :newgroup filename          # Change only group
```

Recursively change ownership:
```bash
chown -R newuser:newgroup directory/
```
**Note:** Only the superuser (root) can change file ownership arbitrarily.

---

## Changing Group Ownership with `chgrp`

```bash
chgrp newgroup filename           # Change group
chgrp -R newgroup directory/      # Change group recursively
```
**Note:** Regular users can only change group to one they belong to.

---

## Special Permissions

### SetUID (`s` on user execute bit)

- When set on an executable file, users run the file with the file owner's permissions.
- Commonly used for programs that need elevated privileges (e.g., `/usr/bin/passwd`).

Set and remove:
```bash
chmod u+s filename   # Set SetUID
chmod u-s filename   # Remove SetUID
```
- In `ls -l`, appears as `s` in the owner's execute position (e.g., `-rwsr-xr-x`).

### SetGID (`s` on group execute bit)

- **Files:** Users run the file with the file's group permissions.
- **Directories:** New files and subdirectories inherit the group ownership of the directory, not the user's primary group. Useful for collaborative directories.

Set and remove:
```bash
chmod g+s filename      # Set on file
chmod g+s directory/    # Set on directory
chmod g-s filename      # Remove SetGID
```
- In `ls -l`, appears as `s` in the group's execute position (e.g., `drwxrwsr-x`).

### Sticky Bit (`t` on others execute bit)

- **Directories:** Only the file's owner, the directory's owner, or root can delete or rename files within the directory, even if others have write permission. Essential for shared directories like `/tmp`.

Set and remove:
```bash
chmod +t directory/
chmod -t directory/
```
- In `ls -l`, appears as `t` in the others' execute position (e.g., `drwxrwxrwt`).

### Numeric Representation of Special Permissions

Special permissions are represented by a fourth digit at the start:
- SetUID = 4
- SetGID = 2
- Sticky = 1

Combine as needed:
```bash
chmod 4755 file      # SetUID + rwxr-xr-x
chmod 2770 dir       # SetGID + rwxrwx---
chmod 1777 /tmp      # Sticky + rwxrwxrwt
```

---

## Default Permissions: `umask`

`umask` defines default permissions for new files and directories by masking out permissions from the system defaults.

- **Default permissions for new files:** 666 (rw-rw-rw-)
- **Default permissions for new directories:** 777 (rwxrwxrwx)
- **umask** subtracts permissions from these defaults.

### How umask Works

- For files: `Final permissions = 666 - umask`
- For directories: `Final permissions = 777 - umask`
- Files never get execute permission by default, even if umask would allow it.

### Common umask Values and Results

| Umask | File Permissions | Directory Permissions | Use Case                |
|-------|------------------|----------------------|-------------------------|
| 000   | 666 (rw-rw-rw-)  | 777 (rwxrwxrwx)      | No restrictions         |
| 002   | 664 (rw-rw-r--)  | 775 (rwxrwxr-x)      | Group collaboration     |
| 022   | 644 (rw-r--r--)  | 755 (rwxr-xr-x)      | Default, general use    |
| 027   | 640 (rw-r-----)  | 750 (rwxr-x---)      | Group only, no others   |
| 077   | 600 (rw-------)  | 700 (rwx------)      | Private, max security   |

### Checking and Setting umask

Check current umask:
```bash
umask
```
Set a new umask for the session:
```bash
umask 027
```
Set umask permanently by adding to your shell profile (e.g., `~/.bashrc`):
```bash
echo "umask 027" >> ~/.bashrc
```

---

## Directory-Specific Permission Behaviors

- **Read (`r`)**: List directory contents.
- **Write (`w`)**: Create, delete, or rename files in the directory.
- **Execute (`x`)**: Enter/traverse the directory; required to access files within.
- **Sticky Bit (`t`)**: Only the file's owner, directory owner, or root can delete/rename files.
- **SetGID (`g`)**: New files/directories inherit the group of the parent directory.

**Key Points:**
- Deleting or renaming a file requires write and execute permissions on the parent directory, not the file itself.
- Permission denied errors often result from missing execute permission on a parent directory.
- Avoid setting directories to `777` unless absolutely necessary, as it poses a security risk.

---

## Access Control Lists (ACLs) and Extended Attributes

- **ACLs** provide more granular permissions than the standard user/group/other model.
- Use `getfacl` and `setfacl` to view and modify ACLs.
- Useful for granting specific users access without changing group membership.

---

## Best Practices and Security Considerations

- **Principle of Least Privilege:** Grant only the permissions necessary for users and processes .
- **Use Groups for Access Control:** Assign permissions to groups for easier management .
- **Avoid World-Writable Permissions:** Do not use `chmod 777` or `o+w` unless absolutely necessary .
- **Regularly Review and Audit Permissions:** Use tools like `find` and `ls -l` to check for overly permissive files .
- **Secure Shared Directories with the Sticky Bit:** Prevent users from deleting others' files in shared directories .
- **Use Special Permissions Carefully:** Only set SetUID/SetGID on trusted executables and audit them regularly .
- **Set umask Appropriately:** Choose a restrictive umask for sensitive environments .
- **Educate Users:** Ensure users understand permission management and its importance .
- **Automate Permission Management:** Use scripts or configuration management tools for consistency .
- **Monitor and Log Permission Changes:** Use audit frameworks to track changes .

---

## Summary Table: Directory Permission Effects

| Permission | Directory Effect                                      |
|------------|------------------------------------------------------|
| r          | List directory contents                              |
| w          | Create/delete/rename files in directory              |
| x          | Enter directory, access files if name is known       |
| t (sticky) | Only owner/root can delete/rename files              |
| g (setgid) | New files inherit group ownership