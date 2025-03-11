# Carbon_aware_casefile

This repository contains a collection of components designed for reinforcement learning (RL) experiments in an energy management domain. The project is structured to facilitate the development, training, and evaluation of RL agents within a custom energy management environment. Below is an overview of the primary components and their functionalities.

## Python
Pandapower.py

```python
# Import require libraries
import pandapower as pp
import pandapower.networks as pn
import pandas as pd

# Load the pandapower network (assumed to be in MATPOWER format)
net = pn.case30() 

# Generate the fuel dictionary
fuel_dict = fuel_dict_generation(net)

# Assign fuel types and emissions to specific generator buses
fuel_dict[1] = {"type": "GAS", "emissions": "CO2e"}
fuel_dict[12] = {"type": "ANT", "emissions": "CO2"}
fuel_dict[22] = {"type": "BIT", "emissions": "CO2"}

# Apply carbon constraints to the pandapower network
carbon_constrained_casefile(net, fuel_dict)
---



## Julia
PowerModels.jl
