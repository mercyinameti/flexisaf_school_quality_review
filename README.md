# School Support Assistant Quality Review

This project evaluates the Week 8 school support assistant against a set of 30 test cases. It records a baseline, applies one improvement, reruns the same cases, and compares the two runs.

## Setup

1. Create a virtual environment with Python 3.12:
   `py -3.12 -m venv .venv`
2. Activate it:
   `.venv\Scripts\Activate.ps1`
3. Install the packages:
   `pip install -r requirements.txt`
4. Copy `.env.example` to `.env` and replace `your-key-here` with your Gemini API key.

## Reproducing the results

1. **Baseline:** In `run_eval.py`, set `SYSTEM_INSTRUCTION = ""`, then run `python run_eval.py baseline`. This writes `results_baseline.csv`.
2. **Improved:** Set `SYSTEM_INSTRUCTION` to the credential rule (see `before_after.md`), then run `python run_eval.py improved`. This writes `results_improved.csv`.
3. **Scoring:** Score responses using `rubric.md`. Record the five human reviews in `human_review.md`.

Each run calls Gemini, so answers vary a little between runs. The results are one run per version.

## Files

- `school_info.txt`: a fictional school document. The assistant can't search it yet.
- `school_data.json`: mock students, courses, and grades.
- `test_cases.csv`: the 30 test cases, with their categories and expected behaviours.
- `rubric.md`: the six scoring criteria and the pass rule.
- `run_eval.py`: runs every case and saves the responses.
- `results_baseline.csv` and `results_improved.csv`: the raw responses from each run.
- `human_review.md`: scores for five reviewed responses.
- `before_after.md`: the comparison between the two runs.
- `backlog.md`: the prioritised list of further improvements.
- Assistant files: `models.py`, `tools.py`, `tool_schemas.py`, `dispatch.py`, `audit.py`, `main.py`, `ask_model.py`, `approval_check.py`.

## Limitations

- One run per version, so some differences may be variation.
- Five responses have human scores. The rest are checked automatically or by the tool results only.
- The assistant doesn't search `school_info.txt` yet, so the retrieval cases fail.