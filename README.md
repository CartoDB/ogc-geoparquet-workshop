# Workshop

 virtualenv venv

 . venv/bin/activate

## Install dependencies

Using pip:
```bash
pip install -r requirements.txt
```

Or use poetry:
```bash
poetry install
```

## Get BigQuery SA

Set the env var:
```
export GOOGLE_APPLICATION_CREDENTIALS=ogc-workshop-sa.json
```


## Convert to parquet a dataset from BigQuery

```bash
python bigquery_to_parquet.py \
    --input-query "SELECT * FROM carto-demo-data.demo_tables.retail_stores" \
    --primary-column geom \
    --mode file \
    --output retail_stores.parquet
```


## Visualize the dataset with geopandas

Open jupyter and the notebook ogc_workshop.ipynb:

```bash
jupyter notebook ogc_workshop.ipynb
```

## Let's upload the parquet to BigQuery

Open jupyter and the notebook ogc_workshop.ipynb:

```bash
python parquet_to_bigquery.py \
    --input retail_stores.parquet \
    --output "cartodb-gcp-backend-data-team.ogc_workshop.retail_stores_alasarr"
```


## Create a map using CARTO

### Signup

Go to https://carto.com/signup


### Create a connection 

Go to connections and select create and BigQuery.

Type a name.
As service account key, submit the file `ogc-workshop-sa.json`

Select `cartodb-gcp-backend-data-team` as the billing project.

Click on connect.

Don't spend too much money :).

### Create a map

Create a new map.

Add a data source with the table you created before.
