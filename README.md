# YT-ELT

## Overview
YT-ELT is an end-to-end data pipeline that extracts YouTube video statistics, transforms them, and validates data quality. The pipeline uses Airflow for orchestration, PostgreSQL for storage, and Soda for data quality checks.

## Features
- **Extract**: Retrieves video statistics from the YouTube API.
- **Load**: Stores raw data into a PostgreSQL staging schema.
- **Transform**: Cleans and structures data into a core schema for analytics.
- **Data Quality**: Implements custom Soda SQL checks to enforce business rules across both schemas.
- **CI/CD**: Automated pipeline runs unit, integration, and end-to-end tests on every push. Docker images are rebuilt only when dependencies change.

## Architecture
1. **Airflow DAGs** orchestrate the pipeline:
   - `produce_json`: Extracts and saves video statistics.
   - `update_db`: Loads data into staging and transforms it into core.
   - `data_quality`: Validates data quality with Soda.
2. **PostgreSQL** stores staging and core tables.
3. **Soda** ensures data consistency and integrity with custom checks.
