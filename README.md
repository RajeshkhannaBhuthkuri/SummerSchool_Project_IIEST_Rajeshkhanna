# Summer School Project – A-NUCA-DREM for Energy-Aware Autonomous EV Platooning under Mixed Traffic Conditions

## Overview

This project develops an **Adaptive Non-Uniform Cellular Automata (A-NUCA)** framework for modelling autonomous vehicle traffic under mixed traffic conditions.

The proposed framework extends the classical **Nagel–Schreckenberg (NaSch) Cellular Automata** model by introducing adaptive vehicle states, dynamic rule selection, traffic-density information, vehicle interactions, platooning behaviour, electric-vehicle energy states, and real-world traffic trajectory data.

The project is implemented progressively through five Google Colab notebooks.

---

## Project Objective

The main objective is to develop an adaptive cellular-automata-based traffic modelling framework in which vehicles can dynamically modify their behaviour according to their surrounding traffic environment and individual vehicle states.

The framework considers:

- Vehicle position and speed
- Acceleration and braking
- Traffic density
- Vehicle neighbourhood
- Headway
- Lane changes
- Platoon formation and maintenance
- Electric-vehicle State of Charge (SOC)
- Energy consumption
- Predicted traffic density
- Dynamic rule selection

---

# Overall Project Workflow

