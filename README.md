# 🧠 VJTI CoE Internship – Reverse Engineering Challenges

This repository contains three reverse engineering tasks I solved as part of my internship at the **Centre of Excellence (CoE), VJTI Mumbai**. Each Windows-based executable required analysis to determine the correct input string that would cause the program to output `"Correct"`.

---

## 📂 Practice It Yourself

I've included each **original executable file** (shared during the internship) along with the solved `flag.txt` — so you can try reversing them on your own before checking the answers.

> ⚠️ These are safe, challenge-only binaries intended for **educational use**.

---

## 🧩 Challenge Overview

| Task                          | Binary       | Status   | Flag Provided | Explanation |
|------------------------------|--------------|----------|----------------|-------------|
| RE Task 1 – Easycmp          | easycmp.exe  | ✅ Solved | ✅ `flag.txt`  | ✖           |
| RE Task 2 – Cmpcmp           | cmpcmp.exe   | ✅ Solved | ✅ `flag.txt`  | ✖           |
| RE Task 3 – Haxxor           | haxxor.exe   | ✅ Solved | ✅ `flag.txt`  | ✅ `README.md` |

---

## 📁 Repo Structure

```txt
vjti-internship-reverse-engineering/
├── RE-Task-1_Easycmp/
│   └── flag.txt
├── RE-Task-2_Cmpcmp/
│   └── flag.txt
├── RE-Task-3_Haxxor/
│   ├── flag.txt
│   └── README.md
└── README.md
```
---

> Each folder corresponds to a reverse engineering challenge. Task 3 includes a write-up.

---

## 🛠 Tools Used

* Ghidra
* x64dbg
* PE-bear
* Notepad++ (for analysis/notes)

---

## 👤 About Me

I’m **Astra (Sharvari Dubey)** — a cybersecurity learner focused on red teaming, CTFs, and reverse engineering. This was my first formal internship working on Windows binaries and analyzing executables in a low-level environment.

---

## 🔒 Note

All reverse engineering was performed on intentionally provided educational binaries in a legal and ethical manner under the scope of the VJTI internship.

---

# 🔐 RE Task 3 – haxxor.exe

## ✅ Objective

Analyze the binary `haxxor.exe` and reverse engineer the correct input string that makes the program output `"Correct"`.

---

## 📥 Challenge File

`haxxor.exe`  
Language: C  
Platform: Windows  
Tools Used: Ghidra, x64dbg

---

## 📄 Solution

The program contains two byte arrays in the `.data` section:
- `local_24` → contains static values used in XOR
- `local_3f` → contains the obfuscated flag result

The binary XORs each input character with the corresponding value from `local_24` and compares the result to `local_3f`.

By reversing the XOR logic:
```c
for (i = 0; i < 0x1b; i++) {
  correct_char = local_3f[i] ^ local_24[i];
}
````

I wrote a Python snippet to automate it and recovered the input string:

```txt
T915{I_L0V3_X0R_3NCRYP710N}
```

---

## 🚩 Flag

Saved as: `flag.txt`
Contents:

```
T915{I_L0V3_X0R_3NCRYP710N}
```

---

## 💡 What I Learned

* How XOR obfuscation works in compiled binaries
* Understanding how to read static data segments in Ghidra
* Use of x64dbg for breakpoint-based confirmation
* The importance of reconstructing logic flow for deobfuscation

This challenge helped solidify my reverse engineering fundamentals.

---
