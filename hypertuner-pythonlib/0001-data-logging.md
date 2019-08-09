- Start Date: 2019-08-09
- RFC PR: (leave this empty)
- React Issue: (leave this empty)

# Summary

Hypertuner logging will allow users to log and graph performance data collected during training of thier models and display it with the hypertuner GUI.

# Basic example

```python
import hypertuner

# Initialize logger
logger = hypertuner.Logger()
# Log squares of numbers from 0 to 9
for i in range(10):
  logger.log({"Square": i**2}, i)
```

# Motivation

While training machine learning models and tuning hyperparameters it is often important to graph the performance of a model and compare it with different configurations. Hypertuner provides logging for users to view/store the performance of the model.

# Detailed design

This will be a part of the `hypertuner` python library. It will write training data to a json log file.

### Requirement

- The script imports the hypertuner library

- The script calls `hypertuner.Logger()` and stores the object this call returns (typically as `logger`)

- The script calls `logger.log(<DICT_OF_LOGS>, <FRAME_NUM>)`

### Log Call

The object returned by `hypertuner.Logger()` can be used to log data at any time (traditionally this object is called `logger`).

Whenever the user calls `logger.log(DICT_OF_LOGS>, <FRAME_NUM>)` they have to pass in a dict containing string-value pairs representing the data to be logged (`<DICT_OF_LOGS>). The user can also include an optional second parameter representing the frame, step or epoch number (<FRAME_NUM>). This argument is used to determine the position of the data point along the x axis. If omitted it will be replaced by a timestamp. of when `logger.log(<DICT_OF_LOGS>)` was called.

For example:

```python
import hypertuner

# Initialize logger
logger = hypertuner.Logger()
# Log squares of numbers from 0 to 9
for i in range(10):
  logs = {
    "Square": i**2,
    "Cube": i**3,
    "Float": 3.18e5,
    "Word of the day": "Peacoc",
    "This is working": True
  }
  logger.log(logs, i)
```



# Drawbacks

- It will take time to implement

# Alternatives

- Apps with similar functionality exist (like Tensorboard), but they do not plug into the hypertuner echo system which allowes for easy tuning of parameters, job scheduling and storing.

# Adoption strategy

Since this is the first ever build of hypertuner it will be adopted with the first wave of people initialy learning to use hypertuner.

# How we teach this

We will have a demo/tutorial on our website showing how to use this feature.

# Unresolved questions

None
