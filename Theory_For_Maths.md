# Java Number System & Related Concepts – Tutorial

## 1. Number Systems

**Core Idea:**  
Numbers can be represented in different bases. This is important in bit manipulation, encoding, and competitive programming.

| System   | Base | Symbols    | Use Case |
|----------|------|------------|----------|
| Binary   | 2    | 0, 1       | Computers, bitwise operations |
| Octal    | 8    | 0–7        | Unix file permissions, legacy systems |
| Decimal  | 10   | 0–9        | Default human-readable numbers |
| Hex      | 16   | 0–9, A–F   | Memory addresses, colors, bit masking |

**Important Points:**  
- Each digit position represents a power of the base.  
- Binary is fastest for computers.  
- Hexadecimal is often used in color codes, memory addresses, and bit masking.  

---

## 2. Conversion Between Number Systems

### Decimal → Other Base (Divide & Remainder Method)
**Algorithm:**  
1. Take the number `n` and the target base.  
2. Divide `n` by base and store remainder.  
3. Set `n = n / base`.  
4. Repeat until `n = 0`.  
5. Build the result string from remainders **in reverse order** (least significant digit comes first).

**Important:** Remainder gives the least significant digit first.

---

### Other Base → Decimal (Multiply & Sum Method)
**Algorithm:**  
1. Take the number in other base and initialize `decimal = 0`, `pow = 0`.  
2. While number > 0:  
   - Extract last digit `r = number % 10`.  
   - Add `r * (base^pow)` to `decimal`.  
   - Remove last digit `number = number / 10`.  
   - Increment `pow`.  

**Important:**  
- For binary ↔ hex conversion, use grouping of 4 bits per hex digit.  
- Handle leading zeros and negative numbers carefully.  

---

### General Conversion Algorithm
**Steps:**  
1. Convert `fromBase` → decimal using multiply & sum.  
2. Convert decimal → `toBase` using divide & remainder.  
3. Test for large numbers and base 16 edge cases.  

---

## 3. Digit Extraction

**Idea:** Extract each digit → useful in DSA problems, palindrome check, sum/product of digits, reversing numbers.

**Algorithm (from back):**  
1. While number > 0:  
   - Last digit = number % 10  
   - Remove last digit: number = number / 10  

**Algorithm (from front):**  
1. Use loop or Math.pow to find highest place value.  
2. Extract front digit by dividing number by place value.  

**Edge Case:** If number = 0, treat as single digit.

---

## 4. Digit Formation from Front & Back

**Back formation:**  
- `num = num * 10 + digit` → builds number in reverse order.  

**Front formation:**  
- Multiply digit by power of 10 based on remaining digits.  

**Algorithm to reverse number:**  
1. Initialize `rev = 0`.  
2. While number > 0:  
   - Extract last digit.  
   - `rev = rev * 10 + last digit`.  
   - Remove last digit from number.  

**Important:** Used in reversing numbers, palindrome checks.

---

## 5. Find Even/Odd

**Simple Algorithm:**  
- If `n % 2 == 0`, number is even.  
- Else, number is odd.  

**Optimized (Bitwise):**  
- If `(n & 1) == 0`, number is even.  
- Else, number is odd.  

**Tip:** Bitwise method is faster; common in competitive programming.

---

## 6. Power of a Number

### Naive Method
**Algorithm:**  
1. Initialize `res = 1`.  
2. Loop `i` from 0 to `b-1`:  
   - Multiply `res` by `a`.  
3. Return `res`.  

**Complexity:** O(b) → works for small b.  
Used in modular exponentiation and combinatorics.

---

### Fast Exponentiation (Exponentiation by Squaring)
**Algorithm:**  
1. Initialize `res = 1`.  
2. While `b > 0`:  
   - If `b` is odd: `res = res * a`.  
   - Square `a = a * a`.  
   - Divide `b` by 2 (`b = b >> 1`).  
3. Return `res`.  

**Complexity:** O(log b)  
- Often used in DSA, modular arithmetic, competitive programming.  
- Can apply modulo at every step to prevent overflow:  
  - `res = (res * a) % MOD`  
  - `a = (a * a) % MOD`  

---

## Challenge Questions
1. Convert decimal `145` into binary, octal, and hex manually.  
2. Write an algorithm to check if a number is palindrome without converting to string.  
3. Modify fast exponentiation algorithm to work under modulo `10^9+7`.  
