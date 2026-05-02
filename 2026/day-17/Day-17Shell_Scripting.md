
# Day 17 – Shell Scripting (Loops, Arguments & Automation)

---

## 🧪 Task 1: For Loop

### 📄 for_loop.sh
```bash
#!/bin/bash

fruits=("Apple" "Banana" "Mango" "Orange" "Grapes")

for fruit in "${fruits[@]}"; do
    echo "$fruit"
done
```
**📊 Output**
```text
Apple
Banana
Mango
Orange
Grapes
```

### 📄 count.sh
```bash
#!/bin/bash

for i in {1..10}; do
    echo "$i"
done
```
**📊 Output**
```text
1
2
3
...
10
```

---

## 🧪 Task 2: While Loop

### 📄 countdown.sh
```bash
#!/bin/bash

read -p "Enter a number: " num

while [ "$num" -ge 0 ]; do
    echo "$num"
    ((num--))
done

echo "Done!"
```
**📊 Output**
```text
Enter a number: 5
5
4
3
2
1
0
Done!
```

---

## 🧪 Task 3: Command-Line Arguments

### 📄 greet.sh
```bash
#!/bin/bash

if [ -z "$1" ]; then
    echo "Usage: ./greet.sh <name>"
    exit 1
fi

echo "Hello, $1!"
```
**📊 Output**
```bash
./greet.sh Govind
# Hello, Govind!
```

### 📄 args_demo.sh
```bash
#!/bin/bash

echo "Script name: $0"
echo "Total arguments: $#"
echo "All arguments: $@"
```
**📊 Output**
```bash
./args_demo.sh one two three
# Script name: ./args_demo.sh
# Total arguments: 3
# All arguments: one two three
```

---

## 🧪 Task 4: Install Packages via Script

### 📄 install_packages.sh
```bash
#!/bin/bash

set -e

# Check root
if [ "$EUID" -ne 0 ]; then
    echo "Run as root ❌"
    exit 1
fi

packages=("nginx" "curl" "wget")

for pkg in "${packages[@]}"; do
    if dpkg -s "$pkg" &> /dev/null; then
        echo "$pkg already installed ✅"
    else
        echo "Installing $pkg..."
        apt-get install -y "$pkg" || echo "Failed to install $pkg ❌"
    fi
done
```
**▶️ Run**
```bash
sudo ./install_packages.sh
```

---

## 🧪 Task 5: Error Handling (Integrated)

✔️ **Implemented directly inside `install_packages.sh` using:**
* `set -e`: Automatically exits the script if a command fails.
* `||`: Used for fallback messages and custom error logging.
* **Root user validation**: Ensures the script has the necessary permissions before execution.

---

## 🧠 What I Learned

1. **Loops for Automation**
   * `for` loop: Best for iterating over fixed lists or arrays.
   * `while` loop: Best for dynamic conditions that change during execution.
2. **Command-Line Arguments**
   * `$1`: Captures the first argument passed to the script.
   * `$#`: Provides the total count of arguments.
   * `$@`: Represents all arguments as a single string.
3. **Error Handling & Real DevOps Use**
   * `set -e` improves reliability by preventing "cascading" failures.
   * Root checks prevent permission issues during system-level tasks.
   * Automating package installation is a core skill for CI/CD and configuration management.

---

## 🚀 Summary
Today I learned how to:
* Use loops to automate repetitive tasks.
* Handle user inputs and command-line arguments.
* Write production-level scripts with error handling.
* Automate package installation like a DevOps engineer.
