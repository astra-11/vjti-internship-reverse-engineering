# 🔐 RE Task 3 – haxxor.exe

## 🎯 Objective

Reverse engineer the binary `haxxor.exe` and determine the correct input string that causes the program to print:

```
Correct
```

---

## 📂 Provided Files

- `haxxor.exe` — the Windows executable  
- `flag.txt` — contains the correct input string  
- `Report.pdf` — detailed write-up of the full reverse engineering process  
- `README.md` — this explanation summary

> 📘 A complete step-by-step report (`Report.pdf`) is included for those who want to learn from the full solution.  
 
> You’re encouraged to attempt the challenge yourself before checking the flag or report.

---

## 🛠 Tools Used

- Ghidra  
- x64dbg  
- Notepad++ (for notes)

---

## 🔍 Step-by-Step Approach

### 1. Binary Analysis in Ghidra  
- Loaded the binary into Ghidra and let it auto-analyze  
- Found the `main` function and studied the input validation logic  
- Located two key arrays:
  - `local_24[]` — stores XOR keys  
  - `local_3f[]` — stores expected XOR results

---

### 2. XOR Decryption Logic  
- Input characters are XORed with values from `local_24`  
- Result is checked against `local_3f`  
- Decompiled structure looked like:

```c
for (i = 0; i < 0x1b; i++) {
  if ((input[i] ^ local_24[i]) != local_3f[i]) {
    printf("Wrong");
    exit();
  }
}
printf("Correct");
```

---

### 3. Reversing the XOR  
- Reconstructed each correct character with:
  ```c
  correct_char[i] = local_3f[i] ^ local_24[i];
  ```
- Used Python to automate the XOR operations  
- Built the full correct input string

---

### 4. Validation  
- Ran `haxxor.exe`, entered the reconstructed string  
- Output: `"Correct"` — success confirmed

---

## 🚩 Flag (Input String)

The flag is saved in `flag.txt`.  
🔒 **It is intentionally not shown here** so you can try solving it yourself.

---

## 📘 Want to Learn?

A detailed explanation of every step — from identifying key variables to reversing the XOR logic — is documented in `Report.pdf`.

If you're new to reverse engineering, this challenge is a great hands-on XOR puzzle to build your skills.

---

## 💡 What I Learned

- How XOR is used to obfuscate inputs  
- Reading and interpreting static memory in `.data` sections  
- Practical use of Ghidra and x64dbg for RE workflows  
- Reconstructing logic using pseudocode and scripting

---

> 🧠 Tip: Try solving it yourself before opening the `flag.txt` or reading the full report.
