# 🚀 Bash Scripting Cheat Sheet 

---

# 📊 Quick Reference Table

| Topic    | Key Syntax          | Example                            |
| -------- | ------------------- | ---------------------------------- |
| Variable | `VAR="value"`       | `NAME="DevOps"`                    |
| Argument | `$1, $2`            | `./script.sh arg1`                 |
| If       | `if [ cond ]; then` | `if [ -f file ]; then`             |
| For loop | `for i in list; do` | `for i in 1 2 3; do`               |
| Function | `name() {}`         | `greet() { echo "Hi"; }`           |
| Grep     | `grep pattern file` | `grep -i "error" log.txt`          |
| Awk      | `awk '{print $1}'`  | `awk -F: '{print $1}' /etc/passwd` |
| Sed      | `sed 's/a/b/g'`     | `sed -i 's/foo/bar/g' file`        |

---

# 🧠 Task 1: Basics

## 🔹 Shebang

```bash
#!/bin/bash
```

👉 Tells system to use Bash interpreter

---

## 🔹 Running Script

```bash
chmod +x script.sh
./script.sh
bash script.sh
```

---

## 🔹 Comments

```bash
# This is a comment
echo "Hello" # inline comment
```

---

## 🔹 Variables

```bash
NAME="Govind"
echo $NAME
echo "$NAME"   # safe
echo '$NAME'   # literal
```

---

## 🔹 User Input

```bash
read -p "Enter name: " NAME
echo "Hello $NAME"
```

---

## 🔹 Arguments

```bash
echo $0  # script name
echo $1  # first arg
echo $#  # count
echo $@  # all args
echo $?  # last exit code
```

---

# ⚙️ Task 2: Operators & Conditionals

## 🔹 String

```bash
[ "$a" = "$b" ]
[ "$a" != "$b" ]
[ -z "$a" ]
[ -n "$a" ]
```

---

## 🔹 Integer

```bash
[ "$a" -eq "$b" ]
[ "$a" -gt "$b" ]
[ "$a" -lt "$b" ]
[ "$a" -ge "$b" ]
```

---

## 🔹 File Tests

```bash
[ -f file ]  # file exists
[ -d dir ]   # directory
[ -r file ]  # readable
[ -w file ]  # writable
[ -x file ]  # executable
[ -s file ]  # not empty
```

---

## 🔹 If-Else

```bash
if [ -f file ]; then
    echo "Exists"
elif [ -d file ]; then
    echo "Dir"
else
    echo "Not found"
fi
```

---

## 🔹 Logical Operators

```bash
[ condition ] && echo "True"
[ condition ] || echo "False"
[ ! condition ]
```

---

## 🔹 Case

```bash
case $var in
    start) echo "Start";;
    stop) echo "Stop";;
    *) echo "Unknown";;
esac
```

---

# 🔁 Task 3: Loops

## 🔹 For Loop

```bash
for i in 1 2 3; do
    echo $i
done
```

---

## 🔹 C-style Loop

```bash
for ((i=1; i<=5; i++)); do
    echo $i
done
```

---

## 🔹 While Loop

```bash
i=1
while [ $i -le 3 ]; do
    echo $i
    ((i++))
done
```

---

## 🔹 Until Loop

```bash
i=1
until [ $i -gt 3 ]; do
    echo $i
    ((i++))
done
```

---

## 🔹 Loop Control

```bash
break
continue
```

---

## 🔹 Loop Files

```bash
for file in *.log; do
    echo $file
done
```

---

## 🔹 Read Output

```bash
cat file.txt | while read line; do
    echo $line
done
```

---

# 🔧 Task 4: Functions

## 🔹 Define & Call

```bash
greet() {
    echo "Hello"
}
greet
```

---

## 🔹 Arguments

```bash
add() {
    echo $(($1 + $2))
}
add 2 3
```

---

## 🔹 Return vs Echo

```bash
return 1   # exit code
echo "value"  # output
```

---

## 🔹 Local Variables

```bash
func() {
    local x=10
    echo $x
}
```

---

# 🧾 Task 5: Text Processing

## 🔹 Grep

```bash
grep "error" file
grep -i "error" file
grep -r "error" .
grep -n "error" file
grep -v "info" file
grep -E "error|fail" file
```

---

## 🔹 Awk

```bash
awk '{print $1}' file
awk -F: '{print $1}' /etc/passwd
awk 'BEGIN {print "Start"}'
```

---

## 🔹 Sed

```bash
sed 's/old/new/g' file
sed -i 's/foo/bar/g' file
sed '2d' file
```

---

## 🔹 Cut

```bash
cut -d: -f1 /etc/passwd
```

---

## 🔹 Sort & Uniq

```bash
sort file
sort -n file
sort -r file
uniq file
uniq -c file
```

---

## 🔹 Tr

```bash
echo "abc" | tr 'a-z' 'A-Z'
```

---

## 🔹 WC

```bash
wc -l file
wc -w file
wc -c file
```

---

## 🔹 Head / Tail

```bash
head -n 5 file
tail -n 5 file
tail -f file
```

---

# ⚡ Task 6: One-Liners

```bash
# Delete old files
find . -mtime +7 -delete

# Count lines in logs
wc -l *.log

# Replace string
sed -i 's/old/new/g' *.txt

# Check service
systemctl is-active nginx

# Disk usage alert
df -h | grep /dev

# Tail errors live
tail -f app.log | grep ERROR
```

---

# 🛠️ Task 7: Error Handling

## 🔹 Exit Codes

```bash
echo $?
exit 0
exit 1
```

---

## 🔹 Strict Mode

```bash
set -e   # exit on error
set -u   # undefined vars error
set -o pipefail
set -x   # debug
```

---

## 🔹 Trap

```bash
trap 'echo "Cleanup done"' EXIT
```

---

# 🎯 Summary

This cheat sheet covers:

* ✅ Bash basics
* ✅ Conditionals & loops
* ✅ Functions
* ✅ Text processing tools
* ✅ Debugging & error handling

---
