# 03 – Viewing and Searching Text

Most troubleshooting in cloud and networking is reading logs.
These commands find what matters fast.

## Viewing files
| Command | What it does |
|---|---|
| `head file` | First 10 lines |
| `head -n 3 file` | First 3 lines |
| `tail file` | Last 10 lines (newest entries in a log) |
| `tail -n 1 file` | Last line only |
| `tail -f file` | Follow the file live – new lines appear as they're written. Stop with Ctrl + C |
| `less file` | Scroll through a whole file (read-only). `Space`/`b` page, `G` end, `g` start, `/word` search, `n`/`N` next/previous, `q` quit |

## Searching inside files – grep
| Command | What it does |
|---|---|
| `grep "word" file` | Show lines containing the word |
| `grep -c "word" file` | Count matching lines |
| `grep -i "word" file` | Ignore upper/lower case |
| `grep -n "word" file` | Show line numbers |
| `grep -v "word" file` | Show lines that do NOT match |
| `grep "a" file \| grep -c "b"` | Pipe: filter, then count |

**Lesson learnt:** be exact. `grep -c "failed"` counted 6 (including a backup error).
`grep -c "failed password for admin"` counted the real answer: 4.
A wrong word (`as root` instead of `for root`) returns 0 with no warning –
run the search without `-c` first to see what matches.

## Finding files – find
| Command | What it finds |
|---|---|
| `find . -name "*.log"` | Files by name (case-sensitive), from here down |
| `find . -iname "ROUTER*"` | By name, ignoring case |
| `find . -type f` / `-type d` | Files only / folders only |
| `find . -size +100M` | Files bigger than 100 MB (disk full?) |
| `find . -mtime -1` / `-mmin -60` | Changed in the last day / hour |

## Real-world use
- Server disk full → `find / -size +100M`
- Who is attacking SSH? → `grep "failed password" /var/log/auth.log`
- Watch a service restart live → `tail -f /var/log/syslog`

## Errors met
- `zsh: command not found: greg` → typo. "Command not found" = check spelling first.
