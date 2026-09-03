# File System Navigation
|Command|Purpose|Example|
|---|---|---|
|`pwd`|**Print Working Directory** – shows your current location in the filesystem.|`pwd` → `/home/user/documents`|
|`ls`|**List** – displays files/directories in the current or specified location.|`ls -la` (shows all files + permissions)|
|`cd`|**Change Directory** – move to another folder.|`cd /etc/` or `cd ..` (go up one level)|
# **File & Directory Permissions (chmod, chown)**
| Command | Purpose                                                                                      | Example                                                                                          |
| ------- | -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| `chmod` | **Change Mode** – modify read (r), write (w), execute (x) permissions for user/group/others. | `chmod 600 secret.txt` (owner: rw, others: none) or `chmod u+x script.sh` (add execute for user) |
| `chown` | **Change Owner** – assign file/directory to a specific user and/or group.                    | `chown admin:staff report.pdf`                                                                   |
# **Package Management**
|Command|Purpose|Example|
|---|---|---|
|`apt`|**Advanced Package Tool** – high-level Debian/Ubuntu package manager (handles dependencies).|`apt update` (refresh repo), `apt upgrade` (apply patches), `apt install nginx`|
|`dpkg`|**Debian Package** – low-level tool for direct `.deb` file installation.|`dpkg -i package.deb`, `dpkg -l` (list installed packages)|
