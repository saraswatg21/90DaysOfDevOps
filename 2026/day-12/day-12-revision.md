# Day 12 – Revision & Consolidation (Focused Self-Check)


---

## 1️⃣ Which 3 commands save you the most time right now, and why?

- **ls -l**
  - Instantly shows permissions, owner, group.
  - Helps diagnose 70% of “Permission denied” issues quickly.

- **systemctl status <service>**
  - Quickly confirms whether a service is running, failed, or inactive.
  - Shows recent logs and uptime.

- **chmod**
  - Fixes access issues immediately.
  - Essential when scripts fail due to missing execute permission.

---

## 2️⃣ How do you check if a service is healthy?

First 3 commands I would run:

1. `systemctl status <service>`
   - Check if service is active or failed.

2. `ps aux | grep <service>`
   - Confirm process is running.

3. `journalctl -u <service> -n 20`
   - Check recent logs for errors.

These three commands confirm:
- Service state
- Running process
- Error logs

---

## 3️⃣ How do you safely change ownership and permissions without breaking access?

Steps:
- Check current permissions using `ls -l`
- Confirm user/group exists using `id username` or `getent group groupname`
- Apply change carefully
- Verify again

Example:

```bash
sudo chown professor:planners heist-project/
```

#  What Will I Focus On Improving in the Next 3 Days?

- Advanced permissions (SUID, SGID, Sticky Bit)
- Faster troubleshooting under time pressure
- Service debugging practice
- More real-world production-style scenarios

---

# Processes & Services (Re-run Practice)

## Commands Re-run

### 1️⃣ ps aux

- Observed all active processes.
- Identified user running each process.
- Checked CPU and memory usage.
- Understood process visibility across the system.

---

### 2️⃣ systemctl status ssh

- Confirmed SSH service was active and running.
- Observed uptime information.
- Saw recent log snippet in the output.

---

## Key Learning

Service issues can be quickly diagnosed using:
- `systemctl status`
- `journalctl -u <service>`

Checking service state + logs gives quick clarity on failures.

---

#  File Skills Practice (Days 06–11)

## 3 Quick Operations Practiced

### 1️⃣ Append Without Overwriting

```bash
echo "Test line" >> file.txt

