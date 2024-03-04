# RecordFuse: A Record Linkage Application

## Overview

RecordFuse is a record linkage application designed to deduplicate and link records from datasets without unique identifiers. It is built on Splink, a Python package for probabilistic record linkage (entity resolution) that allows you to perform record linkage tasks without the need for training data.

## Key Features

- **Speed**: Capable of linking a million records on a laptop in approximately one minute.
- **Accuracy**: Supports term frequency adjustments and user-defined fuzzy matching logic.
- **Scalability**: Executes linkage jobs in Python (using DuckDB) or big-data backends like AWS Athena or Spark for 100+ million records.
- **Unsupervised Learning**: No training data is required, as models can be trained using an unsupervised approach.
- **Interactive Outputs**: Provides a wide range of interactive outputs to help users understand their model and diagnose linkage problems.

## Usage

To use RecordFuse, you will need to install Splink using pip:

```bash
pip install --upgrade splink
```

After installation, you can read in your dataset using pandas and import the necessary libraries:

```python
import pandas as pd
import splink
from splink.duckdb.linker import DuckDBLinker
from splink.duckdb.blocking_rule_library import block_on
import splink.duckdb.comparison_template_library as ctl
import splink.duckdb.comparison_library as cl
```

You can then read in your household and facility data:

```python
household_data = pd.read_csv("../machine-learning/data/synthetic_hdss_v3.csv")
facility_data = pd.read_csv("../machine-learning/data/synthetic_facility_v3.csv")
```

Next, you can create a Splink linker and apply blocking rules to the data:

```python
linker = DuckDBLinker(household_data, facility_data)
linker.apply_blocking_rules(block_on)
```

Finally, you can link the data using Splink's comparison templates and comparison library  
  
Citations:
[1] https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/2178462/6854dabc-35af-4c15-807d-64cb46931af0/model.ipynb