```text
Classical Nagel–Schreckenberg Model
                │
                ▼
       Adaptive Non-Uniform CA
                │
                ▼
      Dynamic Rule Evolution
                │
                ▼
       EV Energy & Battery Model
                │
                ▼
       Platoon & Traffic Analysis
                │
                ▼
        NGSIM Real-World Data
                │
                ▼
      Traffic Density Prediction
                │
                ▼
       Adaptive Rule Selection
                │
                ▼
       Vehicle State Transition
                │
                ▼
        Performance Evaluation
Notebook 1 – Classical Cellular Automata Baseline
File: CA_NB1A.ipynb

This notebook establishes the classical Nagel–Schreckenberg (NaSch) cellular automata model as the baseline traffic model.

The notebook implements:

Highway and vehicle initialization
Vehicle acceleration
Braking
Randomization
Vehicle movement
Traffic-flow simulation
Vehicle trajectories
Space–time diagrams
Speed and density analysis
Fundamental diagrams
Traffic animation
Congestion formation
Stop-and-go behaviour
Traffic shockwave analysis

The classical model provides the reference framework for developing and evaluating the proposed adaptive approach.

Notebook 2 – Adaptive Non-Uniform Cellular Automata
File: ANUCA2.ipynb

This notebook develops the core Adaptive Non-Uniform Cellular Automata (A-NUCA) framework with a Dynamic Rule Evolution Mechanism (DREM).

The vehicle state incorporates information such as:

Position
Lane
Speed
Acceleration
Energy
State of Charge (SOC)
Battery temperature
Local traffic density
Predicted density
Headway
Platoon role
Platoon ID
Neighbour relationships

The adaptive rule library contains eight rules:

Rule	Behaviour
R1	Accelerate
R2	Join Platoon
R3	Maintain Platoon
R4	Increase Headway
R5	Split Platoon
R6	Lane Change
R7	Reduce Acceleration / Eco Driving
R8	Cooperative Braking

The Dynamic Rule Evolution Mechanism selects an appropriate rule based on the vehicle state and surrounding traffic conditions.

Notebook 3 – EV Battery and Traffic Analytics
File: ANUCA3.ipynb

This notebook extends the A-NUCA framework with an EV-oriented energy and analytics layer.

The notebook investigates:

Vehicle power demand
Battery current
Battery temperature
Energy consumption
Cumulative energy usage
Battery degradation-related quantities
Simulation logging
Platoon analytics
Traffic metrics
Vehicle-level statistics

This stage connects vehicle traffic behaviour with the energy-related state of electric vehicles.

Notebook 4 – Real-World NGSIM Traffic Integration
File: Copy_of_ANUCA4.ipynb

This notebook integrates real-world traffic trajectory data from the NGSIM dataset, including US-101 and I-80 traffic observations.

The workflow includes:

Dataset discovery
Dataset loading
Data cleaning
Data standardization
Unit conversion
Vehicle trajectory reconstruction
Vehicle-dynamics analysis
Lane-change analysis
Local traffic-density calculation
A-NUCA adaptive-state generation
Rule-decision preparation

The processed real-world trajectory data are used as inputs for the final adaptive decision-making stage.

Important Data Note

NGSIM provides real-world traffic variables such as:

Position
Velocity
Acceleration
Lane
Headway
Vehicle relationships

NGSIM does not provide direct EV battery measurements such as SOC, battery energy, or battery temperature.

Therefore, EV-specific battery variables used by the A-NUCA framework are modelled/synthetically estimated variables.

Notebook 5 – Traffic Prediction, DREM and Evaluation
File: ANUCA5_1.ipynb

This notebook completes the adaptive decision-making and evaluation pipeline.

The workflow is:

NGSIM Traffic Data
        │
        ▼
Frame-Level Traffic Density
        │
        ▼
Lag Features
        │
        ▼
Temporal Train/Test Split
        │
        ▼
Traffic Density Prediction
        │
        ▼
Predicted Density
        │
        ▼
Dynamic Rule Selection
        │
        ▼
Rule Execution
        │
        ▼
Adaptive State Transition
        │
        ▼
Performance Evaluation

Traffic-density prediction is evaluated using:

Mean Absolute Error (MAE)
Root Mean Square Error (RMSE)
R²

The final evaluation includes:

Average speed
Mean absolute acceleration
Average SOC
Energy consumption
Average traffic density
Predicted traffic density
Density prediction error
Platoon participation
Rule distribution
Rule-wise performance
Throughput
Adaptive State Transition

The proposed framework represents vehicle evolution using:

$$ S_i(t+1)=F_i(S_i(t),N_i,R_i) $$

where:

\(S_i(t)\) = current state of vehicle \(i\)
\(N_i\) = neighbourhood information
\(R_i\) = dynamically selected rule
\(F_i\) = state-transition function

The adaptive rule-selection mechanism considers vehicle, traffic, neighbourhood, energy, and predicted-density information.

Dataset

The real-world traffic component uses NGSIM US-101 and I-80 trajectory data.

The raw dataset is not included in this repository. Users should obtain the dataset separately and configure the data path in the corresponding notebook.

Execution Order

The notebooks should be executed in the following order:

CA_NB1A.ipynb
      ↓
ANUCA2.ipynb
      ↓
ANUCA3.ipynb
      ↓
Copy_of_ANUCA4.ipynb
      ↓
ANUCA5_1.ipynb

Each stage builds upon the concepts and/or outputs developed in the previous stage.

Software Requirements

The project is implemented in Python and designed for Google Colab.

Major libraries include:

NumPy
Pandas
Matplotlib
Scikit-learn
tqdm
NetworkX where required
Research Contribution

The project integrates:

Cellular Automata + Adaptive Vehicle Behaviour + Dynamic Rule Evolution + EV Energy State + Autonomous Platooning + Real-World Traffic Data + Traffic Density Prediction

The central idea is to move beyond fixed and uniform traffic rules by allowing vehicles to dynamically select their behaviour according to current traffic conditions, neighbouring vehicles, platoon conditions, predicted traffic density, and EV energy state.

Research Limitation

A distinction should be maintained between real-world and modelled variables.

NGSIM trajectory variables such as position, velocity, acceleration, lane, and headway are derived from real traffic observations.

EV-specific variables such as SOC, energy consumption, and battery temperature are modelled within the proposed framework.

Therefore, energy-related results should be interpreted as outputs of the proposed EV-state model coupled with real-world traffic trajectories rather than as directly measured EV battery outcomes from NGSIM.

Project Structure
SummerSchool_Project_IIEST_Rajeshkhanna/
│
├── README.md
│
├── CA_NB1A.ipynb
├── ANUCA2.ipynb
├── ANUCA3.ipynb
├── Copy_of_ANUCA4.ipynb
└── ANUCA5_1.ipynb
Author

Dr. B. Rajeshkhanna

Summer School Project
IIEST Shibpur

Implementation Platform: Google Colab

Keywords

Adaptive Non-Uniform Cellular Automata, A-NUCA, Dynamic Rule Evolution Mechanism, DREM, Nagel–Schreckenberg Model, Autonomous Vehicles, Electric Vehicles, EV Platooning, Mixed Traffic, NGSIM, Traffic Density Prediction, Energy-Aware Traffic Modelling, Cellular Automata.
