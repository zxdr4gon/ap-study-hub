# AP Computer Science A: Complete Mastery Guide

### A High-Density Reference for a Perfect Score of 5

---

# Unit 1: Primitive Types

## 1. Core Concepts

Java has **8 primitive types**, but AP CSA focuses on three:

| Type | Size | Range | Default |
|---|---|---|---|
| `int` | 32-bit | $-2^{31}$ to $2^{31}-1$ | `0` |
| `double` | 64-bit | ~$\pm 1.8 \times 10^{308}$ | `0.0` |
| `boolean` | 1-bit | `true` / `false` | `false` |

**Arithmetic Operators:** `+`, `-`, `*`, `/`, `%` (modulo)

**Integer Division:** When both operands are `int`, the result is truncated (not rounded).

**Casting:** Explicitly converting one type to another. Widening (int → double) is automatic. Narrowing (double → int) requires explicit cast.

**Operator Precedence:** Follows standard math — `*`, `/`, `%` before `+`, `-`. Parentheses override.

---

## 2. Code Logic & Syntax

```java
// --- Integer Division vs. Double Division ---
int a = 7, b = 2;
int intResult = a / b;        // → 3 (truncated, NOT rounded)
double dblResult = a / b;     // → 3.0 (still int division first!)
double correct = (double) a / b; // → 3.5 (cast BEFORE division)

// --- Modulo Operator ---
int remainder = 17 % 5;  // → 2
boolean isEven = (num % 2 == 0);
boolean isOdd  = (num % 2 != 0);
// Check last digit:
int lastDigit = num % 10; // → e.g., 237 % 10 = 7

// --- Casting ---
double pi = 3.99;
int truncated = (int) pi;     // → 3 (floor toward zero, NOT rounded)
int x = 5;
double d = x;                 // Widening: automatic, no cast needed

// --- Compound Assignment ---
int n = 10;
n += 3;   // n = 13
n -= 2;   // n = 11
n *= 4;   // n = 44
n /= 4;   // n = 11
n %= 3;   // n = 2
n++;      // n = 3 (post-increment)
++n;      // n = 4 (pre-increment — same effect in isolation)

// --- Integer.MAX_VALUE and Overflow ---
int max = Integer.MAX_VALUE;  // 2,147,483,647
int overflow = max + 1;       // → -2,147,483,648 (wraps to MIN_VALUE!)

// --- Final Variables (Constants) ---
final double TAX_RATE = 0.08; // Cannot be reassigned after declaration
```

---

## 3. Under the Hood

**Stack Memory:** All primitive variables live on the **call stack**. When you write `int x = 5;`, the value `5` is stored directly in the stack frame of the current method. There is no reference, no address — just the raw bits.

**Integer Overflow:** Java uses **two's complement** for 32-bit integers. When you add 1 to `Integer.MAX_VALUE` ($2^{31}-1$), the bit pattern wraps around to $10000...0_2$, which represents $-2^{31}$. Java does **not** throw an exception — it silently overflows. This is a frequent AP trap.

**Integer Division Mechanics:** The JVM executes `idiv` (integer divide) which discards the remainder at the bytecode level. The result is always truncated toward zero: $-7 / 2 = -3$ (not $-4$).

**Casting Mechanics:** `(int) 3.99` calls a narrowing primitive conversion. The JVM truncates toward zero, stripping all decimal bits. It does **not** round. `(int) -3.9` → `-3`, not `-4`.

---

## 4. AP-Style Scenarios (FRQ Prep)

- **Digit Extraction:** Given an integer `n`, isolate its tens digit: `(n / 10) % 10`. Isolate hundreds: `(n / 100) % 10`. This is a classic warm-up in FRQ Part A.
- **Temperature Conversion:** Write an expression to convert Fahrenheit to Celsius: $C = \frac{5}{9}(F - 32)$. The trap: `5/9` in Java integer math is `0`. Must write `5.0 / 9` or cast.
- **Earnings Calculator:** Compute total pay when overtime (hours > 40) pays 1.5x rate. Tests compound conditionals and mixed arithmetic.
- **Range Checking:** Given a score 0–100, compute a letter grade using division: `score / 10` to get a bucket (10 = A, 9 = A, 8 = B, etc.).

---

## 5. The Bug List — Common Traps

| Trap | Buggy Code | Correct Code |
|---|---|---|
| Integer division when double expected | `double avg = sum / count;` | `double avg = (double) sum / count;` |
| Cast applies only to one operand | `(double)(a / b)` → still truncates | `(double) a / b` |
| Modulo on negative numbers | `-7 % 3` → `-1` in Java (not `2`) | Use `Math.abs()` if needed |
| Overflow silently wraps | `Integer.MAX_VALUE + 1` → negative | Use `long` for large values |
| `(int)` truncates, doesn't round | `(int) 3.9` → `3` | Use `Math.round()` to round |
| Confusing `++n` vs `n++` in expressions | `int y = n++;` gives old value | `int y = ++n;` gives new value |

---
---

# Unit 2: Using Objects

## 1. Core Concepts

**Object:** An instance of a class. Objects live on the **heap**; variables hold references (addresses) to them.

**Constructor:** A special method that initializes an object. Called with `new`. Has no return type.

**`null`:** A reference that points to nothing. Calling a method on `null` throws a `NullPointerException`.

**Key Classes tested on AP Exam:**
- `String` — immutable sequence of characters
- `Math` — static utility methods (no instantiation)
- `Integer`, `Double` — wrapper classes for primitives

---

## 2. Code Logic & Syntax

```java
// --- Constructors and Object Instantiation ---
String s1 = new String("hello"); // Explicit constructor (rare for String)
String s2 = "hello";             // String literal (preferred)

// --- String Methods (ALL are non-mutating — Strings are immutable) ---
String str = "AP Computer Science";

int len     = str.length();             // → 19
char c      = str.charAt(3);           // → 'C' (0-indexed)
String sub  = str.substring(3);        // → "Computer Science"
String sub2 = str.substring(3, 5);     // → "Co" (end index EXCLUSIVE)
int idx     = str.indexOf("Science");  // → 12 (returns -1 if not found)
String up   = str.toUpperCase();       // → "AP COMPUTER SCIENCE"
String low  = str.toLowerCase();       // → "ap computer science"
boolean eq  = str.equals("AP Computer Science");  // → true
int cmp     = str.compareTo("AP Biology");  // → positive (S > B)

// --- String Concatenation ---
String name = "Alice";
int age = 17;
String msg = "Name: " + name + ", Age: " + age; // int auto-converts to String

// --- Math Class (static methods — NO instantiation) ---
double absVal  = Math.abs(-4.5);        // → 4.5
double power   = Math.pow(2, 10);       // → 1024.0
double root    = Math.sqrt(144);        // → 12.0
double maxVal  = Math.max(3.2, 7.8);    // → 7.8
double minVal  = Math.min(3.2, 7.8);    // → 3.2
// Math.random() returns [0.0, 1.0) — note: 1.0 is EXCLUDED
double rand    = Math.random();         // 0.0 ≤ rand < 1.0

// Generate random int in range [min, max] inclusive:
// (int)(Math.random() * (max - min + 1)) + min
int roll = (int)(Math.random() * 6) + 1; // Simulates a die: 1–6

// --- Wrapper Classes ---
int primitive = 42;
Integer wrapped = Integer.valueOf(42);      // Boxing (explicit)
Integer autoBoxed = primitive;             // Autoboxing (automatic)
int unboxed = wrapped;                     // Unboxing (automatic)

int parsed = Integer.parseInt("123");      // String → int
String intStr = Integer.toString(456);     // int → String

int maxInt = Integer.MAX_VALUE;  // 2147483647
int minInt = Integer.MIN_VALUE;  // -2147483648
```

