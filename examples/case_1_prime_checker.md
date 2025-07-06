# Prompt Evaluation for: `write a prime checker`

## Prompt
> `write a prime checker`

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

### Characteristics of Expected Output:

* **Single function**
* **Straightforward logic**
* **Beginner-friendly**
* **Aligned with prompt simplicity**

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
# Prompt Evaluation for: `add error handling`

## Prompt
> `add error handling`

---

## Expected Output

Expected a **minimal enhancement** to an existing prime-checking function — e.g., adding basic error checks such as:

- Validating input type (must be an `int`)
- Validating that input is non-negative
- Raising appropriate exceptions (`TypeError`, `ValueError`)

**Example of expected enhancement:**
````
def is_prime(n):
    if not isinstance(n, int):
        raise TypeError("Input must be an integer")
    if n < 0:
        raise ValueError("Input must be non-negative")
    
    if n < 2:
        return False
    for i in range(2, int(n**0.5) + 1):
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
    
    Args:
        n: Integer to check for primality
        
    Returns:
        bool: True if n is prime, False otherwise
        
    Raises:
        TypeError: If n is not an integer
        ValueError: If n is negative
    """
    if not isinstance(n, int):
        raise TypeError(f"Expected integer, got {type(n).__name__}")
    
    if n < 0:
        raise ValueError("Cannot check primality of negative numbers")
    
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
    
    Args:
        n: Integer to check for primality
        
    Returns:
        bool: True if n is prime, False otherwise
        
    Raises:
        TypeError: If n is not an integer
        ValueError: If n is negative
    """
    if not isinstance(n, int):
        raise TypeError(f"Expected integer, got {type(n).__name__}")
    
    if n < 0:
        raise ValueError("Cannot check primality of negative numbers")
    
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
    
    Args:
        n: Integer to check for primality
        
    Returns:
        bool: True if n is prime, False otherwise
        
    Raises:
        TypeError: If n is not an integer
        ValueError: If n is negative
    """
    if not isinstance(n, int):
        raise TypeError(f"Expected integer, got {type(n).__name__}")
    
    if n < 0:
        raise ValueError("Cannot check primality of negative numbers")
    
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
    
    Args:
        start: Starting number of the range (inclusive)
        end: Ending number of the range (inclusive)
        
    Returns:
        list: List of prime numbers in the range
        
    Raises:
        TypeError: If start or end is not an integer
        ValueError: If start or end is negative, or if start > end
    """
    if not isinstance(start, int) or not isinstance(end, int):
        raise TypeError("Range bounds must be integers")
    
    if start < 0 or end < 0:
        raise ValueError("Range bounds cannot be negative")
    
    if start > end:
        raise ValueError("Start must be less than or equal to end")
    
    primes = []
    for num in range(start, end + 1):
        try:
            if is_prime_optimized(num):
                primes.append(num)
        except (TypeError, ValueError):
            # Skip invalid numbers and continue
            continue
    return primes


def sieve_of_eratosthenes(limit):
    """
    Generate all primes up to a given limit using Sieve of Eratosthenes
    Very efficient for finding many primes at once
    Time complexity: O(n log log n)
    
    Args:
        limit: Upper limit for prime generation
        
    Returns:
        list: List of all primes up to limit
        
    Raises:
        TypeError: If limit is not an integer
        ValueError: If limit is negative
        OverflowError: If limit is too large for memory allocation
    """
    if not isinstance(limit, int):
        raise TypeError(f"Expected integer, got {type(limit).__name__}")
    
    if limit < 0:
        raise ValueError("Limit cannot be negative")
    
    if limit < 2:
        return []
    
    # Check for memory constraints (rough estimate)
    if limit > 10**8:
        raise OverflowError("Limit too large - may cause memory issues")
    
    try:
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
    
    except MemoryError:
        raise OverflowError(f"Cannot allocate memory for limit {limit}")
    except Exception as e:
        raise RuntimeError(f"Unexpected error in sieve calculation: {e}")


