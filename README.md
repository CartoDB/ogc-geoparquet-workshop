# Workshop

## Get BigQuery SA

Create a file named `ogc-workshop-sa.json` with the content provided separately.

Set the env var:
```
export GOOGLE_APPLICATION_CREDENTIALS=ogc-workshop-sa.json
```


## Convert to parquet a dataset from BigQuery

```bash
poetry run python bigquery_to_parquet.py \
    --input-query "SELECT * FROM carto-demo-data.demo_tables.retail_stores" \
    --primary-column geom \
    --mode file \
    --output retail_stores.parquet
```


## Visualize the dataset with geopandas

Open jupyter and the notebook ogc_workshop.ipynb:

```bash
poetry run jupyter notebook ogc_workshop.ipynb
```