---

## 3. Under the Hood

**Stack vs. Heap:**
```
Stack                    Heap
─────────────────        ─────────────────────────
str → [reference] ──────► [ "AP Computer Science" ]
s1  → [reference] ──────► [ "hello" ]
s2  → [reference] ──────► [ "hello" ] (may be same object — String pool)
```
Primitive variables store their value directly on the stack. Object variables store a **reference** (memory address) on the stack pointing to the actual object data on the heap.

**String Immutability:** Every `String` method returns a **new** `String` object. The original is never modified. `str.toUpperCase()` does **not** change `str`; it creates a new object. If you don't capture the return value, the result is lost.

**String Pool:** String literals (e.g., `"hello"`) are stored in a special area of the heap called the **String Constant Pool**. Two variables assigned the same literal may reference the exact same object — which is why `==` can return `true` for literals but should never be used for logical equality.

**Autoboxing/Unboxing:** The compiler inserts `Integer.valueOf()` and `intValue()` calls automatically. This can cause subtle `NullPointerException` bugs if an `Integer` variable is `null` and is then unboxed.

**`Math.random()` internals:** Uses a `Random` object internally seeded with `System.nanoTime()`. Returns a `double` in $[0.0, 1.0)$ — the upper bound is strictly excluded via IEEE 754 arithmetic.

---

## 4. AP-Style Scenarios (FRQ Prep)

- **String Parsing:** Extract initials from a full name (`"John Doe"`) using `indexOf(" ")` and `charAt()`. Tests chained String method usage.
- **Password Validator:** Check that a password has length ≥ 8, contains no spaces (`indexOf(" ") == -1`), etc.
- **Random Simulation:** Generate random numbers in a specified range; e.g., simulate a coin flip or card draw.
- **Wrapper Class Usage:** Convert a `String[]` of numbers from user input into `int` values using `Integer.parseInt()`. Common in data-processing FRQs.
- **compareTo Logic:** Sort or compare strings alphabetically in a loop using `compareTo` — tests understanding of negative/zero/positive return values.

---

## 5. The Bug List — Common Traps

| Trap | Explanation |
|---|---|
| `str.toUpperCase()` without reassigning | Strings are immutable; result discarded if not captured |
| `str.substring(a, b)` — b is exclusive | `"hello".substring(1, 3)` → `"el"`, not `"ell"` |
| `==` on Strings | Compares references, not content; use `.equals()` |
| Calling method on `null` | `NullPointerException` — always check nullity first |
| `Math.random()` range off-by-one | Forgetting `+1` in `(int)(Math.random() * n)` gives `[0, n-1]` |
| `Integer.parseInt()` on non-numeric string | Throws `NumberFormatException` |
| `str.charAt()` out of bounds | Valid indices: `0` to `str.length() - 1` |

---
---

# Unit 3: Boolean Expressions and if Statements

## 1. Core Concepts

**Boolean Expressions:** Evaluate to `true` or `false`. Built from relational operators (`<`, `>`, `<=`, `>=`, `==`, `!=`) and logical operators (`&&`, `||`, `!`).

**Short-Circuit Evaluation:**
- `A && B`: If `A` is `false`, `B` is never evaluated.
- `A || B`: If `A` is `true`, `B` is never evaluated.

**De Morgan's Laws:**

$$\neg(A \land B) \equiv \neg A \lor \neg B$$

$$\neg(A \lor B) \equiv \neg A \land \neg B$$

In Java: `!(a && b)` is equivalent to `(!a || !b)`, and `!(a || b)` is equivalent to `(!a && !b)`.

**Object Equality:** Use `.equals()` for objects, `==` only for primitives.

---

## 2. Code Logic & Syntax

```java
// --- Basic if / else if / else ---
int score = 85;
if (score >= 90) {
    System.out.println("A");
} else if (score >= 80) {
    System.out.println("B");   // → This branch executes
} else if (score >= 70) {
    System.out.println("C");
} else {
    System.out.println("F");
}

// --- Boolean Operators ---
boolean a = true, b = false;
System.out.println(a && b);   // → false
System.out.println(a || b);   // → true
System.out.println(!a);       // → false
System.out.println(a ^ b);    // → true (XOR — exclusive or)

// --- De Morgan's Laws in Practice ---
int x = 5;
// Original:
boolean original = !(x > 3 && x < 10);
// De Morgan's equivalent:
boolean deMorgan = (x <= 3 || x >= 10);
// Both evaluate identically for any x

// --- Short-Circuit Safety Pattern ---
String str = null;
// Safe: if str is null, second condition never evaluated
if (str != null && str.length() > 0) {
    System.out.println("Non-empty string");
}
// UNSAFE order (throws NullPointerException if str is null):
// if (str.length() > 0 && str != null)

// --- Object Equality ---
String s1 = new String("hello");
String s2 = new String("hello");
System.out.println(s1 == s2);      // → false (different heap addresses)
System.out.println(s1.equals(s2)); // → true  (same content)

// --- Nested if Statements ---
int age = 20;
boolean hasID = true;
if (age >= 18) {
    if (hasID) {
        System.out.println("Entry granted");
    } else {
        System.out.println("No ID, denied");
    }
} else {
    System.out.println("Too young");
}

// --- The Dangling Else Problem ---
int val = 5;
if (val > 0)
    if (val > 10)
        System.out.println("Greater than 10");
else                                  // ← This else belongs to INNER if!
    System.out.println("Not > 10");   //   (Java pairs else with nearest if)
// Best practice: ALWAYS use braces {}
```

---

## 3. Under the Hood

**Short-Circuit at Bytecode Level:** The JVM uses conditional jump instructions (`ifeq`, `ifne`). For `&&`, if the left operand is `false`, it jumps directly to the false branch without ever evaluating the right operand. This is not just an optimization — it is guaranteed behavior per the Java Language Specification and is essential for null-safety patterns.

**`==` for Objects:** The `==` operator compares the raw **reference values** (memory addresses stored on the stack). Two `new String("hello")` calls allocate two separate heap objects, so their addresses differ. `.equals()` dispatches a virtual method call that compares character-by-character content.

**`==` Exception — Integer Cache:** Java caches `Integer` objects in the range $[-128, 127]$. So `Integer a = 127; Integer b = 127; a == b` is `true` (same cached object). But `Integer a = 128; Integer b = 128; a == b` is `false`. This is an obscure but real AP trap.

---

## 4. AP-Style Scenarios (FRQ Prep)

- **Range Validation:** Check if a value falls within `[low, high]` — must write `x >= low && x <= high`. Negation via De Morgan's: `x < low || x > high`.
- **Null-Safe String Comparison:** Write a method that returns `true` if two strings are equal, handling `null` inputs without crashing.
- **Grade Classifier:** A classic multi-branch `if/else if` chain. AP graders look for proper structure (no redundant checks) and correct boundary conditions.
- **Leap Year Logic:** `(year % 4 == 0 && year % 100 != 0) || (year % 400 == 0)` — tests compound boolean logic.

---

## 5. The Bug List — Common Traps

| Trap | Explanation |
|---|---|
| `==` instead of `.equals()` for Strings | Reference vs. content comparison |
| Overlapping `else if` conditions | Order matters — check most specific condition first |
| Dangling else — no braces | `else` binds to the nearest `if`, not the intended one |
| Incorrect De Morgan's application | Students negate condition but forget to flip `&&`/`||` |
| Short-circuit assumption violated | Placing null-check after the method call that could throw NPE |
| `=` instead of `==` in condition | `if (x = 5)` is a compile error in Java (unlike C) |
| Missing `else` causing fall-through logic errors | Multiple `if` statements vs. `if/else if` chain behave differently |

---
---

# Unit 4: Iteration

## 1. Core Concepts

