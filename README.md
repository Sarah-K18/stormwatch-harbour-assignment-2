# Stormwatch Harbour - CGD-460 Assignment 2

A small harbour-management simulation: Lookout, Dockworkers, Quartermaster and an LLM Harbour Master,
with two Dockworker policies (baseline simple reflex, model-based) and a guarded LLM layer.

## How to run

    pip install matplotlib numpy
    python run.py              # seeds 11, 12, 13 (Task 2 + Task 3 with the offline mock LLM + safety cases)
    python run.py 11           # one seed (repeatable: the same seed always gives the same non-LLM result)
    python run.py --hf         # Task 3 with a real small LLM (Qwen/Qwen2.5-1.5B-Instruct; needs transformers, accelerate, torch and Internet)

## Files

* run.py - the full program (built from the Kaggle notebook cells 1-11)
* results/ - task2_results.csv, chart_task2.png (Task 2, no LLM); task3_results.csv, safety_cases.csv,
  hm_log_seed11/12/13.csv, chart.png (Task 3, real LLM Qwen/Qwen2.5-1.5B-Instruct, run on Kaggle)

## Notes

* All randomness is one random.Random(seed) used to pre-build the schedule (storm times, ship arrivals,
  berth preferences). The policies never draw random numbers, so both policies see the same harbour.
* Without --hf, Task 3 uses an offline MockLLM stand-in. It is not a real model and its numbers differ
  from the real-LLM results in results/.
* No API keys or secrets are used or stored.
