# DSA Pattern-Based Practice Roadmap (C++)

> Goal: Recognize the **pattern** behind any new problem within 60 seconds, then implement.
> Schedule: 1 problem/day, 7:00–8:00 AM. ~190 problems → ~6 months.

---

## How to use this roadmap

1. **Pick today's problem** from the next unchecked row in the current pattern.
2. **Read the title only** — try to predict the pattern from the title before reading the problem.
3. **Solve in C++** in `solutions/<pattern>/<slug>.cpp`. Aim for an optimal solution.
4. **Before checking your answer**, write your own one-line **trigger phrase** in the table (e.g., *"sorted array → find pair"*). This is what locks in pattern recognition.
5. **Mark the checkbox** (`☐` → `✅`) and fill the **Date**.
6. **Weekly (Sunday)**: redo 1 random problem from the past week without looking at your old code.
7. **After all 16 patterns**: jump to **Mixed Practice** at the bottom — predict the pattern *before* expanding the answer.

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
| ☐ |      | 523 | [Continuous Subarray Sum](https://leetcode.com/problems/continuous-subarray-sum/) | 🟡 |  |
| ☐ |      | 525 | [Contiguous Array](https://leetcode.com/problems/contiguous-array/) | 🟡 |  |
| ☐ |      | 1248| [Count Number of Nice Subarrays](https://leetcode.com/problems/count-number-of-nice-subarrays/) | 🟡 |  |
| ☐ |      | 437 | [Path Sum III](https://leetcode.com/problems/path-sum-iii/) | 🟡 |  |
| ☐ |      | 49  | [Group Anagrams](https://leetcode.com/problems/group-anagrams/) | 🟡 |  |
| ☐ |      | 128 | [Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/) | 🟡 |  |
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
| ☐ |      | 704 | [Binary Search](https://leetcode.com/problems/binary-search/) | 🟢 |  |
| ☐ |      | 35  | [Search Insert Position](https://leetcode.com/problems/search-insert-position/) | 🟢 |  |
| ☐ |      | 278 | [First Bad Version](https://leetcode.com/problems/first-bad-version/) | 🟢 |  |
| ☐ |      | 33  | [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/) | 🟡 |  |
| ☐ |      | 153 | [Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/) | 🟡 |  |
| ☐ |      | 34  | [Find First and Last Position of Element](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/) | 🟡 |  |
| ☐ |      | 162 | [Find Peak Element](https://leetcode.com/problems/find-peak-element/) | 🟡 |  |
| ☐ |      | 74  | [Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/) | 🟡 |  |
| ☐ |      | 875 | [Koko Eating Bananas](https://leetcode.com/problems/koko-eating-bananas/) | 🟡 |  |
| ☐ |      | 1011| [Capacity to Ship Packages Within D Days](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/) | 🟡 |  |
| ☐ |      | 410 | [Split Array Largest Sum](https://leetcode.com/problems/split-array-largest-sum/) | 🔴 |  |
| ☐ |      | 4   | [Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays/) | 🔴 |  |

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
| ☐ |      | 20  | [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/) | 🟢 |  |
| ☐ |      | 155 | [Min Stack](https://leetcode.com/problems/min-stack/) | 🟡 |  |
| ☐ |      | 150 | [Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/) | 🟡 |  |
| ☐ |      | 739 | [Daily Temperatures](https://leetcode.com/problems/daily-temperatures/) | 🟡 |  |
| ☐ |      | 496 | [Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/) | 🟢 |  |
| ☐ |      | 503 | [Next Greater Element II](https://leetcode.com/problems/next-greater-element-ii/) | 🟡 |  |
| ☐ |      | 901 | [Online Stock Span](https://leetcode.com/problems/online-stock-span/) | 🟡 |  |
| ☐ |      | 71  | [Simplify Path](https://leetcode.com/problems/simplify-path/) | 🟡 |  |
| ☐ |      | 394 | [Decode String](https://leetcode.com/problems/decode-string/) | 🟡 |  |
| ☐ |      | 22  | [Generate Parentheses](https://leetcode.com/problems/generate-parentheses/) | 🟡 |  |
| ☐ |      | 84  | [Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/) | 🔴 |  |
| ☐ |      | 85  | [Maximal Rectangle](https://leetcode.com/problems/maximal-rectangle/) | 🔴 |  |

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

**Problems:**

| ✓ | Date | # | Problem | Diff | Trigger phrase |
|---|------|---|---------|------|----------------|
| ☐ |      | 206 | [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/) | 🟢 |  |
| ☐ |      | 21  | [Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/) | 🟢 |  |
| ☐ |      | 83  | [Remove Duplicates from Sorted List](https://leetcode.com/problems/remove-duplicates-from-sorted-list/) | 🟢 |  |
| ☐ |      | 92  | [Reverse Linked List II](https://leetcode.com/problems/reverse-linked-list-ii/) | 🟡 |  |
| ☐ |      | 86  | [Partition List](https://leetcode.com/problems/partition-list/) | 🟡 |  |
| ☐ |      | 24  | [Swap Nodes in Pairs](https://leetcode.com/problems/swap-nodes-in-pairs/) | 🟡 |  |
| ☐ |      | 61  | [Rotate List](https://leetcode.com/problems/rotate-list/) | 🟡 |  |
| ☐ |      | 138 | [Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/) | 🟡 |  |
| ☐ |      | 148 | [Sort List](https://leetcode.com/problems/sort-list/) | 🟡 |  |
| ☐ |      | 2   | [Add Two Numbers](https://leetcode.com/problems/add-two-numbers/) | 🟡 |  |
| ☐ |      | 25  | [Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/) | 🔴 |  |
| ☐ |      | 23  | [Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/) | 🔴 |  |

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
| ☐ |      | 104 | [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/) | 🟢 |  |
| ☐ |      | 100 | [Same Tree](https://leetcode.com/problems/same-tree/) | 🟢 |  |
| ☐ |      | 226 | [Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/) | 🟢 |  |
| ☐ |      | 543 | [Diameter of Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree/) | 🟢 |  |
| ☐ |      | 110 | [Balanced Binary Tree](https://leetcode.com/problems/balanced-binary-tree/) | 🟢 |  |
| ☐ |      | 112 | [Path Sum](https://leetcode.com/problems/path-sum/) | 🟢 |  |
| ☐ |      | 98  | [Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/) | 🟡 |  |
| ☐ |      | 230 | [Kth Smallest Element in a BST](https://leetcode.com/problems/kth-smallest-element-in-a-bst/) | 🟡 |  |
| ☐ |      | 236 | [Lowest Common Ancestor of a Binary Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/) | 🟡 |  |
| ☐ |      | 105 | [Construct Binary Tree from Preorder and Inorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/) | 🟡 |  |
| ☐ |      | 124 | [Binary Tree Maximum Path Sum](https://leetcode.com/problems/binary-tree-maximum-path-sum/) | 🔴 |  |
| ☐ |      | 297 | [Serialize and Deserialize Binary Tree](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/) | 🔴 |  |

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
| ☐ |      | 102 | [Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/) | 🟡 |  |
| ☐ |      | 107 | [Level Order Traversal II](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/) | 🟡 |  |
| ☐ |      | 103 | [Zigzag Level Order Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/) | 🟡 |  |
| ☐ |      | 199 | [Binary Tree Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/) | 🟡 |  |
| ☐ |      | 637 | [Average of Levels in Binary Tree](https://leetcode.com/problems/average-of-levels-in-binary-tree/) | 🟢 |  |
| ☐ |      | 111 | [Minimum Depth of Binary Tree](https://leetcode.com/problems/minimum-depth-of-binary-tree/) | 🟢 |  |
| ☐ |      | 116 | [Populating Next Right Pointers in Each Node](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/) | 🟡 |  |
| ☐ |      | 117 | [Populating Next Right Pointers II](https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii/) | 🟡 |  |
| ☐ |      | 515 | [Find Largest Value in Each Tree Row](https://leetcode.com/problems/find-largest-value-in-each-tree-row/) | 🟡 |  |
| ☐ |      | 1161| [Maximum Level Sum of a Binary Tree](https://leetcode.com/problems/maximum-level-sum-of-a-binary-tree/) | 🟡 |  |

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
| ☐ |      | 200 | [Number of Islands](https://leetcode.com/problems/number-of-islands/) | 🟡 |  |
| ☐ |      | 695 | [Max Area of Island](https://leetcode.com/problems/max-area-of-island/) | 🟡 |  |
| ☐ |      | 994 | [Rotting Oranges](https://leetcode.com/problems/rotting-oranges/) | 🟡 |  |
| ☐ |      | 130 | [Surrounded Regions](https://leetcode.com/problems/surrounded-regions/) | 🟡 |  |
| ☐ |      | 133 | [Clone Graph](https://leetcode.com/problems/clone-graph/) | 🟡 |  |
| ☐ |      | 207 | [Course Schedule](https://leetcode.com/problems/course-schedule/) | 🟡 |  |
| ☐ |      | 210 | [Course Schedule II](https://leetcode.com/problems/course-schedule-ii/) | 🟡 |  |
| ☐ |      | 785 | [Is Graph Bipartite?](https://leetcode.com/problems/is-graph-bipartite/) | 🟡 |  |
| ☐ |      | 417 | [Pacific Atlantic Water Flow](https://leetcode.com/problems/pacific-atlantic-water-flow/) | 🟡 |  |
| ☐ |      | 1091| [Shortest Path in Binary Matrix](https://leetcode.com/problems/shortest-path-in-binary-matrix/) | 🟡 |  |
| ☐ |      | 127 | [Word Ladder](https://leetcode.com/problems/word-ladder/) | 🔴 |  |
| ☐ |      | 269 | [Alien Dictionary](https://leetcode.com/problems/alien-dictionary/) | 🔴 |  |

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

# 🎲 Mixed Practice — Pattern Recognition Drill

> Do this **after** you complete all 16 patterns above. For each problem, **predict the pattern** before expanding the answer. Aim for a 60-second decision.

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

**Current streak:** 0 days · **Longest streak:** 0 days · **Total solved:** 0 / ~190

### Weekly review (Sundays — redo 1 random problem from the past week)

| Week | Date | Pattern in focus | Problems solved | Re-solved problem |
|------|------|------------------|-----------------|-------------------|
| 1    |      | Two Pointers     | / 7             |                   |
| 2    |      | Two Pointers + Sliding Window | / 7 |                   |
| 3    |      | Sliding Window + Fast/Slow | / 7 |                   |
| 4    |      | Prefix Sum       | / 7             |                   |
| …    |      |                  |                 |                   |

> Tip: At the end of each week, scan the **Trigger phrase** column you filled in. If two patterns share similar trigger phrases, that's a sign you need to refine them — pattern recognition lives in the *differences*.
