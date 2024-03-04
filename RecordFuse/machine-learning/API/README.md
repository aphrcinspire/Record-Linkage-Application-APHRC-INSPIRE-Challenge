# README: Probabilistic Record Linkage API using Splink

This API provides a service for probabilistic record linkage using the Splink library. It's designed to link records from two datasets, that is household and facility data, based on names and dates of birth and sex identifiers. Below is a detailed explanation of its functionalities based on the provided code:

### Endpoints:

#### 1. `/results` [POST]

This endpoint accepts two CSV files containing household data and facility data respectively. It performs record linkage between these datasets using the Splink library.

#### Input:

- `household_data`: UploadFile - CSV file containing household data.
- `facility_data`: UploadFile - CSV file containing facility data.

#### Output:

The endpoint returns a CSV file with the results of the record linkage process. The linked records are represented with match probabilities and other relevant information.

### Functionality:

1. **Data Processing:**

   - The uploaded CSV files are read into pandas DataFrames.
   - The column names of the DataFrames are standardized by renaming the first column to "unique_id" for both datasets.
   - The date of birth (DOB) columns are processed to ensure consistency in format (day-month-year) and converted to the standard YYYY-MM-DD format.

2. **Linking Process:**

   - The Splink linker model is initialized with the processed household and facility DataFrames and pre-trained settings.
   - The model predicts record linkage probabilities based on configured match thresholds.
   - Results are obtained as a DataFrame and further processed to drop unnecessary columns and sort the matches by first name.

3. **Output:**

   - The final DataFrame with linked records and match probabilities is converted to CSV format.
   - This CSV content is returned as the response to the API request.

### Installation and Usage:

To access this API, you can find the hosted files [here](https://huggingface.co/spaces/theonlydeity/mirage/tree/main). The endpoint for accessing the API is [https://theonlydeity-mirage.hf.space](https://theonlydeity-mirage.hf.space). You can send POST requests to the `/results` endpoint with the necessary CSV files containing household and facility data.

### Dependencies:

- `fastapi`: A modern, fast (high-performance), web framework for building APIs with Python.
- `pydantic`: Data validation and settings management using Python type annotations.
- `pandas`: A powerful data manipulation library for Python.
- `splink`: A Python library for probabilistic record linkage.

### How to Run:

You can run this API locally by executing the provided script. Ensure that you have the required dependencies installed, and then run:

```bash
uvicorn <filename>:app --host localhost --port 8000
```

Replace `<filename>` with the name of the Python file containing the API code.

### Note:

- Make sure to configure CORS middleware if you're accessing the API from a different origin.
- Ensure that the model file (`model.json`) is available in the same directory as the API script for successful loading of trained settings.
