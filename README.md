![Python](https://img.shields.io/badge/Python-3.11%2B-blue)
![Docker](https://img.shields.io/badge/Docker-Compose-blue)
![Spark](https://img.shields.io/badge/Apache%20Spark-3.x-orange)
![Trino](https://img.shields.io/badge/Trino-SQL%20Engine-blueviolet)
![MinIO](https://img.shields.io/badge/MinIO-S3%20Compatible-red)
![License](https://img.shields.io/badge/License-MIT-green)

# DataOpsPlayground
A Docker-based mini data platform using a **lakehouse** approach (**Bronze/Silver/Gold** layers), **SQL on the data lake**, and **incremental, reprocessable** pipelines with **data quality gates** and **run tracking**.

## Goals
- Showcase production-like data engineering practices at low cost (local)
- Implement layered datasets (Bronze → Silver → Gold)
- Query lake data using SQL (Trino)
- Enforce minimum data quality before promotion (quality gates)
- Track pipeline runs and key metrics (run tracking)

## Stack
- **MinIO**: S3-compatible object storage (local data lake)
- **Apache Spark**: transformations/jobs (Bronze → Silver → Gold)
- **Trino**: SQL engine to query partitioned Parquet directly on the lake
- **PostgreSQL** (optional): metadata, auditing, run tracking
- **Airflow** (optional): pipeline orchestration
- **GitHub Actions** (optional): CI (lint/tests/checks)

## Architecture (high level)
- **Bronze**: raw append-only data, partitioned by ingestion date
- **Silver**: cleaned and standardized data (casts, dedup, business rules)
- **Gold**: analytics-ready marts (KPIs/aggregations)

## Repository structure
```text
dataops-playground/
  docker/
    docker-compose.yml
    .env.example
  pipelines/
    ingest/
    spark_jobs/
    quality/
    utils/
  sql/
    trino/
    marts/
  infra/
    trino-catalog/
    init-db/
  airflow/
    dags/
  docs/
    architecture.md
    screenshots/
  Makefile
  README.md
  README.pt-BR.md
  LICENSE