**Three loop types in AP CSA:**
- `while` — condition checked before each iteration (pre-test)
- `for` — compact; init, condition, update in one line
- `for-each` (`enhanced for`) — read-only traversal of arrays/collections

**Loop Invariant:** A condition that remains true before and after each iteration. Helps reason about correctness.

**String Traversal:** Access each character using `charAt(i)` in a loop from `0` to `str.length() - 1`.

**Nested Loops:** Inner loop completes fully for each iteration of the outer loop. Total iterations = outer × inner.

---

## 2. Code Logic & Syntax

```java
// --- while loop ---
int count = 0;
while (count < 5) {
    System.out.println(count);  // Prints 0,1,2,3,4
    count++;                    // Must update; else INFINITE LOOP
}

// --- do-while loop (executes at least once) ---
int n;
do {
    n = (int)(Math.random() * 10);
} while (n % 2 != 0);  // Keep rolling until even

// --- Standard for loop ---
for (int i = 0; i < 10; i++) {
    System.out.print(i + " ");  // 0 1 2 3 4 5 6 7 8 9
}

// --- for loop traversal tricks ---
// Forward:  i = 0; i < arr.length
// Backward: i = arr.length - 1; i >= 0; i--
// Step by 2: i += 2
// Every other: i += 2 (even indices only)

// --- String Traversal ---
String word = "Recursion";
int vowelCount = 0;
for (int i = 0; i < word.length(); i++) {
    char ch = word.charAt(i);
    String lower = ("" + ch).toLowerCase();
    if (lower.equals("a") || lower.equals("e") || lower.equals("i") ||
        lower.equals("o") || lower.equals("u")) {
        vowelCount++;
    }
}
// vowelCount → 4 (e, u, i, o)

// --- Building a new String (since Strings are immutable) ---
String original = "Hello World";
String result = "";
for (int i = 0; i < original.length(); i++) {
    char ch = original.charAt(i);
    if (ch != ' ') {
        result += ch;  // Creates new String each time — O(n²) but fine for AP
    }
}
// result → "HelloWorld"

// --- Nested Loops: Multiplication Table ---
for (int row = 1; row <= 5; row++) {
    for (int col = 1; col <= 5; col++) {
        System.out.printf("%4d", row * col);
    }
    System.out.println();
}

// --- Nested Loop: Triangular Pattern ---
for (int i = 1; i <= 5; i++) {
    for (int j = 1; j <= i; j++) {
        System.out.print("* ");
    }
    System.out.println();
}
// Row 1: *
// Row 2: * *
// Row 3: * * *  ...etc.

// --- Computing Sum, Product ---
int sum = 0;
int product = 1;
for (int i = 1; i <= 10; i++) {
    sum += i;      // → 55
    product *= i;  // → 3628800 (10!)
}

// --- Classic: Find digits of a number ---
int num = 12345;
while (num > 0) {
    int digit = num % 10;      // Extract last digit
    System.out.println(digit); // 5, 4, 3, 2, 1
    num /= 10;                 // Remove last digit
}
```

---

## 3. Under the Hood

**Loop Overhead:** Each `for` loop iteration involves: evaluating the boolean condition, executing the body, executing the update statement. The JVM's JIT compiler can unroll simple loops (duplicate loop body to reduce branch overhead), but this is transparent to the programmer.

**String Concatenation in Loops:** `result += ch` compiles to `result = result + ch`. Because `String` is immutable, this allocates a **new `String` object on the heap** every iteration. For a loop of $n$ iterations, this copies $1 + 2 + 3 + \cdots + n = \frac{n(n+1)}{2}$ characters total — making it $O(n^2)$. In production, `StringBuilder` is used instead. On the AP Exam, `+=` is accepted.

**Infinite Loop Risk:** A `while` loop with no update to the controlling variable, or a `for` loop where the update moves the wrong direction (e.g., `i--` when condition is `i < 10`), runs forever and eventually causes a stack overflow or must be force-quit.

---

## 4. AP-Style Scenarios (FRQ Prep)

- **String Reversal:** Use a loop from `str.length() - 1` down to `0`, appending `charAt(i)` to a result string.
- **Counting Occurrences:** Count how many times a target character appears in a string using `charAt` and comparison.
- **Number Decomposition:** Repeatedly `% 10` and `/ 10` to process digits. E.g., sum of digits, check for palindrome number.
- **Nested Loop Grid:** Fill a 2D pattern, print a specific shape, or compute pairwise comparisons between elements.
- **Loop + Accumulator Pattern:** Compute average, sum, count of elements meeting a condition.

---

## 5. The Bug List — Common Traps

| Trap | Explanation |
|---|---|
| Off-by-one: `i <= str.length()` | Valid indices are `0` to `length()-1`; `length()` throws `StringIndexOutOfBoundsException` |
| Forgetting to update loop variable | Classic infinite `while` loop |
| Initializing accumulator inside loop | Resets every iteration — place sum/count **outside** loop |
| Nested loop variable shadowing | Using `i` for both outer and inner loop — inner shadows outer |
| `for-each` loop with index needed | Enhanced for doesn't give index; use standard `for` when position matters |
| Off-by-one in backward traversal | Should start at `length - 1`, not `length` |
| Modifying string inside traversal | Strings are immutable; use a separate result variable |

---
---

# Unit 5: Writing Classes

## 1. Core Concepts

**Encapsulation:** Bundling data (fields) and methods that operate on that data into a single class. Fields are `private`; access is controlled through `public` methods.

**Access Modifiers:**
- `private` — accessible only within the class
- `public` — accessible from anywhere
- (No `protected` or package-private on AP Exam)

**`this` keyword:** Refers to the current object instance. Used to disambiguate between a parameter and a field with the same name.

**Static vs. Instance:**
- **Instance variable/method:** Belongs to a specific object. Accessed via `objectReference.method()`.
- **Static variable/method:** Belongs to the class itself. Shared among all instances. Accessed via `ClassName.method()`.

**Constructors:** No return type. Can be overloaded (multiple constructors with different parameter lists).

---

## 2. Code Logic & Syntax

```java
// ─────────────────────────────────────────────
//  Complete Class Example: BankAccount
// ─────────────────────────────────────────────
public class BankAccount {

    // --- Instance Variables (private for encapsulation) ---
    private String owner;
    private double balance;

    // --- Static Variable (shared across ALL instances) ---
    private static int accountCount = 0;
    private static final double INTEREST_RATE = 0.05; // static constant

    // --- Constructor ---
    public BankAccount(String owner, double initialBalance) {
        this.owner = owner;           // 'this.owner' = field, 'owner' = param
        this.balance = initialBalance;
        accountCount++;               // Every new account increments counter
    }

    // --- Overloaded Constructor (no initial balance) ---
    public BankAccount(String owner) {
        this(owner, 0.0);  // Calls the other constructor — must be FIRST line
    }

    // --- Accessor (getter) ---
    public double getBalance() {
        return balance;
    }

    public String getOwner() {
        return owner;
    }

    // --- Mutator (setter) ---
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }

    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
        }
    }

    // --- Static Method ---
    public static int getAccountCount() {
        return accountCount;  // Can ONLY access static members directly
    }

    // --- toString Override ---
    @Override
    public String toString() {
        return owner + ": $" + balance;
    }
}

// ─────────────────────────────────────────────
//  Using the Class
// ─────────────────────────────────────────────
BankAccount acct1 = new BankAccount("Alice", 1000.0);
BankAccount acct2 = new BankAccount("Bob");

acct1.deposit(500.0);
acct1.withdraw(200.0);
System.out.println(acct1.getBalance());          // → 1300.0
System.out.println(BankAccount.getAccountCount()); // → 2 (static access)
System.out.println(acct1);                       // → Alice: $1300.0 (toString)
```

---

