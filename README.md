# Secure Hash Standard - Assessment Repository  
### Computational Theory - ATU Galway  
### Nathan Carr (G00410214)

This repository contains my work for the Secure Hash Standard (FIPS 180-4) assessment.  
All solutions are implemented and explained in the main notebook:

``problems.ipynb``

My aim was to present the notebook in a clear and structured way for someone who is comfortable with Python and basic cryptography, but may not be familiar with the internal workings of SHA-256. Each problem is broken down with explanations, code, and tests so that the full process can be followed without additional context.

---

## Repository Contents

├── problems.ipynb # Main assessment notebook with full solutions

├── roughwork.ipynb # Scratch/testing notebook (not part of final marking, just my working area)

├── requirements.txt # Allowed packages for the assignment

└── README.md # This file


---

## What Each Problem Covers

### **Problem 1 - Binary Word Operations**
I implemented the core 32-bit operations used by SHA-256, including Ch, Maj, Σ0, Σ1, σ0 and σ1.  
These are all wrapped as `np.uint32` to match the behaviour in the Secure Hash Standard.  
I also included tests that show the expected bitwise behaviour.

### **Problem 2 - SHA-256 Constants**
I generated the first 64 prime numbers, took the fractional parts of their cube roots, and extracted the first 32 bits just like FIPS 180-4 describes.  
I then verified that my computed constants match the official constants exactly.

### **Problem 3 - Padding and Message Blocks**
I implemented the SHA-256 padding rules, turning any input message into 512-bit blocks.  
I tested edge cases (like messages of length 55, 56, and 57 bytes) to make sure the padding matches the standard perfectly.

### **Problem 4 - Full SHA-256 Hash Function**
I built the message schedule (W[0..63]) and the compression function (the 64 rounds), using the functions from earlier problems.  
Finally, I wrote `sha256_custom(msg)` and confirmed that it matches Python’s `hashlib.sha256` on a variety of standard test messages.

### **Problem 5 - Password Hashing and Security**
I used SHA-256 to demonstrate a simple dictionary attack on three given password hashes.  
After recovering the passwords, I explained why hashing passwords with just SHA-256 is insecure and discussed better alternatives like PBKDF2, bcrypt, and Argon2, along with salts, peppers, and rate limiting.

---

## Running the Notebook

1. Install the required packages:
```bash
pip install -r requirements.txt


Launch Jupyter:

Open problems.ipynb and run the cells in order.

Everything is self-contained, and all tests run automatically.