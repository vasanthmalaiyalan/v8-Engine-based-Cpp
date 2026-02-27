# 🧾 VM / Compiler / GC Books vs V8 Docs — Concept Map

---

## ✅ உங்கள் 4 Books Cover பண்ணும் Theory

**Books:**
```
Crafting Interpreters  → VM + bytecode
Engineering a Compiler → SSA + optimizer
GC Handbook            → GC
C++                    → memory + objects
```

**இதனால் தெரிந்திருப்பது:**
```
interpreter loop
bytecode VM
closures
SSA IR
register allocation
optimizations
GC algorithms
```

✔ universal compiler/runtime theory

---

## 🎯 V8 Docs-ல் மட்டும் இருக்கும் (Books-ல் இல்லாதது)

---

### 1️⃣ Hidden Classes (Maps)

**V8 docs:** Maps, aka Hidden Classes

✔ Books-ல் இது கிடையாது

**ஏன்?**

Books assume:
```
objects = hash map
```

V8 reality:
```
objects = struct-like layout
shape transitions
inline property offsets
```

✔ JS dynamic objects → static-like optimization  
✔ இது V8-specific trick

---

### 2️⃣ Inline Caches (Real JS IC Design)

**V8 docs:**
```
monomorphic
polymorphic
megamorphic
feedback vector
```

**Books-ல் IC concept வரும் BUT:**
```
❌ JS property IC இல்லை
❌ FeedbackVector இல்லை
❌ shape-based IC இல்லை
```

✔ V8 IC = language-specific specialization

---

### 3️⃣ Slack Tracking

**V8 docs:** Slack Tracking — what is it?

✔ Books-ல் 0%

**Idea:**
```
constructor objects
initial size guess
unused slots shrink later
```

✔ JS object allocation optimization trick

---

### 4️⃣ Torque Language

**V8 docs:**
```
Torque user manual
CSA builtins
```

✔ Books-ல் இல்லை

**Torque =**
```
DSL for VM objects + builtins
```

✔ V8 internal meta-language

---

### 5️⃣ JS-Specific Deoptimization Realities

**Books:**
```
deopt exists
```

**V8 docs:**
```
speculative JS assumptions
maps + IC + feedback
real bailout causes
```

✔ dynamic language JIT reality

---

### 6️⃣ Ignition Accumulator Design

**Crafting Interpreters:**
```
stack VM
```

**V8:**
```
register + accumulator hybrid
```

✔ design difference

---

### 7️⃣ TurboFan Sea-of-Nodes for JS

**Engineering a Compiler:**
```
SSA graph
```

**V8:**
```
JS typed nodes
speculative types
feedback driven IR
```

✔ dynamic language SSA

---

## 📊 Summary — Books vs V8 Docs

| Topic | Books | V8 docs |
|-------|-------|---------|
| VM | ✅ | — |
| Bytecode | ✅ | — |
| SSA | ✅ | — |
| GC | ✅ | — |
| Register alloc | ✅ | — |
| Closures | ✅ | — |
| Hidden classes | ❌ | ✅ |
| JS inline caches | ❌ | ✅ |
| Feedback vector | ❌ | ✅ |
| Slack tracking | ❌ | ✅ |
| Torque | ❌ | ✅ |
| JS deopt causes | ❌ | ✅ |
| JS shapes | ❌ | ✅ |

---

## ✅ Answer

V8 docs-ல் இருக்கும் Hidden Classes, Inline Caches, Slack Tracking, Torque, JS-specific deoptimization, JS object layout இந்த topics-ஐ எந்த compiler/VM/GC books-லும் முழுமையாக கற்றுக்கொள்ள முடியாது, ஏனெனில் அவை JavaScript language-க்கு குறிப்பாக V8 engine உருவாக்கிய implementation strategies ஆகும்.

---

## 🎯 Exactly What YOU Should Read

**From your list — Under the hood → read:**
```
Ignition
TurboFan
Maps (Hidden Classes)
Slack Tracking
```

**Optional later:**
```
Torque
```

---

## ✅ Bottom Line

```
Books    → universal engine theory
V8 docs  → JS engine reality
```

✔ இரண்டும் சேரும் இடம் = V8 mastery
