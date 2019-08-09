# Architecture

`hypertuner-backend` will be bootstrapped using create-pastel-app to allows simpler tooling and code conventions.

`hypertuner-backend start` will start the websocket server that has the following topics:

1. create-config | payload: a hypertuner conf
  The client will send the hypertuner conf to the websocket server to process and write into a nodejs file