# Workshop

## Get BigQuery SA

Create a file named `ogc-workshop-sa.json` with this content:

```
{
  "type": "service_account",
  "project_id": "cartodb-gcp-backend-data-team",
  "private_key_id": "392bc18bf77087f7460542c3debd7fea75a68956",
  "private_key": "-----BEGIN PRIVATE KEY-----\nMIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIBAQCZYK/sjcVCpHVx\nqJzZ/W471VAixVfKB9qd+z779nAUY9Kkan4DSyv7Sea66pBFrCV7UwVvFQGr4EA2\ne43/psgihuIqz7XoPEAXqU46M2lQt9x4jlZQU2h/YYOgqSwM0N723EdI2og+aU1T\nxoPHV+boSUnKA8gRJRvR46VhzFP+8mmwnK+Rs1iyV5Hr+Q2zDDqkfjLN0TMSlpE3\njxncTspbt8RLqCyobuqVvl+nr9zyhVGGVCZvR0M8Cux8va9+qEOPBeyXTW6YuEIF\nJy0s1MaicCqLKNP+lxBCnF4bw1ofnx32fruaWiOgUpb0NDTMXoXbCt17GO6Zlfr1\n03yKD2sxAgMBAAECggEADbJdM347keZ22HYKv8rKd8xmUhyWaOPHqZkAuGZ6/s8l\nRep+o1Oos1GXqbR9usMTO86fqxpQomUtxs/E0AI4WCD8fH89CuaqgJJtenQR4RPy\nO8/WNGkmaU2vf/7rgJ98ccYdFYvyY8Rqk+Mj7H7Uj4TP8prg2Gscb2NpZvDkxV0E\nALRttVT4qfeq87x5XAhdMexzqDbGV0TUJNzgPTv8n7CujIW/AmZgdaLf+d6u3qC/\n64sbT5TZ4JPkm8S9aiTtaFlPL74rY6VtqqlzRaytYmuTDjV8FdAAECKxzEntfOnW\nyjWdtKW/3A2qNfkKTaU0f57MJnB8wVD8tChSz6IhIwKBgQDXWg0tNIE97O8mSV0m\nE3ZAYFnSH1SCJtkBkrFJku55tt0LrkL99C4o/ylI7efmnj/ms9ljxkizXPaDPIur\n74JxpsXKiIfOanPVJ8PVtrhRfeGOPXok1DJVQfOIK/nJc+Lgxso8qJQOMBUidFCB\nLLiK1GmxTLsEyRTVzwtV7psT/wKBgQC2VAEyzs7ERiXe2xVI3I1qhHVRlVaiFyWg\nirrQyOsBVP1xHA8j+x61jwAZQIV2w5FDh3Bgx3m4KTBPdTIHG3qcjUH3+cKfpFtV\nFkqQj6MG+W3kglL3XuFQKCWzOma9Z2r6t+DEOGATvbpZSTkNVJCbN3n3yit4Zmtn\ni6ZRWFXAzwKBgDHmifsZmYER7/B9O3phNBuCuA16eQiXm91DcpVL2LqXZu0X+ioC\ndNfHGHfvuLa1oLUCo7L89UeqmOycEPlMTHutW1OtA1sPS7vutPBGoLsxYhylnjH+\ngZND7vx0xDKsCbxwE9iub3BCMAOF1Em6ZSC2S69rykI3nf5VNZk56vFdAoGBAKKF\nyvOxKNoH9WXrP9PM1TmnjLQGPE0L+Pxb7R6Cmgh769ZRPqXCCKOqLlpUCyPMO8ZI\nCkIaTUN9Y5TQUKHJOsglmjIirfuDk+4KirjFcHqdB/nyuWXLa2f6AXD7k+0tLE0E\nbxQ5dFrkeiFwhax+PtA86TmZOpp+ISsRblWAOiA9AoGAKRTcGPJaXzzX/8ZZRD4M\n2mdZygjBd6HRUG/qgoBLyF/AnQap3tMzLw48AhPqs31ARimY1iW+x85C5P7m3Acw\nx/viRBZKcSrL5pB0CbiPlBiE/OyjinLqf5o9RNCWmZ38oIOXAPpao1+IFU45BiyM\nDJIii3mq8XABtd/dqbhpSow=\n-----END PRIVATE KEY-----\n",
  "client_email": "ogc-workshop@cartodb-gcp-backend-data-team.iam.gserviceaccount.com",
  "client_id": "110630212564644630887",
  "auth_uri": "https://accounts.google.com/o/oauth2/auth",
  "token_uri": "https://oauth2.googleapis.com/token",
  "auth_provider_x509_cert_url": "https://www.googleapis.com/oauth2/v1/certs",
  "client_x509_cert_url": "https://www.googleapis.com/robot/v1/metadata/x509/ogc-workshop%40cartodb-gcp-backend-data-team.iam.gserviceaccount.com"
}
```

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