<!-- CTF Name -->
<div align="center">
  <img src="challenge-name.svg" alt="Baby aes" />
</div>


### 📌 Challenge Details
- **CTF:** Baby aes 
- **Category:** Crypto 🔑<!-- [Crypto / Web / Pwn / Forensics / Misc] -->
- **Points:**  N/A
- **Difficulty:** Easy <!-- [Easy / Medium / Hard] -->
- **Date:** 21-09-2025  
- **Author / Handle:** Giovanni Pascuzzi (Giunco171)  

---

### 📝 Challenge Description
The challenge, as the name implies, is a simplified — and deliberately insecure — implementation of the AES block cipher operating in Electronic Code Book (ECB) mode. In particular, _Baby aes_ omits some of AES’s standard round transformations (SubBytes, ShiftRows, MixColumns, AddRoundKey) and, to make matters worse, uses a key of only two bytes. That tiny keyspace can be trivially brute-forced — and it’s exactly this weakness that the challenge exploits.

<p align="center">
  <img src="images/Baby_aes_chall.png" alt="Challenge banner" width="600" />
</p>

---

### 🧠 Thought Process
Describe your approach and reasoning:
- Initial observations  
- Hypotheses and ideas considered  
- Dead ends or false leads you explored  
- Key insight that enabled the solution  

---

### 🔍 Solution
Step-by-step explanation of how you solved the challenge. Be explicit and reproducible:

1. [First step — reconnaissance, commands or hints]  
2. [Next step — exploitation, decoding, or reversing]  
3. [Final step — extracting the flag]

Include commands and code snippets where useful:

<!-- ```bash
# Example command
nc example.ctf 1337 -->

---

### 🚩 Flag
```
flag{B3ll0_c0n_5oL0_uN_c1cLo}
```

---

### 📚 Tools & Resources

Tools used: `gdb`, `radare2`, `ghidra`, `binwalk`, `python3`, `curl`, etc.

References / helpful links:

- [Reference 1 — short description]
- [Reference 2 — short description]

---

### 📈 Notes / Alternative Approaches

- Other valid approaches (briefly described)
- Potential optimizations or edge cases to consider
- Assumptions made while solving

---

### 📚 Lessons Learned

- Key takeaways from this challenge
- Mistakes or pitfalls to avoid next time
- New tools, commands, or techniques discovered

---

### 🤝 Credits

- Challenge author(s): [if known]

- Writeup by: [Your Name / Handle]

- Inspired by / referenced: [other writeups or authors you consulted]
