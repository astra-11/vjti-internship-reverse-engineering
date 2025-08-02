# 🧠 RE Task 1 – easycmp.exe

## 🎯 Objective

Reverse engineer the binary `easycmp.exe` and determine the correct input string that results in the output:

```
Correct
```

---

## 📂 Provided Files

- `easycmp.exe` — the executable to analyze  
- `flag.txt` — contains the correct input string I discovered

---

## 🛠 Tools Used

- Ghidra  
- x64dbg  
- Notepad++ (for notes)

---

## 🔍 Approach Summary

This binary was a good introduction to basic reverse engineering. Here's a brief overview of how I solved it:

1. **Loaded the executable in Ghidra** to analyze the decompiled logic.
2. Identified a simple conditional check comparing user input against a hardcoded string.
3. Found the string used in the comparison — it was directly present or XOR-decoded.
4. Used **x64dbg** to set breakpoints and confirm the control flow.
5. Ran the program with the correct input and verified the `"Correct"` message.

---

## 🚩 Flag (Input String)

Saved in `flag.txt`  
Example content:
```
T915{example_flag}
```

(*Note: This is just a placeholder — the actual value is saved in the file.*)

---

## 💡 What I Learned

- How to statically analyze a small binary with Ghidra  
- Importance of string comparisons in basic RE challenges  
- How to confirm behavior dynamically using x64dbg

This was a beginner-friendly task and a good warm-up for the deeper logic in later challenges.

---

> ✅ Tip: Try solving it yourself first using Ghidra or Cutter before peeking at the flag!
