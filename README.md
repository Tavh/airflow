# Airflow

This module deployds a full airflow eco-system, and adds a DAG that
enriches customer-platform data

To deploy airflow, follow these steps:

1. Clone this repository
2. Make a "bridge" network between customer-platform and airflow:
```
docker network create customer-airflow-bridge
``` 
3. Run the customer-platform, instructions are at: 
https://github.com/Tavh/customer-platform/blob/main/README.md

4. Run the airflow docker-compose in this repo's root
```
docker-compose up -d
```

5. To view logs run (in this repo's root):
```
docker-compose logs -f
```
5. Once the compose is done, fire up a browser and navigate to http://localhost:8080

6. Login by using the 'airflow' as both username and password

7. Search the "user_total_spent" DAG

8. Toggle the DAG to activate:

9. This DAG writes into "user_total_spent" table, to view the written data, open up a database viewing tool
    and run the following query:
```
SELECT customer_id, total_spent FROM user_total_spent;
```