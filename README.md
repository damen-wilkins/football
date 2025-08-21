# Fantasy Football Tiered Projections (2016–2025)

This project builds a **reliable tiering system** for fantasy football player projections.  
It uses **historical projections vs actuals (2016–2024)** to measure bias, reliability, and error at each position (QB, RB, WR, TE), and then applies those corrections to **2025 projections**.  

The result is a **tiered ranking system** that’s more stable than raw projections, helping you identify true value across positions.

---

## 📂 Repository Structure

## ⚙️ Workflow

1. **Projections vs Actuals (2016–2024)**  
   - Notebook: `pro_v_actual.ipynb`  
   - Loads preseason projections and end-of-year actual stats.  
   - Calculates raw errors (`proj - actual`) for every player.  

2. **Reliability & Bias Analysis**  
   - Notebook: `reliability_2.ipynb`  
   - Summarizes positional bias (systematic over/under), reliability, and absolute miss.  
   - Produces position-level correction factors (QB, RB, WR, TE).  

3. **Time Series Context**  
   - Notebook: `time_series_2018_2024.ipynb`  
   - Explores multi-year patterns and volatility by position.  
   - Helps validate how consistent projections are across time.  

4. **Tiered Projections (2025)**  
   - Notebook: `suped_up_tiers.ipynb`  
   - Loads 2025 projections.  
   - Applies historical bias/reliability/error adjustments.  
   - Builds a **fusion score** combining:
     - Bias correction  
     - Reliability weighting  
     - % above positional average  
     - Floor & ceiling uncertainty bands  
   - Assigns players into **tiers per position** (WR: 10, RB: 8, QB: 6, TE: 5).  
   - Exports the final list → `Outputs/tiered_projections_2025.csv`.

---

## 📊 Final Output

The final CSV (`tiered_projections_2025.csv`) contains:

| player            | position | points | adj_points | tier_score | tier |
|-------------------|----------|--------|------------|------------|------|
| Ja'Marr Chase     | WR       | 355    | 358.3      | 358.3      | 1    |
| Justin Jefferson  | WR       | 317    | 304.6      | 304.6      | 1    |
| ...               | ...      | ...    | ...        | ...        | ...  |

- **points** → raw projection  
- **adj_points** → bias-adjusted projection  
- **tier_score** → fusion index (confidence-adjusted strength)  
- **tier** → bucketed ranking (1 = best tier)  

---

## 🚀 How to Run

1. Clone this repo  
   ```bash
   git clone https://github.com/yourname/fantasy-football-tiers.git
   cd fantasy-football-tiers

pip install pandas matplotlib

