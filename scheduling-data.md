# 📅 Scheduling Excel Data Overview

## 🟡 Float Distribution

### Key Concepts

- **Float**  
  The amount of time a task can be delayed before it impacts the **critical path** (i.e., project completion).

- **Critical Path**  
  The sequence of tasks that determine the **shortest time** to complete a project from baseline start to finish.

- **Total Float**  
  The maximum time a task can be delayed **without delaying** the project’s finish date.

- **Positive Float**  
  The task can be delayed **without affecting** the project’s end date.  
  **Example:** A task has `+3 days` of float — it can start 3 days late and still not impact the overall schedule.

- **Negative Float**  
  The task is scheduled to start or finish **earlier than possible**, often due to constraints or missed deadlines.  
  **Example:** A task has `–2 days` of float — it’s behind schedule or violates a project constraint.

> ⚠️ **Zero Float**  
> Tasks with **0 float** are on the **critical path** — any delay will delay the entire project.

---

### 📊 Float Data

- Each row = an **active task** in the project
- Each column = a **month** with corresponding float values

---

### 📐 Float Classification (Example Logic)

```python
# Categorizing tasks based on float threshold
critical = count(num_activities where float <= critical_threshold)
near_critical = count(num_activities where float <= near_critical_threshold)
moderate = count(num_activities where float <= moderate_threshold)

# Overall criticality metric
critical_float_perc = (critical + near_critical + moderate) / total_activities
```

## 📈 BEI – Baseline Execution Index

Measures efficiency of completing work against the baseline.

- A BEI of 1.0 means planned work is completed as scheduled.

- A BEI below 1.0 indicates underperformance.

- A BEI above 1.0 suggests more work was completed than planned (may need review).

### 📄 Data

- Each row = an **activity**
- `BL1 Finish` = Planned finish date
- `Actual Finish` = Real/recorded finish date

### 📊 Calculation

```python
planned_finish = count(BL1_finish)
actual_finish = count(actual_finish)
BEI = actual_finish / planned_finish
```

## ⏱️ SRI – Schedule Reliability Index

### 📄 Data

- Each row = an activity

- Columns include: BL1 Start, Actual Start

📊 Calculation (Previous Month Focus)

```python
planned_start = count(BL1_start where date is last_month)
actual_start = count(actual_start where date is last_month)
SRI = actual_start / planned_start
```

Measures how reliably activities are starting as planned.

- An SRI of 1.0 means starts were exactly as scheduled.

- Below 1.0 indicates delays.

- Above 1.0 may suggest early starts or overperformance (which might not always be ideal).
