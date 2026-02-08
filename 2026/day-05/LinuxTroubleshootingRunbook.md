# Linux Troubleshooting Runbook

## 1. Environment Basics

### Command 1

```bash
uname -a
```

**Observation:** display the kernel name, operating system, processor type, and other system details

### Command 2

```bash
cat /etc/os-release
```

**Observation:** displays distribution name, version, and ID. 

---

## 2. Filesystem Sanity Check

### Command 3

```bash
mkdir /tmp/runbook-demo
```

**Observation:** Directory created successfully under runbook-demo of tmp → filesystem is writable.

### Command 4

```bash
cp /etc/hosts /tmp/runbook-demo/hosts-copy && ls -l /tmp/runbook-demo
```

**Observation:** File copied from /etc/hosts to /tmp/runbook-demo/hosts-copy and permissons of runbook-demo are displayed 

---

## 3. CPU & Memory Snapshot

### Command 5

```bash
ps -o pid,pcpu,pmem,comm -C sshd
```

**Observation:** `sshd` consuming minimal CPU and memory. No abnormal spikes. Displays id , cpu & sshd of processes 

### Command 6

```bash
free -h
```

**Observation:** displays the total amount of free and used physical memory and swap space in the system, as well as the buffers and cache consumed by the kernel

---

## 4. Disk & IO Health

### Command 7

```bash
df -h
```

**Observation:** shows the amount of free disk space on each mounted disk

### Command 8

```bash
du -sh /var/log
```

**Observation:** logs the estimate file space usage ,and prints the human readable summary,Log directory size normal. No uncontrolled log growth.

---

## 5. Network Checks

### Command 9

```bash
ss -tulpn
```

**Observation:** ss - another utility to investigate sockets , t - tcp sockets , u - udp sockets , l - listening sockets , p - processes using sockets , n -  Show exact bandwidth values, instead of human-readable , `sshd` is listening on port 22 and bound correctly.

### Command 10

```bash
curl -I google.com
```

**Observation:** Network stack responds normally. Local connectivity OK.

---

## 6. Logs Inspection

### Command 11

```bash
journalctl -u ssh -n 50
```

**Observation:** No critical errors in recent 50 logs. Normal authentication events.

### Command 12

```bash
tail -n 50 /var/log/auth.log
```

**Observation:** Login attempts look expected. No brute‑force or repeated failures.

---

## Summary

* System resources are stable
* Filesystem and network are healthy
* `sshd` service operating normally
* No immediate corrective action required

---

## If This Worsens (Next Steps)

1. **Restart strategy:** `systemctl restart ssh` and immediately recheck logs.
2. **Increase visibility:** Temporarily raise SSH log verbosity for deeper insight.
3. **Deep diagnostics:** Attach tools like `strace -p <pid>` or `lsof -p <pid>` to detect hangs or leaks.

---

**Reuse Tip:** Replace `ssh/sshd` with any service (docker, nginx, app service) and update ports/log paths to reuse this runbook.
