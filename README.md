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
<img width="1488" alt="Screenshot 2023-03-11 at 0 26 17" src="https://user-images.githubusercontent.com/44731477/224441028-3cd0d012-9c17-43ca-b578-b11d11c1d0ec.png">

9. This DAG writes into "user_total_spent" table, to view the written data, open up a database viewing tool
    and run the following query:
```
SELECT customer_id, total_spent FROM user_total_spent;
```

<img width="497" alt="Screenshot 2023-03-11 at 0 36 15" src="https://user-images.githubusercontent.com/44731477/224441110-0bdb8abc-2f16-4664-a2ef-5c8d84610cdf.png">