## 3. Under the Hood

**Object Creation — `new` keyword:**
1. JVM allocates memory on the **heap** for the new object.
2. All instance fields are initialized to defaults (0, 0.0, false, null).
3. The constructor body executes, assigning actual values.
4. A reference (address) to the heap object is returned and stored in the variable on the stack.

**`this` keyword:** When `this.owner = owner` executes, `this` holds the address of the object currently being constructed. The JVM passes a hidden `this` reference as the first argument to every instance method call.

**Static Storage:** Static variables live in the **Method Area** (also called the Metaspace in Java 8+), not on the heap with instance data. There is exactly one copy, shared by all instances and accessible without creating any object.

**Constructor Chaining (`this(...)`):** When one constructor calls another with `this(...)`, it must be the **very first statement**. This prevents the partially initialized object from being used before all fields are set.

---

## 4. AP-Style Scenarios (FRQ Prep)

This is the most heavily tested unit on the AP Exam, typically appearing as the entire **FRQ #2 (Class Writing)**.

- **Write a complete class from scratch:** Given a description (e.g., "A `Student` class with a name, GPA, and a method `isHonors()` that returns `true` if GPA ≥ 3.5"), implement all fields, constructors, accessors, mutators, and specified methods.
- **Implement a static counter:** Track how many objects have been created.
- **Write a method that uses other methods:** `void transferTo(BankAccount other, double amount)` calls `this.withdraw()` and `other.deposit()`.
- **`toString` implementation:** Return a formatted `String` representation of the object.
- **Precondition enforcement:** Methods that only act if input is valid (e.g., deposit only if `amount > 0`).

---

## 5. The Bug List — Common Traps

| Trap | Explanation |
|---|---|
| Forgetting `this.` when field and parameter share same name | Without `this.`, assignment `owner = owner` does nothing (assigns param to itself) |
| Adding a return type to a constructor | `public void BankAccount(...)` — this makes it a method, not a constructor; object will use default no-arg constructor |
| Accessing instance variable from static method | `balance` cannot be referenced from `getAccountCount()` — compile error |
| Calling static method on an instance | `acct1.getAccountCount()` works but is misleading; use `BankAccount.getAccountCount()` |
| Forgetting `private` on fields | Breaks encapsulation; direct field access from outside bypasses validation logic |
| Returning `balance` (fine) vs. returning a reference to a mutable object | If a field is a mutable object (e.g., `ArrayList`), returning it directly exposes internals |

---
---

# Unit 6: Array

## 1. Core Concepts

**Array:** A fixed-size, ordered collection of elements of the **same type**. Size is set at creation and **cannot change**.

**Zero-Indexed:** First element is at index `0`, last at `arr.length - 1`.

**Default Values:**
- `int[]` → all `0`
- `double[]` → all `0.0`
- `boolean[]` → all `false`
- `Object[]` → all `null`

**`arr.length`:** A field (not a method — no parentheses). For `String`, it's `str.length()` (a method). This distinction is a common exam trap.

---

## 2. Code Logic & Syntax

```java
// --- Array Declaration and Initialization ---
int[] scores = new int[5];              // {0, 0, 0, 0, 0}
double[] gpa  = {3.9, 3.5, 2.8, 4.0};  // Initializer list (no 'new' needed)
String[] names = new String[3];         // {null, null, null}

// --- Access and Modify ---
scores[0] = 95;
scores[1] = 87;
int first = scores[0];   // → 95
int len   = scores.length; // → 5 (field, NOT a method)

// --- Standard for Loop Traversal ---
for (int i = 0; i < scores.length; i++) {
    System.out.println(scores[i]);
}

// --- Enhanced for Loop (read-only) ---
int total = 0;
for (int s : scores) {
    total += s;   // Cannot modify 'scores[i]' through 's'
}

// ─────────────────────────────────────────────
//  STANDARD ALGORITHMS
// ─────────────────────────────────────────────

// --- Find Minimum ---
int[] arr = {4, 2, 8, 1, 9, 3};
int min = arr[0];           // Initialize to FIRST element (not 0 or MAX_VALUE)
for (int i = 1; i < arr.length; i++) {
    if (arr[i] < min) {
        min = arr[i];
    }
}
// min → 1

// --- Find Maximum ---
int max = arr[0];
for (int i = 1; i < arr.length; i++) {
    if (arr[i] > max) {
        max = arr[i];
    }
}
// max → 9

// --- Compute Average ---
double sum = 0;
for (int val : arr) {
    sum += val;
}
double avg = sum / arr.length; // → 4.5

// --- Count Elements Meeting Condition ---
int countEven = 0;
for (int val : arr) {
    if (val % 2 == 0) countEven++;
}
// countEven → 2 (4, 2, 8)

// --- Find Index of a Target (Linear Search) ---
int target = 8;
int foundIndex = -1;              // Sentinel: -1 means "not found"
for (int i = 0; i < arr.length; i++) {
    if (arr[i] == target) {
        foundIndex = i;
        break;                    // Stop after first match
    }
}
// foundIndex → 2

// --- Shift Elements Right (Insert at beginning) ---
int[] data = {1, 2, 3, 4, 0};    // Last slot is empty (0)
// To insert 99 at index 0:
for (int i = data.length - 1; i > 0; i--) {
    data[i] = data[i - 1];       // MUST traverse from right to left
}
data[0] = 99;
// data → {99, 1, 2, 3, 4}

// --- Shift Elements Left (Remove from index k) ---
int removeIndex = 1;
for (int i = removeIndex; i < data.length - 1; i++) {
    data[i] = data[i + 1];       // MUST traverse from left to right
}
data[data.length - 1] = 0;       // Clear last slot

// --- Reverse an Array In-Place ---
int left = 0, right = arr.length - 1;
while (left < right) {
    int temp = arr[left];
    arr[left] = arr[right];
    arr[right] = temp;
    left++;
    right--;
}

// --- Copy an Array ---
int[] copy = new int[arr.length];
for (int i = 0; i < arr.length; i++) {
    copy[i] = arr[i];  // Element-by-element copy required for primitives
}
```

---

## 3. Under the Hood

**Array Memory Layout:** An array is a contiguous block of memory on the heap. For `int[] arr = new int[5]`, Java allocates `5 × 4 = 20` bytes. The variable `arr` on the stack holds a reference (address) to the first byte of this block. Index access `arr[i]` computes `base_address + i × element_size` — a $O(1)$ operation.

**Arrays are Objects:** In Java, arrays are instances of a special class. `arr.length` is a final instance field, not a method. You can call `arr.getClass().getName()` on an array. A `String[]` is a subtype of `Object[]`.

**Array Bounds Checking:** The JVM checks every array access at runtime. If `i < 0` or `i >= arr.length`, it throws `ArrayIndexOutOfBoundsException`. There is no way to disable this (unlike C/C++).

**Shallow Copy:** Assigning `int[] copy = arr` copies the **reference**, not the data. Both variables point to the same heap object. For primitive arrays, the element-by-element loop above gives a true deep copy. For object arrays, a loop copy gives a **shallow copy** — the elements themselves (references) are copied, but the objects they point to are shared.

---

## 4. AP-Style Scenarios (FRQ Prep)

- **Array of Objects:** Given a `Student[]`, find the student with the highest GPA by tracking a `maxIndex`.
- **Partial Fill Pattern:** Array allocated at max size; a separate `int count` tracks how many slots are actually used. Traverse only up to `count`, not `arr.length`.
- **Shift Algorithm FRQ:** "Write a method that removes the element at a given index and shifts remaining elements left." Must handle edge cases (first element, last element).
- **Two-Array Comparison:** Given two arrays, determine if they contain the same elements in the same order (element-by-element comparison).

---

## 5. The Bug List — Common Traps

