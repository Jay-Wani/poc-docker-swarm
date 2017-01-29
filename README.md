Docker Swarm POC
=========

Getting started
---------------

Setup the swarm. 

```
docker swarm init
```

Create Masters and Workers based on your needs.


Once you have your swarm, in the directory run:

```
docker stack deploy --compose-file docker-stack.yml vote
```


The app will be running on port 5000 & the results will be available at port 5001.



Architecture
-----

![Architecture diagram](architecture.png)

* A Python webapp which lets you vote between two options
* A Redis queue which collects new votes
* A .NET worker which consumes votes and stores them in a Postgres DB
* A Postgres database backed by a Docker volume
* A Node.js webapp which shows the results of the voting in real time


Note
----

The voting application only accepts one vote per client. It does not register votes if a vote has already been submitted from a client.
