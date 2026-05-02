# Day 18 – Shell Scripting (Functions, Strict Mode & System Reporting)

---

##  Task 1: Basic Functions

### 📄 functions.sh
```bash
#!/bin/bash

# Function to greet
greet() {
    echo "Hello, $1!"
}

# Function to add two numbers
add() {
    sum=$(( $1 + $2 ))
    echo "Sum: $sum"
}

# Calling functions
greet "Govind"
add 5 10
```

**📊 Output**
```text
Hello, Govind!
Sum: 15
```

---

## 🧪 Task 2: Functions with System Checks

### 📄 disk_check.sh
```bash
#!/bin/bash

check_disk() {
    echo "Disk Usage:"
    df -h /
}

check_memory() {
    echo "Memory Usage:"
    free -h
}

# Main section
check_disk
echo "----------------------"
check_memory
```

---

## 🧪 Task 3: Strict Mode

### 📄 strict_demo.sh
```bash
#!/bin/bash

set -euo pipefail

echo "Testing strict mode..."

# Uncomment one at a time to test:
# echo "$undefined_var"                         # set -u example
# false                                         # set -e example
# grep "text" no_file | wc -l                   # pipefail example

echo "Script completed"
```

### 🧠 What each flag does:
* **`set -e`**: Exit immediately if any command fails.
* **`set -u`**: Treat undefined variables as errors and exit.
* **`set -o pipefail`**: If any command in a pipeline fails, the whole pipeline returns a non-zero status.

---

## 🧪 Task 4: Local Variables

### 📄 local_demo.sh
```bash
#!/bin/bash

# Using local variable
func_local() {
    local var="I am local"
    echo "$var"
}

# Without local (Global)
func_global() {
    var="I am global"
}

func_local
echo "Outside function: $var"   # Will not print local var

func_global
echo "Outside function after global: $var"
```

**📊 Output**
```text
I am local
Outside function:
Outside function after global: I am global
```

---

## 🧪 Task 5: System Info Reporter (Real DevOps Script)

### 📄 system_info.sh
```bash
#!/bin/bash

set -euo pipefail

print_header() {
    echo "=============================="
    echo "$1"
    echo "=============================="
}

system_info() {
    print_header "System Info"
    echo "Hostname: $(hostname)"
    echo "OS: $(uname -a)"
}

uptime_info() {
    print_header "Uptime"
    uptime
}

disk_usage() {
    print_header "Disk Usage (Top 5)"
    df -h | sort -rk5 | head -5
}

memory_usage() {
    print_header "Memory Usage"
    free -h
}

cpu_usage() {
    print_header "Top 5 CPU Processes"
    ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%cpu | head -5
}

main() {
    system_info
    uptime_info
    disk_usage
    memory_usage
    cpu_usage
}

main
```

---

## 🧠 Key Learnings (VERY IMPORTANT)

1. **Functions = Reusable Code**
    *   Creates cleaner scripts and avoids repetition.
    *   Makes logic much easier to manage.
2. **Strict Mode = Production Safety**
    *   Prevents silent failures.
    *   Makes debugging easier by stopping at the exact error.
3. **Local Variables Prevent Bugs**
    *   Avoids accidental overwrites of global variables.
    *   Improves script reliability and modularity.

---

## 🚀 Summary
Today I learned how to:
*   Encapsulate logic using **Functions**.
*   Secure scripts using **Strict Mode** (`-euo pipefail`).
*   Manage variable scope with the `local` keyword.
*   Build a comprehensive **System Info Reporter** for real-world monitoring.