| Trap | Explanation |
|---|---|
| `arr.length()` with parentheses | `length` is a field — no `()` |
| Initializing min/max to `0` | Wrong if all values are positive or negative; always start with `arr[0]` |
| Loop to `arr.length` instead of `arr.length - 1` | Off-by-one → `ArrayIndexOutOfBoundsException` |
| Shallow copy: `int[] b = a` | Both reference same array; changes to `b` affect `a` |
| Shifting right but traversing left-to-right | Overwrites data before it's moved — always shift right by traversing right-to-left |
| Enhanced for loop when modification needed | `for (int x : arr) { x = 0; }` does NOT modify the array |
| `ArrayIndexOutOfBoundsException` in traversal | Most commonly caused by `<=` instead of `<` in loop condition |

---
---

# Unit 7: ArrayList

## 1. Core Concepts

**`ArrayList`:** A dynamically resizable array from `java.util`. Can grow and shrink. Stores **objects only** (not primitives — uses wrapper classes).

**`List` Interface:** `ArrayList` implements `List`. Declared as `List<Type>` for flexibility (polymorphic reference).

**Generic Type Parameter:** `ArrayList<String>` — type specified in angle brackets. Enforced at compile-time; prevents type mismatch.

**Key Methods:**

| Method | Description |
|---|---|
| `add(E e)` | Append to end |
| `add(int i, E e)` | Insert at index `i` |
| `get(int i)` | Return element at index `i` |
| `set(int i, E e)` | Replace element at index `i`, returns old value |
| `remove(int i)` | Remove element at index `i`, shifts elements left |
| `size()` | Number of elements (NOT `.length`) |
| `contains(Object o)` | Returns `true` if element exists |
| `indexOf(Object o)` | Returns index of first occurrence, or `-1` |

---

## 2. Code Logic & Syntax

```java
import java.util.ArrayList;
import java.util.List;

// --- Declaration ---
ArrayList<Integer> nums = new ArrayList<Integer>();  // Full syntax
ArrayList<String>  names = new ArrayList<>();        // Diamond operator (preferred)
List<Double> data = new ArrayList<>();               // Interface reference (best practice)

// --- Core Operations ---
names.add("Alice");
names.add("Bob");
names.add("Charlie");
System.out.println(names.size());    // → 3
System.out.println(names.get(1));    // → "Bob"
names.set(1, "Beth");               // Replaces "Bob" with "Beth"
names.remove(0);                    // Removes "Alice", shifts left → ["Beth","Charlie"]
names.remove("Charlie");            // Removes by VALUE (String overloads remove)

// ── CAUTION: remove(int) vs remove(Object) ──────────────────────────────────
ArrayList<Integer> numList = new ArrayList<>();
numList.add(10); numList.add(20); numList.add(30);
numList.remove(1);              // remove(int index) → removes 20, not the value 1
numList.remove(Integer.valueOf(10)); // remove(Object) → removes value 10
// ────────────────────────────────────────────────────────────────────────────

// --- Traversal with for loop ---
ArrayList<String> list = new ArrayList<>();
list.add("Java"); list.add("Python"); list.add("C++");

for (int i = 0; i < list.size(); i++) {
    System.out.println(i + ": " + list.get(i));
}

// --- Enhanced for loop (read-only) ---
for (String lang : list) {
    System.out.println(lang);
}

// ─────────────────────────────────────────────
//  CONCURRENT MODIFICATION ERROR (CRITICAL)
// ─────────────────────────────────────────────
// WRONG — throws ConcurrentModificationException:
for (String lang : list) {
    if (lang.equals("Python")) {
        list.remove(lang);  // Never modify list inside enhanced for!
    }
}

// CORRECT — traverse backward with index-based loop:
for (int i = list.size() - 1; i >= 0; i--) {
    if (list.get(i).equals("Python")) {
        list.remove(i);  // Safe: backward traversal means indices stay valid
    }
}

// ─────────────────────────────────────────────
//  SORTING ALGORITHMS
// ─────────────────────────────────────────────

// --- Selection Sort: find min, swap to front — O(n²) ---
int[] arr = {64, 25, 12, 22, 11};
for (int i = 0; i < arr.length - 1; i++) {
    int minIdx = i;
    for (int j = i + 1; j < arr.length; j++) {
        if (arr[j] < arr[minIdx]) {
            minIdx = j;
        }
    }
    // Swap arr[i] and arr[minIdx]
    int temp   = arr[i];
    arr[i]     = arr[minIdx];
    arr[minIdx] = temp;
}
// arr → {11, 12, 22, 25, 64}

// --- Insertion Sort: build sorted section left-to-right — O(n²) ---
int[] data = {5, 2, 4, 6, 1, 3};
for (int i = 1; i < data.length; i++) {
    int key = data[i];       // Element to insert
    int j = i - 1;
    // Shift elements greater than key one position right
    while (j >= 0 && data[j] > key) {
        data[j + 1] = data[j];
        j--;
    }
    data[j + 1] = key;       // Place key in correct position
}
// data → {1, 2, 3, 4, 5, 6}

// --- Sequential (Linear) Search — O(n) ---
public static int linearSearch(ArrayList<Integer> list, int target) {
    for (int i = 0; i < list.size(); i++) {
        if (list.get(i) == target) return i;
    }
    return -1;
}

// --- Binary Search (requires sorted list) — O(log n) ---
public static int binarySearch(int[] arr, int target) {
    int low = 0, high = arr.length - 1;
    while (low <= high) {
        int mid = (low + high) / 2;
        if (arr[mid] == target)      return mid;
        else if (arr[mid] < target)  low  = mid + 1;
        else                         high = mid - 1;
    }
    return -1;  // Not found
}
```

---

## 3. Under the Hood

**Dynamic Resizing:** `ArrayList` internally uses a plain `Object[]` array. When the array is full and `add()` is called, Java creates a new array of approximately **1.5× the current capacity**, copies all elements over, and discards the old array. This is $O(n)$ for that single operation, but **amortized $O(1)$** per `add()` over many calls.

**Autoboxing in `ArrayList`:** `ArrayList<Integer>` cannot store `int` primitives. When you write `list.add(5)`, the compiler inserts `Integer.valueOf(5)` automatically (autoboxing). When you retrieve and use it as `int`, `intValue()` is called (unboxing). This adds minor overhead and can cause `NullPointerException` if the stored value is `null`.

**`ConcurrentModificationException`:** `ArrayList`'s iterator tracks a `modCount` (modification count). When you call `remove()` inside an enhanced for loop, `modCount` changes, the iterator detects the mismatch on the next `hasNext()` call, and throws immediately. The backward index-based loop avoids this because it doesn't use an iterator.

**Complexity Summary:**

| Operation | Time Complexity |
|---|---|
| `get(i)` | $O(1)$ |
| `add(e)` (end) | $O(1)$ amortized |
| `add(i, e)` (middle) | $O(n)$ |
| `remove(i)` | $O(n)$ |
| `contains(e)` | $O(n)$ |
| Selection Sort | $O(n^2)$ |
| Insertion Sort | $O(n^2)$ worst, $O(n)$ best |
| Binary Search | $O(\log n)$ |

---

## 4. AP-Style Scenarios (FRQ Prep)

- **Filter and Remove:** Given an `ArrayList<String>`, remove all strings shorter than 3 characters. Must use backward traversal.
- **Merge Two Lists:** Combine two sorted `ArrayList<Integer>` into one sorted list.
- **Trace Sorting Algorithm:** Given an array state and a sorting algorithm, show the array after each pass. Selection Sort after pass $k$ has the $k$ smallest elements in their final positions.
- **ArrayList of Objects:** Given an `ArrayList<Student>`, remove all students below a GPA threshold using the backward-loop technique.

---

## 5. The Bug List — Common Traps

