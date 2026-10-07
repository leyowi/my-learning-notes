# 🐧 Linux Foundations Command Cheat Sheet

> A quick reference for essential Linux commands, covering syntax, common options, and practical examples.

**Topic:** Linux &nbsp;|&nbsp; **Part of:** My Learning Notes

---

## Table of Contents

| # | Section | Commands |
|:-:|:--|:--|
| 1 | [Basic Shell and Information Commands](#1-basic-shell-and-information-commands) | [`date`](#date), [`cal`](#cal), [`clear`](#clear), [`echo`](#echo), [`history`](#history), [`touch`](#touch), [`cat`](#cat) |
| 2 | [User and Group Management](#2-user-and-group-management) | [`useradd`](#useradd), [`usermod`](#usermod), [`userdel`](#userdel), [`passwd`](#passwd), [`groupadd`](#groupadd), [`groupmod`](#groupmod), [`groupdel`](#groupdel), [`gpasswd`](#gpasswd) |
| 3 | [Privilege and Administrative Commands](#3-privilege-and-administrative-commands) | [`su`](#su), [`sudo`](#sudo), [`visudo`](#visudo) |
| 4 | [Text Editors](#4-text-editors) | [`vim`](#vim), [`vimtutor`](#vimtutor), [`nano`](#nano), [`apt-get`](#apt-get), [`gedit`](#gedit) |
| 5 | [File and Directory Navigation](#5-file-and-directory-navigation) | [`pwd`](#pwd), [`cd`](#cd), [`ls`](#ls) |
| 6 | [Viewing and Managing Files](#6-viewing-and-managing-files) | [`more`](#more), [`less`](#less), [`head`](#head), [`tail`](#tail), [`cp`](#cp), [`rm`](#rm), [`mkdir`](#mkdir), [`mv`](#mv), [`rmdir`](#rmdir) |
| 7 | [File Searching and Comparison](#7-file-searching-and-comparison) | [`hash`](#hash), [`cksum`](#cksum), [`find`](#find), [`grep`](#grep), [`diff`](#diff) |
| 8 | [Links and Compression](#8-links-and-compression) | [`ln`](#ln), [`tar`](#tar), [`gzip`](#gzip), [`zip`](#zip), [`unzip`](#unzip) |
| 9 | [File Ownership and Permissions](#9-file-ownership-and-permissions) | [`chown`](#chown), [`chmod`](#chmod) |
| 10 | [Bash Environment and Text Processing](#10-bash-environment-and-text-processing) | [`env`](#env), [`alias`](#alias), [`unalias`](#unalias), [`cut`](#cut), [`sed`](#sed), [`sort`](#sort), [`awk`](#awk) |
| 11 | [Process and Job Management](#11-process-and-job-management) | [`ps`](#ps), [`pstree`](#pstree), [`top`](#top), [`kill`](#kill), [`nice`](#nice), [`renice`](#renice), [`jobs`](#jobs), [`bg`](#bg), [`fg`](#fg) |
| 12 | [Task Scheduling](#12-task-scheduling) | [`at`](#at), [`cron`](#cron), [`crontab`](#crontab) |
| 13 | [Service Management](#13-service-management) | [`systemctl`](#systemctl), [`service`](#service) |
| 14 | [System Monitoring](#14-system-monitoring) | [`lscpu`](#lscpu), [`lshw`](#lshw), [`du`](#du), [`df`](#df), [`fdisk`](#fdisk), [`vmstat`](#vmstat), [`free`](#free), [`uptime`](#uptime) |

---

## 1. Basic Shell and Information Commands

### `date`

**Definition:** Displays the current date and time in a specified format. It can also set the system date.

**Syntax:**

```bash
date
```

**Example:**

```bash
date
```

Displays the current system date and time.

### `cal`

**Definition:** Displays a calendar. Without arguments, it displays the current month.

**Syntax:**

```bash
cal [MONTH] [YEAR]
```

**Examples:**

```bash
cal
```

Displays the current month.

```bash
cal 8 2026
```

Displays August 2026.

### `clear`

**Definition:** Clears the terminal screen and displays a new prompt.

**Syntax:**

```bash
clear
```

**Example:**

```bash
clear
```

### `echo`

**Definition:** Displays specified text or variable values on standard output.

**Syntax:**

```bash
echo [TEXT]
echo $VARIABLE
```

**Examples:**

```bash
echo "Hello Linux"
```

Displays `Hello Linux`.

```bash
echo $HOME
```

Displays the current user’s home directory.

### `history`

**Definition:** Displays the current user’s command history.

**Syntax:**

```bash
history
```

**Examples:**

```bash
history
```

Displays previously executed commands.

```bash
!143
```

Runs the command associated with history event number `143`.

### `touch`

**Definition:** Creates an empty file or updates the access and modification timestamps of an existing file.

**Syntax:**

```bash
touch FILE...
```

**Examples:**

```bash
touch notes.txt
```

Creates an empty `notes.txt` file if it does not exist.

```bash
touch file1.txt file2.txt file3.txt
```

Creates multiple files.

### `cat`

**Definition:** Reads file contents and displays them in the terminal. It can also be used with input redirection and pipes.

**Syntax:**

```bash
cat FILE
```

**Examples:**

```bash
cat /etc/hosts
```

Displays the contents of `/etc/hosts`.

```bash
cat myfirstscript
```

Displays the contents of `myfirstscript`.

<p align="right"><a href="#table-of-contents">⬆ Back to top</a></p>

---

## 2. User and Group Management

### `useradd`

**Definition:** Creates a new user account.

**Syntax:**

```bash
useradd [OPTIONS] USERNAME
```

**Options:**

| Option | Description                       | Example                          |
|:-------|:----------------------------------|:---------------------------------|
| `-c`   | Adds a comment                    | `useradd -c "New Employee" jdoe` |
| `-e`   | Sets account expiration           | `useradd -e 2026-12-31 jdoe`     |
| `-d`   | Specifies the home directory path | `useradd -d /users/jdoe jdoe`    |

**Examples:**

```bash
sudo useradd user20
```

Creates the user `user20` using delegated administrative privileges.

```bash
useradd -c "New Employee" jdoe
```

Creates `jdoe` with a comment.

### `usermod`

**Definition:** Modifies an existing user account.

**Syntax:**

```bash
usermod [OPTIONS] USERNAME
```

**Options:**

| Option | Description                              | Example                           |
|:-------|:-----------------------------------------|:----------------------------------|
| `-c`   | Changes the comment                      | `usermod -c "Mary Major" mmajor`  |
| `-e`   | Changes account expiration               | `usermod -e 2026-12-31 mmajor`    |
| `-aG`  | Appends the user to supplementary groups | `usermod -aG hr,marketing mmajor` |

**Example:**

```bash
usermod -aG hr,marketing mmajor
```

Adds `mmajor` to the `hr` and `marketing` groups without removing existing supplementary groups.

### `userdel`

**Definition:** Deletes a user account.

**Syntax:**

```bash
userdel [OPTIONS] USERNAME
```

**Options:**

| Option | Description                            |
|:-------|:---------------------------------------|
| `-r`   | Also deletes the user’s home directory |

**Example:**

```bash
sudo userdel -r jdoe
```

Deletes `jdoe` and the user’s home directory.

### `passwd`

**Definition:** Sets or changes user passwords.

**Syntax:**

```bash
passwd [USERNAME]
```

**Examples:**

```bash
passwd
```

Changes the password of the current user.

```bash
sudo passwd jdoe
```

Changes the password for `jdoe`.

### `groupadd`

**Definition:** Creates a new group.

**Syntax:**

```bash
groupadd GROUP
```

**Example:**

```bash
sudo groupadd developers
```

Creates the `developers` group.

### `groupmod`

**Definition:** Modifies an existing group.

**Syntax:**

```bash
groupmod -n NEW_GROUP OLD_GROUP
```

**Example:**

```bash
sudo groupmod -n engineers developers
```

Renames `developers` to `engineers`.

### `groupdel`

**Definition:** Deletes an existing group.

**Syntax:**

```bash
groupdel GROUP
```

**Example:**

```bash
sudo groupdel developers
```

Deletes the `developers` group.

### `gpasswd`

**Definition:** Administers group membership through the `/etc/group` file.

**Syntax:**

```bash
gpasswd [OPTION] GROUP
```

**Options:**

| Option           | Description                           | Example                               |
|:-----------------|:--------------------------------------|:--------------------------------------|
| `-a`, `--add`    | Adds a user to a group                | `gpasswd -a jdoe marketing`           |
| `-d`, `--delete` | Removes a user from a group           | `gpasswd -d jdoe marketing`           |
| `-M`             | Sets the list of group members        | `gpasswd -M user1,user2 developers`   |
| `-A`             | Sets the list of group administrators | `gpasswd -A admin1,admin2 developers` |

**Examples:**

```bash
sudo gpasswd -a jdoe ec2-user
```

```bash
sudo gpasswd -M smartinez,rroe ec2-user
```

<p align="right"><a href="#table-of-contents">⬆ Back to top</a></p>

---

## 3. Privilege and Administrative Commands

### `su`

**Definition:** Switches to another user account.

**Syntax:**

```bash
su USERNAME
su - USERNAME
```

**Examples:**

```bash
su root
```

Switches to root while keeping the current user’s environment.

```bash
su - root
```

Switches to root and loads the root user’s environment.

```bash
su student02
```

Switches to `student02`.

### `sudo`

**Definition:** Runs a command with delegated administrative permissions.

**Syntax:**

```bash
sudo COMMAND
```

**Options:**

| Option | Description                         |
|:-------|:------------------------------------|
| `-lU`  | Displays delegated sudo permissions |

**Examples:**

```bash
sudo useradd user20
```

Runs `useradd` with delegated administrative privileges.

```bash
sudo systemctl restart httpd
```

Restarts the `httpd` service with elevated permissions.

### `visudo`

**Definition:** Safely edits the `/etc/sudoers` configuration file.

**Syntax:**

```bash
visudo
```

**Example:**

```bash
sudo visudo
```

Opens the sudoers configuration for editing.

<p align="right"><a href="#table-of-contents">⬆ Back to top</a></p>

---

## 4. Text Editors

### `vim`

**Definition:** A command-line text editor.

**Syntax:**

```bash
vim FILE
```

**Example:**

```bash
vim config.txt
```

#### Vim commands and keystrokes

| Command / Key   | Effect                                       |
|:----------------|:---------------------------------------------|
| `i`             | Enter insert mode                            |
| `ESC`           | Return to command mode                       |
| `x`             | Delete character at cursor                   |
| `G`             | Move to bottom of file                       |
| `gg`            | Move to top of file                          |
| `42G`           | Move to line 42                              |
| `/keyword`      | Search for a keyword                         |
| `y`             | Yank text                                    |
| `p`             | Put/paste text                               |
| `o` / `O` | Open a new line below / above the cursor |
| `a` / `A` | Insert text after the cursor / at the end of the line |
| `h j k l`       | Move left, down, up, right                   |
| `ZZ`            | Save and exit                                |
| `:w`            | Save                                         |
| `:q`            | Quit                                         |
| `:wq`           | Save and quit                                |
| `:wq!`          | Save and force quit                          |
| `:q!`           | Quit without saving                          |
| `:help`         | Open general help                            |
| `:help keyword` | Open help for a keyword                      |
| `K`             | Open the man page for the word at the cursor |

### `vimtutor`

**Definition:** Opens an interactive tutorial for common Vim tasks.

**Syntax:**

```bash
vimtutor
```

### `nano`

**Definition:** A lightweight command-line text editor.

**Syntax:**

```bash
nano FILE
```

**Example:**

```bash
nano notes.txt
```

#### Nano shortcuts

| Shortcut | Effect                      |
|:---------|:----------------------------|
| `Ctrl+X` | Quit                        |
| `Ctrl+O` | Save                        |
| `Ctrl+K` | Cut text                    |
| `Ctrl+U` | Paste text                  |
| `Ctrl+G` | Help                        |
| `Ctrl+W` | Search                      |
| `Ctrl+Y` | Previous screen             |
| `Ctrl+V` | Next screen                 |
| `Ctrl+C` | Display cursor position     |
| `Ctrl+_` | Go to line and column       |
| `Ctrl+\` | Replace                     |
| `Alt+W`  | Repeat last search          |
| `Alt+6`  | Copy current line           |
| `Ctrl+E` | Move to end of current line |
| `Alt+]`  | Move to matching bracket    |
| `Alt+,`  | Previous file buffer        |
| `Alt+.`  | Next file buffer            |

### `apt-get`

**Definition:** Installs packages on Debian or Ubuntu systems.

**Syntax:**

```bash
sudo apt-get install PACKAGE
```

**Example:**

```bash
sudo apt-get install nano
```

Installs Nano.

### `gedit`

**Definition:** A GUI-based text editor available when a graphical environment is installed.

**Syntax:**

```bash
gedit FILE
```

**Example:**

```bash
gedit notes.txt
```

<p align="right"><a href="#table-of-contents">⬆ Back to top</a></p>

---

## 5. File and Directory Navigation

### `pwd`

**Definition:** Displays the absolute path of the current working directory.

**Syntax:**

```bash
pwd
```

### `cd`

**Definition:** Changes the current directory.

**Syntax:**

```bash
cd PATH
```

**Examples:**

```bash
cd /home/userA/Documents/projects
```

Uses an absolute path.

```bash
cd Documents/projects
```

Uses a relative path.

```bash
cd ../
```

Moves up one directory.

### `ls`

**Definition:** Lists the contents of a directory.

**Syntax:**

```bash
ls [OPTIONS] [DIRECTORY...]
```

**Options:**

| Option                   | Description                              | Example  |
|:-------------------------|:-----------------------------------------|:---------|
| `-l`                     | Long format with details and permissions | `ls -l`  |
| `-h`                     | Human-readable file sizes                | `ls -lh` |
| `-a`                     | Shows hidden files                       | `ls -a`  |
| `-R`                     | Lists subdirectories recursively         | `ls -R`  |
| `-X`, `--sort=extension` | Sorts by file extension                  | `ls -X`  |
| `-S`, `--sort=size`      | Sorts by file size                       | `ls -S`  |
| `-t`, `--sort=time`      | Sorts by modification time               | `ls -t`  |
| `-v`, `--sort=version`   | Sorts by version number                  | `ls -v`  |
| `-r`                     | Reverses the sorting order               | `ls -lr` |

**Examples:**

```bash
ls -al
```

Displays all files, including hidden files, in long format.

```bash
ls -lh
```

Displays detailed information with human-readable file sizes.

```bash
ls -S
```

Sorts files by size.

<p align="right"><a href="#table-of-contents">⬆ Back to top</a></p>

---

## 6. Viewing and Managing Files

### `more`

**Definition:** Displays file contents one screen at a time and scrolls downward.

**Syntax:**

```bash
more [OPTIONS] [+LINE_NUMBER] [+/PATTERN] FILE
```

**Options:**

| Option | Description                         |
|:-------|:------------------------------------|
| `-d`   | Displays navigation information     |
| `-f`   | Prevents line wrapping              |
| `-p`   | Clears the screen before displaying |
| `-s`   | Compresses multiple blank lines     |

**Example:**

```bash
cat file.txt | more
```

### `less`

**Definition:** Displays file contents and allows scrolling up and down.

**Syntax:**

```bash
less [OPTIONS] FILE
```

**Options:**

| Option | Description                           |
|:-------|:--------------------------------------|
| `-N`   | Shows line numbers                    |
| `-X`   | Keeps content displayed after exiting |
| `+F`   | Watches for file changes              |

**Example:**

```bash
less -N /var/log/messages
```

Press `Q` to quit.

### `head`

**Definition:** Displays the first 10 lines of a file by default.

**Syntax:**

```bash
head [OPTIONS] FILE...
```

| Option      | Description                                  |
|:------------|:---------------------------------------------|
| `-n NUMBER` | Displays the first specified number of lines |
| `-c NUMBER` | Displays the first specified number of bytes |

**Example:**

```bash
head -n 20 logfile.txt
```

### `tail`

**Definition:** Displays the last 10 lines of a file by default.

**Syntax:**

```bash
tail [OPTIONS] FILE...
```

| Option      | Description                                 |
|:------------|:--------------------------------------------|
| `-n NUMBER` | Displays the last specified number of lines |
| `-c NUMBER` | Displays the last specified number of bytes |
| `-f`        | Monitors the file for changes               |

**Example:**

```bash
tail -f /var/log/secure
```

Continuously monitors new entries.

### `cp`

**Definition:** Copies files and directories.

**Syntax:**

```bash
cp [OPTIONS] SOURCE... DESTINATION
```

**Options:**

| Option | Description                     |
|:-------|:--------------------------------|
| `-a`   | Archive files                   |
| `-f`   | Force overwrite                 |
| `-i`   | Ask before overwriting          |
| `-l`   | Create links instead of copies  |
| `-L`   | Follow symbolic links           |
| `-n`   | Do not overwrite existing files |
| `-R`   | Copy recursively                |
| `-u`   | Copy only when source is newer  |
| `-v`   | Verbose output                  |

**Examples:**

```bash
cp report.txt backup/
```

```bash
cp -R project/ backup/
```

### `rm`

**Definition:** Deletes files and directories.

**Syntax:**

```bash
rm [OPTIONS] FILE...
```

**Options:**

| Option | Description                     |
|:-------|:--------------------------------|
| `-d`   | Removes an empty directory      |
| `-r`   | Removes directories recursively |
| `-f`   | Never prompts                   |
| `-i`   | Prompts for confirmation        |
| `-v`   | Displays deleted file names     |

**Examples:**

```bash
rm notes.txt
```

```bash
rm -r old_project/
```

```bash
rm *.png
```

Removes files ending in `.png`.

### `mkdir`

**Definition:** Creates directories.

**Syntax:**

```bash
mkdir [OPTIONS] DIRECTORY...
```

**Options:**

| Option    | Description                          |
|:----------|:-------------------------------------|
| `-m MASK` | Sets directory permissions           |
| `-p`      | Creates parent directories as needed |

**Examples:**

```bash
mkdir dir1 dir2 dir3
```

```bash
mkdir -m 700 private
```

```bash
mkdir -p /home/user/dir1/dir2
```

### `mv`

**Definition:** Moves or renames files and directories.

**Syntax:**

```bash
mv [OPTIONS] SOURCE DESTINATION
```

**Options:**

| Option | Description                       |
|:-------|:----------------------------------|
| `-i`   | Prompts before overwrite          |
| `-f`   | Avoids prompting                  |
| `-n`   | Does not overwrite existing files |
| `-v`   | Verbose output                    |

**Examples:**

```bash
mv file1 dir1/
```

```bash
mv file1 file2
```

Renames `file1` to `file2`.

```bash
mv *.png images/
```

### `rmdir`

**Definition:** Deletes empty directories.

**Syntax:**

```bash
rmdir DIRECTORY
```

**Example:**

```bash
rmdir empty_folder
```

<p align="right"><a href="#table-of-contents">⬆ Back to top</a></p>

---

## 7. File Searching and Comparison

### `hash`

**Definition:** Displays or modifies remembered command locations maintained in the shell hash table.

**Syntax:**

```bash
hash [-lr] [-p PATH] [-dt] [COMMAND...]
```

**Options:**

| Option    | Description                              |
|:----------|:-----------------------------------------|
| `-d`      | Deletes a command location               |
| `-l`      | Displays reusable output                 |
| `-p PATH` | Sets a command’s full path               |
| `-r`      | Clears the hash table                    |
| `-t`      | Displays a command’s remembered location |

**Examples:**

```bash
hash
```

```bash
hash -r
```

### `cksum`

**Definition:** Generates a CRC checksum and byte count for a file or stream.

**Syntax:**

```bash
cksum FILE
```

**Example:**

```bash
cksum backup.tar
```

### `find`

**Definition:** Searches directories for files that match specified criteria.

**Syntax:**

```bash
find START_DIRECTORY [OPTIONS] CRITERIA
```

**Options:**

| Option          | Description                         |
|:----------------|:------------------------------------|
| `-name NAME`    | Searches by file name               |
| `-iname NAME`   | Searches by file name ignoring case |
| `-user USER`    | Searches by owner                   |
| `-type TYPE`    | Searches by file type               |
| `-fprint FILE`  | Writes results to a file            |
| `-exec COMMAND` | Runs a command on matches           |
| `-delete`       | Deletes matching files              |

**Examples:**

```bash
find /home/student01 -name fileA.txt
```

```bash
find . -iname fileA.txt
```

```bash
find /home/student01 -user student01
```

```bash
find /home/student01 -name "*.jpg"
```

### `grep`

**Definition:** Searches file contents for a text pattern and displays matching results.

**Syntax:**

```bash
grep [OPTIONS] PATTERN FILE_OR_DIRECTORY
```

**Options:**

| Option                 | Description                      |
|:-----------------------|:---------------------------------|
| `-i`                   | Ignore case                      |
| `-r`                   | Search recursively               |
| `-l`                   | Display only matching file names |
| `-n`                   | Display line numbers             |
| `-c`                   | Count matching lines             |
| `--files-with-matches` | Outputs names of matching files  |

**Examples:**

```bash
grep fail /var/log/secure
```

```bash
grep -r "error" /var/log
```

```bash
ps -ef | grep sshd
```

### `diff`

**Definition:** Compares two files line by line and displays their differences.

**Syntax:**

```bash
diff [OPTIONS] FILE1 FILE2
```

**Example:**

```bash
diff config_old.txt config_new.txt
```

<p align="right"><a href="#table-of-contents">⬆ Back to top</a></p>

---

## 8. Links and Compression

### `ln`

**Definition:** Creates links to files.

**Syntax:**

```bash
ln [OPTIONS] ORIGINAL LINK_NAME
```

**Examples:**

```bash
ln file1 fileA
```

Creates a hard link.

```bash
ln -s fileA sym-fileA
```

Creates a symbolic link.

### `tar`

**Definition:** Bundles multiple files into a single archive and can extract archive contents.

**Syntax:**

```bash
tar [OPTIONS] ARCHIVE FILE...
```

**Options:**

| Option | Description                     |
|:-------|:--------------------------------|
| `-x`   | Extracts archive contents       |
| `-z`   | Uses gzip compression           |
| `-f`   | Specifies the archive file name |
| `-v`   | Displays processed file names   |

**Examples:**

```bash
tar -cvf tarball.tar file1 file2 file3
```

```bash
tar -xf tarball.tar
```

### `gzip`

**Definition:** Compresses or decompresses files.

**Syntax:**

```bash
gzip FILE
gzip -d FILE.gz
```

**Example:**

```bash
gzip salesdata.tar
```

```bash
gzip -d salesdata.tar.gz
```

### `zip`

**Definition:** Compresses files or directories into a `.zip` archive.

**Syntax:**

```bash
zip -r ARCHIVE.zip FOLDER
```

**Example:**

```bash
zip -r project.zip project/
```

### `unzip`

**Definition:** Extracts `.zip` archives.

**Syntax:**

```bash
unzip ARCHIVE.zip
```

**Example:**

```bash
unzip project.zip
```

<p align="right"><a href="#table-of-contents">⬆ Back to top</a></p>

---

## 9. File Ownership and Permissions

### `chown`

**Definition:** Changes the owner and optionally the group associated with a file or directory.

**Syntax:**

```bash
chown [OPTIONS] USER[:GROUP] FILE...
```

**Examples:**

```bash
sudo chown jdoe report.txt
```

```bash
sudo chown jdoe:developers project/
```

### `chmod`

**Definition:** Changes file or directory permissions.

**Syntax:**

```bash
chmod MODE FILE
```

#### Symbolic mode components

| Component | Meaning           |
|:----------|:------------------|
| `u`       | User/owner        |
| `g`       | Group             |
| `o`       | Other             |
| `r`       | Read              |
| `w`       | Write             |
| `x`       | Execute           |
| `+`       | Add permission    |
| `-`       | Remove permission |
| `=`       | Set permission    |

**Examples:**

```bash
chmod u+x script.sh
```

```bash
chmod g-w report.txt
```

#### Absolute mode values

| Permission      | Value |
|:----------------|:------|
| Read            | `4`   |
| Write           | `2`   |
| Execute         | `1`   |
| All permissions | `7`   |

**Examples:**

```bash
chmod 400 file_1
```

```bash
chmod 700 private_directory
```

<p align="right"><a href="#table-of-contents">⬆ Back to top</a></p>

---

## 10. Bash Environment and Text Processing

### `env`

**Definition:** Displays environment variables or runs a utility in an altered environment.

**Syntax:**

```bash
env
```

**Example:**

```bash
env
```

Displays variables in the current environment.

### `alias`

**Definition:** Creates a shorter command that represents a longer command.

**Syntax:**

```bash
alias NAME='COMMAND'
```

**Example:**

```bash
alias ll='ls -l'
```

### `unalias`

**Definition:** Removes a configured alias.

**Syntax:**

```bash
unalias NAME
```

**Example:**

```bash
unalias ll
```

### `cut`

**Definition:** Extracts sections of lines based on bytes, characters, fields, or delimiters.

**Syntax:**

```bash
cut [OPTIONS] FILE
```

**Options:**

| Option | Description                 |
|:-------|:----------------------------|
| `-b`   | Extract by byte             |
| `-c`   | Extract by character/column |
| `-f`   | Extract by field            |
| `-d`   | Specifies the delimiter     |

**Examples:**

```bash
cut -c 1-5 file.txt
```

```bash
cut -d ":" -f 1 /etc/passwd
```

### `sed`

**Definition:** A non-interactive text editor used to search, replace, insert, or delete text according to rules.

**Syntax:**

```bash
sed 'RULE' FILE
```

**Example:**

```bash
sed 's/old/new/g' file.txt
```

Replaces occurrences of `old` with `new`.

### `sort`

**Definition:** Sorts file contents in a specified order.

**Syntax:**

```bash
sort [OPTIONS] FILE
```

**Options:**

| Option | Description                |
|:-------|:---------------------------|
| `-r`   | Reverse alphabetical order |
| `-u`   | Removes duplicate entries  |
| `-M`   | Sorts by month             |

**Examples:**

```bash
sort file.txt
```

```bash
sort -r file.txt
```

```bash
sort -u logfile.txt
```

```bash
sort -M months.txt
```

### `awk`

**Definition:** Processes and transforms text using small programs, variables, operators, control flow, and formatted output.

**Syntax:**

```bash
awk [OPTIONS] 'PROGRAM' INPUT_FILE
awk -f PROGRAM_FILE INPUT_FILE
```

**Options:**

| Option           | Description                    |
|:-----------------|:-------------------------------|
| `-F FS`          | Specifies a field separator    |
| `-f SOURCE_FILE` | Uses an AWK script from a file |
| `-v VAR=VALUE`   | Declares a variable            |

**Examples:**

```bash
awk '{print $1}' file.txt
```

```bash
awk -F ":" '{print $1}' /etc/passwd
```

```bash
awk -f script.awk input.txt
```

<p align="right"><a href="#table-of-contents">⬆ Back to top</a></p>

---

## 11. Process and Job Management

### `ps`

**Definition:** Displays running processes.

**Syntax:**

```bash
ps [OPTIONS]
```

**Example:**

```bash
ps -ef
```

```bash
ps -ef | grep sshd
```

### `pstree`

**Definition:** Displays running processes in a tree structure.

**Syntax:**

```bash
pstree
```

### `top`

**Definition:** Provides a real-time view of running processes and system resource usage.

**Syntax:**

```bash
top
```

### `kill`

**Definition:** Sends a signal to a process, commonly to terminate or control it.

**Syntax:**

```bash
kill [SIGNAL] PID
```

**Signals:**

| Signal            | Meaning                       |
|:------------------|:------------------------------|
| `-9` / `SIGKILL`  | Immediately stops the process |
| `-15` / `SIGTERM` | Requests termination          |
| `-19` / `SIGSTOP` | Pauses the process            |

**Example:**

```bash
kill -9 1234
```

### `nice`

**Definition:** Starts a new process with a specified priority.

**Syntax:**

```bash
nice COMMAND
```

**Priority range:** `-20` is highest priority and `19` is lowest priority.

**Example:**

```bash
nice backup_script.sh
```

### `renice`

**Definition:** Changes the priority of an already running process.

**Syntax:**

```bash
renice PRIORITY PID
```

**Example:**

```bash
renice 10 1234
```

### `jobs`

**Definition:** Lists jobs started and managed by the current shell.

**Syntax:**

```bash
jobs
```

### `bg`

**Definition:** Runs a job in the background.

**Syntax:**

```bash
bg JOB_NUMBER
```

**Example:**

```bash
bg %1
```

### `fg`

**Definition:** Brings a job to the foreground.

**Syntax:**

```bash
fg JOB_NUMBER
```

**Example:**

```bash
fg %1
```

<p align="right"><a href="#table-of-contents">⬆ Back to top</a></p>

---

## 12. Task Scheduling

### `at`

**Definition:** Schedules a command or task to run once at a specified time.

**Syntax:**

```bash
at TIME
```

**Related commands:**

| Command | Description |
|:--|:--|
| `at -l`          | Lists scheduled jobs                                |
| `atrm NUMBER` | Deletes a scheduled job |

**Example:**

```bash
at 16:00
```

Schedules a one-time task for 4:00 PM.

### `cron`

**Definition:** Runs recurring tasks at scheduled times.

**Usage:** Cron reads scheduled tasks from crontab files.

### `crontab`

**Definition:** Creates, lists, edits, or manages scheduled cron tasks.

**Syntax:**

```bash
crontab -e
crontab -l
```

**Options:**

| Option | Description           |
|:-------|:----------------------|
| `-e`   | Edits the crontab     |
| `-l`   | Lists scheduled tasks |

**Crontab format:**

```text
MIN HOUR DOM MON DOW CMD
```

**Example:**

```text
0 16 * * 1 /home/user/backup.sh
```

Runs `backup.sh` at 4:00 PM every Monday.

<p align="right"><a href="#table-of-contents">⬆ Back to top</a></p>

---

## 13. Service Management

### `systemctl`

**Definition:** Manages services on Linux.

**Syntax:**

```bash
systemctl SUBCOMMAND SERVICE_NAME
```

**Subcommands:**

| Subcommand | Description             |
|:-----------|:------------------------|
| `status`   | Displays service status |
| `start`    | Starts a service        |
| `stop`     | Stops a service         |
| `restart`  | Restarts a service      |
| `enable`   | Activates the service   |
| `disable`  | Disables the service    |

**Examples:**

```bash
sudo systemctl status httpd
```

```bash
sudo systemctl start httpd
```

```bash
sudo systemctl restart httpd
```

```bash
sudo systemctl enable httpd
```

### `service`

**Definition:** Manages services. `systemctl` provides more options and features.

**Syntax:**

```bash
service SERVICE_NAME ACTION
```

**Example:**

```bash
sudo service httpd restart
```

<p align="right"><a href="#table-of-contents">⬆ Back to top</a></p>

---

## 14. System Monitoring

### `lscpu`

**Definition:** Displays CPU information.

**Syntax:**

```bash
lscpu
```

### `lshw`

**Definition:** Displays hardware information.

**Syntax:**

```bash
lshw
```

### `du`

**Definition:** Displays the amount of disk space used by files and directories.

**Syntax:**

```bash
du [PATH]
```

**Example:**

```bash
du /home/user
```

### `df`

**Definition:** Displays disk size and available/free space.

**Syntax:**

```bash
df
```

**Example:**

```bash
df
```

### `fdisk`

**Definition:** Lists and modifies hard drive partitions.

**Syntax:**

```bash
fdisk [DEVICE]
```

**Example:**

```bash
sudo fdisk /dev/sda
```

### `vmstat`

**Definition:** Displays information about virtual memory usage.

**Syntax:**

```bash
vmstat
```

### `free`

**Definition:** Displays physical memory usage.

**Syntax:**

```bash
free
```

### `uptime`

**Definition:** Displays how long the system has been running, the number of users, and CPU-related load information.

**Syntax:**

```bash
uptime
```

<p align="right"><a href="#table-of-contents">⬆ Back to top</a></p>