# Snell Scoring Module

This module provides an implementation of the Snell scoring method for ordered categorical data. It includes functionality to compute scores based on a frequency table and standardize the results to a 0-100 scale if needed.

## Installation

To use the module, clone the repository and install the necessary dependencies:

```bash
pip install -r requirements.txt
```

## Usage

### Import the Module

```python
from snellscore import Snell
import pandas as pd
```

### Prepare the Frequency Table

The input should be a pandas DataFrame where rows represent groups and columns represent categories.

```python
# Example frequency table
data = {
    "Category A": [10, 20, 30],
    "Category B": [15, 25, 35],
    "Category C": [20, 30, 40]
}
frequency_table = pd.DataFrame(data, index=["Group 1", "Group 2", "Group 3"])
```

### Initialize the Snell Object

Create an instance of the `Snell` class, optionally enabling score standardization.

```python
snell = Snell(standard=True)
```

### Run the Scoring Method

Pass the frequency table to the `run` method.

```python
snell.run(frequency_table)
```

### Retrieve the Scores

Get the calculated scores and standardized scores (if enabled):

```python
# Get the calculated scores
scores = snell.score
print("Calculated Scores:")
print(scores)

# Get the standardized scores (0-100 scale)
standardized_scores = snell.score_standard
print("Standardized Scores:")
print(standardized_scores)
```

### Output Example

For the example frequency table, the output might look like:

```plaintext
Calculated Scores:
Category A    0.5
Category B    1.5
Category C    2.5
dtype: float64

Standardized Scores:
Category A      0
Category B     50
Category C    100
dtype: Int16
```

## Testing

To run tests for the module, use `pytest`:

```bash
pytest tests/
```

## References
https://github.com/pfpetrowski/rsnell

## License

This project is licensed under the MIT License. See the LICENSE file for details.
