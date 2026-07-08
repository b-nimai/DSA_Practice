# 🧠 DSA Pattern-Based Practice Roadmap (C++)

> **Part of the 6-month switch plan.** Sibling roadmaps:
> - 🧩 **LLD:** [`lld-roadmap.md`](./lld-roadmap.md) — 10 concept sections + 11 problems
> - 🚀 **Project + 📨 Apply:** [`project-roadmap.md`](./project-roadmap.md) — Loom-lite AI in 12 weeks + apply phase
> - 📅 **Daily execution:** [`daily-tracker.md`](./daily-tracker.md) — day-by-day integrated tasks across all tracks
> - Project build details: [`PROJECT_PLAN.md`](./PROJECT_PLAN.md) · LLD curriculum source: [`lld_content_index.md`](./lld_content_index.md)
>
> **DSA goal:** recognize the pattern behind any new problem within 60 seconds, then implement. ~200 problems → ~6 months. Mornings 6:30–8:30.

---

## How to use this roadmap

1. **Pick today's problem** from the next unchecked row in the current pattern.
2. **Read the title only** — try to predict the pattern from the title before reading the problem.
3. **Solve in C++** in `solutions/<pattern>/<slug>.cpp`. Aim for an optimal solution.
4. **Before checking your answer**, write your own one-line **trigger phrase** in the table (e.g., *"sorted array → find pair"*). This is what locks in pattern recognition.
5. **Mark the checkbox** (`☐` → `✅`) and fill the **Date**.
6. **Weekly (Sunday)**: redo 1 random problem from the past week without looking at your old code.
7. **After all 20 patterns**: jump to **Mixed Practice** at the bottom — predict the pattern *before* expanding the answer.

Legend: 🟢 Easy · 🟡 Medium · 🔴 Hard

---

## 🧭 Pattern Recognition Cheat Sheet

| If the problem says / has…                                              | Reach for…                          |
| ----------------------------------------------------------------------- | ----------------------------------- |
| Sorted array, pair/triplet, in-place                                    | **Two Pointers**                    |
| Longest/shortest/min/max **substring or subarray** with a constraint    | **Sliding Window**                  |
| Linked list cycle, middle, kth from end                                 | **Fast & Slow Pointers**            |
| "Subarray sum equals K", range sum, count of subarrays                  | **Prefix Sum + Hashing**            |
| Sorted input, OR "minimum/maximum value such that…"                     | **Binary Search** (incl. on answer) |
| Next greater/smaller, valid parentheses, histogram, span                | **Stack / Monotonic Stack**         |
| Reverse, merge, reorder a linked list                                   | **Linked List Manipulation**        |
| Path/sum/diameter in a tree, recursion returns info up                  | **Tree DFS**                        |
| Level-by-level, shortest path in tree/unweighted graph                  | **Tree/Graph BFS**                  |
| Connected components, islands, course schedule, dependencies            | **Graph BFS/DFS / Topo Sort**       |
| "Top K", "K closest", "K largest", median of stream                     | **Heap / Two Heaps**                |
| All permutations / combinations / subsets / paths                       | **Backtracking**                    |
| Intervals (merge/insert), "minimum number of …" with sorting            | **Greedy / Intervals**              |
| "Number of ways", "max profit", choose/skip — 1 dimension               | **DP — 1D**                         |
| Edit distance, LCS, grid paths, palindromes, two strings                | **DP — 2D**                         |
| Prefix lookup / autocomplete / dynamic connectivity                     | **Trie / Union-Find**               |
| Weighted shortest path, "cheapest", connect-all-cost                    | **Weighted Graphs (Dijkstra/MST)**  |
| "Appears once", count bits, add without `+`, power-of-two               | **Bit Manipulation**                |
| Rotate / spiral / set-zeroes a 2-D grid in place                        | **Matrix Simulation**               |
| Implement a class: LRU/LFU cache, O(1) insert/delete/random             | **Design**                          |
| Pow / sqrt / atoi / Roman, digit-cycle, overflow-careful parsing        | **Math / String**                   |

---

# 1. Two Pointers

**When to use it (recognition cues):**
- Input is **sorted** (or can be sorted) and you need a pair/triplet.
- Working from both ends of an array/string toward the middle.
- In-place removal/modification of an array.

**Core idea:** Two indices move toward each other (or in same direction) based on a comparison, reducing O(n²) brute force to O(n).

**Template (C++):**
```cpp
int l = 0, r = nums.size() - 1;
while (l < r) {
    int sum = nums[l] + nums[r];
    if (sum == target) return {l, r};
    else if (sum < target) ++l;
    else --r;
}
```

**Problems:**

