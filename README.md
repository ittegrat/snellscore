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
    "Category1": [0, 6, 0, 0, 0, 2, 3, 0, 1, 2, 0, 5],
    "Category2": [0, 3, 0, 4, 0, 4, 4, 0, 2, 2, 0, 1],
    "Category3": [0, 1, 3, 1, 0, 3, 3, 1, 0, 2, 0, 1],
    "Category4": [3, 0, 2, 2, 0, 1, 0, 1, 0, 0, 0, 0],
    "Category5": [3, 1, 2, 4, 2, 0, 1, 1, 1, 2, 4, 1],
    "Category6": [2, 1, 4, 0, 5, 2, 1, 5, 4, 4, 1, 3],
    "Category7": [4, 0, 1, 1, 5, 0, 0, 4, 4, 0, 7, 1]
}
frequency_table = pd.DataFrame(data, index=[f"Group{item}" for item in range(1, 13)])
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
Snell Scores:
Category0   -1.072418
Category1    1.223775
Category2    2.592759
Category3    3.383042
Category4    4.478767
Category5    6.384713
Category6    5.850891
dtype: float64

Standardized Scores:
Category0      0
Category1     33
Category2     53
Category3     64
Category4     80
Category5    108
Category6    100
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

This project is licensed under the GNU General Public License. See the LICENSE file for details.
