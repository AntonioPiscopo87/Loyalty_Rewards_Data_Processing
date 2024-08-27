![loyalty program](https://github.com/user-attachments/assets/a123ce31-0365-49bb-a060-4300d549a90a)
# Loyalty Rewards Data Processing

## Overview

This repository contains a Python script for processing and analyzing loyalty reward data. The script consolidates data from multiple CSV files, performs data transformations, and generates a report on customer loyalty rewards. The goal is to identify customers who have consistently met certain criteria over specific rolling periods, and to assign them to loyalty reward buckets.

## Table of Contents

1. [Overview](#overview)
2. [Project Structure](#project-structure)
3. [Prerequisites](#prerequisites)
4. [Dataset](#dataset)
5. [Analysis Steps](#analysis-steps)
   - [1. Data Loading and Consolidation](#1-data-loading-and-consolidation)
   - [2. Data Preprocessing](#2-data-preprocessing)
   - [3. Rolling Sum Calculation](#3-rolling-sum-calculation)
   - [4. Loyalty Reward Bucket Assignment](#4-loyalty-reward-bucket-assignment)
   - [5. Output Generation](#5-output-generation)
6. [Results](#results)
7. [How to Use](#how-to-use)
8. [License](#license)
9. [Acknowledgments](#acknowledgments)

## Project Structure

The repository is structured as follows:

```
loyalty-rewards-processing/
│
├── data/
│   └── [Your CSV Files Here]                  # Raw data files to be processed
│
├── notebooks/
│   └── Loyalty_Reward_Processing.ipynb        # Jupyter Notebook containing the script
│
├── README.md                                  # Project documentation
├── LICENSE                                    # License for the project
└── .gitignore                                 # Git ignore file
```

## Prerequisites

Before running the script, ensure you have the following installed:

- **Python 3.x**
- **Jupyter Notebook**
- **Pandas**
- **Dateutil**
- **Tqdm**

You can install the required Python packages using pip:

```bash
pip install pandas python-dateutil tqdm
```

## Dataset

The dataset consists of multiple CSV files, each representing a monthly report on customer charges and payment statuses. The script expects the files to be named in a way that includes the month and year (e.g., `Jan23.csv`, `Feb23.csv`). The relevant columns in each file are:
- **Name**: Customer's name
- **Email**: Customer's email address
- **Charge Status**: Payment status (e.g., "Paid")
- **Month_Year**: The month and year derived from the file name

## Analysis Steps

### 1. Data Loading and Consolidation
The script loads multiple CSV files from the specified directory and consolidates them into a single DataFrame. Only rows with a "Paid" charge status are retained.

### 2. Data Preprocessing
The script converts the `Month_Year` column into a datetime format, fills any missing months with zeros, and sorts the data by month.

### 3. Rolling Sum Calculation
For each customer, the script calculates rolling sums over different periods (e.g., 3 months, 6 months) to identify patterns in their payment history.

### 4. Loyalty Reward Bucket Assignment
Based on the rolling sums, customers are assigned to different loyalty reward buckets. The script determines the last subscription period during which a customer met the criteria and categorizes them accordingly.

### 5. Output Generation
The final processed data is saved as a CSV file named after the folder containing the original data files. This file includes the customer's name, email, all applicable reward buckets, and their most recent loyalty reward assignment.

## Results

The processed data file contains a comprehensive view of customer loyalty behavior, with customers categorized into different reward buckets based on their payment consistency. This data can be used to target loyal customers with special rewards or promotions.

## How to Use

1. **Clone this repository**:
    ```bash
    git clone https://github.com/yourusername/loyalty-rewards-processing.git
    cd loyalty-rewards-processing
    ```

2. **Prepare your data**:
    - Place your monthly CSV files in the `data/` directory.

3. **Run the Jupyter Notebook**:
    ```bash
    jupyter notebook notebooks/Loyalty_Reward_Processing.ipynb
    ```

4. **Follow the steps in the notebook** to process your data and generate the loyalty rewards report.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments

- The dataset used in this analysis was provided for educational purposes.
- Special thanks to the contributors of open-source libraries like Pandas and Tqdm that made this analysis possible.

---

This README should provide a clear guide for anyone looking to use your loyalty rewards processing script. Feel free to customize it further based on your specific needs.
