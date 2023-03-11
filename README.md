# Take-Home Assignment

## How to run the demo
``` sudo docker-compose up -d  ```

### Initialize
Enter the python_assignment directory and invoke the command:
``` python3 get_raw_data.py ``` or you can skip the above step, because when the server starts, it will automatically updates the data every 5 minutes.

## API
### 1. Get Financial Data
``` 
curl -v "http://localhost:8080/v1/financial?start_date=2023-01-01&end_date=2023-03-01&symbol=IBM&limit=20&page=10"
```
* ```start_date``` yyyy-mm-dd, default to be today
* ```end_date``` yyyy-mm-dd, default to be today， end_date must not be earlier than start_date
* ```symbol``` only support IBM or AAPL
* ```page``` integer
* ```limit``` 1-1000   
* all the parameters are optional, parameter which is not regconized will be ignored


### 2. Get Statistics Data

```
curl -v "http://localhost:8080/v1/statistics?start_date=2023-01-01&end_date=2023-03-01&symbol=IBM"
```
 * ```start_date``` yyyy-mm-dd, default to be today
 * ```end_date``` yyyy-mm-dd, default to be today， end_date must not be earlier than start_date
 * ```symbol``` only support IBM or AAPL
 * all the parameters are optional, parameter which is not regconized will be ignored

## SQL Schema
 * see sql/schema.sql

## How to switch between test environment and production environment
 * I create a config.py file which imports prod_key.py or test_key.py depending on the environment variable, so I can switch between different configuration by specifying the environment variable in docker-compose.yml

## Python Packages and Database
* ```Tornado``` a python micro web framework
* ```pymsql``` a python library used to connect to MySQL database
* ```MySQL``` database for storing the financial data, the version is 5.5

## What are not included in this demo
* A load balancer like Nginx, HAProxy, etc.
* WSGI server used in production environment, (Gunicorn, Gevent, etc.)
* Logging, including the request and exception
* A connection pool for better performance
* Multiprocessing
* Testing (for simplicity, only use curl for testing in this demo)