| Trap | Explanation |
|---|---|
| `list.size()` vs `arr.length` | `ArrayList` uses `size()` method; arrays use `length` field |
| `remove(1)` removes by index, not value | For `ArrayList<Integer>`, use `Integer.valueOf(1)` to remove by value |
| Modifying list inside enhanced for loop | `ConcurrentModificationException` — use backward index loop |
| Binary Search on unsorted array | Produces incorrect results — must sort first |
| Off-by-one in Selection Sort | Inner loop starts at `i+1`; outer stops at `length-1` |
| Not capturing return value of `set()` | `set(i, val)` returns the old value — if needed, store it |
| Using `==` to compare Integers in ArrayList | Works for cached values [-128,127]; use `.equals()` or unbox first |

---
---

# Unit 8: 2D Arrays

## 1. Core Concepts

**2D Array:** An array of arrays. Think of it as a grid with **rows** and **columns**.

**Declaration:** `int[][] grid = new int[rows][cols];`

**Access:** `grid[row][col]` — row index first, column index second.

**Dimensions:**
- `grid.length` → number of rows
- `grid[0].length` → number of columns (in row 0)

**Traversal Patterns:**
- **Row-major:** Outer loop over rows, inner loop over columns (most common)
- **Column-major:** Outer loop over columns, inner loop over rows

---

## 2. Code Logic & Syntax

```java
// --- Declaration and Initialization ---
int[][] matrix = new int[3][4];         // 3 rows, 4 columns — all zeros
int[][] grid = {
    {1,  2,  3,  4},   // Row 0
    {5,  6,  7,  8},   // Row 1
    {9, 10, 11, 12}    // Row 2
};

// --- Access ---
int val = grid[1][2];   // → 7 (row 1, col 2)
grid[0][0] = 99;

// --- Dimensions ---
int rows = grid.length;         // → 3
int cols = grid[0].length;      // → 4

// ─────────────────────────────────────────────
//  ROW-MAJOR TRAVERSAL (standard)
// ─────────────────────────────────────────────
for (int r = 0; r < grid.length; r++) {
    for (int c = 0; c < grid[r].length; c++) {
        System.out.print(grid[r][c] + "\t");
    }
    System.out.println();
}
// Output:
// 1   2   3   4
// 5   6   7   8
// 9  10  11  12

// ─────────────────────────────────────────────
//  COLUMN-MAJOR TRAVERSAL
// ─────────────────────────────────────────────
for (int c = 0; c < grid[0].length; c++) {
    for (int r = 0; r < grid.length; r++) {
        System.out.print(grid[r][c] + "\t");
    }
    System.out.println();
}
// Output:
// 1   5   9
// 2   6  10
// 3   7  11
// 4   8  12

// ─────────────────────────────────────────────
//  STANDARD ALGORITHMS ON 2D ARRAYS
// ─────────────────────────────────────────────

// --- Sum of all elements ---
int total = 0;
for (int r = 0; r < grid.length; r++) {
    for (int c = 0; c < grid[r].length; c++) {
        total += grid[r][c];
    }
}
// total → 78

// --- Sum of each row ---
for (int r = 0; r < grid.length; r++) {
    int rowSum = 0;
    for (int c = 0; c < grid[r].length; c++) {
        rowSum += grid[r][c];
    }
    System.out.println("Row " + r + " sum: " + rowSum);
}

// --- Find the maximum element ---
int maxVal = grid[0][0];   // Initialize to first element
for (int r = 0; r < grid.length; r++) {
    for (int c = 0; c < grid[r].length; c++) {
        if (grid[r][c] > maxVal) {
            maxVal = grid[r][c];
        }
    }
}
// maxVal → 12

// --- Check if a value exists (2D Linear Search) ---
int searchTarget = 7;
boolean found = false;
int foundRow = -1, foundCol = -1;
for (int r = 0; r < grid.length && !found; r++) {
    for (int c = 0; c < grid[r].length && !found; c++) {
        if (grid[r][c] == searchTarget) {
            found = true;
            foundRow = r;
            foundCol = c;
        }
    }
}

// --- Diagonal Traversal (square matrix only) ---
// Main diagonal: grid[i][i]
for (int i = 0; i < grid.length; i++) {
    System.out.print(grid[i][i] + " "); // → 1, 6 (for 3x3 portion)
}

// --- Neighbor Average (Classic FRQ Pattern) ---
// For cell (r, c), compute average of its valid neighbors
public static double neighborAverage(int[][] arr, int row, int col) {
    int sum = 0, count = 0;
    for (int dr = -1; dr <= 1; dr++) {
        for (int dc = -1; dc <= 1; dc++) {
            if (dr == 0 && dc == 0) continue;   // Skip the cell itself
            int nr = row + dr;
            int nc = col + dc;
            if (nr >= 0 && nr < arr.length &&   // Bounds check — CRITICAL
                nc >= 0 && nc < arr[0].length) {
                sum += arr[nr][nc];
                count++;
            }
        }
    }
    return count > 0 ? (double) sum / count : 0;
}
```

---

## 3. Under the Hood

**Memory Layout:** Java 2D arrays are **arrays of array references**. `int[][] grid = new int[3][4]` allocates:
1. One array of length 3 on the heap, holding 3 references.
2. Three separate `int[4]` arrays on the heap, each containing 4 integers.

This means each row is an independent object. Rows can even be different lengths (**jagged arrays**): `grid[0].length` may differ from `grid[1].length`. Always use `grid[r].length` (not `grid[0].length`) inside the inner loop for full safety.

**Cache Performance:** Row-major traversal accesses memory sequentially (each row is contiguous), which is **cache-friendly**. Column-major traversal jumps between separate heap objects (each row), causing more cache misses. This is a performance difference (not tested on AP Exam, but good to understand).

**No True Matrix Type:** Java doesn't have a native matrix type. 2D array notation is purely syntactic sugar for "array of arrays." Consequently, there's no built-in transpose, multiply, or inverse.

---

## 4. AP-Style Scenarios (FRQ Prep)

This unit commonly appears as **FRQ #4** and tests nested loop logic:

- **Row/Column Operations:** "Return the sum of column `k`." Outer loop over rows, access `grid[r][k]`.
- **Neighbor Average:** The gold standard FRQ task. Given a grid, for each cell, average all surrounding (up to 8) valid neighbors. Critical: bounds-check every neighbor with `&&` short-circuiting.
- **Spiral/Pattern Fill:** Fill a 2D array with values in a specific pattern (e.g., spiral, zigzag). Tests loop control.
- **Count Specific Values:** Count how many cells contain a value greater than a threshold. Simple double loop with conditional accumulator.
- **Transpose:** Create a new `int[cols][rows]` and set `result[c][r] = grid[r][c]`.

---

## 5. The Bug List — Common Traps

| Trap | Explanation |
|---|---|
| `grid.length` vs `grid[0].length` | `grid.length` = rows; `grid[0].length` = columns — swapping these causes wrong traversal |
| Accessing `grid[r][c]` with r and c swapped | Row-first, column-second — reversal causes reading wrong cell |
| No bounds check in neighbor algorithm | `grid[-1][c]` throws `ArrayIndexOutOfBoundsException` — always check bounds |
| Using `grid[0].length` for jagged arrays | Safer to use `grid[r].length` inside inner loop |
| Off-by-one in loop conditions | `r < grid.length` and `c < grid[r].length` — both must be `<`, not `<=` |
| Forgetting to skip center cell in neighbor average | Must use `if (dr == 0 && dc == 0) continue` |

---
---

# Unit 9: Inheritance

## 1. Core Concepts

**Inheritance:** A subclass (`extends`) inherits all `public` and `protected` members of the superclass. Enables code reuse and models an **"is-a"** relationship.

