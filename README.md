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

**Reference documents (default view):** the app opens on a library of every file you add: the test file, formula sheets, notes, and any file opened as-is (PDF, image, text, Word). Files are shown exactly as uploaded, with download and open-in-new-tab links. PDFs use a built-in PDF.js viewer that works on phones too. Tabs at the top switch to the MCQ, Short answer or Mixed test (tests start from their cover page).

**Test lock:** while a test runs, the other modes are locked. By default reference documents are locked too (Settings can make them available in a side panel instead). Leaving early goes through an Exit test confirmation: submit to keep your score, or exit without submitting.

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
