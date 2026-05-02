#  Day 19 – DevOps Mini Projects (Automation & Scheduling)

---

## 📖 Overview
In Day 19, I applied shell scripting concepts from previous days to build real-world DevOps automation scripts:

*   **Log Rotation Script**
*   **Server Backup Script**
*   **Scheduled Maintenance Script**
*   **Cron Job Scheduling**

---

## 🧪 Task 1: Log Rotation Script

### 📄 log_rotate.sh
```bash
#!/bin/bash
set -euo pipefail

# Check argument
if [ -z "${1:-}" ]; then
    echo "Usage: $0 <log_directory>"
    exit 1
fi

LOG_DIR="$1"

# Check directory exists
if [ ! -d "$LOG_DIR" ]; then
    echo "Error: Directory does not exist ❌"
    exit 1
fi

echo "Processing logs in $LOG_DIR ..."

# Count and compress old logs (older than 7 days)
compressed_count=$(find "$LOG_DIR" -name "*.log" -mtime +7 2>/dev/null | wc -l)
find "$LOG_DIR" -name "*.log" -mtime +7 -exec gzip {} \; 2>/dev/null

# Count and delete old archives (older than 30 days)
deleted_count=$(find "$LOG_DIR" -name "*.gz" -mtime +30 2>/dev/null | wc -l)
find "$LOG_DIR" -name "*.gz" -mtime +30 -delete 2>/dev/null

echo "Compressed files: $compressed_count"
echo "Deleted files: $deleted_count"
```

---

## 🧪 Task 2: Server Backup Script

### 📄 server_backup.sh
```bash
#!/bin/bash
set -euo pipefail

# Validate arguments
if [ -z "${1:-}" ] || [ -z "${2:-}" ]; then
    echo "Usage: $0 <source_directory> <backup_directory>"
    exit 1
fi

SOURCE="$1"
DEST="$2"

# Check source exists
if [ ! -d "$SOURCE" ]; then
    echo "Error: Source directory does not exist ❌"
    exit 1
fi

# Create destination if missing
mkdir -p "$DEST"

TIMESTAMP=$(date +%Y-%m-%d)
ARCHIVE="$DEST/backup-$TIMESTAMP.tar.gz"

# Create backup
tar -czf "$ARCHIVE" "$SOURCE"

# Verify backup
if [ -f "$ARCHIVE" ]; then
    echo "Backup successful ✅"
    echo "File: $ARCHIVE"
    du -h "$ARCHIVE"
else
    echo "Backup failed ❌"
    exit 1
fi

# Delete backups older than 14 days
find "$DEST" -name "backup-*.tar.gz" -mtime +14 -delete
```

---

## 🧪 Task 3: Cron Jobs

### 📄 Cron Entries
```bash
# Run log rotation daily at 2 AM
0 2 * * * /bin/bash /home/ubuntu/log_rotate.sh /var/log >> /home/ubuntu/log_rotate.log 2>&1

# Run backup every Sunday at 3 AM
0 3 * * 0 /bin/bash /home/ubuntu/server_backup.sh /home/ubuntu /home/ubuntu/backups >> /home/ubuntu/backup.log 2>&1

# Health check every 5 minutes
*/5 * * * * /bin/bash /home/ubuntu/health_check.sh >> /home/ubuntu/health.log 2>&1
```

---

## 🧪 Task 4: Maintenance Script

### 📄 maintenance.sh
```bash
#!/bin/bash
set -euo pipefail

LOG_FILE="$HOME/maintenance.log"
touch "$LOG_FILE"

log() {
    echo "$(date '+%Y-%m-%d %H:%M:%S') : $1" | tee -a "$LOG_FILE"
}

run_log_rotation() {
    log "Starting log rotation"
    if /home/ubuntu/log_rotate.sh /var/log >> "$LOG_FILE" 2>&1; then
        log "Completed log rotation"
    else
        log "Log rotation failed ❌"
    fi
}

run_backup() {
    log "Starting backup"
    if /home/ubuntu/server_backup.sh /home/ubuntu /home/ubuntu/backups >> "$LOG_FILE" 2>&1; then
        log "Completed backup"
    else
        log "Backup failed ❌"
    fi
}

main() {
    log "Maintenance started"
    run_log_rotation
    run_backup
    log "Maintenance completed"
}

main
```

### ⏰ Cron Entry for Maintenance
```bash
# Run daily at 1 AM
0 1 * * * /bin/bash /home/ubuntu/maintenance.sh >> /home/ubuntu/maintenance.log 2>&1
```

---

## 🧠 What I Learned

1.  **Real-world Automation**
    *   **Log rotation**: Efficient management using `find` and `gzip`.
    *   **Backup**: Creating compressed snapshots using `tar`.
2.  **Error Handling**
    *   Implementing `set -euo pipefail` for robust scripts.
    *   Handling command failures with clean `if` conditions.
3.  **Scheduling with Cron**
    *   Automating script execution at specific intervals.
    *   Mastering cron syntax and redirecting output to logs for auditing.

---

## 🚀 Summary
Today I built:
*   ✅ **Log rotation system**
*   ✅ **Backup automation**
*   ✅ **Maintenance orchestrator**
*   ✅ **Cron-based scheduling**

---
