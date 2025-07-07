# Prompt Evaluation for: `write a prime checker`

## Prompt
> `write a prime checker`

---

## Expected Characteristics:

* **Single function**
* **Straightforward logic**
* **Beginner-friendly**
* **Aligned with prompt simplicity**

---

## Expected Output

A simple, standalone function to check if a number is prime, for example:

````
def is_prime(n):
    if n < 2:
        return False
    for i in range(2, int(n ** 0.5) + 1):
        if n % i == 0:
            return False
    return True
````

## Actual Output from Claude
````
def is_prime_simple(n):
    """
    Simple prime checker - checks all numbers from 2 to n-1
    Time complexity: O(n)
    """
    if n < 2:
        return False
    
    for i in range(2, n):
        if n % i == 0:
            return False
    return True


def is_prime_optimized(n):
    """
    Optimized prime checker - only checks up to sqrt(n)
    Time complexity: O(sqrt(n))
    """
    if n < 2:
        return False
    if n == 2:
        return True
    if n % 2 == 0:
        return False
    
    # Only check odd divisors up to sqrt(n)
    i = 3
    while i * i <= n:
        if n % i == 0:
            return False
        i += 2
    
    return True


def is_prime_advanced(n):
    """
    Advanced prime checker with additional optimizations
    Handles edge cases and uses wheel factorization concept
    """
    if n < 2:
        return False
    if n in (2, 3):
        return True
    if n % 2 == 0 or n % 3 == 0:
        return False
    
    # Check for divisors of the form 6k ± 1
    i = 5
    while i * i <= n:
        if n % i == 0 or n % (i + 2) == 0:
            return False
        i += 6
    
    return True


def find_primes_in_range(start, end):
    """
    Find all prime numbers in a given range
    """
    primes = []
    for num in range(start, end + 1):
        if is_prime_optimized(num):
            primes.append(num)
    return primes


def sieve_of_eratosthenes(limit):
    """
    Generate all primes up to a given limit using Sieve of Eratosthenes
    Very efficient for finding many primes at once
    Time complexity: O(n log log n)
    """
    if limit < 2:
        return []
    
    # Create a boolean array and initialize all entries as True
    is_prime = [True] * (limit + 1)
    is_prime[0] = is_prime[1] = False
    
    p = 2
    while p * p <= limit:
        if is_prime[p]:
            # Mark all multiples of p as not prime
            for i in range(p * p, limit + 1, p):
                is_prime[i] = False
        p += 1
    
    # Collect all prime numbers
    return [i for i in range(2, limit + 1) if is_prime[i]]


# Test the functions
if __name__ == "__main__":
    # Test individual numbers
    test_numbers = [2, 3, 4, 17, 25, 29, 97, 100, 101]
    
    print("Testing prime checker functions:")
    print("-" * 40)
    
    for num in test_numbers:
        simple = is_prime_simple(num)
        optimized = is_prime_optimized(num)
        advanced = is_prime_advanced(num)
        
        print(f"{num:3d}: Simple={simple}, Optimized={optimized}, Advanced={advanced}")
    
    print("\n" + "-" * 40)
    
    # Find primes in a range
    print("Primes between 1 and 30:")
    primes_range = find_primes_in_range(1, 30)
    print(primes_range)
    
    print("\nPrimes up to 30 using Sieve of Eratosthenes:")
    primes_sieve = sieve_of_eratosthenes(30)
    print(primes_sieve)
    
    # Performance comparison for a larger number
    large_num = 982451653  # This is actually prime
    print(f"\nTesting large number {large_num}:")
    
    import time
    
    start = time.time()
    result_opt = is_prime_optimized(large_num)
    time_opt = time.time() - start
    
    start = time.time()
    result_adv = is_prime_advanced(large_num)
    time_adv = time.time() - start
    
    print(f"Optimized: {result_opt} (took {time_opt:.6f} seconds)")
    print(f"Advanced: {result_adv} (took {time_adv:.6f} seconds)")
````
---

## AI-Generated Output Summary

The response included:

* `is_prime_simple(n)`: Brute-force version
* `is_prime_optimized(n)`: Checks up to sqrt(n)
* `is_prime_advanced(n)`: Wheel factorization (6k ± 1)
* `find_primes_in_range(start, end)`: Uses optimized checker
* `sieve_of_eratosthenes(limit)`: Efficient for finding many primes
* Performance benchmarking using `time` module
* Comprehensive test harness in `if __name__ == "__main__"` block

---

## Differences / Mismatches

| **Category**      | **Expected**                 | **Generated**                                          |
| ----------------- | ---------------------------- | ------------------------------------------------------ |
| Scope             | Single prime checker         | Multiple functions and tools                           |
| Complexity        | Simple loop or sqrt(n) logic | Introduced wheel factorization and sieve algorithm     |
| Explanation style | Minimal or none              | Verbose docstrings and complexity analysis             |
| Intent Awareness  | Direct response to prompt    | Assumes interest in performance, range, and comparison |
| Cognitive Load    | Low                          | High (too many options for a simple ask)               |
| Personalization   | Not applicable               | Lacks adaptation to user intent or skill level         |

---

## Research Insight

This example highlights a **misalignment between the prompt and the AI's response**, directly supporting my research focus:
**"Human-Centered, Intention-Aware Explanations for Code Generation."**

### Key Findings:

* The model was **overly helpful** instead of being intent-aware.
* It failed to **disambiguate or ask follow-up** questions like:

  > *"Do you want a simple or optimized version?"*
* It did not **tailor its verbosity** or **complexity** to the simplicity of the prompt.
* It introduced **cognitive overload**, making it less usable for beginners.

---

## Characteristics of Intention-Aware AI

| Ideal Behavior           | Suggested Implementation                         |
| ------------------------ | ------------------------------------------------ |
| Ask clarifying questions | "Do you want a simple or optimized checker?"     |
| Match scope to prompt    | Provide only one function unless asked otherwise |
| Adapt to user level      | Infer from prompt phrasing or allow user config  |
| Justify code choices     | Briefly explain why this version was selected    |
| Progressive disclosure   | Offer more versions only if user shows interest  |

---

## TL;DR — Summary of Gaps

| **Dimension**         | **Gap Identified**                                       |
| --------------------- | -------------------------------------------------------- |
| Intent Matching       | Prompt asks for one simple checker, code gives multiple  |
| Human-Centered Design | Overwhelming, not tailored to user's likely expectations |
| Explanation Relevance | No rationale tied to prompt — verbose by default         |
| Usability             | Code is comprehensive but not appropriate to context     |

---
