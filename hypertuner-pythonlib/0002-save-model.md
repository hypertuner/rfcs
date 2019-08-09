- Start Date: 2019-08-09
- RFC PR: (leave this empty)
- React Issue: (leave this empty)

# Summary

Hypertuner allows the users to save their ML model alongs side with the configs used to run them.

# Basic example

```python
import hypertuner

# import some neural net
net = Net()

# Initialize saver
saver = hypertuner.Saver(model)
# Save model
saver.save()
```

# Motivation

Saving model weights is a broadly implemented function in machine learning frameworks but saving them in a standardized format along with the parameters used to generate them is not automated. Therefore hypertuner implements a saving feature that plugs in seamlessly with the GUI to enable re-using weights obtained on training runs that proved to be sucessful compared to other settings.

# Detailed design

This will be a part of the `hypertuner` python library. It will save the given model along with the hyperparameter settings.

### Requirement

- The script imports the hypertuner library
- The script calls `hypertuner.Saver(<MODEL_TO_SAVE>)` and stores the object this call returns (traditionally called `saver`)
- The script calls `saver.save()`

### Save Path

The model will be saved as a serialized python object at `./storage/<NAME_OF_RUN>/model.pt` where `<NAME_OF_RUN>` is the specified name of this specific run/job.

### Framework Support

This feature is currently only supported in PyTorch

For example:

```python
import hypertuner

# import some neural net
net = Net()

# Initialize 
saver = hypertuner.Saver()
# Save model
saver.save()
```



# Drawbacks

- It will take time to implement
- It only supports PyTorch (for now)

# Alternatives

- People can use the built in save feature of their ml library (it will not store at a standardized location and will not plug into the hypertuner GUI)

# Adoption strategy

Since this is the first ever build of hypertuner it will be adopted with the first wave of people initialy learning to use hypertuner.

# How we teach this

We will have a demo/tutorial on our website showing how to use this feature.

# Unresolved questions

None
