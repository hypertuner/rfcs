# Architecture

`hypertuner-backend` will be bootstrapped using create-pastel-app to allows simpler tooling and code conventions.

`hypertuner-backend start` will start the websocket server that has the following topics:

1. create-config | payload: a hypertuner conf
  The server will write the conf file into the path detmined in [paths.md](../hypertuner-all/paths.md)

2. watch-graph | payload: a hypertuner conf id
  The server will start a nsfw watcher over the graph and send change to the frontend

