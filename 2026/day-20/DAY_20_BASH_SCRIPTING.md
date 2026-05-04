# 🚀 Day 20 – Bash Scripting Challenge: Log Analyzer & Report Generator

---

## 📌 Overview

In this challenge, I built a Bash script to automate log analysis for system administrators.
The script processes a log file, extracts key insights, and generates a structured report.

---

# 🧪 Script: `log_analyzer.sh`

```bash
#!/bin/bash

set -euo pipefail

# Task 1: Input Validation
if [ -z "${1:-}" ]; then
    echo "Usage: $0 <log_file>"
    exit 1
fi

LOG_FILE="$1"

if [ ! -f "$LOG_FILE" ]; then
    echo "Error: File does not exist ❌"
    exit 1
fi

# Setup
DATE=$(date +%Y-%m-%d)
REPORT="log_report_$DATE.txt"

TOTAL_LINES=$(wc -l < "$LOG_FILE")

# Task 2: Error Count
ERROR_COUNT=$(grep -Ei "ERROR|FAILED" "$LOG_FILE" | wc -l)
echo "Total Errors: $ERROR_COUNT"

# Task 3: Critical Events
CRITICAL_EVENTS=$(grep -n "CRITICAL" "$LOG_FILE" || true)

echo ""
echo "--- Critical Events ---"
echo "$CRITICAL_EVENTS"

# Task 4: Top Error Messages
TOP_ERRORS=$(grep "ERROR" "$LOG_FILE" | \
    awk '{$1=$2=$3=""; print $0}' | \
    sed 's/^ *//' | \
    sort | uniq -c | sort -rn | head -5)

echo ""
echo "--- Top 5 Error Messages ---"
echo "$TOP_ERRORS"

# Task 5: Generate Report
{
    echo "===== Log Analysis Report ====="
    echo "Date: $DATE"
    echo "Log File: $LOG_FILE"
    echo "Total Lines: $TOTAL_LINES"
    echo "Total Errors: $ERROR_COUNT"
    echo ""

    echo "--- Top 5 Error Messages ---"
    echo "$TOP_ERRORS"
    echo ""

    echo "--- Critical Events ---"
    echo "$CRITICAL_EVENTS"

} > "$REPORT"

echo ""
echo "Report generated: $REPORT ✅"

# Task 6: Archive Logs (Optional)
ARCHIVE_DIR="archive"
mkdir -p "$ARCHIVE_DIR"
mv "$LOG_FILE" "$ARCHIVE_DIR/"

echo "Log file moved to $ARCHIVE_DIR/ ✅"
```

---

# 🧪 How to Run

```bash
chmod +x log_analyzer.sh
./log_analyzer.sh sample_log.log
```

---

# 📊 Sample Output

```bash
Total Errors: 4

--- Critical Events ---
3: CRITICAL Disk space below threshold
7: CRITICAL Database connection lost

--- Top 5 Error Messages ---
2 Connection timed out
1 File not found
1 Permission denied
```

---

# 📄 Sample Report File

`log_report_2026-05-04.txt`

```text
===== Log Analysis Report =====
Date: 2026-05-04
Log File: sample_log.log
Total Lines: 7
Total Errors: 4

--- Top 5 Error Messages ---
2 Connection timed out
1 File not found
1 Permission denied

--- Critical Events ---
3: CRITICAL Disk space below threshold
7: CRITICAL Database connection lost
```

---

# 🧠 Approach

### 🔹 1. Input Validation

* Checked if argument is passed using `${1:-}`
* Verified file existence using `-f`

---

### 🔹 2. Error Counting

* Used `grep -Ei "ERROR|FAILED"`
* Counted using `wc -l`

---

### 🔹 3. Critical Event Detection

* Used `grep -n` to include line numbers
* Handled empty results using `|| true`

---

### 🔹 4. Top Error Analysis

* Extracted error messages using `awk`
* Cleaned output using `sed`
* Sorted and counted using `sort | uniq -c`

---

### 🔹 5. Report Generation

* Used `{ } > file` block to write structured output

---

### 🔹 6. Archiving

* Created archive directory using `mkdir -p`
* Moved processed log using `mv`

---

# 🧠 Key Learnings

### ✅ 1. Log processing pipeline

```bash
grep → awk → sort → uniq → sort → head
```

---

### ✅ 2. Defensive scripting

* `set -euo pipefail`
* Prevents silent failures

---

### ✅ 3. Real-world automation

* Log analysis
* Reporting
* File management

---

# 🚀 Summary

Today I built:

* ✅ Log analyzer script
* ✅ Error detection system
* ✅ Report generator
* ✅ Log archiving system

This simulates real-world DevOps log monitoring workflows.

---
