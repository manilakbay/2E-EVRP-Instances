# Two-Echelon Electric Vehicle Routing Problem (2E-EVRP) Instances

## Overview

This repository provides benchmark datasets designed for solving the **Two-Echelon Electric Vehicle Routing Problem (2E-EVRP)**. The datasets include instances with diverse logistical constraints, such as:
- **Time Windows**
- **Simultaneous Pickup and Delivery (SPD)**
- **Partial Deliveries**

These datasets are extensions of established Vehicle Routing Problem (VRP) and Electric Vehicle Routing Problem (EVRP) benchmarks, adapted to a two-echelon logistics structure. The data supports research and benchmarking for sustainable logistics solutions in urban environments.

---

## Dataset Structure

### File Naming Convention

Each dataset file follows this naming pattern:

```
{Prefix}{InstanceNumber}_C{NumberOfCustomers}{Version}.txt
```

- **Prefix**: `C`, `R`, or `RC` indicating the spatial distribution of customers:
  - `C`: Clustered distribution
  - `R`: Random distribution
  - `RC`: Random-Clustered distribution
- **InstanceNumber**: Unique identifier for each instance.
- **C{NumberOfCustomers}**: Number of customers in the dataset (e.g., `C5` for 5 customers, `C50` for 50 customers).
- **Version**:
  - `x`: Original instance with assigned delivery and pickup demands.
  - `y`: Instance with delivery and pickup demands exchanged for each customer.

### Example
- `C101_C5x.txt`: A clustered instance with 5 customers, original demands.
- `C101_C5y.txt`: The same instance but with delivery and pickup demands swapped.

---

## Dataset Layout

Each instance is structured into **two main sections**:

1. **Node Information**:
   This section contains detailed specifications for each node:
   - **StringID**: Unique identifier for the node.
   - **Type**:
     - `d`: Depot (central warehouse)
     - `s`: Satellite (intermediate depot)
     - `f`: Charging station
     - `c`: Customer
   - **Coordinates**: Cartesian `x` and `y` positions.
   - **Demands**:
     - **DeliveryDemand**: Amount to deliver to the customer.
     - **PickupDemand**: Amount to pick up from the customer.
     - **DivisionRate**: Percentage of demand that can be split between vehicles (for partial delivery scenarios).
   - **Time Windows**: `ReadyTime` and `DueDate`.
   - **ServiceTime**: Time required to service the node.

2. **Vehicle Configuration**:
   Specifies attributes for the vehicles used in the problem:
   - **Large vehicle loading capacity** (used in the first echelon).
   - **Electric vehicle loading capacity** (used in the second echelon).
   - **Electric vehicle battery capacity**.
   - **Fuel consumption rate**.
   - **Inverse refueling rate**.
   - **Average velocity**.

---

### Example File Format

Below is an example of a dataset file:

```
StringID   Type       x          y          demand     DeliveryDemand  PickupDemand  DivisionRate ReadyTime  DueDate    ServiceTime
D0         d          50.0       150.0      0.0        0.0             0.0           0            0.0        9999.0     0.0         
S0         s          50.0       75.0       0.0        0.0             0.0           0            0.0        9999.0     0.0         
F0         f          50.0       75.0       0.0        0.0             0.0           0            0.0        9999.0     0.0         
F1         f          31.0       84.0       0.0        0.0             0.0           0            0.0        9999.0     0.0         
C0         c          20.0       55.0       10.0       4.0             6.0           45           456.0      508.0      90.0        
C1         c          25.0       85.0       20.0       6.0             14.0          35           277.0      329.0      90.0        
C2         c          55.0       85.0       20.0       13.0            7.0           25           845.0      899.0      90.0        
C3         c          68.0       60.0       30.0       26.0            4.0           30           838.0      910.0      90.0        
C4         c          48.0       30.0       10.0       6.0             4.0           40           364.0      426.0      90.0        

L Large vehicle loading capacity /800.0/
C Electric vehicle loading capacity /100.0/
Q Electric vehicle battery capacity /77.75/
r Fuel consumption rate /1.0/
g Inverse refueling rate /3.47/
v Average velocity /1.0/
```

---

## Key Features

- **Multiple Instance Sizes**:
  - Small: 5-15 customers with up to 2 satellites.
  - Medium: 50 customers with 4 satellites.
  - Large: 100 customers with 8 satellites.

- **Two Versions**:
  - `x`: Original delivery and pickup demands.
  - `y`: Swapped delivery and pickup demands.

- **Realistic Constraints**:
  - Time windows for each node.
  - Partial deliveries with split demand capabilities.
  - Electric vehicle constraints (battery capacity, recharging rates, etc.).

- **Diverse Geographical Configurations**:
  - Clustered, random, and random-clustered distributions.

---

## Applications

The dataset is suitable for benchmarking and developing solution methods for:
- Two-Echelon Electric Vehicle Routing Problems (2E-EVRP).
- Routing algorithms for urban and last-mile logistics.

---

