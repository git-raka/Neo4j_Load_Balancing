# AUTOMATIC LOAD BALANCE

## OBJECTIVE

See request balancing behavior

## PREPARATION

Open SSH session to all cluster members

Follow query.log (less -S query.log)

Open Neo4j Browser http://34.142.184.59:7474/browser/ 

Open VSCode for Sending READand WRITE

Open JMeter (optional)

## EXECUTION COMMAND
```
CALL dbms.cluster.overview
CALL dbms.cluster.routing.getRoutingTable({}) 
YIELD ttl, servers 
UNWIND servers as server
RETURN ttl, server.role, server.addresses;
```


## SCENARIO

Read Transaction:
Request will be handled by role READ (balance)

Write Transaction:
Request will be forwarded to role WRITE
