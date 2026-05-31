# Quizzler — True/False Quiz App

A Tkinter quiz app that fetches live questions from the Open Trivia Database API.
Answer True/False questions, get instant colour feedback, and track your score — new questions every run.

## Features

- **Live questions** — fetches 10 fresh questions from [Open Trivia DB](https://opentdb.com) on every run
- **Instant feedback** — canvas turns green (correct) or red (wrong) for 1 second
- **Score tracking** — live score display updates after every answer
- **Clean end state** — buttons disable and final score shown when quiz completes
- **HTML entity decoding** — special characters in questions render correctly

## How to Run

```bash
git clone https://github.com/abnsrishik/quizzler-app-python
cd quizzler-app-python
pip install requests
python main.py
```

## Project Structure

```
quizzler-app-python/
├── main.py             # Entry point — builds question bank, launches UI
├── data.py             # API call to Open Trivia DB
├── question_model.py   # Question class — text + answer
├── quiz_brain.py       # Quiz logic — scoring, answer checking, progression
├── ui.py               # QuizInterface — full Tkinter GUI
└── images/
    ├── true.png
    └── false.png
```

## Architecture

| File | Class | Responsibility |
|---|---|---|
| `question_model.py` | `Question` | Data model — holds question text and answer |
| `quiz_brain.py` | `QuizBrain` | Logic — tracks score, checks answers, advances questions |
| `ui.py` | `QuizInterface` | GUI — canvas, buttons, feedback, score display |
| `data.py` | — | Fetches 10 boolean questions from Open Trivia DB API |
| `main.py` | — | Wires everything together |

## Customise Questions

Edit `data.py` to change category or count:

```python
parameters = {
    'amount': 10,       # number of questions
    'type': 'boolean',  # True/False only
    'category': 18,     # 18 = Science: Computers
}
```

Full category list: https://opentdb.com/api_config.php

## Requirements

- Python 3.x
- requests (`pip install requests`)
- tkinter (included with standard Python)

## What I Learned

- REST API integration with requests and query parameters
- Type hints in class constructors (`quiz_brain: QuizBrain`)
- HTML entity decoding with `html.unescape()`
- Multi-file architecture — model, logic, UI separated cleanly
- `window.after()` for timed feedback before advancing
- Disabling UI elements on game completion
