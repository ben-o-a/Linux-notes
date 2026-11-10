# 02 – Linux Filesystem and File Commands

## The Linux filesystem
- / = the root of the whole filesystem so everything starts here and it's just like C:\ on Windows
- /home = users' personal folders, e.g. /home/ben (shortcut: ~)
- /etc = system and service configuration files (like settings/registry on Windows)
- /var/log = log files for the system and services (like Event Viewer on windows)

## Absolute vs relative paths
- Absolute: the full path starting from /, works from anywhere (e.g. cd /var/log)
- Relative: a path starting from where I am now (e.g. cd Documents, cd ../etc)
- .. means: one level up (the parent folder); they stack, e.g. ../../ = two levels up

## Commands I practised
- mkdir -p: create folders, including any missing parent folders (mkdir -p practice/logs/archive)
- > vs >>: > writes to a file and overwrites it; >> appends to the end of it(echo "web-1 > servers.txt && echo "web-2" >> servers.txt)
- cat: show what's inside a file (cat servers.txt)
- cp / cp -r: copy a file / copy a folder and everything inside it
- mv (move and rename): moves a file, renames it, or both in one go
  (mv logs/servers-backup.txt logs/archive/old-servers.txt)
- rm / rm -r: delete a file / delete a folder and its contents (warning: there is no recycle bin;
  always check with pwd and ls before deleting)

## Mistakes I made and what I learned
- | is a pipe, not "and then" – use && instead
- echo prints text, cat shows a file's contents
- Relative paths depend on where I am (pwd first)
- A typo in a filename (server.txt vs servers.txt) gives "No such file or directory"
