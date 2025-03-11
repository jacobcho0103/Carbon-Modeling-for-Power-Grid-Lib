# Carbon_aware_casefile

This repository contains a collection of components designed for reinforcement learning (RL) experiments in an energy management domain. The project is structured to facilitate the development, training, and evaluation of RL agents within a custom energy management environment. Below is an overview of the primary components and their functionalities.

## Python
Pandapower.py

```python
# Import require libraries
import pandapower as pp
import pandapower.networks as pn
import pandas as pd
```

```python
# Load the pandapower network (assumed to be in MATPOWER format)
# Example for case30
net = pn.case30() 
```

```python
# Generate the fuel dictionary
fuel_dict = fuel_dict_generation(net)

# Assign fuel types and emissions to specific generator buses
fuel_dict[1] = {"type": "GAS", "emissions": "CO2e"}
fuel_dict[12] = {"type": "ANT", "emissions": "CO2"}
fuel_dict[22] = {"type": "BIT", "emissions": "CO2"}

# Apply carbon constraints to the pandapower network
carbon_constrained_casefile(net, fuel_dict)
```



## Julia
PowerModels.jl

```julia
# Import require libraries
using PowerModels, HiGHS
```

```julia
# Load the Powermodels.jl network (assumed to be in MATPOWER format)
# Example for case118
net = PowerModels.parse_file("case118.m")
```

```julia
# Generate the fuel dictionary
fuel_dict=fuel_dict_generation(net)

# Assign fuel types and emissions to specific generator buses
fuel_dict[6] = Dict("type" => "GAS", "emissions" => "CO2e")
fuel_dict[55] = Dict("type" => "ANT", "emissions" => "CO2")
fuel_dict[110] = Dict("type" => "BIT", "emissions" => "CO2")

# Apply carbon constraints to the powermodels network
Carbon_constrained_casefile(net,fuel_dict)
```