**`super` keyword:**
- `super(args)` — calls the superclass constructor (must be first line in subclass constructor)
- `super.method()` — calls the superclass version of an overridden method

**Method Overriding:** Subclass provides its own implementation of a method defined in the superclass. Same signature, `@Override` annotation.

**Method Overloading:** Multiple methods in the **same class** with the same name but different parameter lists. Resolved at compile time.

**Polymorphism:** A superclass reference can point to a subclass object. The actual method called is determined at **runtime** (dynamic dispatch).

**Abstract Class/Method:** Cannot be instantiated. Abstract methods have no body; subclasses must implement them.

**Interface:** A contract of method signatures. A class `implements` an interface and provides all method bodies.

---

## 2. Code Logic & Syntax

```java
// ─────────────────────────────────────────────
//  Superclass
// ─────────────────────────────────────────────
public class Animal {
    private String name;
    private int age;

    public Animal(String name, int age) {
        this.name = name;
        this.age  = age;
    }

    public String getName() { return name; }
    public int    getAge()  { return age;  }

    public String makeSound() {
        return "...";
    }

    @Override
    public String toString() {
        return name + " (age " + age + ")";
    }
}

// ─────────────────────────────────────────────
//  Subclass
// ─────────────────────────────────────────────
public class Dog extends Animal {
    private String breed;

    public Dog(String name, int age, String breed) {
        super(name, age);   // MUST be first line; calls Animal constructor
        this.breed = breed;
    }

    public String getBreed() { return breed; }

    @Override
    public String makeSound() {      // Overrides Animal's makeSound()
        return "Woof!";
    }

    @Override
    public String toString() {
        return super.toString() + ", Breed: " + breed;  // Reuses superclass logic
    }
}

// ─────────────────────────────────────────────
//  Polymorphism in Action
// ─────────────────────────────────────────────
Animal a1 = new Animal("Generic", 5);
Animal a2 = new Dog("Rex", 3, "Labrador");  // Superclass ref, subclass obj

System.out.println(a1.makeSound());   // → "..." (Animal's version)
System.out.println(a2.makeSound());   // → "Woof!" (Dog's version — dynamic dispatch)
System.out.println(a2.toString());    // → "Rex (age 3), Breed: Labrador"

// a2.getBreed();   // COMPILE ERROR: Animal reference doesn't know about getBreed()
// Must cast first:
Dog d = (Dog) a2;
System.out.println(d.getBreed());    // → "Labrador"

// --- instanceof operator ---
if (a2 instanceof Dog) {
    Dog myDog = (Dog) a2;            // Safe downcast
    System.out.println(myDog.getBreed());
}

// ─────────────────────────────────────────────
//  Abstract Class
// ─────────────────────────────────────────────
public abstract class Shape {
    private String color;

    public Shape(String color) {
        this.color = color;
    }

    public String getColor() { return color; }

    public abstract double getArea();    // No body — subclass MUST implement
    public abstract double getPerimeter();
}

public class Circle extends Shape {
    private double radius;

    public Circle(String color, double radius) {
        super(color);
        this.radius = radius;
    }

    @Override
    public double getArea() {
        return Math.PI * radius * radius;
    }

    @Override
    public double getPerimeter() {
        return 2 * Math.PI * radius;
    }
}

// ─────────────────────────────────────────────
//  Interface
// ─────────────────────────────────────────────
public interface Comparable<T> {         // Built-in Java interface
    int compareTo(T other);
}

public interface Printable {
    void print();                        // All methods implicitly public & abstract
}

public class Student implements Printable {
    private String name;
    private double gpa;

    public Student(String name, double gpa) {
        this.name = name;
        this.gpa  = gpa;
    }

    @Override
    public void print() {
        System.out.println(name + ": " + gpa);
    }
}

// ─────────────────────────────────────────────
//  Method Overloading (NOT overriding)
// ─────────────────────────────────────────────
public class Calculator {
    public int add(int a, int b)          { return a + b; }
    public double add(double a, double b) { return a + b; }  // Overloaded
    public int add(int a, int b, int c)   { return a + b + c; }  // Overloaded
}
```

---

## 3. Under the Hood

**The Virtual Method Table (vtable):** Every class has a vtable — an array of method pointers. When `a2.makeSound()` is called on an `Animal` reference pointing to a `Dog` object, the JVM looks up `makeSound` in `Dog`'s vtable (not `Animal`'s) at **runtime**. This is **dynamic dispatch** and is the engine of polymorphism. It is resolved at runtime, not compile time.

**`super()` Constructor Chain:** When `new Dog("Rex", 3, "Labrador")` executes:
1. `Dog` constructor body begins.
2. `super(name, age)` is called first — execution jumps to `Animal`'s constructor.
3. `Animal`'s fields (`name`, `age`) are initialized.
4. Control returns to `Dog`'s constructor body.
5. `Dog`'s own fields (`breed`) are initialized.

If you omit `super()` in the subclass constructor, Java automatically inserts a call to the **no-arg superclass constructor** `super()`. If no such constructor exists, it's a compile error.

**Object Class:** Every class in Java implicitly extends `Object`. `toString()`, `equals()`, and `hashCode()` are defined in `Object` and are available to all classes. When you `@Override toString()`, you replace `Object`'s default (which prints something like `Animal@1b6d3586`).

**Casting:** Downcasting (`(Dog) a2`) doesn't change the object. It only tells the compiler "trust me, this `Animal` reference is actually pointing to a `Dog`." If it's wrong at runtime, `ClassCastException` is thrown.

---

## 4. AP-Style Scenarios (FRQ Prep)

This unit frequently forms **FRQ #3 (Inheritance)** and combines with Unit 5:

- **Extend an existing class:** Given a `Vehicle` superclass, write a `Car` subclass that adds a `numDoors` field, calls `super()` in the constructor, and overrides `toString()`.
- **Polymorphic ArrayList:** Given `ArrayList<Shape>`, call `getArea()` on each element — each subclass returns the correct value via dynamic dispatch.
- **Override and extend behavior:** `toString()` in subclass calls `super.toString()` and appends additional info.
- **Abstract method enforcement:** Write an abstract `Employee` class with abstract `double calculatePay()`, then implement `HourlyEmployee` and `SalariedEmployee`.
- **`instanceof` check + downcast:** Given an `Animal[]` of mixed types, count only `Dog` instances.

---

## 5. The Bug List — Common Traps

| Trap | Explanation |
|---|---|
| `super()` not the first line in subclass constructor | Compile error — Java mandates it be the first statement |
| Overloading instead of overriding | Different parameter list = new method, not override; original method not replaced |
| Calling subclass-only method via superclass reference | Compile error — reference type determines what's accessible at compile time |
| Forgetting `@Override` | Not a compile error, but losing the annotation means typo in method name creates a new method instead of overriding |
| Invalid downcast | `(Dog) anAnimal` when `anAnimal` actually holds a `Cat` → `ClassCastException` at runtime |
| Abstract class instantiated | `new Shape()` → compile error; must use a concrete subclass |
| Private fields inherited but not directly accessible | Subclass must use superclass getters/setters to access private superclass fields |

---
---

# Unit 10: Recursion

## 1. Core Concepts

**Recursion:** A method that calls itself. Every recursive solution must have:
1. **Base Case:** A condition that terminates the recursion (no recursive call).
2. **Recursive Case:** Calls itself with a "smaller" or "simpler" input, progressing toward the base case.

**Call Stack:** Each recursive call creates a new **stack frame** with its own local variables. Frames are added (pushed) on each call and removed (popped) when a method returns.

**Stack Overflow:** If the base case is never reached (infinite recursion), the call stack fills up and the JVM throws `StackOverflowError`.

**Tracing Recursion:** Work from the base case upward. Draw the call tree.

