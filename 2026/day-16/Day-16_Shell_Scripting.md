# 🐚 Day 16 – Shell Scripting Basics

---

## 🧪 Task 1: Your First Script

### 📄 hello.sh

```bash
#!/bin/bash
echo "Hello, DevOps!"
```
On Terminal 
```Bash
chmod +x hello.sh
./hello.sh
```
📊 Output
```
Hello, DevOps!
```
❓ What happens if you remove shebang?

Script may still run in some environments (defaults to the current shell).

But the system won’t know strictly which shell to use (e.g., sh vs bash).

Can fail if Bash-specific syntax (Bashisms) is used.

Task 2: Variables
variables.sh
```Bash
#!/bin/bash

NAME="Govind Saraswat"
ROLE="DevOps Engineer"

echo "Hello, I am $NAME and I am a $ROLE"
```
📊 Output

```
Hello, I am Govind Saraswat and I am a DevOps Engineer
```
🔍 Single vs Double Quotes
Single Quotes:

```Bash
echo 'Hello $NAME'
# 👉 Output: Hello $NAME
```
Double Quotes:

```Bash
echo "Hello $NAME"
# 👉 Output: Hello Govind Saraswat
```
🧠 Difference:

' ' → Literal strings: No variable expansion occurs.

" " → Interpolated strings: Variable expansion works.

Task 3: User Input
📄 greet.sh
```Bash
#!/bin/bash

read -p "Enter your name: " name
read -p "Enter your favourite tool: " tool

echo "Hello $name, your favourite tool is $tool"
```

📊 Output

```Plaintext
Enter your name: Govind
Enter your favourite tool: Docker
Hello Govind, your favourite tool is Docker
```
🧪 Task 4: If-Else Conditions
📄 check_number.sh
```Bash
#!/bin/bash

read -p "Enter a number: " num

if [ "$num" -gt 0 ]; then
    echo "$num is Positive"
elif [ "$num" -lt 0 ]; then
    echo "$num is Negative"
else
    echo "$num is Zero"
fi
```
📊 Output

```
Enter a number: -5
-5 is Negative
```
📄 file_check.sh
```Bash
#!/bin/bash

read -p "Enter filename: " file

if [ -f "$file" ]; then
    echo "File exists ✅"
else
    echo "File does not exist ❌"
fi
```
📊 Output

```
Enter filename: test.txt
File exists ✅
```
🧪 Task 5: Combine It All
📄 server_check.sh
```Bash
#!/bin/bash

echo "Enter service (nginx/sshd):"
read service

case $service in
    nginx|sshd)
        read -p "Do you want to check the status? (y/n): " choice

        if [ "$choice" = "y" ]; then
            if systemctl is-active --quiet "$service"; then
                echo "$service is running ✅"
            else
                echo "$service is not running ❌"
            fi
        else
            echo "Skipped."
        fi
        ;;
    *)
        echo "Invalid service ❌"
        ;;
esac
```
📊 Output

```
Enter service (nginx/sshd): nginx
Do you want to check the status? (y/n): y
nginx is running ✅

```
# 🧠 What I Learned
* Shebang Importance

* #!/bin/bash defines the interpreter.

* Crucial for script portability across different systems.

* Variables & Input Handling

* No spaces in assignment (VAR=value).

* Use read to capture real-time user input.

* Quotes matter: Use double quotes to ensure variables are expanded correctly.

* Conditions & Real Use Cases

* if-elif-else manages logical flow.

* -f flag is a quick way to verify file existence.

* systemctl integration allows for basic infrastructure monitoring via script.

# 🚀 Summary
* Today I learned how to:

* Create and execute shell scripts.

* Use variables and handle user input.

* Apply logical conditions and automate basic checks.

*  Build real-world DevOps utility scripts.