| ✓ | Date | # | Problem | Diff | Trigger phrase |
|---|------|---|---------|------|----------------|
| ✅ | 07/05/26 | 167 | [Two Sum II – Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/) | 🟡 | Sorted array, need to find pair |
| ✅ | 07/05/26 | 125 | [Valid Palindrome](https://leetcode.com/problems/valid-palindrome/) | 🟢 | Needs to compare both end of the String |
| ✅ | 07/05/26 | 26  | [Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/) | 🟢 | In-place dedup on sorted; write lags read |
| ✅ | 07/05/26 | 283 | [Move Zeroes](https://leetcode.com/problems/move-zeroes/) | 🟢 | Move target value to end; slow/fast partition |
| ✅ | 07/05/26 | 11  | [Container With Most Water](https://leetcode.com/problems/container-with-most-water/) | 🟡 | Max area between two lines; move shorter wall |
| ✅ | 09/05/26 | 15  | [3Sum](https://leetcode.com/problems/3sum/) | 🟡 | Sort + fix i + inner 2-ptr; skip dups |
| ✅ | 12/05/26 | 16  | [3Sum Closest](https://leetcode.com/problems/3sum-closest/) | 🟡 | Triplet sum closest to target; sort + 2-ptr, track best, move by sum vs target |
| ✅ | 12/05/26 | 18  | [4Sum](https://leetcode.com/problems/4sum/) | 🟡 | Unique quadruplets = target; fix i,j + inner 2-ptr; skip dups ×4; long long sum |
| ✅ | 09/05/26 | 75  | [Sort Colors](https://leetcode.com/problems/sort-colors/) | 🟡 | Sort 3 distinct values; Dutch flag lo/mid/hi |
| ✅ | 09/05/26 | 633 | [Sum of Square Numbers](https://leetcode.com/problems/sum-of-square-numbers/) | 🟡 | a²+b²=c; range 2-ptr on [0, √c] |
| ✅ | 09/05/26 | 680 | [Valid Palindrome II](https://leetcode.com/problems/valid-palindrome-ii/) | 🟢 | Palindrome with ≤1 deletion; on mismatch try both |
| ✅ | 09/05/26 | 42  | [Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/) | 🔴 | Water on elevation map; l/r + lMax/rMax |

---

# 2. Sliding Window

**When to use it (recognition cues):**
- Asking for **longest / shortest / max / min** subarray or substring satisfying some condition.
- Contiguous range and the brute force is "try every window".
- "At most K", "exactly K", "no repeating", "frequency".

**Core idea:** Maintain a window `[l, r]`; expand `r`, shrink `l` while invariant breaks.

**Template (C++):**
```cpp
int l = 0, best = 0;
unordered_map<char,int> freq;
for (int r = 0; r < s.size(); ++r) {
    freq[s[r]]++;
    while (/* window invalid */) { freq[s[l]]--; ++l; }
    best = max(best, r - l + 1);
}
```

**Problems:**

| ✓ | Date | # | Problem | Diff | Trigger phrase |
|---|------|---|---------|------|----------------|
| ✅ | 13/05/26 | 643 | [Maximum Average Subarray I](https://leetcode.com/problems/maximum-average-subarray-i/) | 🟢 | "subarray of length exactly k" → fixed window; slide, track max sum, divide once |
| ✅ | 13/05/26 | 209 | [Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/) | 🟡 | shortest subarray with sum ≥ target (positives) → grow right / shrink left while valid |
| ✅ | 13/05/26 | 3   | [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/) | 🟡 | longest substring with no duplicates → grow right / shrink left while `cnt[s[r]] > 1` |
| ✅ | 14/05/26 | 424 | [Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/) | 🟡 | longest substring of one letter with ≤ k replacements → window valid iff `len - maxFreq ≤ k`; `if`-shrink (window grows by 1/step), don't recompute `maxFreq` on shrink |
| ✅ | 16/05/26 | 567 | [Permutation in String](https://leetcode.com/problems/permutation-in-string/) | 🟡 | "s2 contains a permutation/anagram of s1" → fixed window width `s1.len`; compare letter freqs, or 1 array + `found` counter (add `>0`, remove `>=0`) for O(1)/step |
| ✅ | 16/05/26 | 438 | [Find All Anagrams in a String](https://leetcode.com/problems/find-all-anagrams-in-a-string/) | 🟡 | SubString with same characters count as `s1` → fixed window | 
| ✅ | 16/05/26 | 1004| [Max Consecutive Ones III](https://leetcode.com/problems/max-consecutive-ones-iii/) | 🟡 | "longest run of 1's, flip ≤ k 0's" → same template as 424: window valid while `#zeros ≤ k`; grow `right`, slide `left` over budget. `while`-shrink+`maxi` or `if`-slide + return `n-left` |
| ✅ | 17/05/26 | 904 | [Fruit Into Baskets](https://leetcode.com/problems/fruit-into-baskets/) | 🟡 | I have to find subarray |
| ✅ | 17/05/26 | 1456| [Maximum Number of Vowels in a Substring of Given Length](https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/) | 🟡 | fixed size substring |
| ✅ | 18/05/26 | 992 | [Subarrays with K Different Integers](https://leetcode.com/problems/subarrays-with-k-different-integers/) | 🔴 | "count subarrays with exactly K distinct" → no monotone window for "exactly K"; `exactly K = atMost(K) − atMost(K−1)`. `atMostK`: count-window `+= right-left+1`, `k`-as-budget (no erase) |
| ✅ | 18/05/26 | 76  | [Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/) | 🔴 | "shortest substring of `s` covering all of `t` with duplicates" → variable window, grow `right` / shrink `left` while valid; O(1) validity via `formed == required` counter (bump only when `window[c] == need[c]`), never `map.empty()` |
| ✅ | 19/05/26 | 239 | [Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/) | 🔴 | "max of every fixed-size-`k` window" → max isn't `+in/-out` decomposable → **monotonic deque of indices** (values decreasing front→back); expire front by index `<= i-k`, pop back while `nums[back] <= nums[i]`, emit `nums[front]` once `i >= k-1`. Each index pushed/popped once → O(n) |

---

# 3. Fast & Slow Pointers (Floyd's)

**When to use it (recognition cues):**
- Linked list cycle / cycle entry / length.
- Finding middle, kth-from-end of a linked list in one pass.
- "Happy number" / cycle in a function iteration.

**Core idea:** `slow` moves 1 step, `fast` 2 steps. They meet iff a cycle exists.

**Template (C++):**
```cpp
ListNode *slow = head, *fast = head;
while (fast && fast->next) {
    slow = slow->next;
    fast = fast->next->next;
    if (slow == fast) break;
}
```

**Problems:**

| ✓ | Date | # | Problem | Diff | Trigger phrase |
|---|------|---|---------|------|----------------|
| ✅ | 20/05/26 | 141 | [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/) | 🟢 | "does linked list contain a cycle?" → Floyd's: `slow+=1`/`fast+=2` from head, meet ⇒ cycle, `fast` hits null ⇒ none. O(1) space vs hash-set's O(n) |
| ✅ | 20/05/26 | 142 | [Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/) | 🟡 | "return the node where the cycle begins" → Floyd's phase 1 (detect) + phase 2 (reset one pointer to head, walk both at speed 1 — collide at entry). `a ≡ L-b (mod L)` |
| ✅ | 20/05/26 | 876 | [Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/) | 🟢 | "return the middle node, one pass" → `slow+=1`/`fast+=2` from head; when `fast` falls off, `slow` is middle. Returns 2nd middle on even; for 1st middle start `fast = head->next` |
| ✅ | 22/05/26 | 234 | [Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/) | 🟢 | "is singly linked list a palindrome in O(1) space" → can't walk backwards: find midpoint (slow/fast, guard `fast->next && fast->next->next`), reverse second half `slow->next` in place, compare front-to-back, then reverse back to restore. Loop on shorter half (`while right`) |
| ✅ | 22/05/26 | 202 | [Happy Number](https://leetcode.com/problems/happy-number/) | 🟢 | "repeat digit-square-sum until 1 or loops forever" → it's Floyd's on `x → f(x)`, NOT a list: the sequence is eventually periodic so an endless loop is a cycle. `do { slow=f(slow); fast=f(f(fast)); } while(slow != fast); return slow==1`. Met at 1 ⇒ happy, else non-1 cycle. O(1) space vs hash-set's O(n) |
| ✅ | 22/05/26 | 19  | [Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/) | 🟡 | "remove the n-th node from the end, one pass" → fixed-gap two pointers: pre-advance `fast` by `n`, walk both till `fast` hits end ⇒ `slow` on predecessor. Use a **dummy → head** with gap `n+1` so head-removal needs no special case; `slow->next = slow->next->next`, return `dummy.next` |
| ✅ | 23/05/26 | 143 | [Reorder List](https://leetcode.com/problems/reorder-list/) | 🟡 | "reorder to `L0→Ln→L1→Ln-1→…` in O(1) space, nodes not values" → 3-step combo: find middle (slow/fast, `fast=head->next` so first half is the longer/equal one), cut, **reverse** second half, then **interleave-merge** the two — save both `next`s before rewiring each pair; loop on shorter list (`while start2`) |
| ✅ | 24/05/26 | 287 | [Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/) | 🟡 | "`n+1` ints in `[1,n]`, one repeats, find it without modifying array, O(1) space" → read array as function `f(x)=nums[x]` (not a list!); pigeonhole ⇒ cycle, **entrance = duplicate**. Floyd's phase 1 (`do/while`) + phase 2 (reset to `nums[0]`, walk both 1×). O(n)/O(1) |
| ✅ | 25/05/26 | 457 | [Circular Array Loop](https://leetcode.com/problems/circular-array-loop/) | 🟡 | "circular array, each value = signed jump length, find a cycle that's all one direction and length > 1" → Floyd's on `next(i)=((i+nums[i])%n+n)%n`, but add two guards: reject a **sign flip** (`nums[a]*nums[next(a)] ≤ 0` ⇒ crossed forward/backward) and a **self-loop** (`next(i)==i` ⇒ k=1). `fast` hops twice so validate both hops; mark dead paths `0` for O(n)/O(1) |
| ✅ | 24/05/26 | 2095| [Delete the Middle Node of a Linked List](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/) | 🟡 | "delete the middle node (`⌊n/2⌋`, 0-indexed), return head" → find-middle slow/fast but stop on the **predecessor** to unlink: carry `prev` behind `slow`, or pre-offset `fast=head->next->next` so `slow` halts one early; `prev->next=slow->next; delete slow`. Guard single-node (`!head->next ⇒ nullptr`) |

---

# 4. Prefix Sum & Hashing

**When to use it (recognition cues):**
- "Subarray sum equals K" / "count of subarrays with property X".
- Range sum / range XOR queries.
- Need O(1) lookup of "have I seen this complement before?".

**Core idea:** `prefix[i]` = aggregate up to `i`. Then `range(l..r) = prefix[r] - prefix[l-1]`. Combine with a hashmap of seen prefix values.

**Template (C++):**
```cpp
unordered_map<int,int> cnt{{0, 1}};
int sum = 0, ans = 0;
for (int x : nums) {
    sum += x;
    ans += cnt[sum - k];
    cnt[sum]++;
}
```

**Problems:**

| ✓ | Date | # | Problem | Diff | Trigger phrase |
|---|------|---|---------|------|----------------|
| ✅ | 26/05/26 | 1   | [Two Sum](https://leetcode.com/problems/two-sum/) | 🟢 | "two indices summing to target, can't reuse element" → one-pass hash map `value→index`; for each `nums[i]` look up complement `target-nums[i]` **before** inserting, so duplicates like `[3,3]` don't self-pair |
| ✅ | 26/05/26 | 303 | [Range Sum Query – Immutable](https://leetcode.com/problems/range-sum-query-immutable/) | 🟢 | "many `sumRange(l, r)` on immutable array" → precompute `ps` of size `n+1` with `ps[0]=0`; query is `ps[r+1] - ps[l]` in O(1). `n+1` shift kills the `l==0` edge case. Prefer `vector` over `unordered_map` for dense integer keys |
| ✅ | 27/05/26 | 304 | [Range Sum Query 2D – Immutable](https://leetcode.com/problems/range-sum-query-2d-immutable/) | 🟡 | "many `sumRegion(r1,c1,r2,c2)` on immutable matrix" → 2D prefix sum sized `(m+1)×(n+1)` with zero border; build and query are the same `+ − − +` inclusion–exclusion over four top-left rectangles. O(m·n) build / O(1) query |
| ✅ | 27/05/26 | 560 | [Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/) | 🟡 | "**count** subarrays with sum = K, negatives allowed" → running prefix sum + frequency map of past prefixes; `count += cnt[sum − k]` then `cnt[sum]++`. Seed `cnt[0]=1` for empty prefix, lookup before insert so an element can't self-pair when `k=0`. Two-pointer only works if `nums[i] > 0` (or `≥ 0` via `atMost(k) − atMost(k−1)`) |
| ✅ | 28/05/26 | 974 | [Subarray Sums Divisible by K](https://leetcode.com/problems/subarray-sums-divisible-by-k/) | 🟡 | "**count** subarrays with sum divisible by K, negatives allowed" → modular twin of 560: bucket prefixes by `rem = ((sum%k)+k)%k`, `count += freq[rem]++`. Seed `freq[0]=1`. Use `vector<int>(k)` over `unordered_map` (remainders dense in `[0,k-1]`); **normalize C++ negative `%`** or equivalent prefixes land in different buckets |
| ✅ | 29/05/26 | 523 | [Continuous Subarray Sum](https://leetcode.com/problems/continuous-subarray-sum/) | 🟡 | "**exists** subarray (len ≥ 2) with sum divisible by k" → equal prefix remainders bracket a sum ÷ k; map `rem → earliest index`, return true when `i − firstIdx ≥ 2`. Store **only the first** index per remainder (don't overwrite — gap must grow), seed `{0, -1}` to drop the `rem==0` special case. Earliest-index = exists/longest; frequency-count = "count" twin (560/974) |
| ✅ | 29/05/26 | 525 | [Contiguous Array](https://leetcode.com/problems/contiguous-array/) | 🟡 | "**longest** subarray with **equal #0s and #1s**" → recode `0 → −1`, `1 → +1` so equal counts = the running **balance repeats** (segment sums to 0); store `balance → earliest index`, seed `{0,-1}`, on a repeat `res = max(res, i − firstIdx)`. **Insert only on first sight** (longest needs earliest index). Longest twin of 523; generalizes to "longest subarray with sum k" via `cnt[sum−k]` |
| ✅ | 31/05/26 | 1248| [Count Number of Nice Subarrays](https://leetcode.com/problems/count-number-of-nice-subarrays/) | 🟡 | "**count** subarrays with **exactly k odd numbers**" → recode `odd→1, even→0` and it's literally 560 on parities: running `odds`, `res += cnt[odds − k]` then `cnt[odds]++`, seed `cnt[0]=1`. Either seed the sentinel **or** special-case `if(odds==k) res++` — exactly one. All-positive recode also enables window `atMost(k) − atMost(k−1)` in O(1) space |
| ✅ | 31/05/26 | 437 | [Path Sum III](https://leetcode.com/problems/path-sum-iii/) | 🟡 | "**count** downward tree paths summing to `target`, start/end anywhere" → 560 lifted onto root→node paths: DFS carrying `sum` + prefix-freq map; `count += freq[sum − target]`, `freq[sum]++`, then **`freq[sum]--` (erase on 0) on backtrack** so sibling subtrees stay isolated. Seed `freq[0]=1`. Two traps: **`long long` sum** (path ≈ 1e12 overflows int → phantom paths) and **frequency map not a set** (count occurrences, else `[0,1,1]` undercounts); use `find` not `[]` |
| ✅ | 01/06/26 | 49  | [Group Anagrams](https://leetcode.com/problems/group-anagrams/) | 🟡 | "**group strings equivalent under rearrangement**" → bucket by a **canonical key** in `unordered_map<sig, group>`; each word's **26-letter count signature** is invariant across anagrams. `mpp[key].push_back(word)`, return the values. Count key is **O(N·K)**, beats the sorted-string key's O(N·K log K); fixed-width raw-byte signature needs no `#` separator |
| ✅ | 01/06/26 | 128 | [Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/) | 🟡 | "**longest run of consecutive integers**, unsorted, must be **O(n)**" → sorting is the O(n log n) trap; dump all into `unordered_set`, then walk a run **only from its head** (`x-1` absent ⇒ start), counting `x+1, x+2, …`. Head-only guard keeps the nested walk O(n) not O(n²). Pure-membership cousin of Two Sum — "is `x±1` present?" not a complement |
| ☐ |      | 1590| [Make Sum Divisible by P](https://leetcode.com/problems/make-sum-divisible-by-p/) | 🟡 |  |

---

# 5. Binary Search (classic + on answer)

**When to use it (recognition cues):**
- Sorted input → log(n).
- Monotonic predicate: "smallest/largest X such that f(X) is true".
- "Minimize the maximum" / "maximize the minimum".

**Core idea:** Halve the search space using a monotonic check.

**Template (C++):**
```cpp
int l = lo, r = hi;
while (l < r) {
    int m = l + (r - l) / 2;
    if (check(m)) r = m;
    else l = m + 1;
}
return l;
```

**Problems:**

| ✓ | Date | # | Problem | Diff | Trigger phrase |
|---|------|---|---------|------|----------------|
| ✅ | 02/06/26 | 704 | [Binary Search](https://leetcode.com/problems/binary-search/) | 🟢 | "**sorted** array → exact index of `target` in **O(log n)**" → closed interval `[low, high]`, loop `while (low <= high)`; `mid = low + (high-low)/2` (overflow-safe); `==`→return `mid`, `>`→`high = mid-1`, `<`→`low = mid+1`. Return `-1` after the loop. `mid ± 1` (never `mid`) makes the window strictly shrink; `<=` (not `<`) so the size-1 window is still checked. The exact-match seed of the whole pattern |
| ✅ | 02/06/26 | 35  | [Search Insert Position](https://leetcode.com/problems/search-insert-position/) | 🟢 | "sorted distinct → index of `target`, **or where it'd be inserted**" → it's the 704 loop with `return -1` swapped for **`return low`** (the insertion point = #elements `< target`). Or the pure **lower-bound** template: `high = n`, `while (low < high)`, `nums[mid] < target ? low = mid+1 : high = mid`, return `low`. This is the reusable seed for "min X such that check(X)" / binary-search-on-answer. Watch: don't return `-1`; lower-bound's `high` is `n` not `n-1`, and pairs `high = mid` (no `-1`) with `low < high` |
| ✅ | 03/06/26 | 278 | [First Bad Version](https://leetcode.com/problems/first-bad-version/) | 🟢 | "versions `1..n`, once one is bad **all later ones are bad** → first bad version in the **fewest API calls**" → the bad flags form `F…F T…T`, so binary-search the **leftmost `T`**. It's the lower-bound loop from 35 with the predicate swapped from a value compare to an **API call**: `low = 1, high = n`, `while (low < high)`, `mid = low + (high-low)/2`; `isBadVersion(mid)` → `high = mid` (keep — mid may be first bad), else `low = mid + 1`; return `low`. First "binary-search-on-a-**predicate**", not on array values. Watch: `n` up to `INT_MAX` makes overflow-safe `mid` mandatory; `high = mid` (no `-1`) pairs with `low < high`; call the API once per loop |
| ✅ | 03/06/26 | 33  | [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/) | 🟡 | "ascending **distinct** array **rotated** at an unknown pivot → index of `target` in **O(log n)**" → it's the 704 closed-interval loop (`low=0, high=n-1`, `while (low <= high)`, overflow-safe `mid`) with one extra decision: the array isn't globally sorted, but **at least one half always is**. Test `nums[low] <= nums[mid]` (`<=`, for the `low==mid` case) → left half sorted: if `nums[low] <= target < nums[mid]` go left (`high=mid-1`) else right (`low=mid+1`); otherwise right half sorted: if `nums[mid] < target <= nums[high]` go right else left. Hit (`nums[mid]==target`) checked first; endpoint comparisons inclusive, `mid` side exclusive. Watch: strict `nums[low] < nums[mid]` breaks size-1 windows; only range-check against the half you've **proven** sorted; relies on distinct values (dups → LC 81, O(n) worst case) |
| ✅ | 04/06/26 | 153 | [Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/) | 🟡 | "ascending **distinct** array **rotated** at an unknown pivot → return the **minimum** in **O(log n)**" → the min *is* the rotation pivot, so binary-search for it. Half-open window `low=0, high=n-1`, `while (low < high)`, overflow-safe `mid`; compare `nums[mid]` to **`nums[high]`** (not `nums[low]` — that's always `<= nums[mid]` on a sorted array, tells you nothing): `nums[mid] > nums[high]` → dip is strictly right (`low = mid+1`), else pivot is at `mid` or left so keep it (`high = mid`, **no `-1`** — `mid` is a live candidate). `low == high` lands on the min → `return nums[low]`. Watch: `high = mid` pairs with `low < high` (closed loop + `mid-1` can skip the answer); relies on distinct values (dups → LC 154, `high--` on tie, O(n) worst). Alt: compare to `nums[low]` but then you need an explicit `mini` tracker + closed `low <= high` loop |
| ✅ | 04/06/26 | 34  | [Find First and Last Position of Element](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/) | 🟡 | "sorted array **with duplicates** → the **first and last index** of `target`, else `[-1,-1]`, in **O(log n)**" → run the 704 loop **twice** with an `index = -1` sentinel; the trick is to **not stop on a hit**. First pass (lower bound): on `nums[mid] == target` save `index = mid` then `high = mid-1` (keep probing left); else `>` → `high = mid-1`, `<` → `low = mid+1`. Second pass (upper bound): identical but on a hit `low = mid+1` (probe right). The **tie-break direction on `==` is the only difference**. Return `{lower, upper}`. Watch: empty array makes `n = size()-1 = -1`, and `low <= high` (`0 <= -1`) no-ops the loop so you never touch `nums[-1]`; absent target falls out as `[-1,-1]` from both passes; a one-hit-then-linear-expand approach is O(n) on all-equal arrays (violates log n) | 
| ✅ | 05/06/26 | 162 | [Find Peak Element](https://leetcode.com/problems/find-peak-element/) | 🟡 | "find **any** peak (`> both neighbors`) in **O(log n)** on an array that's **not sorted**, `nums[i] != nums[i+1]`" → can't binary-search a value with no sorted order, so binary-search the **slope**: half-open `low=0, high=n-1`, `while (low < high)`, overflow-safe `mid`; compare `nums[mid]` to **`nums[mid+1]`** — `>` ⇒ falling, peak at `mid` or left (`high = mid`, **no `-1`**, `mid` is a live candidate), else rising ⇒ peak strictly right (`low = mid+1`); `low == high` lands on a peak → `return low`. The imaginary `-∞` walls at both ends make a peak **unavoidable** (walking uphill must hit one), so there's no "not found" case and any peak is accepted. `mid+1` is always in range because `low < high` ⇒ `mid < high`. The single right-neighbor test subsumes all the `mid==0` / `mid+1==n` / `n==1` / `n==2` edge cases of the check-both-neighbors version. Same `high=mid`/`low=mid+1` mechanics as 153 but the signal is the **local slope**, not a global pivot — that's why it works with zero sorted structure |
| ✅ | 06/06/26 | 74  | [Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/) | 🟡 | "`m x n` matrix, **each row sorted** AND **first of each row > last of the previous row** → is `target` present in **O(log(m·n))**" → the two properties together make the row-major read **one globally sorted array of length `m*n`**, so it's plain 704 over an imaginary 1D array. Closed window `low=0, high=rows*cols-1`, `while (low <= high)`, overflow-safe `mid`; decode the flat index to a cell with `value = matrix[mid / cols][mid % cols]` — **divide & mod by the number of COLUMNS (= row length), never the rows** — then standard `==`→`true`, `>`→`high=mid-1`, `<`→`low=mid+1`, fall out → `false`. The *only* new idea vs 704 is the index↔(row,col) arithmetic. Watch: divmod by the **row count** instead of cols silently goes out-of-bounds whenever `cols > rows` (e.g. `[[1,1]], target=2` → reads non-existent `matrix[1][0]`) and only "works" by luck on square/tall grids — name the vars `rows`/`cols` so the divisor is obviously the row length; pair `<=` with `high=mid-1` (exact-match, not the half-open `high=mid`). **Don't confuse with LC 240** (rows and columns each sorted *independently*, not globally) — that one can't be flattened and needs the top-right staircase walk in O(m+n) |
| ✅ | 06/06/26 | 875 | [Koko Eating Bananas](https://leetcode.com/problems/koko-eating-bananas/) | 🟡 | "**minimum integer speed `k`** so Koko clears all piles in `≤ h` hours, where a pile of `p` takes `ceil(p/k)` hours" → there's **no array to search** — binary-search the **answer itself**. The cost `hours(k) = Σ ceil(piles[i]/k)` is **monotonically non-increasing in `k`**, so feasibility (`hours ≤ h`) flips false→true exactly once → lower-bound the first feasible speed. Range `[1, max(piles)]` (`low = 1` — speed 0 is meaningless **and divides by zero**; `high = max(piles)` is tight since at that speed every pile is 1 hr, total `= n ≤ h`, always feasible). Predicate `canFinish(k)`: sum `(p + k - 1) / k` (integer ceil, no floats), **early-`return false` once the running sum > h** (also caps it). Loop: half-open `while (low < high)`, on feasible `high = mid` (keep mid — no `-1`), else `low = mid + 1`, return `low`. Watch: **`long` accumulator** — `n·ceil` reaches ~10¹³, overflows `int`; the predicate must encode "fast enough" (`hours ≤ h`) not "too slow" (`hours >= h`) or the search runs the wrong direction and returns the max speed; closed `<=` pairs with `high = mid-1`, half-open `<` with `high = mid` — never mix. The **binary-search-on-answer** archetype (same lower-bound shape as 35/278 but the predicate is a *computed cost*, not an array compare or API) — siblings 1011, 410 |
| ✅ | 06/07/26 | 1011| [Capacity to Ship Packages Within D Days](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/) | 🟡 | "**minimum ship capacity** so packages shipped **in order** (no reordering/splitting) fit within `days` days, where each day greedily loads consecutive packages up to the capacity" → **binary-search the answer**, not an array. Range `[max(weights), sum(weights)]` — `lo = max` because a capacity below the heaviest package can never carry it; `hi = sum` is everything in one day. Predicate `possible(cap)`: walk left→right with a running `load`, start `reqDay = 1` (first day already in progress), and when `load + w > cap` **close the day** (`reqDay++`, `load = 0`) before adding `w` — **`load += w`, never `load = w`** (overwriting undercounts days and returns a too-small answer). Early-`return false` once `reqDay > days`. Days-needed is **monotonically non-increasing in cap**, so feasibility flips false→true once → lower-bound it: closed `while (lo <= hi)`, on feasible `hi = mid - 1`, else `lo = mid + 1`, return `lo`. Watch: it's a **sequential greedy fill**, not per-item `ceil` (that's the split-allowed model — wrong here); closed `<=` pairs with `hi = mid-1`, half-open `<` with `hi = mid` — never mix; kill stray `cout`s (corrupt stdout → WA). Koko 875's twin — same lower-bound-on-answer shape, cost is a partition instead of a per-item ceil; sibling 410 |
| ✅ | 06/08/26 | 410 | [Split Array Largest Sum](https://leetcode.com/problems/split-array-largest-sum/) | 🔴 | "**split `nums` into `k` contiguous subarrays so the largest subarray sum is minimized**" → the **"minimize the maximum"** phrasing is the binary-search-on-answer tell. Flip it: *given a cap `S`, can we split into ≤ k pieces each ≤ S?* Pieces-needed is **monotonically non-increasing in `S`**, so feasibility flips false→true once → lower-bound the smallest feasible cap. Range `[max(nums), sum(nums)]` — `lo = max` (a piece must hold the biggest element alone; this also guarantees every `num ≤ mid` so the greedy never stalls), `hi = sum` (whole array as one piece). Predicate `possible(S)`: walk left→right, `count = 1` (first piece already open), on `sum + num > S` **cut** (`count++`, `sum = 0`) then `sum += num` (**`+=` not `=`**), early-`return false` once `count > k`. "≤ k" ≡ "== k" here because a coarser split can always be cut further (since `k ≤ n`) without raising any sum. Closed `while (lo <= hi)`, on feasible `hi = mid - 1`, else `lo = mid + 1`, return `lo`. Watch: `count = 1` not 0 (the `++` counts only cuts); `lo = max(nums)` not 0/1; sequential greedy fill, **not** per-item `ceil`; overflow is fine here (`sum ≤ 10⁹` fits `int`) but use `long`/`sum > S - num` if limits grow. **Literally [[10-1011-capacity-to-ship-packages]] with `days → k`** — same code, same `[max, sum]` range; both are Koko 875's descendants. (DP `dp[i][j]` in O(n²k) also works — slower, use if you need the partition.) |
| ✅ | 06/08/26 | 4   | [Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays/) | 🔴 | "**median of two sorted arrays in O(log(m+n))**" → the `O(log)` bound kills the merge; **binary-search the partition**, not a value. Split the union into a left half of `(m+n+1)/2` elements (the `+1` parks the odd extra on the left → median = `max(left)`) and a right half with `max(left) ≤ min(right)`. Pick `cut1` from `nums1`; `cut2 = (m+n+1)/2 − cut1` is forced. **Binary-search `cut1 ∈ [0, n1]` over the SMALLER array** (swap if `n1>n2`, else `cut2` goes negative). Boundaries with sentinels: `l1=cut1>0?a[cut1-1]:INT_MIN`, `r1=cut1<n1?a[cut1]:INT_MAX`, and likewise `l2`/`r2` with `cut2` (INT_MIN/MAX make take-none/take-all legal partitions). Cross-check `l1≤r2 && l2≤r1`: valid → even `(max(l1,l2)+min(r1,r2))/2.0` (use `2.0`!), odd `max(l1,l2)`; `l1>r2` ⇒ `high=cut1-1`, else `low=cut1+1`. **#1 bug: never cross `mid1`/`mid2`** — every `nums1` access (index *and* guard) uses `mid1`, every `nums2` access uses `mid2`; `nums2[mid1-1]` or a `mid1<n2` guard reads `nums2[-1]`/`nums2[n2]` OOB. Unlike 875/410 (search a value-range) this searches *where to cut* and the answer falls out of the boundaries. Alt: two-pointer merge-to-middle O(m+n) if log isn't required | O(log(min(m,n))) | O(1) |

---

# 6. Stack & Monotonic Stack

**When to use it (recognition cues):**
- Matching pairs (parentheses, tags).
- "Next/previous greater/smaller element".
- Histogram / rectangles / stock span / temperatures.

**Core idea:** Push while increasing/decreasing; pop on violation. Each element pushed/popped once → O(n).

**Template (C++):**
```cpp
stack<int> st; // indices
vector<int> nge(n, -1);
for (int i = 0; i < n; ++i) {
    while (!st.empty() && nums[st.top()] < nums[i]) {
        nge[st.top()] = nums[i]; st.pop();
    }
    st.push(i);
}
```

**Problems:**

| ✓ | Date | # | Problem | Diff | Trigger phrase |
|---|------|---|---------|------|----------------|
| ✅ | 09/06/26 | 20  | [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/) | 🟢 | "are `()[]{}` balanced **and** correctly nested?" → LIFO: push openers, on a closer pop iff `top` is its matching opener (guard `!empty()` first — bare closer is UB), valid iff stack ends empty. Match the **type**, not just "closed something" (`"([)]"` must fail); leftover openers ⇒ false. Counter-only can't see order. Odd length ⇒ instant false |
| ✅ | 09/06/26 | 155 | [Min Stack](https://leetcode.com/problems/min-stack/) | 🟡 | "stack that also returns its **min in O(1)**" → can't recompute (O(n)); **store the running min beside each element** so it's always at the top. Pair-stack `{value, minAtOrBelow}` — push `min(v, top.second)`, pop frees the prior min automatically. O(1)-space variant encodes a sentinel `2v−mini` on a new min, decodes `2mini−x` on pop — but needs **64-bit everywhere** (`int x = top()` truncates the sentinel → fails on INT_MIN/MAX). Single-min-var can't restore the min after popping it |
| ✅ | 11/06/26 | 150 | [Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/) | 🟡 | "evaluate a **postfix / RPN** expression (no parens)" → operands wait on a stack, an operator consumes the **last two**. Push numbers; on `+ - * /` pop `b` (top = **right**), then `a` (left), push `a op b`. **Order matters** for `-` and `/` — swapping passes `+`/`*` but fails the rest. C++ `int/int` already truncates toward zero (free); don't classify by `s[0]=='-'` — `"-11"` is a negative number, compare the whole string. Final lone `top()` is the answer |
| ✅ | 11/06/26 | 739 | [Daily Temperatures](https://leetcode.com/problems/daily-temperatures/) | 🟡 | "days until a **strictly warmer** temp?" = **next greater element**, but return the **distance** not the value → **monotonic stack of indices**, temps decreasing. L→R: while `T[i] > T[st.top()]` pop `j`, set `res[j]=i-j`; push `i`; unresolved stay 0. Store **indices** (answer is a gap); **strict** warmer = mind the `<`/`<=` boundary (equal temp doesn't count). Each index pushed/popped once ⇒ O(n) |
| ✅ | 12/06/26 | 496 | [Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/) | 🟢 | "first **greater element to the right**, queried from a subset array" → precompute NGE for **all** of `nums2` in one monotonic-stack pass, store in a `value → answer` map (legal: values **unique**), answer each `nums1[i]` by O(1) lookup ⇒ O(n1+n2). R→L: pop while `top <= num` (an equal element is never anyone's *greater*), record `top` or `-1`, push `num`. Answer is a **value** → stack of values OK; with duplicates or distances, switch to indices |
| ✅ | 12/06/26 | 503 | [Next Greater Element II](https://leetcode.com/problems/next-greater-element-ii/) | 🟡 | "next greater element, but the array is **circular**" → same monotonic-stack template scanned **twice**: loop `i = 2n−1 … 0` on `nums[i % n]`, pop while `top <= num`, write `res[i]` **only when `i < n`** (first sweep just seeds wrap-around candidates), push every step ⇒ O(n), each element pushed/popped ≤ 2×. **Duplicates exist** → `<=` pop is load-bearing and answers go **by index** (496's value-map trick is illegal here). Max always gets −1 |
| ✅ | 13/06/26 | 901 | [Online Stock Span](https://leetcode.com/problems/online-stock-span/) | 🟡 | "prices stream in **one at a time**; for each, how many **consecutive days back** (incl. today) were `≤` today?" = distance to the **previous strictly-greater** price → **decreasing monotonic stack**, pop while `top ≤ price` (`≤`, since equal days *count*) **accumulating their spans** into today's. Start `span=1` (today). Editorial stores `{price, span}` (self-contained); index variant stores `{price, day}` and returns the gap `i - top.day`. **Online** = no peeking ahead, all work in `next`; previous-greater (mirror of 739's next-greater). O(1) amortized |
| ✅ | 13/06/26 | 71  | [Simplify Path](https://leetcode.com/problems/simplify-path/) | 🟡 | "canonicalize a Unix path — collapse `//`, drop `.`, `..` goes up a level" → **stack** of dir names: split on `/`, a real name **pushes**, `..` **pops** (iff non-empty — can't go above root, `/../`→`/`), `.`/empty **ignore**. `...`/`....`/`_` are **valid names** (match *exactly* `.`/`..`). Append a **sentinel `/`** so the last segment flushes in-loop (else the post-loop word re-introduces the `..`/`.` bug). Join front→back; empty ⇒ `"/"`. Use a **local** `vector` (not a member deque). O(n)/O(n) — optimal (must remember dirs for `..` to undo) |
| ✅ | 14/06/26 | 394 | [Decode String](https://leetcode.com/problems/decode-string/) | 🟡 | "expand `k[encoded]`, possibly **nested** (`3[a2[c]]`)" → **stack the context**: keep `current` string + `num`; digit → `num=num*10+(ch-'0')` (**multi-digit**); `[` → push `num` & `current` to two stacks, reset; `]` → pop `k` & `prev`, `current = prev + current*k`; letter → `current+=ch`. Two stacks (count + string) beats single-string stack (no `stoi`, no `[`-marker, **append** not prepend → no O(n²), no `to_string`/`isdigit(top)`/empty-`stoi` traps). Innermost-first = LIFO = recursion made explicit | O(N_out) | O(N_out) |
| ✅ | 15/06/26 | 22  | [Generate Parentheses](https://leetcode.com/problems/generate-parentheses/) | 🟡 | "generate **all** well-formed combinations of `n` pairs" → backtracking DFS, **not** generate-then-filter. Carry `open`/`close` = parens **remaining**; **add `(` when `open > 0`**, **add `)` when `close > open`** (unmatched `(` in string = `close − open`, must be `> 0`). Both 0 ⇒ push (no validity check needed — guards guarantee it). Append → recurse → `pop_back()` to backtrack the shared `string&` (or pass by value). Bugs: dangling `return` outside braces; inverted guard `open > close` → `)` never fires → **empty result**; missing `pop_back`. Count = **Catalan(n)** ⇒ O(4ⁿ/√n), prune beats 2^(2n) |
| ✅ | 15/06/26 | 84  | [Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/) | 🔴 | "fixed-width bars, biggest rectangle?" → each bar is the **shortest** bar of some rectangle, which stretches to its **previous-smaller** and **next-smaller** boundaries → one **increasing** monotonic stack of **indices**. When bar `i` pops `j`: `i` is `j`'s right wall, the new top is `j`'s left wall, `area = h[j] × (i − top − 1)` (or `i` if stack empties). **Sentinel 0** at `i==n` flushes the stack (no separate drain). Pop on `≥` not `>` (equal heights), guard empty-stack width. Reuse row-by-row for Maximal Rectangle (85). O(n)/O(n) |
| ✅ | 16/06/26 | 85  | [Maximal Rectangle](https://leetcode.com/problems/maximal-rectangle/) | 🔴 | "largest all-1s rectangle in a binary matrix" → sweep rows top→bottom building `heights[]` per column (`+1` on `'1'`, **reset 0** on `'0'`), run **Largest Rectangle in Histogram (84)** on each row, take the max. The Hard 1-D monotonic-stack routine lifted to 2-D. O(rows·cols)/O(cols) |

---

# 7. Linked List Manipulation

**When to use it (recognition cues):**
- Reverse / partial reverse / k-group reverse.
- Merge / sort / split a list.
- Pointer rewiring without extra space.

**Core idea:** Use dummy head + 3 pointers (prev/curr/next). Draw arrows on paper before coding.

**Template (C++):**
```cpp
ListNode dummy(0); dummy.next = head;
ListNode *prev = &dummy, *curr = head;
while (curr) { /* rewire */ }
return dummy.next;
```

**Problems:** _Basics already drilled (reverse / merge / partition / cycle done earlier) — only the MAANG-staple hards retained here. Scheduled in the Week 17 breadth block._

| ✓ | Date | # | Problem | Diff | Trigger phrase |
|---|------|---|---------|------|----------------|
| ☐ |      | 25  | [Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/) | 🔴 |  |
| ☐ |      | 138 | [Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/) | 🟡 |  |
| ☐ |      | 23  | [Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/) | 🔴 |  |
| ☐ |      | 146 | [LRU Cache](https://leetcode.com/problems/lru-cache/) | 🟡 | (also in #19 Design) |

---

# 8. Tree DFS

**When to use it (recognition cues):**
- Path / sum / diameter / depth in a binary tree.
- Need info from both subtrees combined upward.
- "Validate" a tree property.

**Core idea:** Recurse; the function returns information that the parent uses to combine left + right.

**Template (C++):**
```cpp
int dfs(TreeNode* node) {
    if (!node) return 0;
    int L = dfs(node->left), R = dfs(node->right);
    // combine L, R, node->val
    return /* value to parent */;
}
```

**Problems:**

| ✓ | Date | # | Problem | Diff | Trigger phrase |
|---|------|---|---------|------|----------------|
| ✅ | Jun 16 | 104 | [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/) | 🟢 | "how deep/tall is the tree" → post-order, each node returns `1 + max(L, R)`, null returns 0 |
| ✅ | Jun 16 | 100 | [Same Tree](https://leetcode.com/problems/same-tree/) | 🟢 | "two trees identical (shape + values)" → parallel DFS, 3 base cases (both null/one null/val differ), recurse L-L & R-R |
| ✅ | Jun 17 | 226 | [Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/) | 🟢 | "mirror/flip the tree left↔right" → swap each node's two children, recurse both; order irrelevant. Mutate-in-place DFS, return root |
| ✅ | Jun 18 | 543 | [Diameter of Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree/) | 🟢 | "longest path between any two nodes, in edges, may skip root" → height recursion, at every node update global `max(L+R)`, return `1+max(L,R)` |
| ✅ | Jun 18 | 110 | [Balanced Binary Tree](https://leetcode.com/problems/balanced-binary-tree/) | 🟢 | "every node's two subtree heights differ by ≤1" → height recursion + `-1` sentinel: return `-1` if any child is `-1` or `abs(L-R)>1`, else `max(L,R)+1`; balanced iff root ≠ `-1` |
| ✅ | Jun 19 | 112 | [Path Sum](https://leetcode.com/problems/path-sum/) | 🟢 | "is there a root-to-leaf path summing to target" → DFS carrying remaining budget (`target - val`), at a leaf test `remaining == 0`, bubble up `left \|\| right`; null tree → false |
| ✅ | Jun 21 | 98  | [Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/) | 🟡 | "is this a valid BST (strict <, recursive)" → DFS carrying an inherited `(low, high)` range; node valid iff `low < val < high`, left tightens high→val, right tightens low→val, `&&` both; seed `long long ±∞` so `INT_MIN/MAX` fit. Local parent-child check is **not** enough |
| ✅ | Jun 21 | 230 | [Kth Smallest Element in a BST](https://leetcode.com/problems/kth-smallest-element-in-a-bst/) | 🟡 | "kth smallest value in a BST" → in-order DFS (left→node→right gives sorted), share `k` **by reference**, `--k` per visit, return `val` when `k==0`, `-1` sentinel bubbles up. Bug: recursing into by-value `k` loses the count. Follow-up: augment subtree sizes for O(h) |
| ✅ | Jun 21 | 236 | [Lowest Common Ancestor of a Binary Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/) | 🟡 | "LCA of two nodes in a **plain** binary tree" → post-order DFS returning the found node; base `!root \|\| root==p \|\| root==q → root`; if **both** children return non-null, this node is the LCA, else bubble up whichever side hit. Match-returns-node handles self-ancestor; no BST shortcut (that's 235) |
| ✅ | Jun 22 | 105 | [Construct Binary Tree from Preorder and Inorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/) | 🟡 | "rebuild tree from preorder + inorder" → march one shared `preIdx` through preorder (each elem = next root), use a `value→inorder index` map to split into left range `[s, mid-1]` / right range `[mid+1, e]`; recurse **left before right**, base `s > e`. Inorder gives the split → uniqueness; O(n) |
| ✅ | Jun 22 | 124 | [Binary Tree Maximum Path Sum](https://leetcode.com/problems/binary-tree-maximum-path-sum/) | 🔴 | "max path sum, path bends anywhere, may skip root" → post-order; each child arm clamped `max(0, dfs(child))` (drop negative branches), update global `best = val + left + right` (bend here), **return** `val + max(left, right)` (straight arm for parent). Init `best = INT_MIN` (single negative node valid). Clamp the **arms**, not `val`. Value twin of 543 Diameter |
| ✅ | Jun 23 | 297 | [Serialize and Deserialize Binary Tree](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/) | 🔴 | "serialize/deserialize a tree, convert tree ↔ string" → pick **one** traversal (preorder DFS or level-order BFS), emit `#` for **every null** (that's what makes shape unambiguous), decode by consuming tokens in the **same** order. Build **left before right**; split on `,` not `-` (negatives); handle empty tree. Mirror of 105 but with explicit nulls → one traversal suffices |

---

# 9. Tree BFS

**When to use it (recognition cues):**
- "Level order", "right side view", "zigzag".
- Minimum depth / shortest path in unweighted tree.
- Process tree level-by-level.

**Core idea:** Queue + iterate one level at a time using `queue.size()` snapshot.

**Template (C++):**
```cpp
queue<TreeNode*> q; q.push(root);
while (!q.empty()) {
    int sz = q.size();
    for (int i = 0; i < sz; ++i) {
        auto n = q.front(); q.pop();
        if (n->left)  q.push(n->left);
        if (n->right) q.push(n->right);
    }
}
```

**Problems:**

| ✓ | Date | # | Problem | Diff | Trigger phrase |
|---|------|---|---------|------|----------------|
| ✅ | Jun 23 | 102 | [Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/) | 🟡 | "level order, group nodes by depth, process level-by-level" → queue + **snapshot `sz = q.size()` before** the inner loop (queue *is* the level at that instant), drain `sz` nodes into a per-level vector, push non-null children for the next level. Empty tree → `[]`. The founding Tree BFS skeleton — zigzag/right-view/level-averages are all this + one tweak |
| ✅ | Jun 23 | 107 | [Level Order Traversal II](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/) | 🟡 | "bottom-up level order, leaf level first" → do plain 102 level order, then **`reverse(result.begin(), result.end())`** once (flips outer list of levels, O(#levels); inner left→right stays). Avoid front-insert per level — that's O(levels²). 102 + one reverse |
| ✅ | Jun 24 | 103 | [Zigzag Level Order Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/) | 🟡 | "zigzag / snake / serpentine by level, left→right then right→left alternating" → plain 102 BFS (enqueue stays left→right!), but **pre-size `vector<int> level(sz)`** and write each value at `index = leftFirst ? i : sz-1-i`, flipping `leftFirst` per level. No `reverse` needed — placement *is* the flip. Don't reverse the traversal (mirrors next level's children) |
| ✅ | Jun 25 | 199 | [Binary Tree Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/) | 🟡 | "right side view, rightmost node per level, silhouette seen from the right" → plain 102 BFS but collect only **one** value per level: `q.back()->val` (the level's last node, read **before** pushing its children). "Right side" ≠ always-go-right — a missing right child exposes the deepest left descendant, which level order handles automatically. Left view = `q.front()`. DFS alt: recurse **right-first**, take the first node seen per depth (O(h) space) |
| ✅ | Jun 25 | 637 | [Average of Levels in Binary Tree](https://leetcode.com/problems/average-of-levels-in-binary-tree/) | 🟢 | "average / sum per level, one aggregate per depth" → plain 102 BFS but fold each level into a single number: snapshot `size`, sum the level's values, push `sum / size`. **Sum into a `double`** (or `long long`) — values span the full `int` range and a level can be wide, so a bare `int`/`long` sum overflows. `double / int` yields real division. DFS alt: depth-indexed `sum[]`/`cnt[]`, divide at end (O(h) space) |
| ✅ | Jun 26 | 111 | [Minimum Depth of Binary Tree](https://leetcode.com/problems/minimum-depth-of-binary-tree/) | 🟢 | "minimum depth, shortest path to the nearest leaf" → plain 102 BFS but **return `depth` at the first leaf popped** (`!left && !right`); BFS reaches the shallowest leaf first, so it short-circuits (DFS must explore everything). **One-child trap:** a node with a single child is **not** a leaf — naive `1 + min(left, right)` wrongly returns via the null side; recurse only into real children or special-case it. DFS alt: `(!l_child‖!r_child) ? 1+l+r : 1+min(l,r)`, O(h) space. Empty tree → 0 |
| ✅ | Jun 27 | 116 | [Populating Next Right Pointers in Each Node](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/) | 🟡 | "connect each node to its right neighbour, next-right pointer, per-level linked list" → plain 102 BFS but instead of collecting, link node `i` to the next in queue: `if (i < size-1) n->next = q.front()` (front is the right sibling since children push to the back); last node keeps its initial `NULL` (no need to set it). **Follow-up O(1) space:** drop the queue — the tree is **perfect**, so use the `next` pointers already built to walk each level: `head->left->next = head->right; if(head->next) head->right->next = head->next->left`, then `leftmost = leftmost->left`. Only works because perfect (LC 117 isn't → needs a dummy node per level) |
| ✅ | Jun 27 | 117 | [Populating Next Right Pointers II](https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii/) | 🟡 | "connect each node to its right neighbour on **any/general** binary tree (ragged levels)" → **same task as 116 but tree isn't perfect**, so the BFS-with-queue code is *identical* (link node `i` to `q.front()`). The O(1) trick breaks — any of `head->left/right/next->left` can be null — so use a **dummy node**: walk the current level via `next`, thread each real child onto a `dummy → prev` chain, then `curr = dummy.next` to descend. `dummy.next` is the next level's head; fresh `dummy` per level. This dummy-node code also solves 116 (the general answer). DFS alt: recurse **right-subtree first** so `next` is set before children query it |
| ✅ | Jun 27 | 515 | [Find Largest Value in Each Tree Row](https://leetcode.com/problems/find-largest-value-in-each-tree-row/) | 🟡 | "largest / max value in each row, one aggregate per depth, per-level reduce" → plain 102 BFS but fold each level into a single number: seed `maxi = INT_MIN`, take `maxi = max(maxi, node->val)` over the level, push `maxi`. **Seed `INT_MIN`, never `0`** — values span the full `int` range incl. negatives (down to `INT_MIN`), so a `0` seed wrongly reports 0 for an all-negative level. Twin of 637 (`max` instead of `sum`) but *easier* — comparing has no overflow/`double` trap. DFS alt: recurse carrying `depth`, push a new slot on first reach else `res[d] = max(res[d], val)`, O(h) space |
| ✅ | Jun 29 | 1161| [Maximum Level Sum of a Binary Tree](https://leetcode.com/problems/maximum-level-sum-of-a-binary-tree/) | 🟡 | "smallest level x with maximal sum, argmax level by sum, return the depth not the value" → 102 BFS, sum each level like 637 but **return the level index**, not the sum. Track `bestLevel` with **strict `if (maxSum < sum)`** so a tie keeps the **smallest** level — `<=` would return the *last* max level (the signature bug). **Levels 1-indexed** (`++level` at top, root = 1). Seed `maxSum = INT_MIN` so an all-negative tree still picks a real level. Sum fits in `int` (≤ ~10^9). DFS alt: depth-indexed `sums[]`, argmax with strict `>`, `+1`, O(h) space |

---

# 10. Graphs — BFS / DFS / Topological Sort

**When to use it (recognition cues):**
- Grid / matrix → 4-directional / 8-directional traversal (islands, regions, rotting).
- Connected components, bipartite check.
- "Course schedule", dependencies → topological sort.
- Shortest path in unweighted graph → BFS.

**Core idea:** BFS for shortest unweighted path; DFS/Union-Find for components; Kahn's BFS for topo.

**Template (C++) — Topo (Kahn's):**
```cpp
vector<int> indeg(n, 0), order;
for (auto& e : edges) indeg[e[1]]++;
queue<int> q;
for (int i = 0; i < n; ++i) if (!indeg[i]) q.push(i);
while (!q.empty()) {
    int u = q.front(); q.pop(); order.push_back(u);
    for (int v : adj[u]) if (--indeg[v] == 0) q.push(v);
}
```

**Problems:**

| ✓ | Date | # | Problem | Diff | Trigger phrase |
|---|------|---|---------|------|----------------|
| ✅ | Jul 1 | 200 | [Number of Islands](https://leetcode.com/problems/number-of-islands/) | 🟡 | "count connected blobs/regions of `1`s in a grid" → #islands = #connected components. Scan cells; each unvisited land cell → `++count` then flood-fill (DFS sink to `'0'` / BFS) its whole 4-adjacent island. **Mark visited on discovery**, not on pop. 4 dirs only. 300×300 ⇒ 90k-deep DFS can overflow → BFS. Dynamic-add → Union-Find (305) |
| ✅ | Jul 1 | 695 | [Max Area of Island](https://leetcode.com/problems/max-area-of-island/) | 🟡 | "largest island / biggest connected region / max area of `1`s" → same scan-and-flood as 200, but DFS **returns a size** (`1 + Σ dfs(neighbour)`) and outer loop keeps the `max`. Mark visited on entry; seed `maxArea = 0`. Sink-in-place = O(1) aux, `visited` grid = non-destructive. 4 dirs only |
| ✅ | Jul 1 | 994 | [Rotting Oranges](https://leetcode.com/problems/rotting-oranges/) | 🟡 | "every minute all rotten cells infect neighbours **simultaneously**; min minutes till none fresh" → **multi-source BFS, level = time** (NOT DFS). Seed queue with all rotten + count fresh; drain **ring by ring**, freeze `sz=q.size()`, mark rotten on discovery (`grid=2`). `fresh==0`→0, end `fresh>0`→-1 |
| ✅ | Jul 2 | 130 | [Surrounded Regions](https://leetcode.com/problems/surrounded-regions/) | 🟡 | "capture regions **fully enclosed** by `X`; a region touching an **edge** survives" → **invert it: flood from the border, not the interior.** An `O` is safe iff connected to a border `O`. BFS/DFS-seed every border `'O'`, tag reachable with temp `'#'`; then sweep: `'O'`→`'X'` (captured), `'#'`→`'O'` (restore). Marker = visited set. Prefer BFS at 200×200 (deep DFS overflows). Same border-flood as Pacific Atlantic (417) |
| ✅ | Jul 2 | 133 | [Clone Graph](https://leetcode.com/problems/clone-graph/) | 🟡 | "**deep copy** a graph with **cycles / shared neighbours**" → **DFS + `oldToNew` map (Node*→clone)**. On first visit `new Node(val)` and **store in map BEFORE recursing** on neighbours — the entry is both memo and cycle-breaker (store after the loop → infinite recursion). Link each cloned neighbour into `copy->neighbors`. `node? clone : nullptr` for empty graph. Key by pointer. BFS variant = same map + queue |
| ✅ | Jul 3 | 207 | [Course Schedule](https://leetcode.com/problems/course-schedule/) | 🟡 | "given **prerequisites / dependencies**, can you finish all courses / is there a valid order?" → **topological sort as cycle detection (Kahn's BFS)**. Edge `b → a` per `[a,b]` (b before a), `indegree[a]++`. Seed queue with all **indegree-0** nodes, peel one at a time (`count++`), decrement dependents, push at 0. `count == numCourses` ⇒ acyclic ⇒ `true` (a cycle never reaches indegree 0). Need the *count*, not the order. Alt: DFS 3-color, in-progress neighbour = back edge = cycle |
| ✅ | Jul 5 | 210 | [Course Schedule II](https://leetcode.com/problems/course-schedule-ii/) | 🟡 | "given **prerequisites / dependencies**, output **a valid order** (empty if impossible)" → **topological sort — same `b → a` DAG as 207, now emit the order.** **Kahn's BFS:** append each node **on pop** — pop sequence *is* the topo order; `topo.size() != numCourses` ⇒ cycle ⇒ `{}`. **DFS alt:** 3-color, collect **post-order** then **reverse** (prereqs finish first); in-progress neighbour = back edge = cycle ⇒ `{}`. BFS = append-on-pop (no reverse); DFS = post-order + reverse. Binary visited can't detect cycles |
| ✅ | Jul 7 | 785 | [Is Graph Bipartite?](https://leetcode.com/problems/is-graph-bipartite/) | 🟡 | "split nodes into **two groups** so **every edge crosses** between them (no edge inside a group)" → **2-coloring: bipartite ⇔ 2-colorable ⇔ no odd cycle.** Color a start `0`, force each neighbour to the **opposite** color (`!color`); a neighbour **already your color** = odd cycle ⇒ `false`. `colors` init `-1`. **Loop over all nodes** (disconnected). Conflict = *same-color*, not just visited. DFS or BFS, both O(V+E). Even cycles fine — only **odd** cycles break it |
| ✅ | Jul 8 | 417 | [Pacific Atlantic Water Flow](https://leetcode.com/problems/pacific-atlantic-water-flow/) | 🟡 | "cells from which water reaches **both** oceans (targets on opposite borders)" → **reverse the flow: flood inward from each ocean's border**, keeping equal-or-**higher** neighbours (guard `heights < prevH → return`); two visited grids `pac`/`atl`, seed Pacific from top+left & Atlantic from bottom+right, answer = `pac && atl`. Naive per-cell flood is O((m·n)²) TLE. Same border-anchored inward flood as Surrounded Regions (130) |
| ☐ |      | 1091| [Shortest Path in Binary Matrix](https://leetcode.com/problems/shortest-path-in-binary-matrix/) | 🟡 |  |
| ☐ |      | 127 | [Word Ladder](https://leetcode.com/problems/word-ladder/) | 🔴 |  |
| ☐ |      | 269 | [Alien Dictionary](https://leetcode.com/problems/alien-dictionary/) | 🔴 |  |

**Weighted Graphs (Dijkstra / Bellman-Ford / MST):** edges have costs → shortest path is no longer plain BFS. Min-heap by distance (Dijkstra), relax-K-times (Bellman-Ford), or grow the cheapest tree (Prim/Kruskal MST). _Scheduled in the Week 17 breadth block._

| ✓ | Date | # | Problem | Diff | Trigger phrase |
|---|------|---|---------|------|----------------|
| ☐ |      | 743 | [Network Delay Time](https://leetcode.com/problems/network-delay-time/) | 🟡 | Dijkstra: min time to reach all nodes from source |
| ☐ |      | 787 | [Cheapest Flights Within K Stops](https://leetcode.com/problems/cheapest-flights-within-k-stops/) | 🟡 | Shortest path with ≤K edges → Bellman-Ford / BFS layers |
| ☐ |      | 1584 | [Min Cost to Connect All Points](https://leetcode.com/problems/min-cost-to-connect-all-points/) | 🟡 | Connect all nodes cheapest → MST (Prim/Kruskal) |
| ☐ |      | 778 | [Swim in Rising Water](https://leetcode.com/problems/swim-in-rising-water/) | 🔴 | Minimize max edge on a path → Dijkstra-on-grid / binary search + DFS |

---

# 11. Heap / Top-K / Two-Heaps

**When to use it (recognition cues):**
- "Top K", "K largest/smallest", "K closest to X".
- Median of running stream → two heaps.
- Merge K sorted things.
- Schedule with priorities / next event.

**Core idea:** A heap gives O(log n) insertion + O(1) min/max access. For "top K largest", keep a min-heap of size K.

**Template (C++):**
```cpp
priority_queue<int, vector<int>, greater<int>> minHeap; // size K
for (int x : nums) {
    minHeap.push(x);
    if (minHeap.size() > k) minHeap.pop();
}
```

**Problems:**

| ✓ | Date | # | Problem | Diff | Trigger phrase |
|---|------|---|---------|------|----------------|
| ☐ |      | 215 | [Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/) | 🟡 |  |
| ☐ |      | 703 | [Kth Largest Element in a Stream](https://leetcode.com/problems/kth-largest-element-in-a-stream/) | 🟢 |  |
| ☐ |      | 347 | [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/) | 🟡 |  |
| ☐ |      | 692 | [Top K Frequent Words](https://leetcode.com/problems/top-k-frequent-words/) | 🟡 |  |
| ☐ |      | 973 | [K Closest Points to Origin](https://leetcode.com/problems/k-closest-points-to-origin/) | 🟡 |  |
| ☐ |      | 658 | [Find K Closest Elements](https://leetcode.com/problems/find-k-closest-elements/) | 🟡 |  |
| ☐ |      | 1046| [Last Stone Weight](https://leetcode.com/problems/last-stone-weight/) | 🟢 |  |
| ☐ |      | 621 | [Task Scheduler](https://leetcode.com/problems/task-scheduler/) | 🟡 |  |
| ☐ |      | 1167| [Minimum Cost to Connect Sticks](https://leetcode.com/problems/minimum-cost-to-connect-sticks/) | 🟡 |  |
| ☐ |      | 378 | [Kth Smallest Element in a Sorted Matrix](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/) | 🟡 |  |
| ☐ |      | 295 | [Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/) | 🔴 |  |
| ☐ |      | 480 | [Sliding Window Median](https://leetcode.com/problems/sliding-window-median/) | 🔴 |  |

---

# 12. Backtracking

**When to use it (recognition cues):**
- Generate **all** subsets / permutations / combinations / paths.
- Constraint satisfaction (N-Queens, Sudoku, word search).
- "Return all possible…" — exponential output.

**Core idea:** Recursively build a partial solution; on dead-end, undo the last choice (backtrack). Skeleton: choose → explore → unchoose.

**Template (C++):**
```cpp
void bt(vector<int>& cur, int start) {
    res.push_back(cur);
    for (int i = start; i < n; ++i) {
        cur.push_back(nums[i]);
        bt(cur, i + 1);
        cur.pop_back();
    }
}
```

**Problems:**

| ✓ | Date | # | Problem | Diff | Trigger phrase |
|---|------|---|---------|------|----------------|
| ☐ |      | 78  | [Subsets](https://leetcode.com/problems/subsets/) | 🟡 |  |
| ☐ |      | 90  | [Subsets II](https://leetcode.com/problems/subsets-ii/) | 🟡 |  |
| ☐ |      | 46  | [Permutations](https://leetcode.com/problems/permutations/) | 🟡 |  |
| ☐ |      | 47  | [Permutations II](https://leetcode.com/problems/permutations-ii/) | 🟡 |  |
| ☐ |      | 39  | [Combination Sum](https://leetcode.com/problems/combination-sum/) | 🟡 |  |
| ☐ |      | 40  | [Combination Sum II](https://leetcode.com/problems/combination-sum-ii/) | 🟡 |  |
| ☐ |      | 17  | [Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number/) | 🟡 |  |
| ☐ |      | 79  | [Word Search](https://leetcode.com/problems/word-search/) | 🟡 |  |
| ☐ |      | 131 | [Palindrome Partitioning](https://leetcode.com/problems/palindrome-partitioning/) | 🟡 |  |
| ☐ |      | 93  | [Restore IP Addresses](https://leetcode.com/problems/restore-ip-addresses/) | 🟡 |  |
| ☐ |      | 51  | [N-Queens](https://leetcode.com/problems/n-queens/) | 🔴 |  |
| ☐ |      | 37  | [Sudoku Solver](https://leetcode.com/problems/sudoku-solver/) | 🔴 |  |

---

# 13. Greedy & Intervals

**When to use it (recognition cues):**
- Intervals: merge / insert / overlap / meeting rooms.
- "Minimum number of …" or "maximum number of …" with sortable input.
- A locally optimal pick is globally optimal (often after sorting by start/end).

**Core idea:** Sort first, then make the locally best choice.

**Template (C++):**
```cpp
sort(intervals.begin(), intervals.end());
vector<vector<int>> merged;
for (auto& iv : intervals) {
    if (merged.empty() || merged.back()[1] < iv[0]) merged.push_back(iv);
    else merged.back()[1] = max(merged.back()[1], iv[1]);
}
```

**Problems:**

| ✓ | Date | # | Problem | Diff | Trigger phrase |
|---|------|---|---------|------|----------------|
| ☐ |      | 56  | [Merge Intervals](https://leetcode.com/problems/merge-intervals/) | 🟡 |  |
| ☐ |      | 57  | [Insert Interval](https://leetcode.com/problems/insert-interval/) | 🟡 |  |
| ☐ |      | 252 | [Meeting Rooms](https://leetcode.com/problems/meeting-rooms/) | 🟢 |  |
| ☐ |      | 253 | [Meeting Rooms II](https://leetcode.com/problems/meeting-rooms-ii/) | 🟡 |  |
| ☐ |      | 435 | [Non-overlapping Intervals](https://leetcode.com/problems/non-overlapping-intervals/) | 🟡 |  |
| ☐ |      | 452 | [Minimum Number of Arrows to Burst Balloons](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/) | 🟡 |  |
| ☐ |      | 55  | [Jump Game](https://leetcode.com/problems/jump-game/) | 🟡 |  |
| ☐ |      | 45  | [Jump Game II](https://leetcode.com/problems/jump-game-ii/) | 🟡 |  |
| ☐ |      | 763 | [Partition Labels](https://leetcode.com/problems/partition-labels/) | 🟡 |  |
| ☐ |      | 134 | [Gas Station](https://leetcode.com/problems/gas-station/) | 🟡 |  |
| ☐ |      | 122 | [Best Time to Buy and Sell Stock II](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/) | 🟡 |  |
| ☐ |      | 1326| [Minimum Number of Taps to Open to Water a Garden](https://leetcode.com/problems/minimum-number-of-taps-to-open-to-water-a-garden/) | 🔴 |  |

---

# 14. Dynamic Programming — 1D

**When to use it (recognition cues):**
- "Number of ways" / "max value" / "min cost".
- At each step: choose / skip / take-multiple.
- Brute force has overlapping subproblems (Fibonacci-like).

**Core idea:** Define `dp[i]` for state `i`; write a recurrence; compute bottom-up.

**Template (C++):**
```cpp
vector<int> dp(n + 1);
dp[0] = base;
for (int i = 1; i <= n; ++i)
    dp[i] = /* combine dp[i-1], dp[i-2], ... */;
return dp[n];
```

**Problems:**

| ✓ | Date | # | Problem | Diff | Trigger phrase |
|---|------|---|---------|------|----------------|
| ☐ |      | 70  | [Climbing Stairs](https://leetcode.com/problems/climbing-stairs/) | 🟢 |  |
| ☐ |      | 746 | [Min Cost Climbing Stairs](https://leetcode.com/problems/min-cost-climbing-stairs/) | 🟢 |  |
| ☐ |      | 198 | [House Robber](https://leetcode.com/problems/house-robber/) | 🟡 |  |
| ☐ |      | 213 | [House Robber II](https://leetcode.com/problems/house-robber-ii/) | 🟡 |  |
| ☐ |      | 53  | [Maximum Subarray](https://leetcode.com/problems/maximum-subarray/) | 🟡 |  |
| ☐ |      | 152 | [Maximum Product Subarray](https://leetcode.com/problems/maximum-product-subarray/) | 🟡 |  |
| ☐ |      | 121 | [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/) | 🟢 |  |
| ☐ |      | 322 | [Coin Change](https://leetcode.com/problems/coin-change/) | 🟡 |  |
| ☐ |      | 300 | [Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/) | 🟡 |  |
| ☐ |      | 139 | [Word Break](https://leetcode.com/problems/word-break/) | 🟡 |  |
| ☐ |      | 91  | [Decode Ways](https://leetcode.com/problems/decode-ways/) | 🟡 |  |
| ☐ |      | 416 | [Partition Equal Subset Sum](https://leetcode.com/problems/partition-equal-subset-sum/) | 🟡 |  |

---

# 15. Dynamic Programming — 2D / Grid / Strings

**When to use it (recognition cues):**
- Two strings → edit distance, LCS, regex match.
- Grid paths / unique paths / min path sum.
- Palindromic substrings / partitions.

**Core idea:** `dp[i][j]` = answer for prefix-i of one input and prefix-j of the other (or row i, col j of grid).

**Template (C++):**
```cpp
vector<vector<int>> dp(m + 1, vector<int>(n + 1, 0));
for (int i = 1; i <= m; ++i)
    for (int j = 1; j <= n; ++j)
        dp[i][j] = /* recurrence using dp[i-1][j], dp[i][j-1], dp[i-1][j-1] */;
return dp[m][n];
```

**Problems:**

| ✓ | Date | # | Problem | Diff | Trigger phrase |
|---|------|---|---------|------|----------------|
| ☐ |      | 62  | [Unique Paths](https://leetcode.com/problems/unique-paths/) | 🟡 |  |
| ☐ |      | 63  | [Unique Paths II](https://leetcode.com/problems/unique-paths-ii/) | 🟡 |  |
| ☐ |      | 64  | [Minimum Path Sum](https://leetcode.com/problems/minimum-path-sum/) | 🟡 |  |
| ☐ |      | 1143| [Longest Common Subsequence](https://leetcode.com/problems/longest-common-subsequence/) | 🟡 |  |
| ☐ |      | 72  | [Edit Distance](https://leetcode.com/problems/edit-distance/) | 🟡 |  |
| ☐ |      | 583 | [Delete Operation for Two Strings](https://leetcode.com/problems/delete-operation-for-two-strings/) | 🟡 |  |
| ☐ |      | 5   | [Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/) | 🟡 |  |
| ☐ |      | 647 | [Palindromic Substrings](https://leetcode.com/problems/palindromic-substrings/) | 🟡 |  |
| ☐ |      | 516 | [Longest Palindromic Subsequence](https://leetcode.com/problems/longest-palindromic-subsequence/) | 🟡 |  |
| ☐ |      | 221 | [Maximal Square](https://leetcode.com/problems/maximal-square/) | 🟡 |  |
| ☐ |      | 10  | [Regular Expression Matching](https://leetcode.com/problems/regular-expression-matching/) | 🔴 |  |
| ☐ |      | 312 | [Burst Balloons](https://leetcode.com/problems/burst-balloons/) | 🔴 |  |

---

# 16. Tries & Union-Find

**When to use it (recognition cues):**
- Prefix lookup / autocomplete / dictionary search → **Trie**.
- "Number of provinces", "redundant connection", dynamic connectivity → **Union-Find**.
- Word search with many queries.

**Core idea (Trie):** Tree of characters with children map + isEnd flag.
**Core idea (Union-Find):** `parent[]` + `rank[]`; path compression on `find`, union by rank.

**Template (C++) — Union-Find:**
```cpp
struct DSU {
    vector<int> p, r;
    DSU(int n): p(n), r(n, 0) { iota(p.begin(), p.end(), 0); }
    int find(int x) { return p[x] == x ? x : p[x] = find(p[x]); }
    bool unite(int a, int b) {
        a = find(a); b = find(b);
        if (a == b) return false;
        if (r[a] < r[b]) swap(a, b);
        p[b] = a; if (r[a] == r[b]) ++r[a];
        return true;
    }
};
```

**Problems:**

| ✓ | Date | # | Problem | Diff | Trigger phrase |
|---|------|---|---------|------|----------------|
| ☐ |      | 208 | [Implement Trie (Prefix Tree)](https://leetcode.com/problems/implement-trie-prefix-tree/) | 🟡 |  |
| ☐ |      | 211 | [Design Add and Search Words Data Structure](https://leetcode.com/problems/design-add-and-search-words-data-structure/) | 🟡 |  |
| ☐ |      | 648 | [Replace Words](https://leetcode.com/problems/replace-words/) | 🟡 |  |
| ☐ |      | 677 | [Map Sum Pairs](https://leetcode.com/problems/map-sum-pairs/) | 🟡 |  |
| ☐ |      | 1268| [Search Suggestions System](https://leetcode.com/problems/search-suggestions-system/) | 🟡 |  |
| ☐ |      | 212 | [Word Search II](https://leetcode.com/problems/word-search-ii/) | 🔴 |  |
| ☐ |      | 547 | [Number of Provinces](https://leetcode.com/problems/number-of-provinces/) | 🟡 |  |
| ☐ |      | 684 | [Redundant Connection](https://leetcode.com/problems/redundant-connection/) | 🟡 |  |
| ☐ |      | 990 | [Satisfiability of Equality Equations](https://leetcode.com/problems/satisfiability-of-equality-equations/) | 🟡 |  |
| ☐ |      | 721 | [Accounts Merge](https://leetcode.com/problems/accounts-merge/) | 🟡 |  |
| ☐ |      | 305 | [Number of Islands II](https://leetcode.com/problems/number-of-islands-ii/) | 🔴 |  |
| ☐ |      | 952 | [Largest Component Size by Common Factor](https://leetcode.com/problems/largest-component-size-by-common-factor/) | 🔴 |  |

---

# 17. Bit Manipulation

**When to use it (recognition cues):**
- "Find the one number that appears once / odd times" → XOR.
- Count bits, swap without temp, check power of two, build from subsets via bitmask.
- Add/subtract without `+`/`-`, or O(1) extra space on a fixed-width integer.

**Core idea:** XOR cancels pairs (`a^a=0`); `n & (n-1)` drops the lowest set bit; shift + mask to read/write individual bits.

**Template (C++):**
```cpp
int x = 0;
for (int v : nums) x ^= v;        // lone element survives
int bits = __builtin_popcount(n); // count set bits
bool isPow2 = n > 0 && !(n & (n-1));
```

**Problems:**

| ✓ | Date | # | Problem | Diff | Trigger phrase |
|---|------|---|---------|------|----------------|
| ☐ |      | 136 | [Single Number](https://leetcode.com/problems/single-number/) | 🟢 | Every element twice except one → XOR all |
| ☐ |      | 338 | [Counting Bits](https://leetcode.com/problems/counting-bits/) | 🟢 | bits[i] = bits[i>>1] + (i&1) DP |
| ☐ |      | 191 | [Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/) | 🟢 | Pop lowest set bit with n & (n-1) |
| ☐ |      | 371 | [Sum of Two Integers](https://leetcode.com/problems/sum-of-two-integers/) | 🟡 | Add without + : XOR = sum, AND<<1 = carry |
| ☐ |      | 190 | [Reverse Bits](https://leetcode.com/problems/reverse-bits/) | 🟢 | Shift out of n, shift into result 32× |

---

# 18. Matrix Simulation

**When to use it (recognition cues):**
- Rotate / transpose / spiral-traverse a 2-D grid.
- Mark-then-sweep state changes on a board (in-place flags).
- "Do it in O(1) extra space" on a matrix.

**Core idea:** Layer-by-layer or boundary pointers (top/bottom/left/right); use the matrix itself (first row/col, or sign bits) as the marker to hit O(1) space.

**Template (C++):**
```cpp
// transpose then reverse each row = rotate 90° clockwise
for (int i = 0; i < n; i++)
    for (int j = i+1; j < n; j++) swap(m[i][j], m[j][i]);
for (auto& row : m) reverse(row.begin(), row.end());
```

**Problems:**

| ✓ | Date | # | Problem | Diff | Trigger phrase |
|---|------|---|---------|------|----------------|
| ☐ |      | 48  | [Rotate Image](https://leetcode.com/problems/rotate-image/) | 🟡 | Rotate 90° in place → transpose + reverse rows |
| ☐ |      | 54  | [Spiral Matrix](https://leetcode.com/problems/spiral-matrix/) | 🟡 | Four shrinking boundaries top/bottom/left/right |
| ☐ |      | 73  | [Set Matrix Zeroes](https://leetcode.com/problems/set-matrix-zeroes/) | 🟡 | O(1) space: use row0/col0 as zero markers |
| ☐ |      | 289 | [Game of Life](https://leetcode.com/problems/game-of-life/) | 🟡 | Encode old+new state in 2 bits, sweep twice |

---

# 19. Design

**When to use it (recognition cues):**
- "Implement a class with O(1) `get`/`put`/`insert`/`remove`."
- Cache eviction (LRU/LFU), random-access set, custom hash map.
- Combine two structures (hash map + linked list / heap) for the right complexities.

**Core idea:** Pick the pair of structures whose strengths cover every required operation in O(1)/O(log n): hash map for lookup + doubly linked list (order) or heap (priority) or array+swap (random).

**Problems:**

| ✓ | Date | # | Problem | Diff | Trigger phrase |
|---|------|---|---------|------|----------------|
| ☐ |      | 146 | [LRU Cache](https://leetcode.com/problems/lru-cache/) | 🟡 | Hash map + doubly linked list, move-to-front |
| ☐ |      | 460 | [LFU Cache](https://leetcode.com/problems/lfu-cache/) | 🔴 | Freq → DLL buckets + key→node map, track minFreq |
| ☐ |      | 380 | [Insert Delete GetRandom O(1)](https://leetcode.com/problems/insert-delete-getrandom-o1/) | 🟡 | Array + value→index map; swap-with-last to delete |
| ☐ |      | 706 | [Design HashMap](https://leetcode.com/problems/design-hashmap/) | 🟢 | Buckets + chaining; modulo hash |

---

# 20. Math / String

**When to use it (recognition cues):**
- Implement an arithmetic/string primitive: power, sqrt, parse an integer, convert numerals.
- Cycle detection on digit transforms (Happy Number → fast/slow).
- Edge-case-heavy parsing (overflow, sign, whitespace).

**Core idea:** Fast exponentiation (halve the power), binary search for sqrt, careful state machine for parsing; watch INT overflow and sign.

**Template (C++):**
```cpp
double myPow(double x, long n) {       // fast power
    if (n < 0) { x = 1/x; n = -n; }
    double r = 1;
    while (n) { if (n & 1) r *= x; x *= x; n >>= 1; }
    return r;
}
```

**Problems:**

| ✓ | Date | # | Problem | Diff | Trigger phrase |
|---|------|---|---------|------|----------------|
| ☐ |      | 50  | [Pow(x, n)](https://leetcode.com/problems/powx-n/) | 🟡 | Fast exponentiation by squaring |
| ☐ |      | 69  | [Sqrt(x)](https://leetcode.com/problems/sqrtx/) | 🟢 | Binary search on answer |
| ☐ |      | 202 | [Happy Number](https://leetcode.com/problems/happy-number/) | 🟢 | Digit-square cycle → fast/slow pointers |
| ☐ |      | 8   | [String to Integer (atoi)](https://leetcode.com/problems/string-to-integer-atoi/) | 🟡 | Skip ws, sign, clamp to INT range |
| ☐ |      | 13  | [Roman to Integer](https://leetcode.com/problems/roman-to-integer/) | 🟢 | Add, but subtract when smaller precedes larger |

---

# 🎲 Mixed Practice — Pattern Recognition Drill

> Do this **after** you complete all 20 patterns above. For each problem, **predict the pattern** before expanding the answer. Aim for a 60-second decision.

1. [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/) — 🟡  <details><summary>Pattern</summary>Sliding Window</details>
2. [Word Ladder](https://leetcode.com/problems/word-ladder/) — 🔴  <details><summary>Pattern</summary>Graph BFS</details>
3. [House Robber](https://leetcode.com/problems/house-robber/) — 🟡  <details><summary>Pattern</summary>DP — 1D</details>
4. [Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/) — 🟡  <details><summary>Pattern</summary>Fast & Slow Pointers</details>
5. [Course Schedule II](https://leetcode.com/problems/course-schedule-ii/) — 🟡  <details><summary>Pattern</summary>Topological Sort (Graph)</details>
6. [Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/) — 🔴  <details><summary>Pattern</summary>Two Heaps</details>
7. [Daily Temperatures](https://leetcode.com/problems/daily-temperatures/) — 🟡  <details><summary>Pattern</summary>Monotonic Stack</details>
8. [Subsets II](https://leetcode.com/problems/subsets-ii/) — 🟡  <details><summary>Pattern</summary>Backtracking</details>
9. [Koko Eating Bananas](https://leetcode.com/problems/koko-eating-bananas/) — 🟡  <details><summary>Pattern</summary>Binary Search on Answer</details>
10. [Merge Intervals](https://leetcode.com/problems/merge-intervals/) — 🟡  <details><summary>Pattern</summary>Greedy / Intervals</details>
11. [Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/) — 🟡  <details><summary>Pattern</summary>Prefix Sum + Hashing</details>
12. [Edit Distance](https://leetcode.com/problems/edit-distance/) — 🟡  <details><summary>Pattern</summary>DP — 2D</details>
13. [Container With Most Water](https://leetcode.com/problems/container-with-most-water/) — 🟡  <details><summary>Pattern</summary>Two Pointers</details>
14. [Number of Provinces](https://leetcode.com/problems/number-of-provinces/) — 🟡  <details><summary>Pattern</summary>Union-Find</details>
15. [Binary Tree Maximum Path Sum](https://leetcode.com/problems/binary-tree-maximum-path-sum/) — 🔴  <details><summary>Pattern</summary>Tree DFS</details>
16. [Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/) — 🟡  <details><summary>Pattern</summary>Tree BFS</details>
17. [Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/) — 🔴  <details><summary>Pattern</summary>Linked List Manipulation</details>
18. [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/) — 🟡  <details><summary>Pattern</summary>Heap / Top-K</details>
19. [Word Search II](https://leetcode.com/problems/word-search-ii/) — 🔴  <details><summary>Pattern</summary>Trie + Backtracking</details>
20. [Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/) — 🟡  <details><summary>Pattern</summary>DP — 2D (or expand-around-center)</details>
21. [Min Stack](https://leetcode.com/problems/min-stack/) — 🟡  <details><summary>Pattern</summary>Stack</details>
22. [Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/) — 🔴  <details><summary>Pattern</summary>Sliding Window</details>
23. [Jump Game II](https://leetcode.com/problems/jump-game-ii/) — 🟡  <details><summary>Pattern</summary>Greedy</details>
24. [Validate BST](https://leetcode.com/problems/validate-binary-search-tree/) — 🟡  <details><summary>Pattern</summary>Tree DFS</details>
25. [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/) — 🟡  <details><summary>Pattern</summary>Binary Search</details>
26. [Number of Islands](https://leetcode.com/problems/number-of-islands/) — 🟡  <details><summary>Pattern</summary>Graph DFS/BFS</details>
27. [Coin Change](https://leetcode.com/problems/coin-change/) — 🟡  <details><summary>Pattern</summary>DP — 1D</details>
28. [3Sum](https://leetcode.com/problems/3sum/) — 🟡  <details><summary>Pattern</summary>Two Pointers</details>
29. [Permutations](https://leetcode.com/problems/permutations/) — 🟡  <details><summary>Pattern</summary>Backtracking</details>
30. [K Closest Points to Origin](https://leetcode.com/problems/k-closest-points-to-origin/) — 🟡  <details><summary>Pattern</summary>Heap</details>
31. [Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/) — 🔴  <details><summary>Pattern</summary>Two Pointers (or Monotonic Stack)</details>
32. [Implement Trie](https://leetcode.com/problems/implement-trie-prefix-tree/) — 🟡  <details><summary>Pattern</summary>Trie</details>
33. [Decode Ways](https://leetcode.com/problems/decode-ways/) — 🟡  <details><summary>Pattern</summary>DP — 1D</details>
34. [Find Peak Element](https://leetcode.com/problems/find-peak-element/) — 🟡  <details><summary>Pattern</summary>Binary Search</details>
35. [Lowest Common Ancestor](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/) — 🟡  <details><summary>Pattern</summary>Tree DFS</details>
36. [Rotting Oranges](https://leetcode.com/problems/rotting-oranges/) — 🟡  <details><summary>Pattern</summary>Multi-source BFS</details>
37. [Maximum Subarray](https://leetcode.com/problems/maximum-subarray/) — 🟡  <details><summary>Pattern</summary>DP — 1D (Kadane)</details>
38. [Generate Parentheses](https://leetcode.com/problems/generate-parentheses/) — 🟡  <details><summary>Pattern</summary>Backtracking</details>
39. [Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/) — 🔴  <details><summary>Pattern</summary>Monotonic Stack</details>
40. [LRU Cache](https://leetcode.com/problems/lru-cache/) — 🟡  <details><summary>Pattern</summary>Hash Map + Doubly Linked List</details>

---

# 📈 Progress Tracker

**Current streak:** 0 days · **Longest streak:** 0 days · **Total solved:** 0 / ~200

### Weekly review (Sundays — redo 1 random problem from the past week)

| Week | Date | Pattern in focus | Problems solved | Re-solved problem |
|------|------|------------------|-----------------|-------------------|
| 1    |      | Two Pointers     | / 7             |                   |
| 2    |      | Two Pointers + Sliding Window | / 7 |                   |
| 3    |      | Sliding Window + Fast/Slow | / 7 |                   |
| 4    |      | Prefix Sum       | / 7             |                   |
| …    |      |                  |                 |                   |

> Tip: At the end of each week, scan the **Trigger phrase** column you filled in. If two patterns share similar trigger phrases, that's a sign you need to refine them — pattern recognition lives in the *differences*.

---

# 🧭 Daily routine cheat sheet

```
06:30 - 08:30  Mornings:     DSA daily problem (May 12 → Sep 12) → LLD problem (Sep 13 → Oct 25) → DSA upkeep + mocks (Oct 26+)
08:30 - 10:00  Commute out:  LLD concept videos → switches to HLD videos (Sep 13+)
10:00 - 20:30  Office
20:30 - 22:00  Commute back: continue LLD/HLD videos
22:00 - 23:30  Eve (non-class): Project work (3 nights/wk × 1.5 hr)
Class evenings (4 nights/wk): Class — recovery
Saturday + Sunday: Project (~5 hr each) + 1 weekly DSA review slot
1 full off-period/week: Sunday afternoon (mandatory)
```

**Red lines** (never break):
- DSA morning slot is sacred until Sep 12 — never lose to project work.
- One full off-period/week — burnout is the #1 reason 6-month plans fail.
- Project work only in evenings/weekends — never push it into DSA time.
