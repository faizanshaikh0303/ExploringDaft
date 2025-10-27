# Exploring Daft: Distributed DataFrames in Action

This project explores Eventual's open-source distributed DataFrame engine, by comparing its performance to Pandas on a real-world dataset. The goal is to understand how Daft handles large-scale analytical workloads efficiently.

---

## Project Overview

I wanted to learn more about Eventual's technology stack and distributed query engine. To do this, I:

- Pulled a real-world dataset: **NYC Yellow Taxi Trips (Jan 2023)** (~1M rows).
- Performed a typical data processing workflow:
  1. Filter trips with `fare_amount > $10`
  2. Group by `passenger_count`
  3. Compute the average fare per passenger
- Compared execution performance between **Pandas** and **Daft**.

This experiment helped me understand **Daft's lazy execution, Arrow-based columnar storage, and multi-threaded parallelism**.

---

## Dataset

- **Source:** [NYC TLC Trip Data](https://d37ci6vzurychx.cloudfront.net/trip-data/yellow_tripdata_2023-01.parquet)  
- **Format:** Parquet (~100MB, 1M+ rows)  
- **Columns used:** `fare_amount`, `passenger_count`

---

## Technologies

- Python 3  
- [Daft](https://github.com/Eventual-Inc/Daft)  
- Pandas  
- PyArrow  
- Colab  
- Matplotlib (for optional visualization)

---
## Results

Example output (runtime may vary depending on environment):

Filter + GroupBy + Aggregation	
Pandas (sec) = 0.40	
Daft (sec) = 0.17

Observation: Daft executes faster due to lazy evaluation, multi-threading, and Arrow columnar storage, which reduces memory overhead and speeds up computations.

Learnings

Daft’s lazy execution allows fusing multiple operations into a single optimized plan.

Columnar Arrow memory provides cache-friendly, high-speed computation.

Multi-threading helps utilize CPU cores efficiently.

Even with smaller datasets, Daft’s architecture demonstrates the principles of distributed data engines used in production AI/ML systems.

