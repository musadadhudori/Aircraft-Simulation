# Aircraft-Simulation
___
In this project, one airplane flight will be simulated to visit all given airports. Each airport has different distances and costs and duration of aircraft maintenance, so this simulation aims to find aircraft flight routes that have the minimum distance (flight costs), maintenance costs and maintenance duration.

# Math formulas

## Parameter definition
* $n$ is the number of airports
* $I = \\{1, 2, 3, ..., n\\}$ is the airport set
* $K = \\{1, 2, 3, ...\\}$ is the set of aircraft age index in days
* $c$ is the flight cost matrix with $𝑐_{𝑖,𝑗}$ is the flight cost from airport $i$ to airport $j$
* $Acost_{i}$ is cost vector per day at airport $i$ of The A check maintenance
* $Bcost_{i}$ is cost vector per day at airport $i$ of The B check maintenance
* $Ccost_{i}$ is cost vector per day at airport $i$ of The C check maintenance
* $Dcost_{i}$ is cost vector per day at airport $i$ of The D check maintenance
* $loss$ is maintenance loss which is defined from the median profit per day
$$loss = \frac{4c_{min} + c_{max}}{2}, \space\space\space  0 < c_{min} < c_{i,j} < c_{max},\space\space\space \forall{i,j} \in I$$

## Optimization Problems
$$ \sum_{k \in K} \sum_{i \in I} \sum_{j \in J} \left( c_{i,j} x_{i,j} + Acost_{i} A_{i,j,k} + Bcost_{i} B_{i,j,k} + Ccost_{i} C_{i,j,k} + Dcost_{i} D_{i,j,k} + lossA_{i,j,k} + lossB_{i,j,k} + lossC_{i,j,k} + lossD_{i,j,k} \right) $$

##### Notes:
* $c_{i,j} x_{i,j}$ is objective function of airline costs
* $Acost_{i} A_{i,j,k}$ is objective function of The A check maintenance costs
* $Bcost_{i} B_{i,j,k}$ is objective function of The B check maintenance costs
* $Ccost_{i} C_{i,j,k}$ is objective function of The C check maintenance costs
* $Dcost_{i} D_{i,j,k}$ is objective function of The D check maintenance costs
* $lossA_{i,j,k}$ is objective function of The A check maintenance time loss
* $lossB_{i,j,k}$ is objective function of The B check maintenance time loss
* $lossC_{i,j,k}$ is objective function of The C check maintenance time loss
* $lossD_{i,j,k}$ is objective function of The D check maintenance time loss



## Constraint


# Assumption
* The data used is data obtained from random numbers generated with certain limits
* Maximum number of flights per day is 4
<br></br>
* [The A check](https://www.qantasnewsroom.com.au/roo-tales/the-a-c-and-d-of-aircraft-maintenance/) aircraft maintenance interval ranges from 56 days to 70 days
* [The B check](https://www.naa.edu/types-of-aviation-maintenance-checks/) aircraft maintenance interval ranges from 180 days to 240 days
* [The C check](https://www.qantasnewsroom.com.au/roo-tales/the-a-c-and-d-of-aircraft-maintenance/) aircraft maintenance interval ranges from 540 days to 720 days
* [The D check](https://www.naa.edu/types-of-aviation-maintenance-checks/) aircraft maintenance interval ranges from 2,160 days to 3,600 days

#### Flight costs
* Airfare ranges from $708 to $51,124

#### Maintenance duration
* The A check maintenance duration per airport is 1 days
* The B check maintenance duration per airport from 1 days to 3 days
* The C check maintenance duration per airport from 7 days to 14 days
* The D check maintenance duration per airport from 21 days to 42 days

#### Maintenance costs
* The A check maintenance cost per airport from $310 to $820
* The B check maintenance cost per airport from $4,960 to $7,380
* The C check maintenance cost per airport from $186,000 to $246,000
* The D check maintenance cost per airport from $930,000 to $2,050,000
