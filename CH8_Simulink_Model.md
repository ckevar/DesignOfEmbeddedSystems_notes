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


