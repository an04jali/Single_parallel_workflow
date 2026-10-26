# LangGraph Parallel Workflow: Batsman Performance Analysis

## Overview

This project demonstrates how to build a **parallel workflow using LangGraph** to calculate cricket batsman performance metrics.

Instead of calculating each metric sequentially, multiple independent nodes process the same input state in parallel and return their results. LangGraph combines the updates into a single output state.

## Tech Stack

- Python
- LangGraph
- Jupyter Notebook
- TypedDict for state definition

## Features

The workflow calculates three batting performance metrics:

- **Strike Rate:** Runs scored per 100 balls faced.
- **Balls per Boundary:** Number of balls faced divided by the total number of fours and sixes.
- **Boundary Run Percentage:** Percentage of total runs scored through fours and sixes.

## Workflow Architecture

```text
                START
                  |
        +---------+---------+
        |         |         |
   Strike Rate  Balls per  Boundary Run
   Calculation  Boundary   Percentage
        |      Calculation Calculation
        |         |         |
        +---------+---------+
                  |
                 END
```

The three calculation nodes can execute in parallel because they independently calculate different metrics.

## Example Input

```python
initial_state = {
    "runs": 60,
    "balls": 30,
    "fours": 6,
    "sixes": 3
}
```

## Formulas

1. **Strike Rate**

   `Strike Rate = (Runs / Balls) × 100`

2. **Balls per Boundary**

   `Balls per Boundary = Balls / (Fours + Sixes)`

3. **Boundary Run Percentage**

   `Boundary Run Percentage = ((4 × Fours + 6 × Sixes) / Runs) × 100`

## Example Output

For the input above:

- Strike Rate: `200.0`
- Balls per Boundary: `3.33`
- Boundary Run Percentage: `80.0%`

## How to Run

1. Clone the repository:

   ```bash
   git clone https://github.com/YOUR_USERNAME/langgraph-parallel-workflow.git
   ```

2. Navigate to the project directory:

   ```bash
   cd langgraph-parallel-workflow
   ```

3. Create and activate a virtual environment (optional but recommended):

   ```bash
   python -m venv .venv
   ```

   Windows:

   ```bash
   .venv\Scripts\activate
   ```

4. Install LangGraph:

   ```bash
   pip install langgraph
   ```

5. Open the Jupyter Notebook in VS Code and run the cells in order.

## Key Learnings

- Defining workflow state using `TypedDict`.
- Creating nodes that read state and return partial state updates.
- Connecting nodes using `StateGraph`, `START`, and `END`.
- Running independent nodes in parallel.
- Compiling a LangGraph workflow and invoking it with input data.

## Future Improvements

- Add input validation and handle zero values safely.
- Add more cricket metrics, such as average and dot-ball percentage.
- Visualize the workflow graph.
- Add unit tests for calculation functions.

---
