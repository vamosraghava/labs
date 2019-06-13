# Getting Started

To run the Labs docker images you must accept the [DataStax Labs Term](https://www.datastax.com/terms/datastax-labs-terms) by using the environmental variable DS_LICENSE.

To Start the images use the following commands 

```
docker run -e DS_LICENSE=accept --name my-dse -p 9042:9042 -d datastax/labs:dse-graph-experimental -s -k -g
```

```
docker run -e DS_LICENSE=accept --link my-dse --name my-studio -p 9091:9091 -d datastax/labs:dse-graph-studio-experimental
```

To download and run the DataStax Graph Labs Docker image:

    docker run -e DS_LICENSE=accept --name my-dse -d datastax/labs:dse-graph-experimental -s -k -g

This will start DataStax Enterprise Server with Graph, Search and
Analytics running (the recommended combination).

After a few minutes, DSE should be running. You can confirm this with
a nodetool status command:

    docker exec -it my-dse dsetool status

In the status message you should see confirmation that the single node
is running and that Graph mode is enabled:

    DC: dc1         Workload: SearchAnalytics Graph: yes    Analytics Master: 172.17.0.2
    ====================================================================================
    Status=Up/Down
    |/ State=Normal/Leaving/Joining/Moving
    --   Address      Load         Effective-Ownership  Token                  Rack     Health [0,1]
    UN   172.17.0.2   124.07 KiB   100.00%              -2702044001711757463   rack1    0.20



### DataStax Studio

To download and run the DataStax Studio Labs Docker image:

    docker run -e DS_LICENSE=accept --link my-dse --name my-studio -p 9091:9091 -d datastax/labs:dse-graph-studio-experimental

This will start DataStax Studio and connect it with the running
DataStax Enterprise Server Docker container.

Once Studio has started it should be viewable in a browser at: <http://DOCKER_HOST_IP:9091>

Configure the connection to the DataStax Enterprise Server:

1. From the action menu in the upper left, choose Connections
2. Click on the 'default localhost' connection
3. In the Host/IP field enter "my-dse"
4. Click Test to confirm the connection
5. Click Save

# Compose Example
Use the docker compose example provided in this repo to automate provising of a single Graph node and single Studio node 

# Support
Images contained in this repository are not intended for production use and are not "Supported Software" under any DataStax subscriptions or other agreements.

Join the [DataStax Community](https://community.datastax.com/spaces/11/index.html) to connect with peers who can help you out in sticky situations and give you pointers.
Please visit  [DataStax Lab Github](https://github.com/datastax/labs) to file any issues encountered

# Next Steps
Head over to the [DataStax Academy](https://academy.datastax.com/) for free training and tutorials.