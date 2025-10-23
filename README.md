# Project Overview

This repository demonstrates a full-stack engineering workflow, including data processing, continuous integration, and static site deployment with GitHub Pages.

## Project Structure

*   `execute.py`: A Python script for processing `data.csv` and generating `result.json`.
*   `data.xlsx`: The original Excel data file.
*   `data.csv`: The converted CSV data file, derived from `data.xlsx`.
*   `index.html`: A responsive web application utilizing Tailwind CSS.
*   `LICENSE`: The MIT License for this project.
*   `.github/workflows/ci.yml`: GitHub Actions workflow for CI/CD.

## Setup and Execution

### Prerequisites

*   Python 3.11+
*   Pandas 2.3+
*   Ruff (for linting)

### Local Development

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/your-username/your-repo-name.git
    cd your-repo-name
    ```
2.  **Convert `data.xlsx` to `data.csv`:**
    The `data.xlsx` file has been converted to `data.csv` for direct use by `execute.py`. This conversion process ensures that the Python script can easily consume the data.
    *(Note: This step is typically done once, and `data.csv` is then committed.)*
    ```python
    import pandas as pd
    df = pd.read_excel('data.xlsx')
    df.to_csv('data.csv', index=False)
    ```
3.  **Install dependencies:**
    ```bash
    pip install pandas ruff
    ```
4.  **Run `execute.py`:**
    This script processes `data.csv` and outputs a `result.json` file.
    *(Note: `result.json` is not committed to the repository; it's generated during CI.)*
    ```bash
    python execute.py > result.json
    ```
    The `execute.py` script has been reviewed and fixed to ensure robust data processing, handle potential non-numeric values gracefully, and correctly aggregate data by category, preventing common errors such as incorrect column references or data type mismatches. It is designed to run efficiently with Python 3.11+ and Pandas 2.3+.

5.  **View `index.html`:**
    Open `index.html` in your web browser to view the responsive web application.

## Continuous Integration and Deployment (CI/CD)

This project uses GitHub Actions for CI/CD, defined in `.github/workflows/ci.yml`.

The workflow performs the following steps on every push to the repository:

1.  **Code Linting with Ruff**: 
    Ensures code quality and adherence to style standards. The results are visible in the CI logs.
2.  **Data Processing**:
    Executes `python execute.py > result.json` to generate the `result.json` file. This file contains processed data derived from `data.csv`.
3.  **GitHub Pages Deployment**:
    The `result.json` file, along with the `index.html` file, is published to GitHub Pages. This makes the `result.json` accessible via the GitHub Pages URL (e.g., `https://your-username.github.io/your-repo-name/result.json`).

## License

This project is licensed under the MIT License - see the `LICENSE` file for details.
