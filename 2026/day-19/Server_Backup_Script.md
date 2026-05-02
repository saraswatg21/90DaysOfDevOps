```Bash
#!/bin/bash

set -euo pipefail

SOURCE="$1"
DEST="$2"

if [ ! -d "$SOURCE" ]; then
       echo "source directory not exist "
       exit 1
fi

mkdir -p "$DEST"

TIMESTAMP=$(date +%Y-%m-%d)
ARCHIVE="$DEST/backup-$TIMESTAMP.tar.gz"


tar -czf "$ARCHIVE" "$SOURCE"

if [ -f "$ARCHIVE" ]; then
       echo "Backup created successfully"
       echo "File: $ARCHIVE "
       du -h "$ARCHIVE"
else
 echo "Backup Failed"
 exit 1
fi


find "$DEST" -name "backup-*.tar.gz" -mtime +14 -delete
```
