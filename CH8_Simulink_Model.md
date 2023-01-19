# Simulink Model

Link: [Lesson 4: Simulink intro: semantics - YouTube](https://www.youtube.com/watch?v=RG7ZBa24wOQ&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=11)

they can be many things: network of blocks, other things to considerate to generate code from a model are:

1. Number of workspace variables, The execution of the model may be conditioned to the value or number of variables.

2. Number of type declarations. Each block is the model is carrying a signal, a funtion in time with values in a given range. They can be premitive types predefined by simulink. Keep in mind that complex types can be used in models, possible variable dimensiones, such as arrays, where each element is a structure. In general, whatever language is being used to develop the system, the capability to create custom data types is desired/required. In simulink, this is called bus objects. This custom types are defined outside the model in a separate enviroment.

3. Other part of the system's bheaviour might be descriped with matlab code or external code, that might not be in the graphical description.

4. Simulation condiguration pages.

## Simulink semantics and flow preservation

The system is a network of functional blocks, for convinience they are labeled as b_j. In simulink the blocks can be regular blocks or **dataflow blocks**, these are Stateless (in reality some blocks do have a state). they can be continuous, discrete or triggered.

1. *Continues* means the outputs is update and is valid at any point in time in a continuous time.

2. *Discrete* means it only updates its output at discrete point in time.

3. *Triggered*, it's kind of a discrete event.

The other type of blocks are **Stateflow** or state machine blocks, this type of blocks are actually managed by a program that in reality is external, it's kind of a plug-ing of external program. In the new versions of simulink the manage of the stateflow blocks is homogeneous to the other blocks.

When generating code out of a model, everything becomes a discrete time block. Everything becomes periodically activated. For embedded systems, out of all those blocks, the most importants are the periodic activated ones. The signals are continues but sample periodically and the output will be periodic as well.

## Simulation Flow

Whenever there's a network of blocks, basically there are __two__ end points, the **initialization** stage at the begining and a **termination** stage at the end.

Then there is the **main** simulation cycle that is repeated until the end of the simulation. basically the end of the simulatio is controlled by the user, i.e. *inf* means the simulation lasts forever.

The model is **first compiled** before simulation, number of things that have to be done before simulating, as part ot this, each block is assigned with a rate. This is because the user doesnt write explicitly a number for the block's period but it's usually left as inheritance. In this case, the backwards block will dictate the period otherwise, there's a forward search in order to find something that defines a period for the block. Therefore, there's a forward and backwards propagation to assign rate to the blocks. Constant values are also prograpagated at compilation time (to avoid recomputation). As well it initialize the simulation structure, inputs, outputs, states, matrices and variables that are in the system.

Inside the cycle, the next simulation time is computed specially when there's a variable rate execution, let's step back, there are three types of blocks, continuos, discrete and event.-drive. if everything in the system is discrete, then, the next event in the sysmte is very easy it would be the next activation for any block in the sysmte, and in this case the simulator will do, basically the simulator will compute the base rate, it computes the gratest como divisor among all the periods of all blocks. i.e., if there are two blocks with periods 3 and 10, the the GCM would be 1, meaning the overall period is 1.

Now, assume some blocks are continuos then, there's an election between performing a variable step o fixed step integration. Continuous blocks usually are related to a set of diferential equations that need to solve integrations and derivatives. For example, the dynamics of a bouncing ball are submitted for simulation. The simulator will describe the ball behaviour as a set of differential equations, as a result these equations will be solve by a solver, the solver may use points in time equally spaced (fixed time/fixed step). The solver will provide the location of ball on those chosen points in time, The model is gonna be affected by the solver, there might be some innacuracies. The solver might want to give the ball position in a particular position, peak, or when hitting bottom, so the step are not fixed anymore.

Whithin the simulation cycle, for variable rates, the next event has to be computed, after that, all outputs, discrete states and integration with continuous time has to be performed, once done, the simulation cycle restarts.

## Functional Representation: SR Simulink Modeling

For our convinience, they all operate in continuos signals, so, inputs and outputs are continuos functions. Blocks might stateful or stateless, these lead us the fact that continuos-type blocks are defined by a set of diferential equations and discrete-type blocks maybe defined by a set of diferent situation (or event ocurrencies). 

The discrete blocks are the most interesting one, because eventually, at generating code, the model has to be simulated with a fixed-step solver. This fixed step will be the period of uptading the states of the blocks and outputs, even continuos blokcs will be treated as if they were discrete. 

Discrete blocks are activate by periodic events with 0 offset, meaning the blocks dont wait for a fixed amount time after the event was triggered. 

$T_b$ is a base period and it must be a divisor of any other periodic input signal.   

### How does each block behaves?

At each activation event, the bock computes its out update and state update functions:

$S_j^{new},o_j = f(S_j,i_j)$

### State Machines

These are activated periodically, they might, but they usually react to a set of event streams $e_{jv}$. And each event is characterized by a period. Merging Data flow blocks and State flow blocks and all activation events in the system will belong to a discrete time base, for events this is translated as: $kT_{jv}$, where $T_{jv}$ is the activation period of each event $e_{jv}$ times a generic integer $k$.



**SIMULATION CONFIGURATION**

On the simulink workspace, click on Simulation, Configuration Parameters. 

Some parameters in here are related to the simulation and some, to the code generation.

Under the Solver, the solver's step (fixed-step or variable), the step size and the solver itself. Meaning, even the continuos blocks will be evaluated periodicaly. Once, variable is chosen an additional number of options are released.

1. **Execution Order - Feedthrough**
   
   if two blocks $b_i$ and $b_j$ are in an input-output relationship and $b_j$ is of type _feedthrough_, then:
   
   $b_i \rarr b_j $, this is a contraint that says $b_i$ has to be executed before $b_j$.
   
   in case $b_j$ isn't a feedthrough type, then, the link has a delay:
   
   $b_i \rarr ^{-1} b\_j$
   
   _What does_ **_feedthrough_** *mean?* 
   
   Each block has an activation event, set of inputs, set of outputs, an output update rule based on in the input and the block inner state and an state update rule based on the input and the block inner state. Many blocks have all of these, and some are stateless or state-only blocks (delay or integrators). Not feedthrough referers to blocks whose output does not depend on inputs. meantime for **_feedthrough_** the inputs are required before computing the outputs. 

2. 


