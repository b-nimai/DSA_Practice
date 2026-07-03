# C++ Lambdas — 60-sec Revision

> **One-liner:** A lambda is a function you can carry around like a variable — and `[ ]` is the list of things it's allowed to remember from where it was born.

**Trigger:** need a throwaway function inline (comparator, accumulator, recursive DSA helper) → reach for a lambda.

## Anatomy (always this order)
```cpp
[ captures ] ( parameters ) -> return_type { body }
```
| Piece | Example | Meaning |
|-------|---------|---------|
| `[ ]` capture | `[&]` | which outer variables the lambda can see/use |
| `( )` params | `(int a)` | normal function arguments |
| `-> T` return | `-> Node*` | return type — **optional**, compiler usually infers it |
| `{ }` body | code | the logic |

## The capture list `[ ]` — the only genuinely new part
A normal function can't see local vars where it's called; a lambda **can**, but only what you list in `[ ]`.

| Capture | Meaning | Mnemonic |
|---------|---------|----------|
| `[&]` | everything **by reference** (share the real variable) | `&` = address = the real thing |
| `[=]` | everything **by value** (private copy) | `=` = copy |
| `[&x]` | just `x` by reference | |
| `[x]`  | just `x` by copy | |
| `[]`   | capture **nothing** (pure function) | |

> **Rule of thumb:** `[&]` when you want to **modify** outer state (accumulate into a map/sum) · `[=]` when you just want a read-only **snapshot** · `[]` when it needs nothing. In DSA, `[&]` is the default.

## Recursion needs `std::function`, not `auto`
A recursive lambda calls its own name inside itself — but `auto f = [&]{ ... f ... }` fails, because `f`'s type isn't known yet at that point. Give it a concrete type:
```cpp
function<ReturnType(ArgTypes)> name = [&](...) { ... name(...) ... };
```
`function<int(int)>` = "any callable taking an `int`, returning an `int`." Now the name exists for the body to call.

## The 3 lines that cover 90% of DSA use
```cpp
// 1. throwaway comparator — captures nothing
sort(v.begin(), v.end(), [](int a, int b){ return a > b; });   // descending

// 2. capture-by-ref to accumulate
int sum = 0;
for_each(v.begin(), v.end(), [&](int x){ sum += x; });

// 3. recursive helper (needs std::function for the self-name)
function<int(int)> fib = [&](int n){ return n < 2 ? n : fib(n-1) + fib(n-2); };
```

## Pitfalls
- **`[=]` on state you mean to mutate** — each call edits its own copy; e.g. a `[=]`-captured visited map never accumulates → infinite recursion / wrong answer. Use `[&]`.
- **`auto` on a recursive lambda** — won't compile; the self-name doesn't exist yet. Use `function<...>`.
- **Dangling reference** — a `[&]` lambda that outlives the captured variable (e.g. returned from a function) reads freed memory. Fine for local DSA helpers, dangerous when stored/returned.
- **Forgetting `-> T`** — usually fine (inferred), but needed when the body has multiple `return`s of different-looking types, or you want to force a type (e.g. `-> Node*`).

*Seen in:* [[8. Graph/5. 133. Clone Graph|Clone Graph]] uses `function<Node*(Node*)>` with `[&]` capture for the recursive DFS clone.
