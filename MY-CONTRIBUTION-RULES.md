# How To Write Like a Human in Open Source

A style guide for everything I write in public: code comments, PR
descriptions, GitHub comments, commit messages, branch names.
Goal: simple, honest, human tone. Easy English everyone can understand.

---

## 1. How to think before writing anything

- First understand the thing fully. If I can't explain it in one simple
  sentence to a friend, I am not ready to write about it.
- Ask myself: "What does the reader need to know?" Write only that.
- Write it the way I would SAY it to a person sitting next to me.
- Then cut it shorter. Then cut again.

---

## 2. Code comments

### When to write a comment

- Only when the code cannot explain itself.
- Explain WHY, not WHAT. The code already shows what it does.
- If the code is simple, write NO comment. Silence is human too.

### How to write it

- One line if possible. Two lines maximum.
- Plain words. No big vocabulary.

### Examples

BAD (AI tone — long, formal, explains everything):
```js
// Only take the fast path for arrays that iterate with the default
// iterator: Array.isArray pierces Proxies, so a Proxy with a custom
// Symbol.iterator must fall through to the iterator-based helpers
// to match native destructuring semantics.
```

GOOD (human tone — short, just the reason):
```js
// Protect against arrays (or proxies) with a custom iterator
```

BAD:
```js
// Iterate over the users array and filter active ones
```
(the code already says this — delete it)

GOOD: no comment at all.

---

## 3. PR descriptions

### Shape

3 to 5 simple sentences. That's all.

```
Fixes #<number>

<what was broken - 1 or 2 sentences>
<what I changed - 1 or 2 sentences>
<tests - 1 sentence>
```

### Rules

- Short sentences. One idea per sentence.
- Say "I" — "I changed", "I added". A human says I.
- Small grammar mistakes are fine. Do not polish it.
- No markdown tables, no bold headers, no emoji, no bullet storms
  (unless the repo template forces a table).

### Words that smell like AI — never use

- "This PR introduces / implements / addresses..."
- "comprehensive", "robust", "seamlessly", "leverages", "ensures"
- "It's worth noting that...", "Additionally...", "Furthermore..."
- "diverging from native semantics" type textbook phrases
- Anything that sounds like documentation or marketing

### Example

BAD (AI tone):
> This PR introduces a comprehensive fix that ensures the helper
> seamlessly handles Proxy objects, maintaining full spec compliance
> across all supported environments.

GOOD (human tone):
> Fixes #18181
>
> Destructuring a Proxy around an array was reading indexes directly,
> but it should use the iterator. I added a check so the fast path
> only applies to normal arrays.
>
> Added a test and updated one old fixture. Tests pass on my machine.

---

## 4. GitHub comments and replies

- Answer the question. Nothing extra.
- Short. One to three sentences is normal for humans.
- Did what reviewer asked? Reply just: "Done." or "Done, pushed."
- Don't know something? Say "I'm not sure" — humans say this, AI never does.
- No thank-you essays. One "thanks" maximum, and only when natural.
- Never argue. If I disagree, ask one polite question:
  "Should this also cover X, or keep it simple for now?"

### Example

BAD (AI tone):
> Thank you so much for the thorough review! I really appreciate your
> valuable feedback. I have carefully addressed all the points you
> raised and pushed the updated changes. Please let me know if there
> is anything else I can improve!

GOOD (human tone):
> Done, pushed. Also shortened the comment like you said.

---

## 5. Commit messages

- One short line, small letters, says what changed.
- Body only if the WHY is not obvious — 2 or 3 plain sentences max.
- A small change gets a small message.

### Examples

GOOD:
```
shorten comment in arrayWithHoles, per review
```
```
fix iterator check for proxy arrays
```

BAD (AI tone):
```
refactor: enhance _arrayWithHoles helper to ensure robust handling
of Proxy-wrapped arrays with comprehensive iterator validation
```

---

## 6. Branch names

- Short, lowercase, dashes: `fix-proxy-iterator`, `fix-enum-warning`
- Says the thing it fixes. Nothing more.
- No ticket-number-only names, no `feature/comprehensive-fix-v2`.

---

## 7. Issue reports (when I report a bug)

```
<what I did - 1-2 sentences>
<what happened - 1 sentence>
<what I expected - 1 sentence>
<small code example that shows it>
```

Plain words. A maintainer should understand it in 30 seconds.

---

## 8. The quick test before I post ANYTHING

Read it once and ask:

1. Would I say this out loud to a person? If no — rewrite simpler.
2. Is any sentence longer than ~15 words? Split it.
3. Any word I would never use when speaking? Replace it.
4. Can I delete half of it and keep the meaning? Delete.
5. Does it sound like a product announcement? Start over.

---

## Everything in one line

**Write short. Write simple. Write like I talk. Delete half. Post.**
