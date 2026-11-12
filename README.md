# Lockdown Practice Test

A single-page app for taking timed practice tests in a fullscreen lockdown mode, with
**multiple-choice** and **short-answer** questions.

- Upload or paste a test (.txt, .csv, .json, .pdf). Intro pages, page numbers and headers are cleaned up automatically.
- Mixed tests, or multiple choice only / short answer only. All questions on one page, or one at a time with a question navigator.
- Short answers are graded automatically from keywords (you can override the grade), or you grade them yourself against a model answer.
- Answer keys (separate or embedded in the test) stay hidden until you submit. Explanations show on the results page.
- Reference materials (formula sheets, notes) open in a side panel without breaking lockdown.
- Fullscreen enforcement, tab-switch and focus-loss detection, violation log, auto-submit, 5-minute warning.

Every test opens on a cover page (title, instructions, test mode, question count, time limit, marks); questions only appear after **Start Test**. Retake and Back to menu return to the cover page.

Exam-style PDFs are supported too: "Question 3 (Two parts; 8 marks in total): …" with parts "(a) (6 marks): …" become one short-answer question per part, each showing its question's setup, its marks, and an image of the original PDF page so tables and formulas stay readable. The time limit is read from the cover ("You have 3 hours").

**Original file (default view):** the app opens on the Original file view, with a drop zone until a file is added. Tabs at the top switch to the MCQ test, Short answer test or Mixed test at any time (tests start from their cover page). Any uploaded file (PDF, image, text, document) is also kept exactly as uploaded. Pick **Original file** on the cover page to view it as-is with a download link, or open it from the setup screen with "Open a file as-is" without making questions from it. During a test, the **Original file** button opens it in a side-by-side pane without losing any answers. If the file contains its own answers, it's hidden during the test unless you allow it in Settings.

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

The app ships with no built-in questions: the question bank starts empty and is filled only from
files you upload or text you paste.
