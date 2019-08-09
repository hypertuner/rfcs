- Start Date: 2019-08-09
- RFC PR: (leave this empty)
- React Issue: (leave this empty)

# Summary

Hyperparameter passing will allow users to access the hyperparameters they set in the hyper tuner GUI inside their python scripts.

# Basic example

```python
import torch.optim as optim
import hypertuner

# import some neurlal net
net = Net()

# Parse args
args = hypertuner.Args()
# Use hypertuner hyperparameters to set learning rate and momentum
optimizer = optim.SGD(net.parameters(), lr=args.learning_rate, momentum=args.momentum)
```

# Motivation

This will allow users to access parameters set with the HyperTuner GUI in their python script which allows for much easier tuning of parameters.

It provides the following conveniences:

- Establishes a standardized format for storing hyperparameters and configs
- Provides a GUI for editing hyper parameters
- Provides a comparative graphing interface for quickly comparing training runs with different hyperparameters

# Detailed design

This will be a part of the `hypertuner` python library. It will parse a json file that is passed to it via a command line argument. It will construct a python object storing the hyperparameters from the json files in fields.

### Requirement

- The script imports the hypertuner library
- The script calls `hypertuner.parse()` and stores the object this call returns
- The script is called with a command line argument `--config=<PATH_TO_CONFIG>` 

### Config File

The config file passed to conform to the hypertuner file spec (INSERT LINK). This file is passed to the script via a command line argument named `--config=<PATH_TO_CONFIG>` where `<PATH_TO_CONFIG>` is the path of the config file relative to the location of the python script. 

### Args object

The object returned by `hypertuner.parse()` contains all the hyperparameters defined in the given json file as fields (traditionally this object is called `args`).

For example:

```python
import hypertuner

# Parse Args
args = hypertuner.parse()
# Print batch size and learning rate
print("Learning Rate: ", args.learning_rate)
print("Batch Size: ", args.batch_size)
```



# Drawbacks

- It will take time to implement

# Alternatives

- People can create their own custom config formats (but these will not work with hypertuner gui and are not standardized)


# Adoption strategy

Since this is the first ever build of hypertuner it will be adopted with the first wave of people initialy learning to use hypertuner.

# How we teach this

We will have a demo/tutorial on our website showing how to use this feature.

# Unresolved questions

None
