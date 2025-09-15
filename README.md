# LEETCODE-Strings-1935
---

### Code Summary

* `check(String word, boolean[] broken)`
  → Returns `0` if the word contains a broken letter, else returns `1`.

* `canBeTypedWords(String text, String brokenLetters)`
  → Splits the text into words, uses `check()` for each, and counts how many words can be typed without broken letters.

---

### Example Dry Run

Suppose:

```java
text = "hello world code"
brokenLetters = "ad"
```

---

#### Step 1: Build `broken[]`

* `broken = new boolean[26]` → all `false` initially.
* For each `ch` in `brokenLetters`:

  * `'a'`: `broken['a'-'a'] = broken[0] = true`
  * `'d'`: `broken['d'-'a'] = broken[3] = true`

So:

```
broken[0] = true  // 'a' is broken
broken[3] = true  // 'd' is broken
others = false
```

---

#### Step 2: Split `text`

`text.split(" ") → ["hello", "world", "code"]`

---

#### Step 3: Process Each Word

1. **word = "hello"**

   * check("hello", broken):

     * 'h' → not broken
     * 'e' → not broken
     * 'l' → not broken
     * 'o' → not broken
       → returns `1`
       → `ans = 1`

2. **word = "world"**

   * check("world", broken):

     * 'w' → not broken
     * 'o' → not broken
     * 'r' → not broken
     * 'l' → not broken
     * 'd' → **broken\[3] = true → return 0**
       → `ans = 1`

3. **word = "code"**

   * check("code", broken):

     * 'c' → not broken
     * 'o' → not broken
     * 'd' → broken\[3] = true → return 0
       → `ans = 1`

---

#### Step 4: Final Answer

`ans = 1`

So only **"hello"** can be typed fully without using broken letters.

---

👉 Output:

```java
canBeTypedWords("hello world code", "ad") → 1
```

---
