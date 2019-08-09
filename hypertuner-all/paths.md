# Developer project paths:

```
hypertuner/
  rfcs
  hypertuner-backend
  hypertuner-frontend
  hypertuner-pythonlib
  hypertuner-demonet
```

To setup, copy/paste and run the script below in a folder you would like to clone all:
```
mkdir hypertuner
cd hypertuner
git clone git@github.com:hypertuner/rfcs.git
git clone git@github.com:hypertuner/hypertuner-backend.git
git clone git@github.com:hypertuner/hypertuner-frontend.git
git clone git@github.com:hypertuner/hypertuner-pythonlib.git
git clone git@github.com:hypertuner/hypertuner-demonet.git
```

# Data storage paths:

The two modules that heavily write files are hypertuner-backend (write config file and read graph file) and hypertuner-pythonlib (read config file and write graph file). The are three paths that need to be considered:

## Path to the neural net project to run
This path shall be hard-coded to hypertuner-demonet

## Config file path and structure convention

hypertuner-demonet/

## Graph file path and structure convention
