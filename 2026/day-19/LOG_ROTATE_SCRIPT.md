```Bash
#!/bin/bash

set -euo pipefail

# Check if argument is passed
if [ -z "${1:-}" ]; then
    echo "Usage: $0 <log_directory>"
    exit 1
fi

LOG_DIR="$1"

# Check if directory exists
if [ ! -d "$LOG_DIR" ]; then
    echo "Error: Directory does not exist ❌"
    exit 1
fi
echo "Processing logs in $LOG_DIR ..."

compressed_count=$(find "$LOG_DIR" -name "*.log" -mtime +7 2>/dev/null | wc -l)
find "$LOG_DIR" -name "*.log" -mtime +7 -exec gzip {} \; 2>/dev/null

deleted_count=$(find "$LOG_DIR" -name "*.gz" -mtime +30 2>/dev/null | wc -l)
find "$LOG_DIR" -name "*.gz" -mtime +30 -delete 2>/dev/null

echo "compressed file: $compressed_count"
echo "Deleted Old archives: $deleted_count"
```
