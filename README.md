# Benchmark instances for the Generalized Correlated Team Orienteering Problem (GCorTOP)

Benchmark instances for the Generalized Correlated Team Orienteering Problem introduced in Glock, K. and Meyer, A. (2020). Mission planning for emergency rapid mapping with drones. Transportation Science 54(2):534-560. https://doi.org/10.1287/trsc.2019.0963.

## Overview

The benchmark instances represent scenarios for the mission planning problem for emergency surveillance, which seeks to determine tours for UAVs through a subset of potential candidate sensing locations such that first responders can be provided with a reliable overview of the distribution of hazardous substances. 

Instances have been generated based on data on population density in the German state of North Rhine-Westphalia combined with artificially generated contributions of contaminants. Detailed information about the generation of the benchmark instances is given in the paper indicated above. 

## Instance files

The name of an instance file encodes basic information about the generated instance and the model configuration and can be read as follows:
    
    a_b-n-v-t.json

with instance parameters as follows:
- `a_b`: the size of the grid of target locations along the horizontal and vertical axis, from 15x15 to 25x25 (representing an area of 1,5x1,5 km² to 2,5x2,5 km², respectively)
- `n`: the running number identifying the specific combination of population data and artificial contaminant distribution for the given target size, with 6 combinations per instance size
- `v`: number of UAVs (1, 2 or 3)
- `t`: maximum flight time in s (600s, 900s, 1200s, 1500s, 1800s)
	
This leads to a total of 450 different instance configurations.

Instances are given as JSON files to be read as follows:
- `nodes`: array of candidate target locations
	- `extId`: unique node ID
	- `groundTruth`: value of the generated distribution
	- `posX`: coordinate in the horizontal direction, i.e. distance in m from the origin (0,0)
	- `posY`: coordinate in the vertical direction, i.e. distance in m from the origin (0,0)
	- `priority`: target node priority, i.e. population information based on the German census 2011 
	- `serviceTime`: time for measuring in s
- `vehicles`: array of deployed UAVs
	- `extId`: unique vehicles ID
	- `speed`: cruise speed, here: 7 meters per second
	- `acceleration`: acceleration, here: 2 m per s^2
	- `posX`: starting and ending coordinate
	- `posY`: starting and ending coordinate
	- `timeLimit`: maximum flight time in s

This information fully describes a GCorTOP instance. For completeness' sake, we additionally give the following information:
- `bbX1`, `bbY1`, `bbX2`, `bbY2` together give the bounding box of the instance with respect to the initial census data in the format for geographic data used therein
- `maxWeight`: maximum weight for neighboring nodes 
- `range`: distance limit for positive weights
		
## Cite

If you use these instances in your work, please cite:
	
	@misc{glock2020,
	  author = {Glock, Katharina and Meyer, Anne},
	  title = {Mission planning for emergency rapid mapping with drones},
	  journal={Transportation science},
	  volume={54},
	  number={2},
	  pages={534--560},
	  year={2020},
	  publisher={INFORMS}
	}
