# Concurrent Requests in Python
This example shows how execute multiple concurrent requests asynchronously with Apache Cassandra™ using the [Python DataStax Driver](https://docs.datastax.com/en/developer/python-driver/latest).

Contributor(s): [Alan Boudreault](https://github.com/aboudreault) - derived from [here](https://github.com/datastax/python-driver/tree/master/examples/concurrent_executions)

## Objectives
- How to limit async concurrent requests using the DataStax Python Driver

## Project Layout
- [execute_async_with_queue.py](execute_async_with_queue.py): uses a Queue to cap the number of simultaneous requests triggered by the Python driver while executing asynchronously. 

## How this works
After running the docker command, there will be a running instance of the DataStax Distribution of Apache Cassandra.

The Python program executes requests in a non-blocking, asynchronous manner while limiting the number of in-flight requests.

## Setup & Running
### Prerequisites
- Docker installed and started: https://docs.docker.com/v17.09/engine/installation/

### Setup
Make sure Cassandra Python Driver is installed
```
pip install cassandra-driver
```
Clone this repository
```
git clone https://github.com/DataStax-Examples/concurrent-requests-python.git
```

Go to the directory
```
cd concurrent-requests-python
```

Start the DDAC docker container
```
docker run -e DS_LICENSE=accept --name ddac -p 127.0.0.1:9042:9042 -d datastax/ddac 
```


### Running
 
Run the Python program
```
python execute_async_with_queue.py
```

Expected Output
```
Finished executing 10000 queries with a concurrency level of 32 in 2.61 seconds.
```
