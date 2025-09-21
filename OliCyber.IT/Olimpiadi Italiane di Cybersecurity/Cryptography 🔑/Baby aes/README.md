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
  <img src="Baby_aes_chal.png" alt="Challenge banner" width="300" />
</p>

---

### 🧠 Thought Process
First, I examined the [cipher](BasbyAes.py) implementation. The S-box matches the standard AES S-box, so the vulnerability is unlikely to come from the S-box. I also noticed that the `ShiftRows` step has been altered — it behaves more like a `ShiftColumns` permutation. That permutation itself doesn’t seem to introduce the weakness, but I kept it in mind because it will be useful in the exploit. At this stage I glanced over the cryptographic routine:
```python
for block in blocks:
        block = xor_with_key(block, key_expanded)
        block = substitution(block)
        block = permutation(block)
        block = xor_with_key(block, key_expanded)
        ciphertext += block
```
At first I suspected the double XOR might cancel out, creating a weakness, but that’s not the case: the substitution/permutation stage between the XORs introduces non-linearity (notably the S-box), so the two XORs do not simply negate each other. Ultimately I concluded that the real weakness is the two-byte key — the keyspace is tiny, so brute-forcing it is feasible (and ultimately necessary) to recover the key.

Not the most fun approach, but sometimes brute force is the practical solution.

I hate brute-forcing challenges.

---

### 🔍 Solution
All steps used to solve the challenge are available in the [exploit](BasbyAes_Exploit.py). Below is a brief summary of the most important points:

- **Invert S-box**: I used the AES standard inverse S-box to reverse the substitution step.
- **Invert permutation**: I implemented the inverse of the modified `ShiftColumns` permutation to undo that transformation.
- **Keyspace**: The keyspace contains 256×256=65536 possible keys (integer values 0–65535), which makes brute-force feasible. 

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
