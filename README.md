
# Temporary Impact Modeling

This project computes the temporary price impact function `g(x)` from limit-order-book data 
and derives an optimized execution schedule to minimize total slippage.

## Structure

- `src/data_loader.py`  
  Loads one-minute LOB snapshots (CSV → DataFrame).

- `src/slippage_simulator.py`  
  Simulates market orders of varying sizes, returns slippage vs. mid-price.

- `src/model_fit.py`  
  1. Fits a power-law `g(x)=α x^γ` via log–log OLS.  
  2. Builds a time-varying αₜ model:  
     

\[
       αₜ = β₀ + β₁ \cdot \mathrm{spread}_t + β₂\cdot (1/\mathrm{depth}_t)
     \]



- `src/execution_schedule.py`  
  Implements the closed-form and rolling execution schedule.

- `notebooks/01-impact-modeling.ipynb`  
  Walks through data loading, simulation, model fitting, diagnostics, and schedule.

## Usage

1. `pip install -r requirements.txt`  
2. Put your raw LOB CSVs under `data/` with filenames `TICKER.csv`  
3. Open `notebooks/01-impact-modeling.ipynb` in JupyterLab.  
4. Run cells top to bottom.

---

