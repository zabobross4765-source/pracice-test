# Lockdown Practice Test

A single-page app for taking timed practice tests in a fullscreen lockdown mode, with
**multiple-choice** and **short-answer** questions.

- Upload or paste a test (.txt, .csv, .json, .pdf). Intro pages, page numbers and headers are cleaned up automatically.
- Mixed tests, or multiple choice only / short answer only. All questions on one page, or one at a time with a question navigator.
- Short answers are graded automatically from keywords (you can override the grade), or you grade them yourself against a model answer.
- Answer keys (separate or embedded in the test) stay hidden until you submit. Explanations show on the results page.
- Reference materials (formula sheets, notes) open in a side panel without breaking lockdown.
- Fullscreen enforcement, tab-switch and focus-loss detection, violation log, auto-submit, 5-minute warning.

Everything runs in the browser. Uploaded files never leave your computer.

## Using your own question bank

Upload or paste any of these formats on the setup screen.

**Text / PDF**

```
1. What is the chemical symbol for gold?
A) Ag
B) Au
C) Gd
D) Go
Answer: B
Explanation: Au comes from the Latin word aurum.

2. What is the powerhouse of the cell?
Type: short                         (optional: no choices = short answer)
Keywords: mitochondria; mitochondrion   (any one counts as correct)
Match: all                          (optional: every keyword must appear)
Model answer: The mitochondria
Explanation: They produce most of the cell's ATP.
```

A short-answer question with only a `Model answer:` (no keywords) is graded by you on the results page.

**CSV** (header row; columns in any order)

```
type,question,A,B,C,D,answer,keywords,model answer,explanation
mcq,What is 2+2?,3,4,5,6,B,,,Two plus two is four.
short,Capital of France?,,,,,,Paris,Paris,
```

**JSON**

```json
[
  { "type": "mcq", "question": "What is 2+2?", "choices": ["3", "4", "5", "6"], "answer": "B",
    "explanation": "Two plus two is four." },
  { "type": "short", "question": "Capital of France?", "keywords": ["Paris"],
    "modelAnswer": "Paris", "match": "any" }
]
```

To ship a built-in test with the site, replace the `SAMPLE` text in `index.html` with your own
questions in the text format above. "Load sample test" will then load them.