---

## 2. Code Logic & Syntax

```java
// ─────────────────────────────────────────────
//  Classic Recursion Examples
// ─────────────────────────────────────────────

// --- Factorial ---
public static int factorial(int n) {
    if (n == 0 || n == 1) return 1;  // Base case
    return n * factorial(n - 1);      // Recursive case
}
// factorial(4):
//   4 * factorial(3)
//     3 * factorial(2)
//       2 * factorial(1)
//         → 1  (base case)
//       → 2 * 1 = 2
//     → 3 * 2 = 6
//   → 4 * 6 = 24

// --- Sum of integers 1..n ---
public static int sum(int n) {
    if (n <= 0) return 0;            // Base case
    return n + sum(n - 1);           // Recursive case
}

// --- Fibonacci ---
public static int fib(int n) {
    if (n == 0) return 0;            // Base case 1
    if (n == 1) return 1;            // Base case 2
    return fib(n - 1) + fib(n - 2); // Two recursive calls (exponential tree)
}
// WARNING: This naive version is O(2^n) — extremely slow for large n

// --- Power (x^n) ---
public static double power(double x, int n) {
    if (n == 0) return 1.0;          // Base case: x^0 = 1
    return x * power(x, n - 1);      // Recursive case
}

// --- String reversal ---
public static String reverse(String s) {
    if (s.length() <= 1) return s;   // Base case
    return reverse(s.substring(1)) + s.charAt(0);
}
// reverse("abc"):
//   reverse("bc") + 'a'
//     reverse("c") + 'b'
//       → "c"  (base case)
//     → "cb"
//   → "cba"

// --- Check palindrome recursively ---
public static boolean isPalindrome(String s) {
    if (s.length() <= 1) return true;          // Base case
    if (s.charAt(0) != s.charAt(s.length()-1)) return false;
    return isPalindrome(s.substring(1, s.length() - 1)); // Trim both ends
}

// ─────────────────────────────────────────────
//  RECURSIVE BINARY SEARCH
// ─────────────────────────────────────────────
public static int binarySearch(int[] arr, int target, int low, int high) {
    // Base case: search space exhausted
    if (low > high) return -1;

    int mid = (low + high) / 2;

    if (arr[mid] == target)  return mid;          // Found!
    if (arr[mid] < target)   return binarySearch(arr, target, mid + 1, high); // Right half
    else                     return binarySearch(arr, target, low, mid - 1);  // Left half
}

// Usage:
int[] sorted = {2, 5, 8, 12, 16, 23, 38, 45};
int idx = binarySearch(sorted, 23, 0, sorted.length - 1); // → 5

// ─────────────────────────────────────────────
//  TRACING A RECURSION CALL TREE (FRQ essential)
// ─────────────────────────────────────────────
// mystery(5):
public static int mystery(int n) {
    if (n <= 1) return 1;
    if (n % 2 == 0) return mystery(n / 2);
    else            return mystery(n - 1) + 1;
}
// mystery(5) → mystery(4) + 1
//   mystery(4) → mystery(2)
//     mystery(2) → mystery(1)
//       → 1 (base case)
//     → 1
//   → 1
// → 1 + 1 = 2
// mystery(5) = 2
```

---

## 3. Under the Hood

**The Call Stack in Detail:**
```
Stack (grows downward)              Each frame holds:
┌──────────────────────┐
│ factorial(1) → n=1   │  ← top    local var n, return address
├──────────────────────┤
│ factorial(2) → n=2   │
├──────────────────────┤
│ factorial(3) → n=3   │
├──────────────────────┤
│ factorial(4) → n=4   │
├──────────────────────┤
│ main()               │  ← bottom
└──────────────────────┘
```

When `factorial(1)` returns `1`, its frame is **popped**. Control returns to `factorial(2)`, which can now evaluate `2 * 1 = 2`, then pops, and so on up the stack.

**Stack Overflow:** The JVM's stack has a fixed size (typically 256KB–1MB depending on platform). Each frame takes memory. A recursion depth of ~5,000–10,000 typically overflows. Infinite recursion (missing base case) overflows immediately.

**Fibonacci's Exponential Problem:** `fib(n)` without memoization calls `fib(n-1)` and `fib(n-2)`, each of which does the same. The call tree has $O(2^n)$ nodes. `fib(50)` makes over a trillion calls. The fix (memoization) is beyond AP CSA scope but good to know.

**Recursive Binary Search Complexity:** Each recursive call halves the search space. After $k$ calls, the space is $\frac{n}{2^k}$. When $\frac{n}{2^k} = 1$, we have $k = \log_2 n$. Thus complexity is $O(\log n)$.

---

## 4. AP-Style Scenarios (FRQ Prep)

- **Trace a mystery recursive method:** Given an unfamiliar recursive method, compute the return value for a specific input. Must manually trace the call stack.
- **Write recursive string method:** Implement `countChar(String s, char c)` that counts how many times `c` appears in `s` recursively.
- **Recursive sum of array:** `public static int arraySum(int[] arr, int index)` — add `arr[index]` to the result of the recursive call on the rest.
- **Identify base case and recursive case:** AP Exam may give partial code and ask to fill in the missing base/recursive case.
- **Compare iterative to recursive:** Know how to rewrite a simple loop as recursion and vice versa.

---

## 5. The Bug List — Common Traps

| Trap | Explanation |
|---|---|
| Missing base case | Infinite recursion → `StackOverflowError` |
| Base case that's never reached | E.g., `if (n == 0)` but `n` starts negative and decrements — never hits 0 |
| Off-by-one in base case | `if (n < 0)` vs `if (n <= 0)` can produce wildly different results |
| Not returning the recursive call result | `binarySearch(arr, t, mid+1, high);` without `return` loses the answer |
| Modifying input incorrectly | Passing wrong updated parameter (e.g., `mid` instead of `mid+1`) in binary search |
| Assuming recursion order (confusing with iteration) | Statements after the recursive call execute in reverse call order |
| Fibonacci exponential slowness | Computing `fib(40)` iteratively takes microseconds; recursively takes seconds |

---
---

# Master Reference Sheet

## Quick Comparison Tables

### Complexity at a Glance

| Algorithm | Best | Worst | Notes |
|---|---|---|---|
| Linear Search | $O(1)$ | $O(n)$ | Unsorted OK |
| Binary Search | $O(1)$ | $O(\log n)$ | Must be sorted |
| Selection Sort | $O(n^2)$ | $O(n^2)$ | Always $n^2$ comparisons |
| Insertion Sort | $O(n)$ | $O(n^2)$ | Best when nearly sorted |

### `==` vs `.equals()` Decision Tree

```
Comparing primitives?
  → YES: use ==
  → NO: Comparing objects?
        → Strings, Integers, custom objects → use .equals()
        → Checking if reference is null    → use ==
```

### The Most Commonly Lost AP Points

1. **`str.substring(a, b)` — end index is exclusive.** `"hello".substring(1,3)` → `"el"`
2. **Integer division.** `7/2` → `3`, not `3.5`. Cast first: `(double)7/2`
3. **Array `length` vs ArrayList `size()`.** No parentheses for arrays.
4. **`ConcurrentModificationException`.** Never remove from a collection inside an enhanced for loop.
5. **`super()` must be the first line** in a subclass constructor.
6. **Off-by-one in loops.** Loop until `< arr.length`, not `<= arr.length`.
7. **String immutability.** Always capture the result of String methods.
8. **Recursion missing `return`.** `return binarySearch(...)`, not just `binarySearch(...)`.
9. **2D array: `grid.length` = rows, `grid[0].length` = cols.** Swapping these is catastrophic.
10. **`Math.random()` range.** `(int)(Math.random() * n)` gives `[0, n-1]`. Add 1 for dice rolls.

---
