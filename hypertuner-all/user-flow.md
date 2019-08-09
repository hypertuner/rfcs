# User Flow

## Entities

A. hypertuner-frontend: React Application 
B. hypertuner-backend: Node Server
C. hypertuner-pythonlib: Python library
D. hypertuner-demonet: Demo ML project

## Flow

### Create and save a hypertuner conf
1. User uses A to create a `hypertuner` configuration and press save
1. A sends a `POST` request to B with a body being the `hypertuner` conf
1. B writes with `fs-extra` the hypertuner body to a file, with a prefixed random uuid.

### Create and run a hypertuner conf 
1. User uses A to create a `hypertuner` configuration and press run
1. A sends a `POST` request to B with a body being the `hypertuner` conf
1. B writes with `fs-extra` the hypertuner body to a file, with a prefixed random uuid.
1. B spawns a D instance that was integrated with C, appended with the path to the conf
1. Every 10 seconds, C would write into the graph file.

### View graph
1. User switch to the view graph page in A
1. A sends a `POST` request to B with a body being all the graph user would like to query
1. B sends back a websocket connection to A to watch the graph change overtime.
1. B spawns a watcher to watch over the graph data and ping A whenever there is new change.
1. A upon payload from B, would parse the data and render the graph