# Models

_Link:_

*UML*, *SM* is a software modeling.

**Why models?** Sometimes enviroments make a system difficult to test, either due to enviromental conditions or costs, examples of this are space exploration or nuclear reactors. That's why modeling has two goals, *documenting* and *simulating*.

*UML* currently and usually is used as a **documenting** tool. Documenting and designing allow reusage and improvement on the code (sofware costs). This makes the software development effective, fast and errors avoidant, also currently known as **model-driven architecture**.

Things such as *Simulink* or *National Instruments*' tools allow us to model in order to know the behaviour of the system, to verify a property on the model, for example, the correct function of a *PID* controller or the safeness of a *SM*. And this is called **model-driven engineering**

**Model-based design** traditionally sees the model as a primary artifact for modeling the behavior and properties verification.

## Model-based design

In our case (embedded systems) models are built to test or verify properties (by simulation) or checking.

### Why automatic code generation?

Programmers can introduce errors in the modeling while implementing the code; so, **code generation** ensures the code is the same as the model.

### RTS and Platform-based Design

The execution plataform. Matches the logical design (HW architecture or OS) into the SW architecture. Using the API of the OS. Time in SW is a property that has to match with the hardware.

Timing properties such as, period and execution time are parameters that are required but the execution platform will dictate the worst case scenario.
