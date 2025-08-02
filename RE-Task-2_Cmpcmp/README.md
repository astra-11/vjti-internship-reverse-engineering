# 🧠 RE Task 2 – cmpcmp.exe

## 🎯 Objective

Reverse engineer the binary `cmpcmp.exe` and determine the correct input string that causes the program to print:

```
Correct!
```

---

## 📂 Provided Files

- `cmpcmp.exe` — the executable to analyze  
- `flag.txt` — contains the correct input string  
- `README.md` — this file with full approach (flag not revealed here)

---

## 🛠 Tools Used

- Ghidra

---

## 🔍 Detailed Approach

### 1. Tool Setup  
I used **Ghidra** for static analysis:
- Imported `cmpcmp.exe` into Ghidra
- Let the tool auto-analyze to produce decompiled pseudocode

---

### 2. Locating the Validation Logic  
- I found a key function named `FUN_00401000` that handles user input.
- This function was responsible for validating the input string character-by-character.

---

### 3. Understanding the Checks  
- The function used **individual local variables** to store each input character:
  - Example: `local_6c`, `local_6b`, `local_6a`, etc.
- Each variable was then compared to a **specific hardcoded character** like:
  ```c
  if (local_6c == 'T') { ... }
  ```
- These comparisons continued for each character in the input, validating the full string.

---

### 4. Reconstructing the Input  
- I traced the variables in **the order of comparison** and extracted each expected character.
- By combining all validated characters in sequence, I formed the full input string that passes all checks.

---

### 5. Verifying the Solution  
- I ran `cmpcmp.exe` in a controlled Windows environment.
- Provided the reconstructed string as input.
- Confirmed that the output was `"Correct!"`

---

### 6. Submitting the Flag  
- The correct string was saved in `flag.txt`
- The final flag is intentionally **not included here** so others can practice the same challenge

---

## 💡 What I Learned

- How to use Ghidra to decompile and read validation logic
- Importance of local variable mapping and renaming for clarity
- Character-by-character comparisons are a common validation pattern
- RE challenges like this can be solved without dynamic analysis if structured well

---

> 🧠 Try reversing it yourself using Ghidra before opening the `flag.txt` file!
