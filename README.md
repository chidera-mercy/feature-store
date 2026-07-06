# Feature Store for ML

> This is an active, ongoing learning project. Progress and design decisions will be documented as the project develops.

This project is a mini feature store — a system that computes reusable pieces of data, called "features" (things like "number of purchases a user made in the last 7 days" or "average order value"), and makes them available in two different ways. 
A batch pipeline ingests simulated e-commerce data and computes these features on a schedule, storing the results in an offline store for historical lookups and analysis. At the same time, those features are pushed to an online store (Redis) so they can be retrieved instantly. 
A backend API sits on top of this, serving features on request with caching and versioning, so consuming them feels fast and reliable regardless of how much computation happened behind the scenes.

## Tech Stack

- **Language:** Python
- **Orchestration:** Dagster
- **Raw data source:** A Python-based generator simulating e-commerce events, stored in Postgres
- **Feature computation:** Pandas / Polars
- **Offline store:** Parquet files, queried with DuckDB 
- **Online store:** Redis
- **API layer:** FastAPI 
- **Containerization:** Docker

