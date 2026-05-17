# 🚀 Abishek's Complete Full Stack / Frontend Interview Preparation Handbook
### Senior Engineer Review · Tailored for React · Next.js · WordPress · Shopify · Full Stack Roles
> **Your foundation:** 2.5+ years | Lynkify (100K+ visitors SaaS) | PI Industries | Beretta Gallery Shopify | Godrej Properties
> **Target:** Frontend · React · Next.js · WordPress · Shopify · Full Stack · Commerce + AI roles

---

# TABLE OF CONTENTS

1. [Interview Roadmap (7-day & 14-day plans)](#section-1)
2. [Question Priority System](#section-2)
3. [JavaScript Deep Dive](#section-3)
4. [React Deep Dive](#section-4)
5. [Next.js Deep Dive](#section-5)
6. [WordPress Deep Dive](#section-6)
7. [Shopify Deep Dive](#section-7)
8. [APIs & Backend Basics](#section-8)
9. [System Design & Architecture](#section-9)
10. [Performance Optimization](#section-10)
11. [Git & Deployment](#section-11)
12. [Coding Questions](#section-12)
13. [Behavioral & HR Questions](#section-13)
14. [Portfolio & Project Discussion](#section-14)
15. [Mock Interview Simulations](#section-15)
16. [Final Revision Notes & Cheat Sheet](#section-16)

---

<a name="section-1"></a>
# SECTION 1 — INTERVIEW ROADMAP

## Your Situation Context
You have ~20 days in notice period, actively applying and interviewing in parallel. The strategy below is designed around that reality: short focused sprints, not marathon study sessions. You are not starting from zero — you have real production experience. The goal is to **rebuild recall and confidence**, not learn new things.

---

## 🗓️ 7-Day Crash Plan (For Immediate Interviews)

| Day | Focus Area | Priority | Time | What To Do |
|-----|-----------|----------|------|-----------|
| **Day 1** | JavaScript Core | CRITICAL | 3–4 hrs | Closures, hoisting, event loop, promises, async/await. Write every concept once by hand. |
| **Day 2** | React Fundamentals | CRITICAL | 3–4 hrs | Hooks (useEffect, useMemo, useCallback, useRef), Virtual DOM, reconciliation, memoization |
| **Day 3** | Next.js + API Routes | HIGH | 3 hrs | SSR vs SSG vs ISR vs CSR, App Router, Server Components, image optimization, SEO |
| **Day 4** | WordPress + Shopify | HIGH | 3 hrs | Actions/filters, WP_Query, ACF, Liquid basics, Shopify sections/snippets, Storefront API |
| **Day 5** | System Design + Performance | HIGH | 3 hrs | Component architecture, Core Web Vitals, lazy loading, caching, Lighthouse |
| **Day 6** | Coding Practice | CRITICAL | 4 hrs | Top 15 JS coding problems, 5 React problems. Practice explaining out loud. |
| **Day 7** | Behavioral + Portfolio | CRITICAL | 3 hrs | "Tell me about yourself" script, project explanations (Lynkify, Shopify, PI Industries) |

**Daily Revision Strategy:** End each day by writing 5 bullet points from memory about what you studied. Don't look. This forces recall.

**What to Memorize vs Understand:**
- **Memorize:** Event loop order (call stack → microtasks → macrotasks), HTTP status codes, Git commands, hook rules
- **Understand deeply:** Closure mechanics, reconciliation algorithm, SSR hydration, why useEffect dependency array matters

---

## 🗓️ 14-Day Strong Preparation Plan

| Day | Topics | Time | Priority |
|-----|--------|------|----------|
| 1 | JS: var/let/const, hoisting, scope, execution context | 3 hrs | CRITICAL |
| 2 | JS: closures, this keyword, bind/call/apply, prototype | 3 hrs | CRITICAL |
| 3 | JS: Promises, async/await, event loop, microtasks | 3 hrs | CRITICAL |
| 4 | JS: Array methods, destructuring, spread/rest, modules, ES6+ | 2 hrs | HIGH |
| 5 | React: Virtual DOM, hooks overview, useState, useEffect deep | 3 hrs | CRITICAL |
| 6 | React: useMemo, useCallback, useRef, Context API, memoization | 3 hrs | HIGH |
| 7 | React: Performance, custom hooks, error boundaries, Suspense, lazy | 2 hrs | HIGH |
| 8 | Next.js: Rendering strategies, App Router vs Pages Router | 3 hrs | CRITICAL |
| 9 | Next.js: Server components, API routes, middleware, auth, SEO | 3 hrs | HIGH |
| 10 | WordPress: Hooks, WP_Query, CPTs, ACF, REST API, WooCommerce | 3 hrs | HIGH |
| 11 | Shopify: Liquid, theme structure, Storefront API, headless | 2 hrs | HIGH |
| 12 | System Design + APIs + Performance | 3 hrs | HIGH |
| 13 | Coding practice (JS + React problems) + Git/Deployment | 4 hrs | CRITICAL |
| 14 | Behavioral, portfolio stories, mock interview (full simulation) | 3 hrs | CRITICAL |

**Mock Interview Practice:** From Day 7 onward, practice answering one technical question out loud every morning before you open any notes. Record yourself on your phone. Watch it back. This trains verbal articulation.

---

<a name="section-2"></a>
# SECTION 2 — QUESTION PRIORITY SYSTEM

Every question in this guide is tagged with:

| Tag | Meaning |
|-----|---------|
| 🔴 VERY COMMON | Asked in 80%+ of interviews |
| 🟠 COMMON | Asked in 50–80% of interviews |
| 🟡 OCCASIONAL | Asked in 25–50% |
| ⚪ RARE | Specialized/senior-only |
| ⭐ CRITICAL | Must know cold |
| 🔥 HIGH | Strong to know |
| 💡 MEDIUM | Good to have |
| 📘 LOW | Bonus points |
| 🟢 EASY | Junior-friendly |
| 🟡 MEDIUM | Mid-level |
| 🔴 HARD | Senior-level |

---

<a name="section-3"></a>
# SECTION 3 — JAVASCRIPT (VERY DEEP)

> The interviewer mindset: JavaScript questions reveal whether you truly understand how the browser and engine work, or whether you've just been copying patterns. Even for React/Next.js roles, JavaScript fundamentals are almost always tested first.

---

## 3.1 — var vs let vs const

🔴 VERY COMMON | ⭐ CRITICAL | 🟢 EASY

**Explanation from First Principles:**

Every variable in JavaScript lives inside a *scope* — a boundary that controls where the variable is accessible. Before ES6 (2015), JavaScript only had `var`. ES6 introduced `let` and `const` to fix real-world bugs caused by `var`'s confusing behavior.

```javascript
// var — function scoped, hoisted with value undefined
function example() {
  console.log(x); // undefined — NOT an error! (hoisting)
  var x = 10;
  console.log(x); // 10
}

// let — block scoped, hoisted but NOT initialized (Temporal Dead Zone)
function example2() {
  console.log(y); // ReferenceError: Cannot access 'y' before initialization
  let y = 10;
}

// const — block scoped, must be assigned at declaration, cannot be reassigned
const z = 10;
z = 20; // TypeError: Assignment to constant variable

// BUT: const objects/arrays can be mutated
const arr = [1, 2, 3];
arr.push(4); // ALLOWED — you're not reassigning arr, you're mutating it
arr = [5, 6]; // NOT allowed
```

**Why it matters in real production code:** Using `var` inside loops is a classic source of bugs because `var` leaks outside the loop block. `let` fixes this.

```javascript
// Classic var bug in loops
for (var i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 100); // prints 3, 3, 3 — NOT 0, 1, 2
}

// Fixed with let (block scoped — each iteration gets its own i)
for (let i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 100); // prints 0, 1, 2 ✅
}
```

**Interview Answer (say this out loud):**
> "var is function-scoped and gets hoisted to the top of its function with the value undefined. let and const are block-scoped, so they're confined to the nearest curly brace block. Both are hoisted but placed in a Temporal Dead Zone — accessing them before their declaration throws a ReferenceError. const additionally prevents reassignment of the binding itself, though it doesn't prevent mutation of object or array values. In modern JavaScript, I default to const everywhere and use let only when I know the value needs to change."

**Common Mistakes Candidates Make:**
- Saying "const makes a value immutable" — No, it makes the *binding* immutable. The object's contents can still change.
- Not knowing about the Temporal Dead Zone for let/const.

**Follow-up Questions:**
- "What is the Temporal Dead Zone?" → The period between the start of the block and the let/const declaration — accessing the variable in this zone throws a ReferenceError.
- "Can you explain the var loop bug with closures?" → See the setTimeout example above.

---

## 3.2 — == vs ===

🔴 VERY COMMON | ⭐ CRITICAL | 🟢 EASY

**Explanation:**
`==` performs *type coercion* before comparison — JavaScript tries to convert one value to match the other's type. `===` performs *strict equality* — no conversion, both type AND value must match.

```javascript
// == with type coercion
0 == false        // true  (false coerces to 0)
"" == false       // true  (both coerce to 0)
null == undefined // true  (special rule — they only equal each other)
1 == "1"          // true  (string "1" coerces to number 1)

// === strict
0 === false       // false (different types)
1 === "1"         // false
null === undefined// false

// Trick questions
NaN == NaN        // false (NaN is not equal to anything, including itself)
NaN === NaN       // false — use Number.isNaN() instead
```

**Interview Answer:**
> "I always use === in production because == has surprising type coercion rules that can cause subtle bugs. The only edge case I'm careful about is null checks — null == undefined is true with ==, which can sometimes be useful, but I still prefer explicit checks like value === null || value === undefined."

**Common Mistakes:**
- Forgetting that `NaN !== NaN` — use `Number.isNaN()` or `Object.is(NaN, NaN)` which returns true.

---

## 3.3 — Hoisting

🔴 VERY COMMON | ⭐ CRITICAL | 🟡 MEDIUM

**Explanation:**
Hoisting is JavaScript's behavior of moving declarations to the top of their scope during the compilation phase, *before* any code runs. Understanding this requires understanding that JavaScript runs in two phases: compilation (where declarations are registered) and execution (where code actually runs).

```javascript
// Function declarations are fully hoisted (both name AND body)
greet(); // "Hello!" — works even before declaration
function greet() {
  console.log("Hello!");
}

// var declarations: name is hoisted, but value stays undefined
console.log(name); // undefined — no error
var name = "Abishek";
console.log(name); // "Abishek"

// Function expressions with var: same as var — only the variable name is hoisted
sayHi(); // TypeError: sayHi is not a function
var sayHi = function() {
  console.log("Hi!");
};

// let and const: Hoisted but in Temporal Dead Zone
console.log(age); // ReferenceError
let age = 25;
```

**Mental Model:** Think of hoisting as JavaScript doing a "pre-scan" of your code before executing it. During that pre-scan, it registers all var declarations (with undefined) and all function declarations (complete). Then when execution begins, it runs line by line.

**Interview Answer:**
> "Hoisting is JavaScript's behavior of processing declarations before code executes. Function declarations are fully hoisted — you can call them before they appear in the code. var declarations are hoisted but initialized to undefined, which is why accessing them before assignment gives undefined instead of an error. let and const are also hoisted but placed in a Temporal Dead Zone, so accessing them before their declaration throws a ReferenceError. In practice, I write code in execution order to avoid any hoisting surprises."

**Trick Questions:**
- "What happens if you have both a var and a function with the same name?" → The function declaration takes precedence.

```javascript
console.log(typeof foo); // "function" — function wins over var
var foo = 1;
function foo() {}
```

---

## 3.4 — Execution Context & Call Stack

🟠 COMMON | ⭐ CRITICAL | 🟡 MEDIUM

**Explanation:**
An *execution context* is the environment in which JavaScript code runs. Think of it as a "bubble" that contains: the variables accessible in that code, the value of `this`, and a reference to the outer scope.

There are three types:
1. **Global Execution Context** — created when your script first loads. Creates the global object (`window` in browsers) and sets `this` to it.
2. **Function Execution Context** — created every time a function is called.
3. **Eval Execution Context** — rarely used.

```javascript
// The Call Stack — JavaScript's "to-do list"
function first() {
  console.log("Inside first");
  second(); // pushes second() onto the stack
  console.log("Back in first");
}

function second() {
  console.log("Inside second");
  // when second() finishes, it's popped off the stack
}

first();
// Call stack sequence:
// [global] → [global, first()] → [global, first(), second()]
// → [global, first()] (second popped) → [global] (first popped)
```

**Diagram:**
```
CALL STACK (Last In, First Out)
┌─────────────┐
│  second()   │ ← top (currently executing)
├─────────────┤
│   first()   │
├─────────────┤
│   global    │ ← bottom (always present)
└─────────────┘
```

**Interview Answer:**
> "Every time JavaScript runs code, it creates an execution context — basically a container holding the current scope's variables, the value of this, and a reference to the outer scope for closures. These contexts are managed by the call stack, which is a LIFO data structure. When a function is called, a new context is pushed onto the stack. When it returns, it's popped off. This is why stack overflow errors happen — infinite recursion keeps pushing contexts until the stack runs out of memory."

---

## 3.5 — Scope & Scope Chain

🟠 COMMON | ⭐ CRITICAL | 🟢 EASY

**Explanation:**
Scope determines where a variable is accessible. JavaScript has:
- **Global scope** — accessible everywhere
- **Function scope** — accessible only within the function
- **Block scope** (ES6+) — accessible only within `{}` for let/const

The *scope chain* is how JavaScript looks up variables: it starts in the current scope, then goes to the outer scope, then its outer scope, all the way up to global. If it can't find the variable, it throws a ReferenceError.

```javascript
const globalVar = "I'm global"; // global scope

function outer() {
  const outerVar = "I'm outer"; // outer function scope

  function inner() {
    const innerVar = "I'm inner"; // inner function scope
    
    // inner can access all of these:
    console.log(innerVar);  // own scope
    console.log(outerVar);  // outer scope (scope chain)
    console.log(globalVar); // global scope (scope chain)
  }

  // outer CANNOT access innerVar:
  // console.log(innerVar); // ReferenceError
}
```

---

## 3.6 — Closures

🔴 VERY COMMON | ⭐ CRITICAL | 🟡 MEDIUM

**Explanation (the most important concept in JS interviews):**
A closure is when a function "remembers" the variables from its outer scope even after the outer function has finished executing. This works because functions in JavaScript carry a reference to the scope chain where they were *defined*, not where they are *called*.

```javascript
// Classic closure example
function makeCounter() {
  let count = 0; // this variable is "closed over"
  
  return function() {
    count++; // inner function remembers count
    return count;
  };
}

const counter = makeCounter(); // makeCounter() finishes, but count lives on
console.log(counter()); // 1
console.log(counter()); // 2
console.log(counter()); // 3

// Another counter doesn't share state
const counter2 = makeCounter();
console.log(counter2()); // 1 — independent
```

**Real-World Usage from your work:**
In Lynkify, you might use closures for event handlers that need to reference component-specific state, or for factory functions that create customized API calls.

```javascript
// Real-world: closure for configuring API requests
function createApiClient(baseURL, token) {
  // baseURL and token are "closed over"
  return {
    get: (endpoint) => fetch(`${baseURL}${endpoint}`, {
      headers: { Authorization: `Bearer ${token}` }
    }),
    post: (endpoint, body) => fetch(`${baseURL}${endpoint}`, {
      method: "POST",
      headers: { Authorization: `Bearer ${token}`, "Content-Type": "application/json" },
      body: JSON.stringify(body)
    })
  };
}

const api = createApiClient("https://api.lynkify.in", userToken);
api.get("/profile"); // token is automatically included
```

**Why Closures Matter:**
- React's `useState` relies on closures internally
- Event listeners that reference state are closures
- Module patterns use closures to create private state
- Debounce and throttle implementations use closures

**Interview Answer:**
> "A closure is a function that retains access to its outer scope's variables even after that outer function has returned. This works because JavaScript functions carry a reference to the lexical environment where they were defined. I use closures constantly — React hooks use them under the hood to capture state values, my factory functions for API clients use them to encapsulate auth tokens, and debounce/throttle utilities use them to store timers. One important gotcha is the stale closure problem in React — if a useEffect or useCallback captures a state value via closure but doesn't list it in the dependency array, it will always see the old value."

**Stale Closure Problem (very important for React interviews):**
```javascript
// Stale closure in React
function Counter() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => {
      // BUG: count is captured at 0 (stale closure)
      console.log(count); // always prints 0
    }, 1000);
    return () => clearInterval(interval);
  }, []); // [] means the closure captures count = 0 and never updates
}

// Fix: use functional update form
setCount(prev => prev + 1); // doesn't rely on captured value
// OR add count to the dependency array
useEffect(() => { ... }, [count]);
```

**Follow-up Questions:**
- "What is a stale closure?" → Above example.
- "How do closures cause memory leaks?" → If a closure holds a reference to a large object and the closure itself lives forever (e.g., an unremoved event listener), the object can never be garbage collected.

---

## 3.7 — Event Loop, Call Stack, Microtasks vs Macrotasks

🔴 VERY COMMON | ⭐ CRITICAL | 🔴 HARD

**This is probably the most commonly tested "deep JS" concept. Know this cold.**

**Explanation from first principles:**
JavaScript is single-threaded — it can only do one thing at a time. But browsers need to handle things like timers, network requests, and user events without freezing the page. The *event loop* is the mechanism that makes this possible.

**The components:**
1. **Call Stack** — where JavaScript runs code, one frame at a time
2. **Web APIs** — browser-provided tools (setTimeout, fetch, DOM events). Not part of JavaScript itself.
3. **Microtask Queue** — for Promises, queueMicrotask(), MutationObserver
4. **Macrotask Queue (Task Queue)** — for setTimeout, setInterval, setImmediate, I/O events

**The Event Loop Rule:** After each task completes on the call stack, the event loop first drains ALL microtasks, then picks one macrotask, then drains microtasks again, etc.

```
┌─────────────────────────────────────────────┐
│                  CALL STACK                  │
│  (currently executing code goes here)        │
└──────────────────┬──────────────────────────┘
                   │ (empty? check queues)
                   ▼
┌─────────────────────────────────────────────┐
│            MICROTASK QUEUE                   │
│  Promise.then(), queueMicrotask()            │
│  → ALL microtasks run before next macrotask  │
└──────────────────┬──────────────────────────┘
                   │ (queue empty)
                   ▼
┌─────────────────────────────────────────────┐
│            MACROTASK QUEUE                   │
│  setTimeout, setInterval, UI events          │
│  → ONE macrotask runs, then microtasks again │
└─────────────────────────────────────────────┘
```

**Classic Interview Question:**
```javascript
console.log("1");

setTimeout(() => console.log("2"), 0);

Promise.resolve().then(() => console.log("3"));

console.log("4");

// Output order: 1, 4, 3, 2
// Why?
// "1" — synchronous, runs immediately on call stack
// setTimeout callback → goes to macrotask queue (even with 0ms delay)
// Promise.then callback → goes to microtask queue
// "4" — synchronous, runs next on call stack
// Call stack now empty → microtasks drain first: "3"
// Then one macrotask: "2"
```

**More Complex Example:**
```javascript
console.log("start");

setTimeout(() => {
  console.log("timeout 1");
  Promise.resolve().then(() => console.log("promise inside timeout"));
}, 0);

Promise.resolve()
  .then(() => {
    console.log("promise 1");
    return Promise.resolve();
  })
  .then(() => console.log("promise 2"));

setTimeout(() => console.log("timeout 2"), 0);

console.log("end");

// Output: start, end, promise 1, promise 2, timeout 1, promise inside timeout, timeout 2
```

**Interview Answer:**
> "JavaScript is single-threaded, so it uses an event loop to handle asynchronous operations. When async operations complete — like a timer firing or a network response arriving — their callbacks are placed in queues. There are two types: the microtask queue for Promises and MutationObserver, and the macrotask queue for setTimeout and setInterval. The event loop works like this: after the call stack empties, it first drains every pending microtask completely, then picks exactly one macrotask, then drains microtasks again. This means Promise callbacks always run before setTimeout callbacks, even if the timeout is set to 0ms."

**Follow-up Questions:**
- "What happens if a microtask adds another microtask?" → It gets added to the microtask queue and runs before any macrotask — you can create an infinite loop of microtasks that blocks the macrotask queue entirely.
- "Why does setTimeout(..., 0) not mean 'run immediately'?" → Because 0ms delay just means "add to macrotask queue as soon as possible," but it still waits for the call stack to empty and all microtasks to drain first.

---

## 3.8 — Promises

🔴 VERY COMMON | ⭐ CRITICAL | 🟡 MEDIUM

**Explanation:**
A Promise represents the eventual completion or failure of an asynchronous operation. It exists in one of three states: **pending**, **fulfilled** (resolved), or **rejected**. Once settled (fulfilled or rejected), a Promise cannot change state.

```javascript
// Creating a Promise
const fetchData = new Promise((resolve, reject) => {
  // Simulating async work
  setTimeout(() => {
    const success = true;
    if (success) {
      resolve({ data: "user data" }); // fulfills the promise
    } else {
      reject(new Error("Something went wrong")); // rejects the promise
    }
  }, 1000);
});

// Consuming a Promise
fetchData
  .then(result => {
    console.log(result.data); // "user data"
    return result.data; // chain: value passed to next .then
  })
  .then(data => console.log("Processed:", data))
  .catch(error => console.error("Error:", error.message))
  .finally(() => console.log("Always runs"));
```

**Promise Methods — Critical for interviews:**
```javascript
// Promise.all — all must resolve, rejects if ANY reject
const [user, posts, comments] = await Promise.all([
  fetchUser(id),
  fetchPosts(id),
  fetchComments(id)
]);

// Promise.allSettled — waits for ALL, never rejects, gives status of each
const results = await Promise.allSettled([
  fetchUser(id),
  fetchPosts(id),
  failingRequest() // this one fails
]);
results.forEach(r => {
  if (r.status === "fulfilled") console.log(r.value);
  else console.log(r.reason);
});

// Promise.race — resolves/rejects with whichever settles FIRST
const result = await Promise.race([
  fetchWithTimeout(url, 5000),
  timeoutPromise(5000) // reject after 5 seconds
]);

// Promise.any — resolves with first fulfilled, rejects only if ALL reject (AggregateError)
const fastest = await Promise.any([mirror1, mirror2, mirror3]);
```

**Interview Answer:**
> "A Promise is an object representing the future result of an asynchronous operation. It has three states — pending, fulfilled, and rejected — and once settled, its state never changes. I chain Promises with .then() and .catch(), and for parallel operations I use Promise.all when all requests must succeed, Promise.allSettled when I want results regardless of failures, Promise.race when I need whichever resolves first (like implementing timeouts), and Promise.any when I want the first success."

---

## 3.9 — async/await

🔴 VERY COMMON | ⭐ CRITICAL | 🟢 EASY

**Explanation:**
`async/await` is syntactic sugar over Promises. It makes asynchronous code look and read like synchronous code. An `async` function always returns a Promise. `await` can only be used inside an `async` function, and it pauses execution of that function until the awaited Promise settles.

```javascript
// Without async/await (Promise chaining)
function fetchUserData(id) {
  return fetch(`/api/users/${id}`)
    .then(res => {
      if (!res.ok) throw new Error(`HTTP error! status: ${res.status}`);
      return res.json();
    })
    .then(user => {
      return fetch(`/api/posts?userId=${user.id}`);
    })
    .then(res => res.json())
    .catch(error => console.error(error));
}

// With async/await — much cleaner
async function fetchUserData(id) {
  try {
    const userRes = await fetch(`/api/users/${id}`);
    if (!userRes.ok) throw new Error(`HTTP error! status: ${userRes.status}`);
    
    const user = await userRes.json();
    const postsRes = await fetch(`/api/posts?userId=${user.id}`);
    const posts = await postsRes.json();
    
    return { user, posts };
  } catch (error) {
    console.error("Error fetching user data:", error);
    throw error; // re-throw so caller can handle
  }
}

// Parallel execution with async/await
async function fetchAll(userId) {
  // Sequential (slow — waits for each)
  const user = await fetchUser(userId);
  const posts = await fetchPosts(userId); // only starts after user is done

  // Parallel (fast — both start simultaneously)
  const [user2, posts2] = await Promise.all([
    fetchUser(userId),
    fetchPosts(userId)
  ]);
}
```

**Common Mistake — forgetting to make function async:**
```javascript
// This doesn't work
const handler = () => {
  const data = await fetch("/api/data"); // SyntaxError!
};

// Fix:
const handler = async () => {
  const data = await fetch("/api/data"); // ✅
};
```

**Interview Answer:**
> "async/await is syntactic sugar over Promises that makes async code read linearly. An async function always returns a Promise implicitly. await pauses that function's execution — not the entire thread — until the awaited Promise resolves. I always wrap await calls in try/catch for error handling. One important pattern is to use Promise.all with await when I have multiple independent requests, because sequential awaits run one after another and are significantly slower."

---

## 3.10 — Debounce vs Throttle

🟠 COMMON | 🔥 HIGH | 🟡 MEDIUM

**Explanation:**
Both are performance optimization techniques that limit how often a function executes. Understanding them requires understanding *when* you want to run a function.

**Debounce:** Delays execution until there's been a pause in activity. "Wait until the user stops typing, THEN run."

**Throttle:** Ensures execution happens at most once per time window. "Run at most once every 300ms, regardless of how many times it's triggered."

```javascript
// DEBOUNCE implementation
function debounce(fn, delay) {
  let timer;
  return function(...args) {
    clearTimeout(timer); // cancel any pending execution
    timer = setTimeout(() => {
      fn.apply(this, args); // execute only after delay has passed
    }, delay);
  };
}

// Usage: Search input — only search after user stops typing for 300ms
const searchInput = document.getElementById("search");
const handleSearch = debounce((event) => {
  fetch(`/api/search?q=${event.target.value}`);
}, 300);
searchInput.addEventListener("input", handleSearch);


// THROTTLE implementation
function throttle(fn, interval) {
  let lastCall = 0;
  return function(...args) {
    const now = Date.now();
    if (now - lastCall >= interval) {
      lastCall = now;
      fn.apply(this, args);
    }
  };
}

// Usage: Scroll handler — track scroll position at most once every 200ms
const handleScroll = throttle(() => {
  updateScrollProgress(window.scrollY);
}, 200);
window.addEventListener("scroll", handleScroll);
```

**When to use which:**
| Scenario | Use |
|---------|-----|
| Search input (wait for user to stop typing) | Debounce |
| Auto-save while user types | Debounce |
| Window resize handler | Debounce |
| Scroll events (continuous updates needed) | Throttle |
| Mouse move tracking | Throttle |
| Rate limiting API calls | Throttle |
| Button click protection (prevent double-submit) | Debounce |

**Interview Answer:**
> "Debounce delays execution until activity stops — the classic example is a search input where you only want to hit the API after the user pauses typing, not on every keystroke. Throttle limits execution to a maximum frequency — useful for scroll or resize events where you want continuous updates but not on every single event. In Lynkify, I used debounce on search inputs and throttle on scroll-based animations. Both rely on closures to persist their timer/timestamp between calls."

---

## 3.11 — map, filter, reduce

🔴 VERY COMMON | ⭐ CRITICAL | 🟢 EASY

```javascript
const users = [
  { name: "Abishek", age: 25, active: true },
  { name: "Raj", age: 17, active: false },
  { name: "Priya", age: 30, active: true }
];

// MAP — transforms each element, returns new array of SAME length
const names = users.map(user => user.name);
// ["Abishek", "Raj", "Priya"]

// FILTER — keeps elements matching condition, returns SHORTER or equal array
const activeAdults = users.filter(user => user.active && user.age >= 18);
// [{ name: "Abishek", ... }, { name: "Priya", ... }]

// REDUCE — accumulates to a single value
const totalAge = users.reduce((acc, user) => acc + user.age, 0);
// 72

// Combining them (real-world pattern)
const activeUserNames = users
  .filter(user => user.active)
  .map(user => user.name.toUpperCase());
// ["ABISHEK", "PRIYA"]

// Reduce to build an object (extremely common in production)
const usersByName = users.reduce((acc, user) => {
  acc[user.name] = user;
  return acc;
}, {});
// { Abishek: {...}, Raj: {...}, Priya: {...} }
```

**Interview Answer:**
> "map, filter, and reduce are the holy trinity of functional array operations. map transforms each element and always returns an array of the same length. filter selects elements matching a condition and returns a subset. reduce accumulates elements into any output — a number, string, array, or object. They're all non-mutating — they return new arrays without modifying the original. I use them constantly: filter+map pipelines for transforming API data, reduce for building lookup objects, and grouping arrays by properties."

---

## 3.12 — `this` keyword

🔴 VERY COMMON | ⭐ CRITICAL | 🔴 HARD

**Explanation:**
`this` is not fixed — its value is determined by *how* a function is called, not where it's defined. There are 4 rules:

```javascript
// Rule 1: Global context — this is window (browser) or global (Node.js)
console.log(this); // window

// Rule 2: Method call — this is the object to the left of the dot
const obj = {
  name: "Abishek",
  greet() {
    console.log(this.name); // "Abishek" — this = obj
  }
};
obj.greet();

// Rule 3: Constructor call with new — this is the new object
function Person(name) {
  this.name = name;
}
const p = new Person("Abishek"); // this = new empty object
console.log(p.name); // "Abishek"

// Rule 4: Explicit binding with call/apply/bind
function greet(greeting) {
  console.log(`${greeting}, ${this.name}`);
}
greet.call({ name: "Abishek" }, "Hello"); // "Hello, Abishek"
greet.apply({ name: "Raj" }, ["Hi"]); // "Hi, Raj"
const boundGreet = greet.bind({ name: "Priya" });
boundGreet("Hey"); // "Hey, Priya"

// Arrow functions: this is LEXICALLY inherited — from where they're defined
const obj2 = {
  name: "Abishek",
  greet: function() {
    const inner = () => {
      console.log(this.name); // "Abishek" — arrow inherits outer this
    };
    inner();
  }
};

// Classic this bug with callbacks
const obj3 = {
  name: "Abishek",
  greet: function() {
    setTimeout(function() {
      console.log(this.name); // undefined! regular function, this = window
    }, 100);

    setTimeout(() => {
      console.log(this.name); // "Abishek" ✅ arrow function inherits this
    }, 100);
  }
};
```

**Interview Answer:**
> "The value of this depends on the call site — how the function is invoked. In a method call, this is the object before the dot. In a regular function called alone, it's the global object or undefined in strict mode. With new, it's the newly created object. With call/apply/bind, it's explicitly set. Arrow functions don't have their own this — they inherit it lexically from the surrounding context at definition time. This makes arrow functions ideal for callbacks and event handlers where you want to preserve the outer this."

---

## 3.13 — bind, call, apply

🟠 COMMON | 🔥 HIGH | 🟡 MEDIUM

```javascript
function introduce(greeting, punctuation) {
  console.log(`${greeting}, I'm ${this.name}${punctuation}`);
}

const person = { name: "Abishek" };

// call: invoke immediately, arguments passed individually
introduce.call(person, "Hello", "!");     // "Hello, I'm Abishek!"

// apply: invoke immediately, arguments passed as an array
introduce.apply(person, ["Hi", "."]);    // "Hi, I'm Abishek."

// bind: returns a NEW function with this permanently bound, not called immediately
const boundIntroduce = introduce.bind(person, "Hey");
boundIntroduce("?"); // "Hey, I'm Abishek?" — first arg was pre-filled
```

**Memory trick:** **C**all = **C**omma-separated, **A**pply = **A**rray

---

## 3.14 — Prototype & Prototypal Inheritance

🟠 COMMON | 🔥 HIGH | 🟡 MEDIUM

**Explanation:**
Every JavaScript object has an internal link to another object called its *prototype*. When you access a property on an object, JavaScript first looks on the object itself, then up the *prototype chain* until it reaches null.

```javascript
// Understanding prototype chain
const animal = {
  breathe() {
    console.log("Breathing...");
  }
};

const dog = Object.create(animal); // dog's prototype IS animal
dog.bark = function() {
  console.log("Woof!");
};

dog.bark();    // own property ✅
dog.breathe(); // found on prototype ✅
console.log(dog.hasOwnProperty("bark"));    // true
console.log(dog.hasOwnProperty("breathe")); // false — it's on the prototype

// ES6 Classes are syntactic sugar over prototypes
class Animal {
  constructor(name) {
    this.name = name;
  }
  speak() {
    console.log(`${this.name} makes a sound.`);
  }
}

class Dog extends Animal {
  speak() {
    console.log(`${this.name} barks.`);
  }
}

const d = new Dog("Rex");
d.speak(); // "Rex barks." — Dog's own method, overrides Animal's
```

**Interview Answer:**
> "JavaScript uses prototypal inheritance — every object has a prototype chain. When you access a property, JavaScript walks up the chain until it finds it or reaches null. ES6 class syntax is cleaner but it's just sugar over this prototype mechanism. In practice I use class syntax, but I understand the underlying prototype model so I can debug issues like methods appearing on instances versus prototypes, and understand why Object.create() is sometimes preferable."

---

## 3.15 — Memory Leaks

🟡 OCCASIONAL | 🔥 HIGH | 🟡 MEDIUM

**Common sources of memory leaks in JavaScript:**

```javascript
// 1. Event listeners not removed
function setup() {
  const button = document.getElementById("btn");
  button.addEventListener("click", handleClick); // 🚨 never removed
  // Fix: remove when no longer needed
  // button.removeEventListener("click", handleClick);
}

// 2. Closures holding references to large objects
function leaky() {
  const bigData = new Array(1000000).fill("data");
  return function() {
    // Even if you only need a small part, bigData is fully retained
    return bigData[0];
  };
}

// 3. Forgotten timers
const timer = setInterval(() => {
  updateSomething(); // if updateSomething references DOM nodes, leak!
}, 1000);
// Fix: clearInterval(timer) when done

// 4. Detached DOM nodes
let element = document.getElementById("menu");
document.body.removeChild(element); // removed from DOM
// But 'element' variable still holds a reference — node stays in memory
element = null; // Fix: clear the reference

// 5. Forgotten global variables
function badCode() {
  leakedVar = "I'm accidentally global!"; // no var/let/const — goes to window
}
```

**In React:** The most common leak is a setState call after a component unmounts (e.g., from a fetch inside useEffect with no cleanup).

```javascript
useEffect(() => {
  let cancelled = false;
  
  fetch("/api/data")
    .then(res => res.json())
    .then(data => {
      if (!cancelled) setState(data); // guard against calling setState after unmount
    });

  return () => {
    cancelled = true; // cleanup runs when component unmounts
  };
}, []);
```

---

## 3.16 — Shallow vs Deep Copy

🟠 COMMON | 🔥 HIGH | 🟢 EASY

```javascript
const original = {
  name: "Abishek",
  address: { city: "Bangalore" } // nested object
};

// SHALLOW COPY — only the top level is copied; nested objects still share reference
const shallow1 = Object.assign({}, original);
const shallow2 = { ...original }; // spread operator

shallow1.name = "Raj"; // original.name is still "Abishek" ✅
shallow1.address.city = "Chennai"; // original.address.city ALSO changes! 🚨

// DEEP COPY — every level is copied, completely independent
// Option 1: JSON (simple, but loses functions, undefined, Date objects)
const deep1 = JSON.parse(JSON.stringify(original));

// Option 2: structuredClone (modern, handles more types)
const deep2 = structuredClone(original); // Node 17+, modern browsers

// Option 3: lodash cloneDeep (most reliable for complex objects)
import { cloneDeep } from "lodash";
const deep3 = cloneDeep(original);

deep1.address.city = "Mumbai"; // original.address.city stays "Bangalore" ✅
```

---

## 3.17 — Destructuring, Spread, Rest

🔴 VERY COMMON | ⭐ CRITICAL | 🟢 EASY

```javascript
// OBJECT DESTRUCTURING
const { name, age, email = "default@email.com" } = user; // with default
const { name: userName } = user; // rename while destructuring
const { address: { city } } = user; // nested destructuring

// ARRAY DESTRUCTURING
const [first, second, ...rest] = [1, 2, 3, 4, 5];
// first = 1, second = 2, rest = [3, 4, 5]
const [,, third] = [1, 2, 3]; // skip elements with commas

// FUNCTION PARAMETER DESTRUCTURING (very common in React)
function UserCard({ name, age, avatar = "/default.png" }) {
  return <img src={avatar} alt={name} />;
}

// SPREAD — expands iterable into individual elements
const newArr = [...arr1, ...arr2]; // merge arrays
const newObj = { ...obj1, ...obj2, override: "value" }; // merge objects

// REST — collects remaining elements
function sum(...numbers) { // collects all args into array
  return numbers.reduce((a, b) => a + b, 0);
}
sum(1, 2, 3, 4); // numbers = [1, 2, 3, 4]

// REST in destructuring
const { name, ...otherProps } = user; // otherProps = everything except name
```

---

## 3.18 — Modules (ES Modules vs CommonJS)

🟠 COMMON | 🔥 HIGH | 🟡 MEDIUM

```javascript
// ES MODULES (modern standard — used in React, Next.js, browsers)
// Named exports
export const helper = () => {};
export const API_URL = "https://api.example.com";

// Default export (one per file)
export default function MainComponent() {}

// Importing
import MainComponent from "./MainComponent"; // default import
import { helper, API_URL } from "./helpers"; // named imports
import * as helpers from "./helpers"; // namespace import

// COMMONJS (Node.js legacy)
const express = require("express");
module.exports = { helper, API_URL };

// Key difference: ES Modules are statically analyzed (tree-shakable),
// CommonJS is dynamic (evaluated at runtime)
```

---

## 3.19 — fetch API & Error Handling

🔴 VERY COMMON | ⭐ CRITICAL | 🟢 EASY

```javascript
// Common mistake: fetch only rejects on NETWORK errors, not HTTP errors!
async function fetchUser(id) {
  try {
    const response = await fetch(`/api/users/${id}`);
    
    // MUST check response.ok — fetch doesn't throw on 4xx/5xx
    if (!response.ok) {
      throw new Error(`HTTP ${response.status}: ${response.statusText}`);
    }
    
    const data = await response.json();
    return data;
  } catch (error) {
    if (error.name === "TypeError") {
      console.error("Network error:", error.message);
    } else {
      console.error("API error:", error.message);
    }
    throw error; // re-throw for calling code to handle
  }
}
```

---

## 3.20 — Optional Chaining & Nullish Coalescing

🔴 VERY COMMON | ⭐ CRITICAL | 🟢 EASY

```javascript
const user = {
  profile: {
    address: {
      city: "Bangalore"
    }
  }
};

// Without optional chaining (verbose and error-prone)
const city = user && user.profile && user.profile.address && user.profile.address.city;

// With optional chaining (?.) — returns undefined if any part is null/undefined
const city = user?.profile?.address?.city; // "Bangalore"
const phone = user?.profile?.phone; // undefined (no error)
const method = user?.getDetails?.(); // call method only if it exists

// Nullish coalescing (??) — returns right side only if left is null or undefined
// (unlike ||, which returns right side for ANY falsy value including 0, "", false)
const name = user.name ?? "Anonymous"; // "Anonymous" if name is null/undefined
const count = data.count ?? 0; // 0 if count is null/undefined
// vs
const count2 = data.count || 0; // 0 if count is 0, null, undefined, or "" — often wrong!
```

---

## 3.21 — Immutability & Functional Programming Basics

🟠 COMMON | 🔥 HIGH | 🟡 MEDIUM

```javascript
// Immutability — never mutate, always create new
// BAD (mutation)
const updateUser = (user, newName) => {
  user.name = newName; // mutates original — bad!
  return user;
};

// GOOD (immutable update)
const updateUser = (user, newName) => ({
  ...user,
  name: newName // new object with updated name
});

// Pure functions — same input always gives same output, no side effects
// PURE:
const add = (a, b) => a + b;
const double = arr => arr.map(x => x * 2); // returns new array

// IMPURE (depends on external state):
let multiplier = 2;
const multiply = x => x * multiplier; // result changes if multiplier changes

// Higher-order functions — functions that take or return functions
const withLogging = (fn) => (...args) => {
  console.log("Calling with:", args);
  const result = fn(...args);
  console.log("Result:", result);
  return result;
};

const loggedAdd = withLogging(add);
loggedAdd(2, 3); // logs input and output, then returns 5
```

---

## 3.22 — localStorage, sessionStorage, Cookies

🟠 COMMON | 🔥 HIGH | 🟢 EASY

| Feature | localStorage | sessionStorage | Cookies |
|---------|-------------|----------------|---------|
| Persistence | Until manually cleared | Until tab closes | Configurable (expiry) |
| Size limit | ~5MB | ~5MB | ~4KB |
| Accessible from | JS only | JS only | JS + Server |
| Sent with requests | No | No | Yes (automatically) |
| Cross-tab | Yes | No | Yes |
| Use case | User preferences, tokens | Temp form data | Auth tokens, tracking |

```javascript
// localStorage
localStorage.setItem("theme", "dark");
const theme = localStorage.getItem("theme"); // "dark"
localStorage.removeItem("theme");
localStorage.clear(); // clear all

// Always parse JSON — localStorage only stores strings
localStorage.setItem("user", JSON.stringify({ name: "Abishek" }));
const user = JSON.parse(localStorage.getItem("user"));

// Cookies (via document.cookie — limited API, use js-cookie library in production)
document.cookie = "token=abc123; path=/; max-age=3600; Secure; SameSite=Strict";
```

**Security consideration:** Never store JWTs or sensitive tokens in localStorage — they're accessible to any JavaScript on the page (XSS vulnerability). Use httpOnly cookies for authentication tokens.

---

## 3.23 — Common JavaScript Coding Traps (Rapid Fire)

🔴 VERY COMMON | ⭐ CRITICAL | 🟡 MEDIUM

```javascript
// Trap 1: typeof null
typeof null === "object" // true — historical bug in JS

// Trap 2: Array is object
typeof [] === "object" // true
Array.isArray([]) === true // correct check

// Trap 3: String to number
+"3" === 3 // true — unary plus converts
Number("") === 0 // true
Number("abc") === NaN // true but NaN !== NaN

// Trap 4: Falsy values (6 of them)
// false, 0, "", null, undefined, NaN
// Everything else is truthy, including "0", [], {}!
Boolean("0") // true — non-empty string!
Boolean([]) // true — empty array!
Boolean({}) // true — empty object!

// Trap 5: Object comparison
{} === {} // false — different references
[] === [] // false — different references
// Use JSON.stringify for deep comparison (with caveats)

// Trap 6: parseInt gotcha
parseInt("08") // 8 in modern JS (was 0 in old browsers with octal)
parseInt("10", 2) // 2 — second arg is radix (base)!

// Trap 7: Array sort is alphabetical by default
[10, 1, 21, 2].sort() // [1, 10, 2, 21] — wrong!
[10, 1, 21, 2].sort((a, b) => a - b) // [1, 2, 10, 21] — correct
```

---

<a name="section-4"></a>
# SECTION 4 — REACT (VERY DEEP)

> Interviewer mindset: They want to know if you truly understand how React works, not just how to use it. Expect deep questions on rendering behavior, hook dependencies, memoization, and performance.

---

## 4.1 — Virtual DOM & Reconciliation

🔴 VERY COMMON | ⭐ CRITICAL | 🟡 MEDIUM

**Explanation:**
The real DOM is expensive to manipulate. React introduced the *Virtual DOM* — a lightweight JavaScript object representation of the actual DOM. React keeps two Virtual DOM trees: the previous state and the current state. When state changes, React compares them (this is called *diffing* or *reconciliation*) and computes the minimal set of actual DOM changes needed.

```
State Changes
     ↓
React creates new Virtual DOM
     ↓
Diffing algorithm compares old vs new Virtual DOM
     ↓
Generates minimal "patch" of changes
     ↓
Applies only those changes to real DOM (commit phase)
```

**The Reconciliation Algorithm Key Rules:**
1. **Elements of different types** → Tear down the old tree completely, build new one.
2. **Same type elements** → Update only changed attributes.
3. **Lists without keys** → React compares by position — can cause bugs.
4. **Lists with stable keys** → React matches elements across renders correctly.

```jsx
// Why keys matter in lists
// BAD — key by index:
items.map((item, index) => <Item key={index} data={item} />)
// If you remove item at index 0, ALL items re-render because indexes shift

// GOOD — key by stable unique ID:
items.map(item => <Item key={item.id} data={item} />)
// React correctly identifies which item was removed
```

**Interview Answer:**
> "React's Virtual DOM is a JS object tree that mirrors the real DOM. When state or props change, React creates a new Virtual DOM tree and runs its reconciliation algorithm to diff the old and new trees. It applies the minimal set of changes to the real DOM, which is the expensive part. The algorithm assumes elements of different types produce entirely different trees, and uses keys to identify list elements across renders. This is why stable, unique keys are critical — index keys cause unnecessary re-renders and can corrupt component state."

---

## 4.2 — useState

🔴 VERY COMMON | ⭐ CRITICAL | 🟢 EASY

```jsx
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0); // [currentValue, setter]

  // Functional update form — use when new state depends on old state
  const increment = () => setCount(prev => prev + 1); // ALWAYS use this form
  const badIncrement = () => setCount(count + 1); // can be stale in async contexts

  // State updates are BATCHED — React 18 batches all state updates automatically
  const handleClick = () => {
    setCount(c => c + 1);
    setName("Abishek"); // Both updates cause ONE re-render, not two
  };

  return <button onClick={increment}>{count}</button>;
}

// Object state — always spread to avoid losing other fields
const [user, setUser] = useState({ name: "", age: 0, email: "" });
const updateName = (name) => setUser(prev => ({ ...prev, name })); // ✅
const badUpdate = (name) => setUser({ name }); // 🚨 loses age and email!

// Lazy initialization — for expensive initial state
const [data, setData] = useState(() => {
  return expensiveComputation(); // only runs once, not on every render
});
```

**Key Rules:**
- State updates trigger a re-render
- State updates are asynchronous — you can't read the new value immediately after calling the setter
- Never mutate state directly — always use the setter
- For derived values, compute them during render instead of storing in state

---

## 4.3 — useEffect (Deep)

🔴 VERY COMMON | ⭐ CRITICAL | 🔴 HARD

**The most misunderstood hook. This section is critical.**

```jsx
import { useEffect, useState } from "react";

function UserProfile({ userId }) {
  const [user, setUser] = useState(null);

  // useEffect(callback, dependencyArray)
  // callback runs AFTER React commits changes to DOM

  // No dependency array — runs after EVERY render
  useEffect(() => {
    console.log("Runs after every render");
  });

  // Empty array — runs only ONCE after initial mount
  useEffect(() => {
    console.log("Runs once — like componentDidMount");
  }, []);

  // With dependencies — runs when any dependency changes
  useEffect(() => {
    let cancelled = false;

    async function fetchUser() {
      const response = await fetch(`/api/users/${userId}`);
      const data = await response.json();
      if (!cancelled) setUser(data); // prevent state update after unmount
    }

    fetchUser();

    // Cleanup function — runs before next effect AND on unmount
    return () => {
      cancelled = true; // cancel pending fetch
      // Also good for: clearInterval, removeEventListener, unsubscribe
    };
  }, [userId]); // Re-runs whenever userId changes

  return <div>{user?.name}</div>;
}
```

**The Phases of useEffect:**
```
Component mounts
  → React renders (DOM updated)
  → useEffect callback runs ← "after paint"

State/props change
  → React re-renders
  → useEffect CLEANUP runs (previous effect's cleanup)
  → New useEffect callback runs

Component unmounts
  → useEffect CLEANUP runs
```

**Common useEffect Mistakes:**

```jsx
// Mistake 1: Missing dependency — stale closure
useEffect(() => {
  const interval = setInterval(() => {
    console.log(count); // always 0 if count not in deps
  }, 1000);
  return () => clearInterval(interval);
}, []); // 🚨 should be [count]

// Mistake 2: Objects/functions in deps cause infinite loops
useEffect(() => {
  fetchData(options); // fetchData runs → state updates → re-render
}, [options]); // 🚨 if options is created inline during render, it's a new object every time!

// Fix: useMemo for objects in deps
const stableOptions = useMemo(() => ({ limit: 10, offset: 0 }), []);
useEffect(() => {
  fetchData(stableOptions);
}, [stableOptions]);

// Mistake 3: Setting state unconditionally inside useEffect
useEffect(() => {
  setLoading(true);
  fetch("/api/data")
    .then(r => r.json())
    .then(data => {
      setLoading(false);
      setData(data); // 🚨 if component unmounted, this is a memory leak
    });
}, []);
```

**Interview Answer:**
> "useEffect synchronizes a component with an external system — fetching data, setting up subscriptions, or manipulating the DOM. It runs after React has committed to the DOM, not during rendering. The dependency array controls when it re-runs: no array means every render, empty array means once, and specific deps means whenever those values change. The returned cleanup function runs before the next effect and on unmount — critical for removing event listeners, cancelling fetches, and clearing timers to prevent memory leaks. The most common mistake I see is either missing dependencies — which causes stale closures — or including unstable references like inline objects in the dep array, which causes infinite loops."

---

## 4.4 — useMemo

🟠 COMMON | ⭐ CRITICAL | 🟡 MEDIUM

**Explanation:**
`useMemo` caches the result of an expensive computation. It only recalculates when its dependencies change.

```jsx
import { useMemo } from "react";

function ProductList({ products, searchTerm, sortBy }) {
  // Without useMemo: filters and sorts on EVERY render, even unrelated ones
  const processedProducts = useMemo(() => {
    console.log("Filtering and sorting..."); // only logs when deps change
    return products
      .filter(p => p.name.toLowerCase().includes(searchTerm.toLowerCase()))
      .sort((a, b) => {
        if (sortBy === "price") return a.price - b.price;
        return a.name.localeCompare(b.name);
      });
  }, [products, searchTerm, sortBy]); // only recalculate when these change

  return processedProducts.map(p => <ProductCard key={p.id} product={p} />);
}
```

**When to use useMemo:**
- Expensive computations (filtering large arrays, complex calculations)
- Creating stable references for objects/arrays passed to child components or used in useEffect deps
- When the computation is genuinely CPU-intensive

**When NOT to use useMemo:**
- Don't memoize everything — the memoization itself has overhead
- Simple operations like `products.length` or basic string operations
- When dependencies change on every render anyway (memoization is useless)

---

## 4.5 — useCallback

🟠 COMMON | ⭐ CRITICAL | 🟡 MEDIUM

**Explanation:**
`useCallback` returns a *memoized function* — the same function reference across renders, as long as dependencies haven't changed. This matters because in JavaScript, functions created inline are new references every render.

```jsx
import { useCallback, memo } from "react";

// Why this matters:
function Parent() {
  const [count, setCount] = useState(0);

  // Without useCallback: new function reference every render
  const handleDelete = (id) => {
    deleteItem(id); // Child re-renders even if count changed, not items
  };

  // With useCallback: stable reference — Child only re-renders if deps change
  const handleDelete = useCallback((id) => {
    deleteItem(id);
  }, []); // no deps — function never changes

  return (
    <>
      <p>{count}</p>
      <button onClick={() => setCount(c => c + 1)}>Increment</button>
      {/* ExpensiveChild won't re-render just because count changed */}
      <ExpensiveChild onDelete={handleDelete} />
    </>
  );
}

// For useCallback to actually prevent re-renders, child must be wrapped in React.memo
const ExpensiveChild = memo(({ onDelete }) => {
  console.log("ExpensiveChild rendered");
  return <button onClick={() => onDelete(1)}>Delete</button>;
});
```

**Critical insight:** `useCallback` is only useful when passing callbacks to memoized child components (`React.memo`) or when the function is a dependency of `useEffect`/`useMemo`. Using it everywhere is premature optimization.

---

## 4.6 — useRef

🟠 COMMON | 🔥 HIGH | 🟡 MEDIUM

**useRef serves two very different purposes:**

```jsx
import { useRef, useEffect } from "react";

// Purpose 1: Accessing DOM elements directly
function VideoPlayer() {
  const videoRef = useRef(null);

  const handlePlay = () => {
    videoRef.current.play(); // direct DOM manipulation
  };

  return (
    <video ref={videoRef} src="/video.mp4" />
  );
}

// Purpose 2: Persisting mutable values across renders WITHOUT causing re-renders
function Timer() {
  const [running, setRunning] = useState(false);
  const intervalRef = useRef(null); // store the interval ID

  const start = () => {
    setRunning(true);
    intervalRef.current = setInterval(() => {
      // ... update timer
    }, 1000);
  };

  const stop = () => {
    setRunning(false);
    clearInterval(intervalRef.current); // access stored interval ID
    intervalRef.current = null;
  };
}

// useRef vs useState:
// - useRef changes do NOT trigger re-renders
// - useRef persists across renders (unlike regular variables which reset)
// - useState changes DO trigger re-renders
```

---

## 4.7 — Context API

🔴 VERY COMMON | ⭐ CRITICAL | 🟡 MEDIUM

**Explanation:**
Context solves *prop drilling* — the need to pass props through many intermediate components that don't need them. It creates a "broadcast" channel that any descendant can subscribe to.

```jsx
// 1. Create context
const ThemeContext = createContext({ theme: "light", toggle: () => {} });

// 2. Provide context (usually near the root)
function App() {
  const [theme, setTheme] = useState("light");

  return (
    <ThemeContext.Provider value={{
      theme,
      toggle: () => setTheme(t => t === "light" ? "dark" : "light")
    }}>
      <Router />
    </ThemeContext.Provider>
  );
}

// 3. Consume context (any descendant, no matter how deep)
function ThemeToggle() {
  const { theme, toggle } = useContext(ThemeContext);

  return (
    <button onClick={toggle}>
      Current: {theme}
    </button>
  );
}

// Custom hook pattern — best practice
function useTheme() {
  const context = useContext(ThemeContext);
  if (!context) throw new Error("useTheme must be used within ThemeProvider");
  return context;
}
```

**Context Performance Caveat:**
Every consumer re-renders when the context VALUE changes. If you put many different values in one context, any change re-renders ALL consumers.

```jsx
// Anti-pattern: one large context
const AppContext = createContext(); // { user, theme, cart, notifications }
// Updating cart re-renders ALL components that consume AppContext

// Better: Split contexts by update frequency
const UserContext = createContext();      // updates rarely
const ThemeContext = createContext();     // updates occasionally
const CartContext = createContext();      // updates frequently
```

---

## 4.8 — React.memo

🟠 COMMON | 🔥 HIGH | 🟡 MEDIUM

```jsx
import { memo } from "react";

// Without memo: re-renders every time parent re-renders
const UserCard = ({ user }) => {
  console.log("UserCard rendered");
  return <div>{user.name}</div>;
};

// With memo: only re-renders when user prop changes (shallow comparison)
const UserCard = memo(({ user }) => {
  console.log("UserCard rendered");
  return <div>{user.name}</div>;
});

// Custom comparison function (for when shallow comparison isn't enough)
const UserCard = memo(
  ({ user, config }) => <div>{user.name}</div>,
  (prevProps, nextProps) => {
    // Return true if props are "equal" (skip re-render)
    return prevProps.user.id === nextProps.user.id;
  }
);
```

---

## 4.9 — Custom Hooks

🔴 VERY COMMON | ⭐ CRITICAL | 🟡 MEDIUM

**Custom hooks let you extract and reuse stateful logic between components.**

```jsx
// useFetch — reusable data fetching hook
function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    let cancelled = false;
    setLoading(true);
    setError(null);

    fetch(url)
      .then(res => {
        if (!res.ok) throw new Error(`HTTP ${res.status}`);
        return res.json();
      })
      .then(data => {
        if (!cancelled) {
          setData(data);
          setLoading(false);
        }
      })
      .catch(err => {
        if (!cancelled) {
          setError(err.message);
          setLoading(false);
        }
      });

    return () => { cancelled = true; };
  }, [url]);

  return { data, loading, error };
}

// Usage
function UserProfile({ userId }) {
  const { data: user, loading, error } = useFetch(`/api/users/${userId}`);

  if (loading) return <Spinner />;
  if (error) return <Error message={error} />;
  return <div>{user.name}</div>;
}

// useLocalStorage — persists state to localStorage
function useLocalStorage(key, initialValue) {
  const [value, setValue] = useState(() => {
    try {
      const stored = localStorage.getItem(key);
      return stored ? JSON.parse(stored) : initialValue;
    } catch {
      return initialValue;
    }
  });

  const setStoredValue = (newValue) => {
    setValue(newValue);
    localStorage.setItem(key, JSON.stringify(newValue));
  };

  return [value, setStoredValue];
}

// useDebounce
function useDebounce(value, delay) {
  const [debouncedValue, setDebouncedValue] = useState(value);

  useEffect(() => {
    const timer = setTimeout(() => setDebouncedValue(value), delay);
    return () => clearTimeout(timer);
  }, [value, delay]);

  return debouncedValue;
}
```

**Interview Answer:**
> "Custom hooks let me extract reusable stateful logic out of components — they start with 'use' by convention and can use any built-in hooks. In Lynkify, I built custom hooks for data fetching with loading/error state, for debounced search inputs, and for local storage persistence. They make components cleaner and the logic testable in isolation."

---

## 4.10 — Error Boundaries

🟡 OCCASIONAL | 🔥 HIGH | 🟡 MEDIUM

```jsx
// Error boundaries are CLASS components (no hook equivalent yet)
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false, error: null };
  }

  static getDerivedStateFromError(error) {
    return { hasError: true, error };
  }

  componentDidCatch(error, errorInfo) {
    // Log to error monitoring service
    logErrorToService(error, errorInfo.componentStack);
  }

  render() {
    if (this.state.hasError) {
      return this.props.fallback || <h2>Something went wrong.</h2>;
    }
    return this.props.children;
  }
}

// Usage
function App() {
  return (
    <ErrorBoundary fallback={<ErrorPage />}>
      <UserDashboard />
    </ErrorBoundary>
  );
}
```

**Note:** Error boundaries catch errors in rendering, lifecycle methods, and constructors of child components. They do NOT catch: event handlers (use try/catch), async code, or errors thrown in the error boundary itself.

---

## 4.11 — Suspense & Lazy Loading

🟠 COMMON | 🔥 HIGH | 🟡 MEDIUM

```jsx
import { lazy, Suspense } from "react";

// Lazy load components — only downloads the code when the component is first rendered
const Dashboard = lazy(() => import("./Dashboard"));
const Settings = lazy(() => import("./Settings"));

function App() {
  return (
    <Suspense fallback={<LoadingSpinner />}>
      <Routes>
        <Route path="/dashboard" element={<Dashboard />} />
        <Route path="/settings" element={<Settings />} />
      </Routes>
    </Suspense>
  );
}
// This splits the bundle — Dashboard and Settings are separate chunks
// Only loaded when user navigates to those routes
```

---

## 4.12 — Controlled vs Uncontrolled Components

🟠 COMMON | 🔥 HIGH | 🟡 MEDIUM

```jsx
// CONTROLLED — React state is the single source of truth
function ControlledForm() {
  const [name, setName] = useState("");

  return (
    <input
      value={name}        // controlled by React state
      onChange={e => setName(e.target.value)} // update state on change
    />
  );
}

// UNCONTROLLED — DOM manages its own state, accessed via ref
function UncontrolledForm() {
  const inputRef = useRef(null);

  const handleSubmit = () => {
    console.log(inputRef.current.value); // read value when needed
  };

  return <input ref={inputRef} defaultValue="initial" />;
}

// When to use each:
// Controlled: When you need validation, conditional rendering, derived state
// Uncontrolled: Simple forms where you only need value at submit, file inputs
```

---

## 4.13 — State Management & Redux Basics

🟠 COMMON | 🔥 HIGH | 🟡 MEDIUM

```jsx
// Redux Toolkit (modern Redux — never write plain Redux)
import { createSlice, configureStore } from "@reduxjs/toolkit";

// Slice — combines reducer + actions
const cartSlice = createSlice({
  name: "cart",
  initialState: { items: [], total: 0 },
  reducers: {
    addItem: (state, action) => {
      // Immer under the hood — you CAN mutate here (it produces immutable update)
      state.items.push(action.payload);
      state.total += action.payload.price;
    },
    removeItem: (state, action) => {
      state.items = state.items.filter(item => item.id !== action.payload);
    },
    clearCart: (state) => {
      state.items = [];
      state.total = 0;
    }
  }
});

export const { addItem, removeItem, clearCart } = cartSlice.actions;

const store = configureStore({
  reducer: { cart: cartSlice.reducer }
});

// Using in components
import { useSelector, useDispatch } from "react-redux";

function CartIcon() {
  const itemCount = useSelector(state => state.cart.items.length);
  const dispatch = useDispatch();

  return (
    <button onClick={() => dispatch(clearCart())}>
      Cart ({itemCount})
    </button>
  );
}
```

**When to use state management vs Context:**
- **Local useState:** Component-specific state (form inputs, toggle, local UI)
- **Context:** Infrequently updated shared state (theme, auth user, locale)
- **Redux/Zustand:** Frequently updated, complex state; multiple components accessing and mutating the same data; cart, real-time data, complex workflows

---

<a name="section-5"></a>
# SECTION 5 — NEXT.JS (VERY DEEP)

> Next.js interviews often focus on rendering strategies — interviewers want to know you can choose the RIGHT strategy for each use case, not just use SSR for everything.

---

## 5.1 — Rendering Strategies Explained

🔴 VERY COMMON | ⭐ CRITICAL | 🟡 MEDIUM

**There are 4 rendering strategies. Understanding the tradeoffs is key.**

```
CSR (Client-Side Rendering)
  → HTML is minimal shell
  → JavaScript runs in browser to fetch and render content
  → Slow initial load, fast subsequent navigation
  → Bad for SEO (unless search engines wait for JS)
  → Use for: dashboards, admin panels, authenticated apps

SSR (Server-Side Rendering)
  → Server fetches data and renders HTML for EACH request
  → Fresh data on every load
  → Good for SEO, slower TTFB under load
  → Use for: pages with user-specific data, real-time data

SSG (Static Site Generation)
  → HTML generated at BUILD TIME
  → Served as static files from CDN — extremely fast
  → Data can be stale until next build
  → Use for: marketing pages, documentation, blogs

ISR (Incremental Static Regeneration)
  → SSG + background revalidation
  → Static file served immediately, regenerated in background after revalidation period
  → Best of SSG speed + SSR freshness
  → Use for: product pages, news articles, anything that changes but not in real-time
```

**Next.js App Router (React Server Components):**
```jsx
// app/page.tsx — Server Component by default
async function HomePage() {
  // Runs on server — can directly query DB or call APIs
  const products = await db.query("SELECT * FROM products LIMIT 10");
  
  return (
    <main>
      <h1>Products</h1>
      {products.map(p => <ProductCard key={p.id} product={p} />)}
    </main>
  );
}

// app/components/AddToCart.tsx — needs to be client component for interactivity
"use client";
function AddToCart({ productId }) {
  const [loading, setLoading] = useState(false);
  
  const handleAdd = async () => {
    setLoading(true);
    await addToCart(productId);
    setLoading(false);
  };
  
  return <button onClick={handleAdd}>{loading ? "Adding..." : "Add to Cart"}</button>;
}
```

**Real Example from Lynkify (how to discuss this in interviews):**
> "In Lynkify, creator bio pages are served with ISR — the page is statically generated for fast loading but revalidates every 60 seconds so link updates are reflected quickly. The analytics dashboard is CSR because it shows real-time user-specific data. The landing page and blog are pure SSG."

---

## 5.2 — App Router vs Pages Router

🔴 VERY COMMON | ⭐ CRITICAL | 🟡 MEDIUM

| Feature | Pages Router | App Router (Next.js 13+) |
|---------|-------------|--------------------------|
| Default component type | Client component | Server component |
| Data fetching | getServerSideProps, getStaticProps | async/await directly in component |
| Layouts | _app.js (entire app) | Nested layout.tsx files |
| Loading states | Manual | loading.tsx convention |
| Error handling | Error pages | error.tsx convention |
| Server Actions | No | Yes |
| Streaming | No | Yes (with Suspense) |

```jsx
// Pages Router — getStaticProps
export async function getStaticProps({ params }) {
  const product = await fetchProduct(params.id);
  return {
    props: { product },
    revalidate: 60 // ISR: regenerate after 60 seconds
  };
}

// App Router — async Server Component (no boilerplate)
async function ProductPage({ params }) {
  const product = await fetchProduct(params.id); // direct, no wrapper
  return <ProductDetails product={product} />;
}

// App Router — nested layouts
// app/layout.tsx — wraps entire app
export default function RootLayout({ children }) {
  return (
    <html lang="en">
      <body>
        <Header />
        {children}
        <Footer />
      </body>
    </html>
  );
}

// app/dashboard/layout.tsx — wraps only dashboard routes
export default function DashboardLayout({ children }) {
  return (
    <aside>
      <Sidebar />
      <main>{children}</main>
    </aside>
  );
}
```

---

## 5.3 — API Routes

🔴 VERY COMMON | ⭐ CRITICAL | 🟢 EASY

```typescript
// app/api/users/[id]/route.ts (App Router)
import { NextRequest, NextResponse } from "next/server";

export async function GET(
  request: NextRequest,
  { params }: { params: { id: string } }
) {
  try {
    const user = await db.users.findById(params.id);
    if (!user) {
      return NextResponse.json({ error: "User not found" }, { status: 404 });
    }
    return NextResponse.json(user);
  } catch (error) {
    return NextResponse.json({ error: "Internal server error" }, { status: 500 });
  }
}

export async function PUT(request: NextRequest, { params }) {
  const body = await request.json();
  const updated = await db.users.update(params.id, body);
  return NextResponse.json(updated);
}
```

---

## 5.4 — Middleware

🟠 COMMON | 🔥 HIGH | 🟡 MEDIUM

```typescript
// middleware.ts — runs before every matched request
import { NextResponse } from "next/server";
import type { NextRequest } from "next/server";

export function middleware(request: NextRequest) {
  const token = request.cookies.get("auth-token");
  const isAuthRoute = request.nextUrl.pathname.startsWith("/dashboard");

  if (isAuthRoute && !token) {
    // Redirect to login if accessing protected route without auth
    return NextResponse.redirect(new URL("/login", request.url));
  }

  // Add custom header to all responses
  const response = NextResponse.next();
  response.headers.set("x-custom-header", "value");
  return response;
}

export const config = {
  matcher: ["/dashboard/:path*", "/api/:path*"]
};
```

---

## 5.5 — Image Optimization

🟠 COMMON | ⭐ CRITICAL | 🟢 EASY

```jsx
import Image from "next/image";

// next/image handles:
// - Automatic WebP/AVIF conversion
// - Responsive sizes
// - Lazy loading by default
// - Prevents layout shift (requires width/height or fill)
// - CDN optimization via Vercel Image Optimization

function Hero() {
  return (
    <Image
      src="/hero.jpg"
      alt="Hero image"
      width={1200}
      height={600}
      priority // load eagerly (above the fold, affects LCP)
      quality={85} // default 75
      placeholder="blur" // shows blurred version while loading
      blurDataURL="data:image/jpeg;base64,..." // tiny base64 for blur
    />
  );
}

// Responsive/fill images
function CoverImage() {
  return (
    <div style={{ position: "relative", width: "100%", height: "400px" }}>
      <Image
        src="/cover.jpg"
        alt="Cover"
        fill
        style={{ objectFit: "cover" }}
        sizes="(max-width: 768px) 100vw, 50vw" // helps browser choose right size
      />
    </div>
  );
}
```

---

## 5.6 — SEO & Metadata

🔴 VERY COMMON | ⭐ CRITICAL | 🟢 EASY

```typescript
// app/layout.tsx — default metadata
import type { Metadata } from "next";

export const metadata: Metadata = {
  title: {
    default: "Lynkify — Creator Platform",
    template: "%s | Lynkify" // page titles become "Page Name | Lynkify"
  },
  description: "Smart links, bio pages, and music distribution for creators",
  openGraph: {
    type: "website",
    url: "https://lynkify.in",
    siteName: "Lynkify",
    images: [{ url: "/og-image.jpg", width: 1200, height: 630 }]
  },
  twitter: {
    card: "summary_large_image",
    creator: "@lynkify"
  }
};

// app/creators/[username]/page.tsx — dynamic metadata
export async function generateMetadata({ params }): Promise<Metadata> {
  const creator = await fetchCreator(params.username);
  return {
    title: creator.name,
    description: creator.bio,
    openGraph: {
      images: [{ url: creator.avatar }]
    }
  };
}
```

---

## 5.7 — Caching in Next.js (App Router)

🟠 COMMON | 🔥 HIGH | 🔴 HARD

```typescript
// Request Memoization — duplicate fetch() calls in same render tree are deduped
async function getUser(id: string) {
  const res = await fetch(`/api/users/${id}`, {
    next: { revalidate: 3600 } // revalidate every hour (ISR)
  });
  return res.json();
}

// Can call this in multiple server components — only ONE request made per render
const userInHeader = await getUser("123");
const userInProfile = await getUser("123"); // same request, cached!

// Cache options:
fetch(url, { cache: "force-cache" });  // default in Server Components: static
fetch(url, { cache: "no-store" });      // always fresh: dynamic SSR
fetch(url, { next: { revalidate: 60 } }); // ISR: revalidate after 60s
fetch(url, { next: { tags: ["product"] } }); // tag-based revalidation

// On-demand revalidation (webhook pattern)
import { revalidateTag } from "next/cache";

export async function POST(request: NextRequest) {
  // Called by a webhook when product changes
  revalidateTag("product");
  return NextResponse.json({ revalidated: true });
}
```

---

## 5.8 — Authentication in Next.js

🔴 VERY COMMON | ⭐ CRITICAL | 🟡 MEDIUM

```typescript
// Using NextAuth.js (Auth.js)
// app/api/auth/[...nextauth]/route.ts

import NextAuth from "next-auth";
import GoogleProvider from "next-auth/providers/google";
import CredentialsProvider from "next-auth/providers/credentials";

const handler = NextAuth({
  providers: [
    GoogleProvider({
      clientId: process.env.GOOGLE_CLIENT_ID!,
      clientSecret: process.env.GOOGLE_CLIENT_SECRET!,
    }),
    CredentialsProvider({
      name: "Credentials",
      credentials: {
        email: { label: "Email", type: "email" },
        password: { label: "Password", type: "password" }
      },
      async authorize(credentials) {
        const user = await verifyCredentials(credentials);
        return user || null;
      }
    })
  ],
  callbacks: {
    async session({ session, token }) {
      session.user.id = token.sub; // add user ID to session
      return session;
    }
  }
});

export { handler as GET, handler as POST };

// Protecting routes in middleware
import { getToken } from "next-auth/jwt";

export async function middleware(request: NextRequest) {
  const token = await getToken({ req: request });
  if (!token && request.nextUrl.pathname.startsWith("/dashboard")) {
    return NextResponse.redirect(new URL("/login", request.url));
  }
}
```

---

<a name="section-6"></a>
# SECTION 6 — WORDPRESS (DEEP)

> Note: Your experience with Divi, Elementor, custom plugins for PI Industries, and WooCommerce is highly relevant. Frame your answers around real work you've done.

---

## 6.1 — WordPress Architecture

🟠 COMMON | 🔥 HIGH | 🟢 EASY

**WordPress is built on PHP + MySQL. Its core architecture:**

```
Browser Request
    ↓
wp-config.php (database connection, constants)
    ↓
wp-settings.php (loads core, plugins, theme)
    ↓
Template Hierarchy (which template file to load)
    ↓
The Loop (query posts and display them)
    ↓
HTML Response
```

**Template Hierarchy (critical to understand):**
WordPress checks for increasingly general template files:
```
Single post: single-{post-type}-{slug}.php → single-{post-type}.php → single.php → singular.php → index.php
Category: category-{slug}.php → category-{ID}.php → category.php → archive.php → index.php
```

---

## 6.2 — Actions vs Filters (Hooks System)

🔴 VERY COMMON | ⭐ CRITICAL | 🟡 MEDIUM

**This is the most important WordPress concept. Everything in WordPress runs through hooks.**

```php
// ACTIONS — "do something at this point" (no return value expected)
// Syntax: add_action( hook_name, callback, priority, accepted_args )

// Example: Add custom scripts to the frontend
add_action('wp_enqueue_scripts', function() {
    wp_enqueue_style(
        'my-theme-style',        // handle
        get_stylesheet_uri(),     // source
        [],                       // dependencies
        '1.0.0'                  // version
    );
    
    wp_enqueue_script(
        'my-custom-js',
        get_template_directory_uri() . '/js/custom.js',
        ['jquery'],              // depends on jquery
        '1.0.0',
        true                    // load in footer
    );
});

// Adding custom content after post
add_action('the_content', function($content) {
    // This is actually a FILTER (has return), not a pure action
});

// FILTERS — "modify this value and return it"
// Syntax: add_filter( hook_name, callback, priority, accepted_args )

// Example: Modify post title
add_filter('the_title', function($title, $post_id) {
    if (get_post_type($post_id) === 'product') {
        return '🛍️ ' . $title;
    }
    return $title; // ALWAYS return from filters!
}, 10, 2); // priority 10, accepts 2 arguments

// Example: Modify WooCommerce checkout fields
add_filter('woocommerce_checkout_fields', function($fields) {
    unset($fields['billing']['billing_company']); // remove company field
    $fields['billing']['billing_phone']['required'] = true;
    return $fields; // always return!
});

// Example: Remove an existing hook
remove_action('woocommerce_after_shop_loop_item', 'woocommerce_template_loop_add_to_cart', 10);
remove_filter('the_content', 'wpautop'); // remove auto-paragraph formatting
```

**Interview Answer:**
> "WordPress's hook system is its most powerful feature. Actions let plugins and themes run code at specific points in WordPress's execution — like after a post is saved or before the footer renders. Filters let you intercept and modify data — like post content, query arguments, or menu items — and must always return the modified value. In the PI Industries plugin I built, I used a custom hook system so different modules could extend each other without coupling. Priority controls execution order — lower numbers run first."

---

## 6.3 — WP_Query

🟠 COMMON | ⭐ CRITICAL | 🟡 MEDIUM

```php
// WP_Query — WordPress's main way to query posts
$args = [
    'post_type'      => 'product',          // custom post type
    'post_status'    => 'publish',
    'posts_per_page' => 10,
    'paged'          => get_query_var('paged'), // pagination
    'meta_query'     => [
        [
            'key'     => 'price',
            'value'   => [100, 500],
            'type'    => 'NUMERIC',
            'compare' => 'BETWEEN'
        ]
    ],
    'tax_query'      => [
        [
            'taxonomy' => 'product_category',
            'field'    => 'slug',
            'terms'    => ['electronics', 'gadgets']
        ]
    ],
    'orderby'        => 'meta_value_num',
    'meta_key'       => 'price',
    'order'          => 'ASC'
];

$query = new WP_Query($args);

if ($query->have_posts()) {
    while ($query->have_posts()) {
        $query->the_post();
        // Use template tags: the_title(), the_content(), get_the_ID()
        echo '<h2>' . get_the_title() . '</h2>';
    }
    wp_reset_postdata(); // ALWAYS call this after custom queries!
} else {
    echo 'No posts found';
}

// REST API approach (modern)
$posts = get_posts([
    'post_type'   => 'product',
    'numberposts' => 10,
    // simpler API, doesn't set global $post
]);
```

---

## 6.4 — Custom Post Types & Taxonomies

🟠 COMMON | 🔥 HIGH | 🟡 MEDIUM

```php
// Register Custom Post Type (in functions.php or plugin)
add_action('init', function() {
    register_post_type('product', [
        'labels' => [
            'name'          => 'Products',
            'singular_name' => 'Product',
            'add_new_item'  => 'Add New Product',
        ],
        'public'       => true,
        'has_archive'  => true,
        'show_in_rest' => true, // enables Gutenberg editor and REST API
        'supports'     => ['title', 'editor', 'thumbnail', 'excerpt'],
        'rewrite'      => ['slug' => 'products'],
    ]);
});

// Register Custom Taxonomy
add_action('init', function() {
    register_taxonomy('product_category', 'product', [
        'labels'        => ['name' => 'Product Categories'],
        'hierarchical'  => true, // true = category-like, false = tag-like
        'show_in_rest'  => true,
        'rewrite'       => ['slug' => 'product-category'],
    ]);
});
```

---

## 6.5 — ACF (Advanced Custom Fields)

🟠 COMMON | 🔥 HIGH | 🟢 EASY

```php
// Getting field values
$price = get_field('price'); // returns the field value
$gallery = get_field('gallery'); // returns array for gallery fields
$relationship = get_field('related_products'); // returns array of WP_Post objects

// The Field Key vs Field Name
get_field('price'); // by name — easier to read
get_field('field_60a7f8b2c3d4e'); // by key — more reliable when fields renamed

// Flexible Content field (accordion of layout blocks)
$layouts = get_field('page_builder');
if ($layouts) {
    foreach ($layouts as $layout) {
        switch ($layout['acf_fc_layout']) {
            case 'hero_section':
                echo '<h1>' . $layout['heading'] . '</h1>';
                break;
            case 'text_block':
                echo '<p>' . $layout['content'] . '</p>';
                break;
        }
    }
}

// Saving fields programmatically
update_field('price', 299.99, $post_id);
update_field('field_key', $value, $post_id);
```

---

## 6.6 — WordPress REST API

🟠 COMMON | 🔥 HIGH | 🟡 MEDIUM

```php
// Register custom REST API endpoint
add_action('rest_api_init', function() {
    register_rest_route('myapp/v1', '/products', [
        'methods'  => 'GET',
        'callback' => 'get_products_api',
        'permission_callback' => function() {
            return current_user_can('read'); // auth check
        },
        'args' => [
            'category' => [
                'type'     => 'string',
                'required' => false,
            ]
        ]
    ]);
});

function get_products_api(WP_REST_Request $request) {
    $category = $request->get_param('category');
    
    $args = ['post_type' => 'product', 'posts_per_page' => 20];
    if ($category) {
        $args['tax_query'] = [['taxonomy' => 'category', 'field' => 'slug', 'terms' => $category]];
    }
    
    $posts = get_posts($args);
    $data = array_map(function($post) {
        return [
            'id'    => $post->ID,
            'title' => $post->post_title,
            'price' => get_field('price', $post->ID),
        ];
    }, $posts);
    
    return new WP_REST_Response($data, 200);
}

// Calling the WP REST API from JS (Headless)
const response = await fetch('https://site.com/wp-json/wp/v2/posts?per_page=10');
const posts = await response.json();
```

---

## 6.7 — WordPress Security

🟠 COMMON | ⭐ CRITICAL | 🟡 MEDIUM

```php
// 1. Nonces — prevent CSRF attacks
// Generate nonce
$nonce = wp_create_nonce('my-action');

// In form
echo '<input type="hidden" name="_wpnonce" value="' . $nonce . '">';

// Verify nonce in handler
if (!wp_verify_nonce($_POST['_wpnonce'], 'my-action')) {
    wp_die('Security check failed');
}

// 2. Sanitization — clean INPUT before storing
$email = sanitize_email($_POST['email']);
$text  = sanitize_text_field($_POST['name']);
$html  = wp_kses_post($_POST['content']); // allow safe HTML

// 3. Escaping — clean OUTPUT before displaying
echo esc_html($user_input);    // escape for HTML context
echo esc_attr($attribute);     // escape for HTML attributes
echo esc_url($url);            // escape for URLs
echo esc_js($js_string);       // escape for JavaScript

// 4. Capability checks
if (!current_user_can('manage_options')) {
    wp_die('You do not have permission to do this.');
}
```

---

## 6.8 — Performance Optimization (WordPress)

🟠 COMMON | 🔥 HIGH | 🟡 MEDIUM

Key strategies:
- **Caching:** Use WP Rocket, W3 Total Cache, or Redis Object Cache. Cache at page level, object level, and database query level.
- **Database:** Avoid N+1 queries. Use `$wpdb->prepare()` for raw queries. Minimize meta queries on large tables.
- **Images:** Use WebP, lazy loading (`loading="lazy"`), proper sizes.
- **CDN:** Offload static assets to Cloudflare or similar.
- **Query optimization:** Avoid `posts_per_page => -1` (loads all posts). Use `fields => ids` if you only need IDs.

```php
// Efficient query — only get IDs when you just need count/existence
$args = [
    'post_type'      => 'product',
    'fields'         => 'ids', // returns array of IDs only — much faster
    'posts_per_page' => -1
];
$ids = get_posts($args);
$count = count($ids);

// N+1 query problem — bad
foreach ($posts as $post) {
    $price = get_field('price', $post->ID); // separate DB query for each post!
}

// Better — use pre-fetched meta
$post_ids = wp_list_pluck($posts, 'ID');
// Use wp meta cache or query all at once
```

---

<a name="section-7"></a>
# SECTION 7 — SHOPIFY (DEEP)

> Your work on Beretta Gallery ($2.5M+ revenue) and 45R USA migration is excellent interview material. Always frame your answers around the business impact.

---

## 7.1 — Shopify Architecture

🟠 COMMON | 🔥 HIGH | 🟢 EASY

**Shopify's Architecture:**
```
Shopify Platform (SaaS)
├── Admin (Shopify Admin — merchant control panel)
├── Storefront (Customer-facing — built with Liquid or headless)
├── APIs
│   ├── Admin API (GraphQL + REST) — for apps, backend operations
│   ├── Storefront API (GraphQL) — for headless/custom storefronts
│   └── Partner API — for app development
├── Liquid (Template language for themes)
└── App ecosystem (Shopify Apps extend functionality)
```

---

## 7.2 — Liquid Templating

🔴 VERY COMMON | ⭐ CRITICAL | 🟡 MEDIUM

```liquid
{# Liquid syntax overview #}

{# Output a variable #}
{{ product.title }}

{# Tag — logic, no output #}
{% if product.available %}
  <button>Add to Cart</button>
{% else %}
  <button disabled>Sold Out</button>
{% endif %}

{# Loops #}
{% for product in collection.products %}
  <div class="product-card">
    <img src="{{ product.featured_image | img_url: '400x' }}" alt="{{ product.title }}">
    <h3>{{ product.title }}</h3>
    <p>{{ product.price | money }}</p>
    {% unless product.available %}
      <span class="badge">Sold Out</span>
    {% endunless %}
  </div>
{% endfor %}

{# Filters — transform output #}
{{ product.price | money }}                    {# formats as currency #}
{{ product.title | upcase }}                   {# UPPERCASE #}
{{ product.description | truncate: 150 }}      {# truncate to 150 chars #}
{{ image | img_url: '600x400', crop: 'center' }}  {# resize image #}
{{ 'custom.css' | asset_url | stylesheet_tag }}   {# load CSS asset #}

{# Assign variables #}
{% assign discounted_price = product.price | times: 0.9 %}

{# Capture block — assign multiline string to variable #}
{% capture button_html %}
  <button type="submit" name="add" class="btn">
    Add to Cart
  </button>
{% endcapture %}
{{ button_html }}

{# Pagination #}
{% paginate collection.products by 24 %}
  {% for product in collection.products %}
    ...
  {% endfor %}
  {{ paginate | default_pagination }}
{% endpaginate %}
```

---

## 7.3 — Theme Structure

🔴 VERY COMMON | ⭐ CRITICAL | 🟢 EASY

```
theme/
├── assets/          → CSS, JS, images, fonts
├── config/          → settings_schema.json, settings_data.json
├── layout/
│   └── theme.liquid → Master layout (like base template)
├── sections/        → Reusable, customizable page sections
│   ├── header.liquid
│   ├── hero-banner.liquid
│   └── product-grid.liquid
├── snippets/        → Reusable code fragments (no schema)
│   ├── product-card.liquid
│   └── icon-cart.liquid
├── templates/       → Page type templates
│   ├── index.json
│   ├── product.json
│   ├── collection.json
│   └── page.about.json  ← custom template for specific page
└── locales/         → Translation files
```

**Sections vs Snippets:**
- **Sections** can have a `{% schema %}` block defining customizable settings (like drag-and-drop blocks in the theme editor). They're rendered with `{% section 'header' %}` or assigned to templates via JSON.
- **Snippets** are plain reusable code fragments with no settings. Included with `{% render 'product-card', product: product %}`.

```liquid
{# Section with schema — enables Theme Editor customization #}
<div class="hero" style="background-color: {{ section.settings.background_color }}">
  <h1>{{ section.settings.heading }}</h1>
  <p>{{ section.settings.subheading }}</p>
</div>

{% schema %}
{
  "name": "Hero Banner",
  "settings": [
    {
      "type": "text",
      "id": "heading",
      "label": "Heading",
      "default": "Welcome to our store"
    },
    {
      "type": "color",
      "id": "background_color",
      "label": "Background Color",
      "default": "#ffffff"
    }
  ],
  "blocks": [
    {
      "type": "cta_button",
      "name": "CTA Button",
      "settings": [
        { "type": "text", "id": "button_label", "label": "Button Label" },
        { "type": "url", "id": "button_link", "label": "Button Link" }
      ]
    }
  ],
  "max_blocks": 3,
  "presets": [
    { "name": "Hero Banner" }
  ]
}
{% endschema %}
```

---

## 7.4 — Shopify Storefront API (Headless)

🟠 COMMON | 🔥 HIGH | 🔴 HARD

```javascript
// Storefront API uses GraphQL
const PRODUCT_QUERY = `
  query getProduct($handle: String!) {
    product(handle: $handle) {
      id
      title
      description
      priceRange {
        minVariantPrice {
          amount
          currencyCode
        }
      }
      images(first: 5) {
        edges {
          node {
            url
            altText
          }
        }
      }
      variants(first: 20) {
        edges {
          node {
            id
            title
            availableForSale
            price {
              amount
              currencyCode
            }
          }
        }
      }
    }
  }
`;

async function fetchProduct(handle) {
  const response = await fetch(
    `https://my-store.myshopify.com/api/2024-01/graphql.json`,
    {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
        "X-Shopify-Storefront-Access-Token": process.env.SHOPIFY_STOREFRONT_TOKEN
      },
      body: JSON.stringify({
        query: PRODUCT_QUERY,
        variables: { handle }
      })
    }
  );
  const { data } = await response.json();
  return data.product;
}

// Creating a cart and adding items
const CREATE_CART = `
  mutation createCart {
    cartCreate {
      cart {
        id
        checkoutUrl
      }
    }
  }
`;

const ADD_TO_CART = `
  mutation addToCart($cartId: ID!, $variantId: ID!, $quantity: Int!) {
    cartLinesAdd(cartId: $cartId, lines: [
      { merchandiseId: $variantId, quantity: $quantity }
    ]) {
      cart {
        id
        lines(first: 10) {
          edges {
            node {
              id
              quantity
              merchandise {
                ... on ProductVariant {
                  title
                  price { amount }
                }
              }
            }
          }
        }
        cost {
          totalAmount { amount currencyCode }
        }
      }
    }
  }
`;
```

---

## 7.5 — Shopify Performance Optimization

🟠 COMMON | 🔥 HIGH | 🟡 MEDIUM

Key areas from your Beretta work:
- **JavaScript minimization:** Avoid loading large app scripts on every page. Use `defer` for scripts, only load on relevant pages.
- **Image optimization:** Use `img_url` filter with proper sizes. Add `loading="lazy"` for below-fold images.
- **Reduce app bloat:** Every installed Shopify app can inject scripts. Audit with Lighthouse.
- **Critical CSS:** Inline critical above-fold styles, load rest asynchronously.
- **Minimal liquid loops:** Avoid nested loops over large collections.

```liquid
{# Lazy load images #}
<img
  src="{{ product.featured_image | img_url: '400x' }}"
  loading="lazy"
  width="400"
  height="400"
  alt="{{ product.featured_image.alt | escape }}"
>

{# Only load heavy scripts on product pages #}
{% if template == 'product' %}
  {{ 'product-customizer.js' | asset_url | script_tag }}
{% endif %}
```

---

<a name="section-8"></a>
# SECTION 8 — APIs & BACKEND BASICS

---

## 8.1 — REST APIs & HTTP Methods

🔴 VERY COMMON | ⭐ CRITICAL | 🟢 EASY

| Method | Purpose | Body? | Idempotent? |
|--------|---------|-------|-------------|
| GET | Retrieve resource | No | Yes |
| POST | Create resource | Yes | No |
| PUT | Replace resource (full update) | Yes | Yes |
| PATCH | Partial update | Yes | No |
| DELETE | Delete resource | Optional | Yes |

**Idempotent** means calling it multiple times has the same effect as calling once. GET/PUT/DELETE are idempotent; POST and PATCH are not.

```javascript
// RESTful API design
GET    /api/products          → list all products
GET    /api/products/:id      → get single product
POST   /api/products          → create new product
PUT    /api/products/:id      → replace product entirely
PATCH  /api/products/:id      → update specific fields
DELETE /api/products/:id      → delete product

// Query parameters for filtering
GET /api/products?category=electronics&sort=price&order=asc&page=2&limit=20
```

---

## 8.2 — HTTP Status Codes

🔴 VERY COMMON | ⭐ CRITICAL | 🟢 EASY

| Code | Meaning | When to use |
|------|---------|------------|
| 200 | OK | Successful GET, PATCH, DELETE |
| 201 | Created | Successful POST (resource created) |
| 204 | No Content | Successful DELETE (no body returned) |
| 301 | Moved Permanently | Permanent redirect (updates bookmark) |
| 302 | Found | Temporary redirect |
| 400 | Bad Request | Invalid input, malformed request |
| 401 | Unauthorized | Not authenticated (no/invalid token) |
| 403 | Forbidden | Authenticated but not authorized |
| 404 | Not Found | Resource doesn't exist |
| 409 | Conflict | Resource already exists (duplicate) |
| 422 | Unprocessable Entity | Validation errors |
| 429 | Too Many Requests | Rate limit exceeded |
| 500 | Internal Server Error | Server-side error |
| 503 | Service Unavailable | Server down/overloaded |

**Interview Trap:** 401 vs 403 — 401 means "who are you?" (not authenticated), 403 means "I know who you are, but you can't do this" (not authorized).

---

## 8.3 — Authentication: JWT vs Sessions vs Cookies

🔴 VERY COMMON | ⭐ CRITICAL | 🟡 MEDIUM

```
SESSION-BASED AUTH:
  1. User logs in with credentials
  2. Server creates a session in DB/memory, returns session ID
  3. Browser stores session ID in cookie
  4. Each request: browser sends cookie → server looks up session in DB
  Pros: Easy to revoke (delete session from DB)
  Cons: Server must store sessions (not stateless), harder to scale horizontally

JWT (JSON Web Token) AUTH:
  1. User logs in with credentials
  2. Server creates JWT (header.payload.signature), returns it
  3. Client stores JWT (localStorage or httpOnly cookie)
  4. Each request: client sends JWT → server validates signature (no DB lookup)
  Pros: Stateless, scalable, works across domains
  Cons: Can't easily revoke (must wait for expiry or maintain blacklist)

COOKIE vs LOCALSTORAGE for JWT:
  localStorage: Accessible by JS → vulnerable to XSS attacks!
  httpOnly Cookie: Not accessible by JS → safe from XSS, but vulnerable to CSRF
    → mitigate CSRF with SameSite cookie attribute
```

```javascript
// JWT structure
// Header: {"alg": "HS256", "typ": "JWT"}
// Payload: {"sub": "user123", "name": "Abishek", "iat": 1516239022, "exp": 1516242622}
// Signature: HMACSHA256(base64(header) + "." + base64(payload), secret)

// All three joined: xxxxx.yyyyy.zzzzz

// Verifying JWT in Node.js
import jwt from "jsonwebtoken";

const token = req.headers.authorization?.split(" ")[1]; // "Bearer <token>"

try {
  const decoded = jwt.verify(token, process.env.JWT_SECRET);
  req.user = decoded; // { sub, name, iat, exp }
} catch (error) {
  if (error.name === "TokenExpiredError") {
    return res.status(401).json({ error: "Token expired" });
  }
  return res.status(401).json({ error: "Invalid token" });
}
```

---

## 8.4 — CORS

🔴 VERY COMMON | ⭐ CRITICAL | 🟡 MEDIUM

**CORS (Cross-Origin Resource Sharing)** is a browser security mechanism that prevents web pages from making requests to a different domain than the one that served the page — unless the server explicitly allows it.

```
Origin: https://lynkify.in
Request to: https://api.lynkify.in ← different origin (different subdomain)
Browser: "I need to check if the server allows this"
  → Sends OPTIONS preflight request
Server: "I allow requests from lynkify.in"
  → Access-Control-Allow-Origin: https://lynkify.in
Browser: "Great, proceeding with actual request"
```

```javascript
// Express.js CORS setup
import cors from "cors";

app.use(cors({
  origin: ["https://lynkify.in", "http://localhost:3000"], // allowed origins
  methods: ["GET", "POST", "PUT", "DELETE", "PATCH"],
  allowedHeaders: ["Content-Type", "Authorization"],
  credentials: true // allow cookies/auth headers
}));

// Common mistake: setting origin to "*" AND credentials to true — not allowed!
// If credentials: true, you must specify exact origins
```

**CORS is a BROWSER security feature.** It doesn't affect server-to-server requests. Tools like curl and Postman can make cross-origin requests freely because they're not browsers.

---

## 8.5 — Pagination

🟠 COMMON | 🔥 HIGH | 🟡 MEDIUM

```javascript
// Offset Pagination (simple, but slow for large datasets)
GET /api/posts?page=3&limit=20
// SQL: SELECT * FROM posts LIMIT 20 OFFSET 40

// Cursor Pagination (efficient for large datasets, social feeds)
GET /api/posts?cursor=<last_post_id>&limit=20
// SQL: SELECT * FROM posts WHERE id < {cursor} ORDER BY id DESC LIMIT 20
// Pros: consistent results even if new data added, faster on large tables
// Cons: can't jump to arbitrary page

// Response format with pagination metadata
{
  "data": [...],
  "pagination": {
    "total": 500,
    "page": 3,
    "limit": 20,
    "totalPages": 25,
    "hasNext": true,
    "hasPrev": true,
    "nextCursor": "post_123" // for cursor pagination
  }
}
```

---

## 8.6 — Webhooks

🟠 COMMON | 🔥 HIGH | 🟡 MEDIUM

**Webhooks are "reverse APIs"** — instead of your app calling an external API, the external service calls YOUR endpoint when something happens.

```
Traditional polling: "Did anything change? Did anything change? Did anything change?"
Webhook: "Here's what just changed — I'll tell you when it happens."
```

```javascript
// Shopify webhook handler
app.post("/webhooks/orders/created", express.raw({ type: "application/json" }), (req, res) => {
  // Verify webhook authenticity — CRITICAL
  const hmac = req.headers["x-shopify-hmac-sha256"];
  const body = req.body;
  
  const computedHmac = crypto
    .createHmac("sha256", process.env.SHOPIFY_WEBHOOK_SECRET)
    .update(body)
    .digest("base64");

  if (hmac !== computedHmac) {
    return res.status(401).send("Unauthorized");
  }

  // Process the webhook
  const order = JSON.parse(body);
  console.log("New order:", order.id);
  
  // Respond quickly (under 5 seconds) — process async if needed
  res.status(200).send("OK");
  
  // Do heavy processing after responding
  processOrderAsync(order);
});
```

---

<a name="section-9"></a>
# SECTION 9 — SYSTEM DESIGN & ARCHITECTURE

---

## 9.1 — Frontend Architecture for Scalable Apps

🟠 COMMON | 🔥 HIGH | 🔴 HARD

**Folder Structure (Feature-based — recommended for medium/large apps):**
```
src/
├── app/                    → Next.js app router or React app entry
│   ├── (auth)/             → Route group — auth pages
│   ├── (dashboard)/        → Route group — protected routes
│   └── layout.tsx
├── components/
│   ├── ui/                 → Generic UI components (Button, Input, Modal)
│   │   ├── Button/
│   │   │   ├── Button.tsx
│   │   │   ├── Button.test.tsx
│   │   │   └── index.ts
│   └── common/             → App-specific shared components (Header, Sidebar)
├── features/               → Feature-based modules
│   ├── auth/
│   │   ├── components/     → Auth-specific components
│   │   ├── hooks/          → useAuth, useLogin
│   │   ├── api.ts          → Auth API calls
│   │   └── types.ts
│   ├── products/
│   └── cart/
├── hooks/                  → Global custom hooks (useDebounce, useLocalStorage)
├── lib/                    → Utility functions, configuration
│   ├── api.ts              → API client setup (axios instance, base URL)
│   ├── constants.ts
│   └── utils.ts
├── store/                  → Global state (Redux, Zustand)
├── types/                  → TypeScript type definitions
└── styles/                 → Global styles, theme
```

---

## 9.2 — State Management Strategy

🟠 COMMON | 🔥 HIGH | 🟡 MEDIUM

**Decision tree for state management:**

```
Is the state used in only ONE component?
  → YES: useState
  → NO: Continue...

Is it used in a few nearby components?
  → YES: Lift state up + prop drilling (if not too deep)
  → NO: Continue...

Does it change infrequently (auth, theme)?
  → YES: Context API
  → NO: Continue...

Is it complex, frequently changing, or needs middleware?
  → YES: Redux Toolkit or Zustand
  
Is it server state (data from API)?
  → Consider: TanStack Query (React Query) — handles caching, loading, errors automatically
```

**TanStack Query for server state (production recommendation):**
```javascript
import { useQuery, useMutation } from "@tanstack/react-query";

function Products() {
  // Handles: fetching, caching, loading state, error state, refetching, background updates
  const { data, isLoading, error } = useQuery({
    queryKey: ["products", { category: "electronics" }], // cache key
    queryFn: () => fetchProducts({ category: "electronics" }),
    staleTime: 5 * 60 * 1000, // consider data fresh for 5 minutes
    gcTime: 10 * 60 * 1000   // garbage collect after 10 minutes
  });

  const mutation = useMutation({
    mutationFn: createProduct,
    onSuccess: () => {
      queryClient.invalidateQueries({ queryKey: ["products"] }); // refetch
    }
  });
}
```

---

## 9.3 — Authentication Flow (Production)

🔴 VERY COMMON | ⭐ CRITICAL | 🟡 MEDIUM

```
Complete JWT + Refresh Token Flow:

1. User submits login form
2. Server validates credentials
3. Server creates: 
   - Access Token (short-lived: 15 minutes) → sent in response body
   - Refresh Token (long-lived: 7 days) → stored in httpOnly cookie
4. Client stores access token in memory (NOT localStorage)
5. Each API request includes: Authorization: Bearer <access_token>
6. When access token expires (401 response):
   a. Client sends refresh token (httpOnly cookie sent automatically)
   b. Server validates refresh token, issues new access token
   c. Client continues seamlessly
7. Logout: Server invalidates refresh token, client clears access token

Why this approach:
- Short-lived access token → reduces damage window if stolen
- httpOnly refresh token → not accessible by JS (XSS protection)
- Refresh token in DB → can be revoked anytime
```

---

## 9.4 — CDN & Caching Strategy

🟠 COMMON | 🔥 HIGH | 🟡 MEDIUM

```
Cache hierarchy (fastest to slowest):
1. Browser cache (local, instant)
2. CDN edge cache (close to user, ~10-50ms)
3. Server-side cache (Redis, ~1-5ms)
4. Database (original source)

Cache-Control headers:
Cache-Control: public, max-age=31536000, immutable  → static assets (CSS, JS with hash)
Cache-Control: public, max-age=60, stale-while-revalidate=300  → pages (ISR-like)
Cache-Control: private, max-age=0, no-store  → authenticated/sensitive pages

CDN usage (Vercel/Cloudflare):
- Static assets: versioned filenames (main.abc123.js), cached forever
- Next.js SSG pages: served from edge, invalidated on deploy
- Next.js ISR: cached at edge, auto-revalidated
- API routes: cache headers control CDN caching
```

---

<a name="section-10"></a>
# SECTION 10 — PERFORMANCE OPTIMIZATION

---

## 10.1 — Core Web Vitals (Critical for any senior frontend role)

🔴 VERY COMMON | ⭐ CRITICAL | 🟡 MEDIUM

Google's performance metrics — directly impact SEO ranking:

| Metric | Measures | Good | Bad |
|--------|---------|------|-----|
| **LCP** (Largest Contentful Paint) | Loading — how fast main content appears | < 2.5s | > 4s |
| **INP** (Interaction to Next Paint) | Interactivity — how fast UI responds to clicks | < 200ms | > 500ms |
| **CLS** (Cumulative Layout Shift) | Visual stability — how much layout shifts | < 0.1 | > 0.25 |

**How to improve each:**

```javascript
// LCP — optimize the largest image/element
// 1. Use next/image with priority on above-fold images
<Image src="/hero.jpg" priority />

// 2. Preload critical fonts
<link rel="preload" href="/fonts/Inter.woff2" as="font" type="font/woff2" crossOrigin />

// 3. Eliminate render-blocking resources
// Inline critical CSS, defer non-critical JS

// CLS — prevent layout shifts
// 1. Always set width/height on images
<img width="400" height="300" src="..." />
// 2. Reserve space for dynamic content (ads, embeds)
.ad-slot { min-height: 250px; }
// 3. Use CSS transform for animations (not top/left)

// INP (formerly FID) — improve interaction responsiveness
// 1. Reduce JavaScript execution time
// 2. Defer non-critical scripts
// 3. Break up long tasks with setTimeout
// 4. Use web workers for heavy computation
```

**In Lynkify, you can discuss:** You implemented SSR and Core Web Vitals optimizations that drove sustained organic growth. Specifically:
- Used next/image for all creator profile images
- Implemented ISR to serve static pages with near-instant load times
- Minimized JavaScript on creator bio pages (most content is static)

---

## 10.2 — Bundle Optimization

🟠 COMMON | 🔥 HIGH | 🟡 MEDIUM

```javascript
// 1. Code splitting — split bundle into chunks loaded on demand
// React lazy + Suspense (covered in React section)
// Next.js does this automatically per page

// 2. Tree shaking — remove unused code
// Works with ES Modules (import/export)
import { debounce } from "lodash-es"; // ✅ tree-shakable
import _ from "lodash"; // 🚨 imports entire library

// 3. Analyze bundle size
// next build then: npx @next/bundle-analyzer
// Or: npx vite-bundle-visualizer

// 4. Dynamic imports for heavy libraries
const Chart = dynamic(() => import("react-chartjs-2"), { ssr: false });

// 5. External CDN for large unchanged libraries (next.config.js)
const nextConfig = {
  webpack: (config) => {
    config.externals = [...config.externals, { "react-pdf": "ReactPDF" }];
    return config;
  }
};
```

---

## 10.3 — Rendering Optimization

🟠 COMMON | 🔥 HIGH | 🟡 MEDIUM

```
Strategies ranked by impact:
1. Serve HTML pre-rendered (SSG/ISR) — avoids JS execution entirely for initial paint
2. Minimize client-side JavaScript — smaller bundle = faster parse/execute
3. React.memo + useCallback/useMemo — prevent unnecessary re-renders
4. Virtualize long lists — only render visible items
5. Avoid layout thrashing — batch DOM reads and writes
```

```javascript
// Virtualizing long lists — react-virtual or react-window
import { useVirtualizer } from "@tanstack/react-virtual";

function LargeList({ items }) {
  const parentRef = useRef(null);
  
  const virtualizer = useVirtualizer({
    count: items.length,
    getScrollElement: () => parentRef.current,
    estimateSize: () => 50, // estimated row height
  });

  return (
    <div ref={parentRef} style={{ height: "500px", overflow: "auto" }}>
      <div style={{ height: virtualizer.getTotalSize() }}>
        {virtualizer.getVirtualItems().map(virtualRow => (
          <div
            key={virtualRow.index}
            style={{ transform: `translateY(${virtualRow.start}px)` }}
          >
            {items[virtualRow.index].name}
          </div>
        ))}
      </div>
    </div>
  );
  // Renders ~10 items regardless of list size — 10,000 items = same performance
}
```

---

<a name="section-11"></a>
# SECTION 11 — GIT & DEPLOYMENT

---

## 11.1 — Git Workflow

🔴 VERY COMMON | ⭐ CRITICAL | 🟢 EASY

```bash
# Daily workflow
git status              # see what's changed
git add .               # stage all changes
git add -p              # stage interactively (chunk by chunk)
git commit -m "feat: add user profile page" # commit with conventional message
git push origin feature/user-profile

# Branch management
git checkout -b feature/payment-integration  # create and switch
git branch -d feature/done                   # delete local branch
git push origin --delete feature/done        # delete remote branch

# Keeping feature branch up to date
git fetch origin
git rebase origin/main  # rebase feature branch on latest main
# OR
git merge origin/main   # merge main into feature

# Undoing mistakes
git reset --soft HEAD~1  # undo last commit, keep changes staged
git reset --hard HEAD~1  # undo last commit, discard changes
git revert <commit-hash> # create new commit that undoes a commit (safe for shared branches)
git stash               # temporarily save uncommitted changes
git stash pop           # restore stashed changes
```

---

## 11.2 — Merge vs Rebase

🔴 VERY COMMON | ⭐ CRITICAL | 🟡 MEDIUM

```
MERGE — creates a merge commit, preserves full history
  main:    A - B - C - - - - - G (merge commit)
                   \         /
  feature:          D - E - F

REBASE — rewrites feature branch to start from latest main, linear history
  main:    A - B - C
  feature:          D' - E' - F' (replayed on top of C)

When to use merge:
  - Merging completed feature branches into main (preserves context)
  - When history of when branches diverged matters

When to use rebase:
  - Keeping your feature branch up-to-date with main (before PR)
  - NEVER rebase shared/public branches — rewrites history causes problems for others

Golden rule: Never rebase commits that have been pushed to a shared remote branch.
```

---

## 11.3 — Branching Strategy

🟠 COMMON | 🔥 HIGH | 🟡 MEDIUM

**Git Flow (for projects with scheduled releases):**
```
main           → production code only
develop        → integration branch
feature/*      → new features (branch from develop)
hotfix/*       → urgent production fixes (branch from main)
release/*      → release preparation
```

**GitHub Flow (simpler — for continuous deployment):**
```
main            → always deployable
feature/*       → branch from main, PR back to main
hotfix/*        → same as feature
```

**Trunk-Based Development (for mature teams with good CI/CD):**
```
main            → everyone commits here (or very short-lived feature branches)
feature flags   → control what's "live" vs "in development"
```

---

## 11.4 — CI/CD & Deployment

🟠 COMMON | 🔥 HIGH | 🟡 MEDIUM

```yaml
# GitHub Actions workflow (.github/workflows/deploy.yml)
name: Deploy to Production

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    
    steps:
      - uses: actions/checkout@v4
      
      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: "20"
          cache: "npm"
      
      - name: Install dependencies
        run: npm ci
      
      - name: Run tests
        run: npm test
      
      - name: Build
        run: npm run build
        env:
          DATABASE_URL: ${{ secrets.DATABASE_URL }}
          NEXT_PUBLIC_API_URL: ${{ secrets.API_URL }}
      
      - name: Deploy to Vercel
        uses: amondnet/vercel-action@v25
        with:
          vercel-token: ${{ secrets.VERCEL_TOKEN }}
          vercel-org-id: ${{ secrets.VERCEL_ORG_ID }}
          vercel-project-id: ${{ secrets.VERCEL_PROJECT_ID }}
          vercel-args: "--prod"
```

**Vercel deployment (from your Lynkify experience):**
- Automatic deployments on every push to main
- Preview deployments for every PR
- Environment variables per environment (development, preview, production)
- Edge functions for middleware
- Analytics and Core Web Vitals monitoring built-in

---

<a name="section-12"></a>
# SECTION 12 — CODING QUESTIONS

---

## 12.1 — Most Common JavaScript Coding Problems

**Problem 1: Implement debounce from scratch**

🔴 VERY COMMON | ⭐ CRITICAL | 🟡 MEDIUM

```javascript
function debounce(fn, delay) {
  let timer;
  
  return function(...args) {
    // Cancel any previously scheduled call
    clearTimeout(timer);
    
    // Schedule a new call after delay
    timer = setTimeout(() => {
      fn.apply(this, args); // preserve 'this' context and pass all args
    }, delay);
  };
}

// Test
const search = debounce((query) => console.log("Searching:", query), 300);
search("a");     // cancelled
search("ab");    // cancelled  
search("abc");   // runs after 300ms: "Searching: abc"

// Interview explanation:
// "I create a closure over 'timer'. Each time the debounced function is called,
// I clear any pending timer and start a new one. Only when the delay expires
// without another call does the original function run."
```

---

**Problem 2: Flatten a nested array**

🔴 VERY COMMON | ⭐ CRITICAL | 🟡 MEDIUM

```javascript
// Method 1: Built-in (ES2019)
[1, [2, [3, [4]]]].flat(Infinity); // [1, 2, 3, 4]

// Method 2: Recursive (asked in interviews to test recursion)
function flatten(arr) {
  return arr.reduce((flat, item) => {
    return flat.concat(Array.isArray(item) ? flatten(item) : item);
  }, []);
}

// Method 3: Iterative with stack (shows depth)
function flattenIterative(arr) {
  const stack = [...arr];
  const result = [];
  
  while (stack.length > 0) {
    const item = stack.pop();
    if (Array.isArray(item)) {
      stack.push(...item); // unpack arrays back onto stack
    } else {
      result.unshift(item); // add primitives to result
    }
  }
  
  return result;
}

flatten([1, [2, [3, [4]]]]); // [1, 2, 3, 4]
```

---

**Problem 3: Deep clone an object without JSON.parse/stringify**

🟠 COMMON | 🔥 HIGH | 🟡 MEDIUM

```javascript
function deepClone(value) {
  // Primitives (null, undefined, numbers, strings, booleans) — return as-is
  if (value === null || typeof value !== "object") return value;
  
  // Handle Date
  if (value instanceof Date) return new Date(value.getTime());
  
  // Handle Array
  if (Array.isArray(value)) return value.map(deepClone);
  
  // Handle plain Object
  const cloned = {};
  for (const key in value) {
    if (Object.prototype.hasOwnProperty.call(value, key)) {
      cloned[key] = deepClone(value[key]);
    }
  }
  return cloned;
}

const obj = { a: 1, b: { c: [1, 2, 3] }, d: new Date() };
const clone = deepClone(obj);
clone.b.c.push(4);
console.log(obj.b.c); // [1, 2, 3] — original unaffected
```

---

**Problem 4: Implement Promise.all from scratch**

🟠 COMMON | 🔥 HIGH | 🔴 HARD

```javascript
function myPromiseAll(promises) {
  return new Promise((resolve, reject) => {
    const results = [];
    let completed = 0;
    
    if (promises.length === 0) {
      resolve([]); // handle empty array
      return;
    }
    
    promises.forEach((promise, index) => {
      Promise.resolve(promise) // handle non-promise values
        .then(value => {
          results[index] = value; // preserve order!
          completed++;
          if (completed === promises.length) {
            resolve(results); // all done
          }
        })
        .catch(reject); // reject immediately on first failure
    });
  });
}

// Test
myPromiseAll([
  Promise.resolve(1),
  Promise.resolve(2),
  Promise.resolve(3)
]).then(console.log); // [1, 2, 3]

myPromiseAll([
  Promise.resolve(1),
  Promise.reject("Error!"),
  Promise.resolve(3)
]).catch(console.error); // "Error!"
```

---

**Problem 5: Event Emitter (Pub/Sub)**

🟡 OCCASIONAL | 🔥 HIGH | 🔴 HARD

```javascript
class EventEmitter {
  constructor() {
    this.events = {};
  }
  
  on(event, listener) {
    if (!this.events[event]) {
      this.events[event] = [];
    }
    this.events[event].push(listener);
    return this; // for chaining
  }
  
  off(event, listener) {
    if (!this.events[event]) return this;
    this.events[event] = this.events[event].filter(l => l !== listener);
    return this;
  }
  
  emit(event, ...args) {
    if (!this.events[event]) return false;
    this.events[event].forEach(listener => listener(...args));
    return true;
  }
  
  once(event, listener) {
    const wrapper = (...args) => {
      listener(...args);
      this.off(event, wrapper); // auto-remove after first call
    };
    this.on(event, wrapper);
    return this;
  }
}

const emitter = new EventEmitter();
emitter.on("data", (data) => console.log("Received:", data));
emitter.emit("data", { user: "Abishek" }); // "Received: { user: 'Abishek' }"
```

---

**Problem 6: Find duplicates in an array**

🔴 VERY COMMON | ⭐ CRITICAL | 🟢 EASY

```javascript
// Method 1: Using Set
function findDuplicates(arr) {
  const seen = new Set();
  const duplicates = new Set();
  
  for (const item of arr) {
    if (seen.has(item)) {
      duplicates.add(item);
    } else {
      seen.add(item);
    }
  }
  
  return [...duplicates];
}

findDuplicates([1, 2, 3, 2, 4, 3, 5]); // [2, 3]

// Time complexity: O(n), Space: O(n)
```

---

**Problem 7: Implement memoization**

🟠 COMMON | 🔥 HIGH | 🟡 MEDIUM

```javascript
function memoize(fn) {
  const cache = new Map();
  
  return function(...args) {
    const key = JSON.stringify(args); // create cache key from args
    
    if (cache.has(key)) {
      console.log("Cache hit!");
      return cache.get(key);
    }
    
    const result = fn.apply(this, args);
    cache.set(key, result);
    return result;
  };
}

// Test with expensive computation
const expensiveAdd = memoize((a, b) => {
  console.log("Computing...");
  return a + b;
});

expensiveAdd(1, 2); // "Computing..." → 3
expensiveAdd(1, 2); // "Cache hit!" → 3 (no recomputation)
expensiveAdd(2, 3); // "Computing..." → 5
```

---

## 12.2 — React Coding Problems

**Problem 1: Build a custom useFetch hook**
*(Already covered in Section 4.9 — refer there)*

**Problem 2: Implement infinite scroll**

🟠 COMMON | 🔥 HIGH | 🟡 MEDIUM

```jsx
function InfiniteList() {
  const [items, setItems] = useState([]);
  const [page, setPage] = useState(1);
  const [loading, setLoading] = useState(false);
  const [hasMore, setHasMore] = useState(true);
  const observerRef = useRef(null);
  const sentinelRef = useRef(null); // invisible element at bottom of list

  useEffect(() => {
    async function loadMore() {
      if (loading || !hasMore) return;
      setLoading(true);
      
      const newItems = await fetchItems(page);
      setItems(prev => [...prev, ...newItems]);
      setHasMore(newItems.length > 0);
      setLoading(false);
    }
    loadMore();
  }, [page]);

  // Intersection Observer watches the sentinel element
  useEffect(() => {
    observerRef.current = new IntersectionObserver(
      entries => {
        if (entries[0].isIntersecting && hasMore && !loading) {
          setPage(p => p + 1); // load next page when sentinel is visible
        }
      },
      { threshold: 0.1 }
    );

    if (sentinelRef.current) {
      observerRef.current.observe(sentinelRef.current);
    }

    return () => observerRef.current?.disconnect();
  }, [hasMore, loading]);

  return (
    <div>
      {items.map(item => <ItemCard key={item.id} item={item} />)}
      <div ref={sentinelRef}> {/* invisible sentinel */}
        {loading && <Spinner />}
        {!hasMore && <p>No more items</p>}
      </div>
    </div>
  );
}
```

---

**Problem 3: Counter with reset and history**

🟠 COMMON | 🔥 HIGH | 🟢 EASY

```jsx
function CounterWithHistory() {
  const [count, setCount] = useState(0);
  const [history, setHistory] = useState([0]);

  const addToHistory = (newCount) => {
    setHistory(prev => [...prev, newCount]);
    setCount(newCount);
  };

  const increment = () => addToHistory(count + 1);
  const decrement = () => addToHistory(count - 1);
  const reset = () => { setCount(0); setHistory([0]); };
  const undo = () => {
    if (history.length <= 1) return;
    const newHistory = history.slice(0, -1);
    setHistory(newHistory);
    setCount(newHistory[newHistory.length - 1]);
  };

  return (
    <div>
      <h2>{count}</h2>
      <button onClick={increment}>+</button>
      <button onClick={decrement}>-</button>
      <button onClick={undo} disabled={history.length <= 1}>Undo</button>
      <button onClick={reset}>Reset</button>
      <p>History: {history.join(" → ")}</p>
    </div>
  );
}
```

---

<a name="section-13"></a>
# SECTION 13 — BEHAVIORAL & HR QUESTIONS

---

## 13.1 — "Tell me about yourself"

🔴 VERY COMMON | ⭐ CRITICAL

**Strong Answer (PAST → PRESENT → FUTURE structure):**

> "I'm a Full Stack Developer with around 2.5 years of experience, primarily in the JavaScript ecosystem — React, Next.js, and Node.js. I started my career at Kiruvin Creations building websites and integrating REST APIs for clients across different industries. From there, I joined Luxeveda Brand Services, where I've been working on enterprise-level projects — I built a modular WordPress plugin system for PI Industries, a $6 billion company, and developed a Shopify storefront for Beretta Gallery USA that supports over $2.5 million in annual revenue. Alongside that, I independently built and scaled Lynkify — a SaaS creator platform — from scratch to over 100,000 monthly visitors, handling everything from the Next.js frontend and Node.js backend to PostgreSQL and MongoDB databases and CI/CD pipelines. I'm now looking for a role where I can go deeper into frontend architecture and React development, ideally in a product-focused environment where I can contribute to real business outcomes."

**What the interviewer evaluates:** Structure, confidence, relevance to the role, whether you can tell a compelling story about your career trajectory.

**Weak answer (avoid):** "I'm a developer with 2.5 years of experience. I know React, Next.js, and JavaScript. I like problem-solving and learning new technologies..."

---

## 13.2 — "Why are you leaving your current company?"

🔴 VERY COMMON | ⭐ CRITICAL

**Strong Answer:**

> "I've had genuinely great experiences at Luxeveda — enterprise clients, real production impact, and the freedom to build Lynkify independently. But I feel I've reached a point where I've extracted most of the learning I can in this environment. I want to join a team with stronger engineering culture — more code reviews, architectural discussions, and mentorship — where I can grow as a senior developer rather than continuing to operate as a one-person engineering team. The role you're hiring for aligns well with that."

**What NOT to say:** "My manager is difficult" / "Salary is too low" / "The work is boring" — even if true.

---

## 13.3 — "Tell me about a difficult bug you solved"

🟠 COMMON | ⭐ CRITICAL

**Strong Answer (use your real Lynkify experience):**

> "One that stands out is a production issue on Lynkify where some users were seeing stale data on their bio pages even after updates. After ruling out browser caching, I dug into the Next.js ISR configuration and found that the revalidation interval was set to a very long period for some pages — which was fine for most content but wasn't acceptable for link updates. The deeper issue was that our CDN was also caching responses independently, with a longer TTL than our ISR revalidation period. The fix involved two parts: shortening the ISR revalidation time for user-generated content pages, and implementing on-demand revalidation via a webhook that fires whenever a user updates their links. After deploying, I verified with cache-control header inspection and monitored for 24 hours before closing the issue. The experience made me much more careful about understanding the full caching chain — CDN, Next.js, and browser — not just one layer."

**Structure:** SITUATION → INVESTIGATION → ROOT CAUSE → SOLUTION → OUTCOME

---

## 13.4 — "Tell me about your biggest failure"

🟡 OCCASIONAL | 🔥 HIGH

**Strong Answer:**

> "Early in building Lynkify, I made the mistake of premature optimization. I spent about two weeks implementing a sophisticated caching layer before I had any real users. That time would have been much better spent building features that actually drove user acquisition. By the time I launched, some of the infrastructure I built was unused and added complexity I then had to maintain. The lesson was real — validate the problem before optimizing the solution. Since then, I ship a simpler working version first, measure actual bottlenecks, and then optimize based on data."

---

## 13.5 — "What are your strengths and weaknesses?"

🔴 VERY COMMON | ⭐ CRITICAL

**Strengths:**
> "My strongest area is translating business requirements into technical implementations quickly. When PI Industries needed a modular plugin system that could serve multiple projects, I designed an architecture that reduced delivery effort by 40% across their subsidiary. I'm also strong at performance-first thinking — I care about Core Web Vitals and real-user experience, not just making code work."

**Weakness (be honest but show growth):**
> "I've been very independent for most of my career — building Lynkify solo means I don't always default to asking for input or code review. I'm actively working on that — deliberately seeking feedback on architectural decisions and treating code review as a learning tool, not just a quality gate."

---

## 13.6 — "Tell me about a conflict with a teammate"

🟡 OCCASIONAL | 🔥 HIGH

**Strong Answer:**

> "At Kiruvin, we had a situation where a junior developer and I disagreed on the approach for an API integration — they wanted to build a custom caching solution from scratch, while I felt we should use an established library given our deadline. Rather than pushing my view, I asked them to walk me through their reasoning. They had a valid performance concern I hadn't fully considered. We ended up doing a quick spike: their approach outperformed the library in that specific use case, so we went with it. The lesson for me was to create space for technical disagreement rather than defaulting to seniority."

---

## 13.7 — Salary Expectations

🔴 VERY COMMON | ⭐ CRITICAL

**Strategy:**
Research current market rates for your target roles in Bangalore before every interview. Use LinkedIn Salary, Glassdoor, levels.fyi (for product companies), and AmbitionBox for Indian market data.

**Answer template:**
> "Based on my research and my experience with production systems at scale — enterprise clients and a SaaS product with 100K+ monthly visitors — I'm targeting the [X to Y] range. That said, I'm more interested in the right fit, so I'm open to discussion based on the overall compensation structure."

**Never give a number first** if you can avoid it. "What's the budget for this role?" is a valid counter.

---

<a name="section-14"></a>
# SECTION 14 — PORTFOLIO & PROJECT DISCUSSION

---

## 14.1 — How to Talk About Lynkify (Your Star Project)

**The STAR + Technical Depth structure:**

**Situation:**
> "I identified a gap in the Indian creator economy — artists and musicians needed a unified link-in-bio tool combined with music distribution and analytics, and the existing tools were either too expensive or too generic."

**Task:**
> "I architected and built the entire platform myself — product decisions, design, engineering, DevOps, and growth."

**Technical Architecture (go deep here):**
> "The stack is Next.js for the frontend with a heavy focus on SSR and ISR for creator bio pages — SEO discoverability is critical for creators. The backend is a Node.js/Express API layer with PostgreSQL as the primary database for structured relational data (users, subscriptions, analytics) and MongoDB for flexible schema data like link configurations and bio page layouts. I deployed the entire system on Vercel for the frontend and a self-hosted VPS using Coolify for the backend services."

**Performance:**
> "For Core Web Vitals, the main challenge was creator bio pages needing to load fast globally for diverse audiences. I used ISR with a 60-second revalidation window — so the page is served as a static file from Vercel's CDN globally, and updates propagate within a minute of a creator changing their links. This gave us sub-2 second LCP at P75. For the analytics dashboard, it's CSR with React Query, since it shows real-time user-specific data that doesn't benefit from SSR."

**Challenges:**
> "The hardest scaling challenge was the analytics pipeline — tracking link clicks at 100K+ monthly visitors without hammering the database. I implemented a write-behind cache pattern where clicks are buffered in Redis and flushed to PostgreSQL in batch every 5 minutes. This reduced database write load by about 90% while keeping analytics data accurate within a 5-minute window, which is acceptable for the use case."

**Outcome:**
> "100K+ monthly visitors, adopted by enterprise music marketing firms, subscription revenue through Dodo Payments integration."

---

## 14.2 — How to Talk About the PI Industries WordPress Plugin

> "PI Industries is a $6 billion agricultural chemicals company. They needed a custom WordPress system to manage their product catalog, dealer network, and regulatory documentation across multiple languages and markets. I built a modular plugin architecture where core functionality — data models, admin UI framework, REST API endpoints — lived in one plugin, and market-specific extensions were separate plugins that hooked into the core. This meant when we built a similar system for PI Health Sciences, we reused about 60% of the core plugin with zero modifications, just adding a new extension plugin for their specific requirements. That's where the 40% delivery time reduction came from."

---

## 14.3 — How to Talk About Beretta Gallery Shopify

> "Beretta Gallery is a high-end firearms retailer doing over $2.5M annually on Shopify. The main challenges were conversion rate optimization and performance. I rebuilt their theme with a focus on product discovery — custom filtration UX in Liquid with JavaScript-driven filtering that didn't require page reloads. For performance, I audited every section and snippet, eliminated render-blocking scripts from third-party apps, and implemented lazy loading for all product images below the fold. I also built a seasonal campaign system using Shopify's section schema that allowed the marketing team to self-serve campaign banners without developer intervention, which dramatically reduced the back-and-forth during their peak sales periods."

---

## 14.4 — Strong Storytelling Framework

When explaining any project, hit these 6 points:

1. **Context:** What was the business problem?
2. **Decision:** What technical approach did you choose and why?
3. **Alternative:** What did you NOT choose and why?
4. **Execution:** What was technically interesting or difficult?
5. **Result:** What was the measurable outcome?
6. **Learning:** What would you do differently?

---

<a name="section-15"></a>
# SECTION 15 — MOCK INTERVIEW SIMULATIONS

---

## Mock Interview 1 — Beginner Level (React/Frontend Role)

**Q: What is the difference between state and props in React?**

Expected Answer: Props are read-only data passed from parent to child — a component cannot modify its own props. State is mutable data managed within a component — changes to state trigger re-renders. The key distinction is ownership: props are owned by the parent, state is owned by the component.

Follow-up: "Can a child component change its parent's state?" → Not directly, but a parent can pass a callback function as a prop, and the child can call that function, which updates the parent's state.

---

**Q: What happens when you call setState in a React class component?**

Expected Answer: It schedules a state update — it doesn't mutate state immediately. React batches state updates and triggers a re-render. You should never rely on the state value immediately after calling setState; use the callback form `setState(prevState => ...)` if the new state depends on the current one.

---

**Q: What is the difference between useEffect with no deps, [], and [dep]?**

Expected Answer: (Covered in Section 4.3) — no deps = runs after every render, [] = runs once after mount, [dep] = runs when dep changes.

---

## Mock Interview 2 — Mid-Level (Next.js / Full Stack)

**Q: How would you implement authentication in a Next.js application?**

Expected Answer: Walk through the JWT + Refresh Token flow from Section 8.3. Mention NextAuth.js as the production solution. Discuss protecting routes with middleware. Cover storing tokens securely (httpOnly cookies vs localStorage). Mention the difference between SSR-aware auth (reading auth in getServerSideProps/server components) vs CSR auth.

Follow-up: "How would you protect an API route?" → Check the token in the route handler. "How would you protect an entire section of pages?" → Next.js middleware.

---

**Q: You have a page that shows a product list. The data changes every hour. What rendering strategy would you use?**

Expected Answer: ISR (Incremental Static Regeneration) with `revalidate: 3600`. The page is statically generated for fast delivery from CDN, and Next.js regenerates it in the background every hour. If a deploy triggers before the hour, `revalidateTag` can force an immediate refresh.

Follow-up: "What if data must be real-time?" → SSR or CSR with polling/WebSocket.

---

**Q: What are Server Components in Next.js and how do they differ from Client Components?**

Expected Answer: Server Components run only on the server — they can directly access databases, APIs, and environment secrets. They send only HTML to the client, with no JavaScript bundle for the component. Client Components run on both server (for initial SSR) and client (for interactivity). They have access to hooks, browser APIs, and event handlers. The "use client" directive marks a component as a Client Component. The rule of thumb is: make everything a Server Component by default, and opt into Client Components only when you need interactivity, state, or browser APIs.

---

## Mock Interview 3 — Senior-Style Pressure Interview

**Q: I want you to design a URL shortener + analytics dashboard like Lynkify's smart links. Walk me through the system design.**

Expected Answer Framework:

> "Let me clarify requirements first. Core features: shorten URLs, track clicks, show analytics. Scale assumption: 100K users, 1M clicks per day. Let me break it into components.

> **Data models:** Links table (id, short_code, original_url, user_id, created_at). Clicks table or analytics store (link_id, timestamp, ip, country, device, referrer).

> **Short code generation:** 6-character base62 (a-z, A-Z, 0-9) gives 56 billion combinations — more than enough. Options: random generation with collision check, or counter-based with base62 encoding for predictability.

> **Redirect flow:** User hits `lynkify.in/abc123` → edge function or CDN checks cache → if cached, redirect immediately → if not, query database → return 301 or 302 redirect → log click asynchronously.

> **Analytics:** Direct database writes at 1M clicks/day means ~12 writes/second — manageable but I'd still buffer in Redis and flush every 30 seconds to reduce database pressure and enable batching for geographical aggregation.

> **Rendering:** Dashboard is CSR with React Query — real-time, user-specific. Public bio pages are ISR — static with revalidation.

> **Caching:** Redis for hot links (top 10K links serve 80% of traffic). CDN for public pages. Browser 301 redirects for permanent links — users' browsers cache them."

Follow-up Pressure Questions:
- "What if a creator has 1M followers and all click the link simultaneously?" → CDN absorbs redirect traffic. Database reads are cached in Redis. Queue analytics writes.
- "How would you handle geographic analytics?" → MaxMind GeoIP database for IP → country mapping. Aggregate in analytics service, not raw database.
- "What would you change about your current Lynkify architecture?" → "I'd separate the analytics service into its own microservice with ClickHouse as the analytics database (columnar, built for time-series), rather than PostgreSQL which is better for transactional data."

---

<a name="section-16"></a>
# SECTION 16 — FINAL REVISION NOTES & CHEAT SHEET

---

## 🗒️ Last-Day Revision Sheet

Read this the morning of your interview. Nothing new — just refreshing what you know.

---

### JavaScript Rapid-Fire

- **Hoisting:** var → undefined; function declarations → fully hoisted; let/const → TDZ (ReferenceError)
- **Event loop order:** Call stack → Microtasks (all) → One Macrotask → Microtasks again
- **Closure:** Function retains access to its lexical scope even after outer function returns
- **this in arrow function:** Inherited from surrounding context at definition time
- **== vs ===:** == coerces types; === checks type AND value
- **null == undefined:** true; **null === undefined:** false
- **typeof null:** "object" (historical bug)
- **NaN === NaN:** false → use Number.isNaN()
- **Promise.all vs allSettled:** all = fails fast on rejection; allSettled = waits for all, reports each result

---

### React Rapid-Fire

- **Virtual DOM:** JS object tree; React diffs old vs new to compute minimal real DOM updates
- **useEffect dependencies:** [] = once; no array = every render; [dep] = when dep changes
- **useMemo:** Caches computed value; recalculates when deps change
- **useCallback:** Caches function reference; prevents child re-render if wrapped in memo
- **useRef:** Persists value across renders without triggering re-render; also for DOM access
- **React.memo:** Prevents re-render if props haven't changed (shallow comparison)
- **Key rule:** Use stable unique IDs, not array index, for list keys
- **Stale closure:** useEffect captures old values → fix with correct deps or functional updates
- **Context performance:** All consumers re-render when context value changes; split contexts

---

### Next.js Rapid-Fire

- **SSG:** HTML at build time; `revalidate` = ISR; fastest, CDN-cached
- **SSR:** HTML per request; always fresh; slowest initial TTFB under load
- **CSR:** Browser renders; worst initial SEO; best for private/real-time data
- **Server Component:** No client JS bundle; can access DB/secrets directly; no hooks/events
- **Client Component:** "use client"; has hooks, events, browser APIs; sent to client
- **Middleware:** Runs at edge before request; good for auth, redirects, A/B testing
- **Image component:** Auto WebP, lazy loading, prevents CLS; use `priority` for LCP images

---

### WordPress Rapid-Fire

- **add_action:** Run code at a point; no return needed
- **add_filter:** Modify data and return it; ALWAYS return from filters
- **WP_Query:** Main post query class; always `wp_reset_postdata()` after custom queries
- **Nonces:** CSRF protection; create with `wp_create_nonce()`, verify with `wp_verify_nonce()`
- **Sanitize input:** `sanitize_text_field()`, `sanitize_email()`, `wp_kses_post()`
- **Escape output:** `esc_html()`, `esc_attr()`, `esc_url()`

---

### Shopify Rapid-Fire

- **Sections:** Have `{% schema %}` — customizable in Theme Editor; rendered in templates
- **Snippets:** No schema, just reusable code; `{% render 'snippet-name' %}`
- **Liquid output:** `{{ variable }}`; Liquid tags: `{% tag %}`
- **Filters:** `| money`, `| img_url: '400x'`, `| upcase`, `| truncate: 100`
- **Storefront API:** GraphQL, client-side/headless access; needs Storefront token
- **Admin API:** Full access to store data; server-side only; not for browser

---

### HTTP/API Rapid-Fire

- **401 vs 403:** 401 = not authenticated; 403 = authenticated but not authorized
- **PUT vs PATCH:** PUT = replace entire resource; PATCH = partial update
- **CORS:** Browser security; server must allow origin via headers; doesn't affect server-to-server
- **JWT:** Header.Payload.Signature; stateless; store in httpOnly cookie (not localStorage)
- **Idempotent:** GET, PUT, DELETE (calling multiple times = same result)

---

### Core Web Vitals Rapid-Fire

- **LCP:** How fast main content appears → target < 2.5s → optimize hero image, `priority` on above-fold
- **INP:** How fast UI responds to interaction → target < 200ms → reduce JS, defer non-critical
- **CLS:** How much layout shifts → target < 0.1 → always set image dimensions, reserve space for ads

---

## 🗣️ Interview Communication Tips

**Before answering any technical question:**
1. Repeat or rephrase the question ("So you're asking about...")
2. Think out loud — interviewers evaluate reasoning process, not just final answer
3. Start with the simple case, then handle edge cases
4. Say what you're unsure about honestly — "I believe it works this way, but I'd want to verify..."

**Phrases that show senior-level thinking:**
- "It depends on the use case — let me walk through the tradeoffs..."
- "In production, I'd also consider..."
- "The simple answer is X, but at scale you'd want to think about Y..."
- "I've used this in Lynkify where..."

**Phrases to avoid:**
- "I don't know" without following with "but I'd approach it by..."
- "I've never used that" without a bridge to what you HAVE used
- Rushing to answer before thinking

**If you blank on something:**
> "I know the general concept here, but I'm blanking on the exact syntax. The idea is [explain concept]. I'd look up the specific API in documentation — here's how I'd approach using it..."

**Body language:** Speak at 80% of your natural pace. Pauses are fine — they signal thinking. Filler words like "um" and "like" increase under pressure; replace with literal silence.

---

## ⚡ The Night Before Checklist

- [ ] Read the JD again — identify their stack, their scale, their product
- [ ] Prepare your 3 project stories using STAR + Technical Depth framework
- [ ] Review your own resume — be ready to explain every line
- [ ] Prepare 3 thoughtful questions to ask the interviewer
- [ ] Know the company's product — use it, understand the UX
- [ ] Test your internet, mic, and camera (for remote interviews)
- [ ] Sleep by 11pm — cognitive performance degrades sharply with sleep deprivation
- [ ] Review this rapid-fire section once over breakfast

---

## ❓ 5 Questions to Ask the Interviewer (Signals You're Serious)

1. "What does a typical pull request review process look like here? How do you handle technical disagreements?"
2. "What are the biggest frontend performance or architecture challenges the team is currently working on?"
3. "How does the team decide between using an established library vs building in-house?"
4. "What does career growth look like for engineers here — is there a defined path from mid to senior?"
5. "What's one thing you'd change about the engineering culture if you could?"

---

## 💪 Confidence Foundation

You have shipped production code that makes real money:
- **$2.5M+ in Shopify revenue** — your UX and performance work directly impacted conversion rates
- **$6B+ enterprise client** — PI Industries trusted you with a system used across multiple entities
- **100K+ monthly visitors** — Lynkify, built entirely by you, at meaningful scale
- **Real CI/CD, real databases, real observability** — not toy projects

The gap between knowing concepts and articulating them clearly is what interview preparation closes. You have the real experience. This guide helps you communicate it at the level it deserves.

**You're more prepared than you feel. Now go execute.**

---

*Guide Version: May 2026 | Tailored for Abishek M — Full Stack Developer*
*Stack: React · Next.js · WordPress · Shopify · Node.js · PostgreSQL · MongoDB*
