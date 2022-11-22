# Aircraft Simulation
___
In this project, one airplane flight will be simulated to visit all given airports. Each airport has different distances and costs and duration of aircraft maintenance, so this simulation aims to find aircraft flight routes that have the minimum distance (flight costs), maintenance costs and maintenance duration.

# Optimization Problems

## Parameter Definition
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
<br></br>

## Decision Variables

$$x_{i,j,k} = \left \\{ 
\begin{array} \\ 
    1, & \mbox{if $j$ is visited after $i$ on day  $k$ } \\  
    0, & \mbox{otherwise}  
\end{array} 
\right.$$

<br></br>

$$A_{i,j,k} = \left \\{ 
\begin{array} \\ 
    1, & \mbox{if $j$ is visited after $i$ and The A check maintenance at $j$ on day $k$ } \\  
    0, & \mbox{otherwise}  
\end{array} 
\right.$$

<br></br>

$$B_{i,j,k} = \left \\{ 
\begin{array} \\ 
    1, & \mbox{if $j$ is visited after $i$ and The B check maintenance at $j$ on day $k$ } \\  
    0, & \mbox{otherwise}  
\end{array} 
\right.$$

<br></br>

$$C_{i,j,k} = \left \\{ 
\begin{array} \\ 
    1, & \mbox{if $j$ is visited after $i$ and The C check maintenance at $j$ on day $k$ } \\  
    0, & \mbox{otherwise}  
\end{array} 
\right.$$

<br></br>

$$D_{i,j,k} = \left \\{ 
\begin{array} \\ 
    1, & \mbox{if $j$ is visited after $i$ and The D check maintenance at $j$ on day $k$ } \\  
    0, & \mbox{otherwise}  
\end{array} 
\right.$$

<br></br>

## Objective Function
$$ \min\left( \sum_{k \in K} \sum_{i \in I} \sum_{j \in J} \left( c_{i,j} x_{i,j} + Acost_{i} A_{i,j,k} + Bcost_{i} B_{i,j,k} + Ccost_{i} C_{i,j,k} + Dcost_{i} D_{i,j,k} + lossA_{i,j,k} + lossB_{i,j,k} + lossC_{i,j,k} + lossD_{i,j,k} \right)\right) $$

Notes:
* $c_{i,j} x_{i,j}$ is objective function of airline costs
* $Acost_{i} A_{i,j,k}$ is objective function of The A check maintenance costs
* $Bcost_{i} B_{i,j,k}$ is objective function of The B check maintenance costs
* $Ccost_{i} C_{i,j,k}$ is objective function of The C check maintenance costs
* $Dcost_{i} D_{i,j,k}$ is objective function of The D check maintenance costs
* $lossA_{i,j,k}$ is objective function of The A check maintenance time loss
* $lossB_{i,j,k}$ is objective function of The B check maintenance time loss
* $lossC_{i,j,k}$ is objective function of The C check maintenance time loss
* $lossD_{i,j,k}$ is objective function of The D check maintenance time loss


<br></br>

## Constraint
$$ \sum_{k \in K} \sum_{j=1}^{n} x_{i,j,k} = 1, \space\space\space for \space i\in I  $$

$$ \sum_{k \in K} \sum_{i=1}^{n} x_{i,j,k} = 1, \space\space\space for \space j\in I  $$

<br></br>

# Assumption
* The data used is data obtained from random numbers generated with certain limits
* Maximum number of flights per day is 4
* Maximum airfare per day is $51,124
<br></br>
* [The A check](https://www.qantasnewsroom.com.au/roo-tales/the-a-c-and-d-of-aircraft-maintenance/) aircraft maintenance interval ranges from 56 days to 70 days
* [The B check](https://www.naa.edu/types-of-aviation-maintenance-checks/) aircraft maintenance interval ranges from 180 days to 240 days
* [The C check](https://www.qantasnewsroom.com.au/roo-tales/the-a-c-and-d-of-aircraft-maintenance/) aircraft maintenance interval ranges from 540 days to 720 days
* [The D check](https://www.naa.edu/types-of-aviation-maintenance-checks/) aircraft maintenance interval ranges from 2,160 days to 3,600 days

#### Flight Costs
* Airfare ranges from $708 to $51,124

#### Maintenance Duration
* The A check maintenance duration per airport is 1 days
* The B check maintenance duration per airport from 1 days to 3 days
* The C check maintenance duration per airport from 7 days to 14 days
* The D check maintenance duration per airport from 21 days to 42 days

#### Maintenance Costs
* The A check maintenance cost per airport from $310 to $820
* The B check maintenance cost per airport from $4,960 to $7,380
* The C check maintenance cost per airport from $186,000 to $246,000
* The D check maintenance cost per airport from $930,000 to $2,050,000


# Simple illustration without maintenance
![image](https://user-images.githubusercontent.com/69705568/203385123-0bd2301b-ed7c-4898-8150-d0f0d54911ef.png)

For example, the flight route is A, B, C, D, E, F, G, H, I, J and back to A. When the plane arrives at airport E, the flight costs are more than $51124, because the maximum flight cost per day is $51124, so at airport D the age of the plane increases by one day. On routes D, E, F, G, H and I, even though from airport D to airport I the flight costs were less than $51124, but because at airport H the plane visited four airports, the age of the plane increased by one day. On routes H.I, J and A, even though from airport H to airport A the flight costs spent are less than $51124 and have not visited four airports, but because the airport is the last route, the aircraft's age increases by one day.
