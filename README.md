# Tour Routing in Tirana: BF, GA, and SA (TSP)

This repository benchmarks **Brute Force (BF)**, **Genetic Algorithm (GA)**, and **Simulated Annealing (SA)** for one-day tourist itineraries in Tirana, Albania, modeled as a TSP over real attraction coordinates.

- **OS**: Windows 10 Pro  
- **Python**: 3.12.2  
- **JupyterLab**: 4.1.2  

## Structure
```
tour-routing-tirana-bf-ga-sa/
├─ README.md
├─ requirements.txt
├─ .gitignore
└─ code/
   ├─ one_cell_evaluation.py        # single executable file
   ├─ L1.json                       # N=7 points
   ├─ L2.json                       # N=10 points
   ├─ L3.json                       # N=32 points
   └─ reports/                      # generated outputs (CSV, PNG)
```

## How to run
```bash
python -m venv .venv
. .venv/Scripts/activate   # Windows PowerShell: .venv\Scripts\Activate.ps1
pip install -r requirements.txt

cd code
python one_cell_evaluation.py
# or open in JupyterLab and run the single cell
```

### Inputs
- You can press **Enter** to use the default built-in list.
- Or type **L1**, **L2**, or **L3** to load from `L1.json`, `L2.json`, or `L3.json` in the `code/` folder.
- Or choose **ANY** and paste a Python list literal like:
  ```python
  [("Skanderbeg Square", (41.3275, 19.8187)), ("National History Museum", (41.3270, 19.8180)), ...]
  ```

### Outputs
The script writes results to `code/reports/`:
- `runs_ga.csv`, `runs_sa.csv`
- `summary_n<N>_metrics.csv`
- `boxplot_distance_n<N>.png`, `boxplot_time_n<N>.png`
- `convergence_ga_n<N>.png`, `convergence_sa_n<N>.png`
- `tourist_spots.json` (the actual spots used during the run)

> Note: BF is attempted with a **90s soft timeout**; if exceeded, GA/SA best becomes the baseline for success/gap metrics.