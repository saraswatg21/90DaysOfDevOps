```Bash
#!/bin/bash

set -euo pipefail

LOG_FILE="$HOME/maintenance.log"

log() {
    echo "$(date '+%Y-%m-%d %H:%M:%S') : $1" >> "$LOG_FILE"
}
run_log_rotation() {
    log "Starting log rotation"
    if /home/ubuntu/log_rotate.sh /var/log; then
        log "Completed log rotation"
    else
        log "Log rotation failed "
    fi
}

run_backup() {
    log "Starting backup"
    /home/ubuntu/server_backup.sh /home/ubuntu /home/ubuntu/backup >> "$LOG_FILE" 2>&1
    log "Completed backup"
}

main() {
    log "Maintenance started"

    run_log_rotation
    run_backup

    log "Maintenance completed"
}

main
```
