
# Amazon Electronics US Reviews Data Pipeline

This project demonstrates an end-to-end, layered data pipeline using Python and Pandas on the [Amazon US Reviews dataset](https://s3.amazonaws.com/amazon-reviews-pds/tsv/index.txt).

## Overview

- **Goal:** Load, transform, validate, and create analytics-ready data from a large real-world CSV/TSV file.
- **Layers:** The pipeline follows industry-standard staging, auditing, and feature engineering principles.

## Pipeline Steps

1. **Intermediate Source of Truth:**  
   - Load the raw TSV.
   - Basic cleanup (e.g., drop rows with missing review text).

2. **Auditing / Staging for Review:**  
   - Filter for reviews longer than 10 characters.
   - Mark rows for further review/auditing (e.g., very long reviews).

3. **Staging (Refinement):**  
   - Deduplicate rows.
   - Enrich with review length.

4. **Feature Engineering / Mart Layer:**  
   - Create new features (e.g., length buckets, verified reviews).
   - Output final analytics-ready file.

## Project Structure

amazon_us_reviews_pipeline/
├── data/
│ ├── amazon_reviews_us_Electronics_v1_00.tsv
│ ├── layer_raw.csv
│ ├── layer_audited.csv
│ ├── layer_staged.csv
│ └── layer_mart.csv
├── pipeline.py
├── README.md
└── .gitignore

## Usage

1. **Clone the repo and navigate into it:**
    ```bash
    git clone <https://github.com/ray-dataworks1/amazon_electronics_reviews_analytics_pipeline.git
    cd amazon_electronics_reviews_analytics_pipeline
    ```

2. **(Optional) Download the dataset**  
   *(If not already in `/data`):*  
   [Download here](https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Electronics_v1_00.tsv.gz) and extract it to `data/`.

3. **Install dependencies:**
    ```bash
    pip install pandas
    ```

4. **Run the pipeline:**
    ```bash
    python pipeline.py
    ```

5. **Output files for each layer will appear in the `data/` folder.**


6. **Automate the pipeline via a cron/Task Scheduler job**

## Notes

- The pipeline is designed for clarity, learning, and reproducibility.
- Each step outputs a CSV so you can inspect results and debug easily.
- The project showcases "meta-skills" of data pipeline design, not just code.

## License

MIT (or choose your favorite OS license!)

---

## Next Steps

- Add schema validation (e.g., with Great Expectations or pandas checks)
- Scale to chunked processing for very large datasets
- Parameterize for other Amazon review categories

---