# Test the functions
if __name__ == "__main__":
    # Test individual numbers
    test_numbers = [2, 3, 4, 17, 25, 29, 97, 100, 101]
    
    print("Testing prime checker functions:")
    print("-" * 40)
    
    for num in test_numbers:
        try:
            simple = is_prime_simple(num)
            optimized = is_prime_optimized(num)
            advanced = is_prime_advanced(num)
            
            print(f"{num:3d}: Simple={simple}, Optimized={optimized}, Advanced={advanced}")
        except Exception as e:
            print(f"{num:3d}: Error - {e}")
    
    print("\n" + "-" * 40)
    
    # Test error handling
    print("Testing error handling:")
    error_test_cases = [
        ("string", "abc"),
        ("float", 3.14),
        ("negative", -5),
        ("boolean", True),
        ("none", None)
    ]
    
    for test_name, test_value in error_test_cases:
        try:
            result = is_prime_optimized(test_value)
            print(f"{test_name}: {result} (unexpected success)")
        except Exception as e:
            print(f"{test_name}: {type(e).__name__} - {e}")
    
    print("\n" + "-" * 40)
    
    # Find primes in a range with error handling
    try:
        print("Primes between 1 and 30:")
        primes_range = find_primes_in_range(1, 30)
        print(primes_range)
    except Exception as e:
        print(f"Range error: {e}")
    
    try:
        print("\nPrimes up to 30 using Sieve of Eratosthenes:")
        primes_sieve = sieve_of_eratosthenes(30)
        print(primes_sieve)
    except Exception as e:
        print(f"Sieve error: {e}")
    
    # Test invalid ranges
    print("\nTesting invalid ranges:")
    invalid_ranges = [
        (10, 5),    # start > end
        (-1, 10),   # negative start
        (1, -10),   # negative end
        ("a", 10),  # non-integer start
        (1, "b")    # non-integer end
    ]
    
    for start, end in invalid_ranges:
        try:
            result = find_primes_in_range(start, end)
            print(f"Range {start} to {end}: {result} (unexpected success)")
        except Exception as e:
            print(f"Range {start} to {end}: {type(e).__name__} - {e}")
    
    # Performance comparison for a larger number with error handling
    large_num = 982451653  # This is actually prime
    print(f"\nTesting large number {large_num}:")
    
    import time
    
    try:
        start = time.time()
        result_opt = is_prime_optimized(large_num)
        time_opt = time.time() - start
        
        start = time.time()
        result_adv = is_prime_advanced(large_num)
        time_adv = time.time() - start
        
        print(f"Optimized: {result_opt} (took {time_opt:.6f} seconds)")
        print(f"Advanced: {result_adv} (took {time_adv:.6f} seconds)")
    except Exception as e:
        print(f"Performance test error: {e}")
    
    # Test memory limit protection
    print(f"\nTesting memory limit protection:")
    try:
        result = sieve_of_eratosthenes(10**9)  # Should raise OverflowError
        print(f"Large sieve: {len(result)} primes found (unexpected)")
    except OverflowError as e:
        print(f"Large sieve: {type(e).__name__} - {e}")
    except Exception as e:
        print(f"Large sieve: {type(e).__name__} - {e}")
````

---

## AI-Generated Output Summary

The AI responded with:

* **Error handling added** to *all* prime-checker functions (`simple`, `optimized`, `advanced`)
* Error handling in **utility functions** like `find_primes_in_range` and `sieve_of_eratosthenes`
* **Edge case** coverage including:

  * Negative inputs
  * Non-integer inputs (string, float, etc.)
  * Out-of-bounds memory allocation (`OverflowError`)
* Added a **full test suite** for:

  * Valid cases
  * Invalid input types
  * Invalid ranges
  * Memory overload tests

---

## Differences / Mismatches

| **Category**          | **Expected**                            | **Generated**                                                      |
| --------------------- | --------------------------------------- | ------------------------------------------------------------------ |
| Scope                 | Add error handling to a single function | Adds error handling to all functions in the module                 |
| Depth                 | Basic type/negativity checks            | Includes memory, range, and exception handling + failover recovery |
| Prompt Matching       | Targeted enhancement                    | Full audit + test harness + range checking                         |
| Explanation verbosity | Likely implicit or short comments       | Full docstrings with `Raises` sections                             |
| Test coverage         | Not explicitly expected                 | Extensive test suite for all types of invalid input                |
| Complexity            | Low to moderate                         | High – complete exception flow control system                      |

---

## Research Insight

This is another example for my research on:

> **"Human-Centered, Intention-Aware Explanations for Code Generation."**

### Key Issues Identified:

* **Over-implementation**: The AI didn't stop at a surgical "error handling" improvement. It **refactored and tested the entire module**.
* **Intent mismatch**: No attempt was made to ask ***which* function** to enhance, or to what extent.
* **Lack of progressive disclosure**: No stepwise enhancement or follow-up was offered like:

  > *"Would you like full validation and test coverage, or just input type checking?"*

---

## What an Intention-Aware AI Should Have Done

| Ideal Behavior              | Implementation Suggestion                                          |
| --------------------------- | ------------------------------------------------------------------ |
| Ask for clarification       | “Do you want basic input checks or full-range exception coverage?” |
| Modify only target code     | Focus on the core prime-checker function, not the full module      |
| Use progressive enhancement | Suggest minimal changes, then offer optional test coverage         |
| Prioritize user experience  | Avoid bloated output for simple prompt                             |

---

## TL;DR — Summary of Gaps

| **Dimension**         | **Gap Identified**                                              |
| --------------------- | --------------------------------------------------------------- |
| Scope Control         | Enhanced *all* code instead of just the target function         |
| Simplicity            | Simple enhancement prompt led to verbose, overly complex output |
| Human-Centered Design | No effort to align with developer intention or clarify scope    |
| Cognitive Overhead    | Added extra mental burden with unnecessary context switching    |

---


