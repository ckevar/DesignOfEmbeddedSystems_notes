# Simulink Intro

*Link: [Lesson 4: Simulink Intro - YouTube](https://www.youtube.com/watch?v=-8CaGKwRLzQ&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=9)*

## -> Lab

- This lab is pretty much built over something that the professor already have.
- In *Simulink*, the blocks are different from what they are in *SysML*, it's called *S-Function*. 
  (**SIDE NOTE**) **S-Function** is a custom block with a special behaviour.
  This lab's goal is to built a stopwatch that consists of two parts (that will end up in three parts, actually):
- *First part*: the plant, just a front end (no physicis here). Already provided. It can be the simulation of the plant or the physics, though.
- *Second part*: the controller part, that's split into two parts:
  - State of the Stopwatch
  - Managing the condition of the inputs
    This has to be provide by us. How to controll the display of the digits, a mechanism has to be added to translated the *SM* output, such as: hours, minutes and seconds, tens of a second and, blinking.
  - *Third part*: set of blocks that are required at code generation time to manage the actual IO.

## -> Lab (again)

- By double clicking a susbsystem block it opens its content. The inputs can be: Hours, Minutes and, Seconds, tenths, mode, blinking. The outputs can be: Row1 and Row2. This subsystem will be named "Row_encoding". Row encondig was used for the old project, where the output for the user was double row LCD display.  The updated project uses a touch LCD screen. Most the "graph" shown in  the videos referers to previous project, you can skip this video.
- By right-clicking on the block, *Format*, *Flip Block*, it flips the selected block.
- *Counter Limited* block will count to 23 for hours, 59 for minutes and seconds and to 99 for tenths of a second.
- _"-1" sample time means_ Each and everyblock is associated with a sample time, time which the block needs to be evaluated. Discrete Time blocks are usually periodic and that's sample time, but "-1" means inherited from the succesor and if it doesnt have one then it is useless but it means that it will produce the output whenever the consumer needs data.
- A *Math Function* block is a generic mathematical function that can be used any several function, such as: *exp*, *log*, *log10*, ***mod***, etc.
- A *Mux* is something that is gonna compose a set of single scalars and creates an array out of them. A *Mux* can also compose array of arrays.

## Model Implementation: multi-task

*Link: [Lesson 4: Simulink - code generation and RT blocks - YouTube](https://youtu.be/WGuB5_vwGDs)*

The communication variables need to be protected whenever there's a multi-task system that shares these variables among the task, these variables should be preserved or at least they should have a deterministic behaviour.
 On *Simulink*, the commercial code generator, there's a block that can handle this type of problem and it's called *Rate Transition Blocks*. This block can be added explicitly by the user or the code generation code can add this and other needed blocks in an implicit way (not nice Matlab!).

**What are Rate Transition Blocks?** This blocks are needed in case, preemption is needed among task executions. These tasks might implement the reader part and the writer part in two different task, if not, and if they dont preempt each other, then, there's no problem.

The protection mechanism and the Rate Transition block is only featured when there's a need to deal with a task implementation and the scheduling mechanism. It's not a functional meaning, it's an implementation meaning.

Writers and Readers have 4 possible interactions but only three of them are interesting and 2 of them need support for the implementation.

There are only 4 possible combinations of rates and priorities:

- High rate writer / Low rate reader
- Low rate writer / High rate reader
- High priority writer / Low priority reader
- Low priority writer / High priority reader

Given the fact the simulink code generator uses Rate Monotonic, the possible cases are only two:

- High-rate high-priority writer communicating with a low-rate low-priority reader.
- Low-rate low-priority writer communicating with a high-rate high-priority reader

**Mechanism that is provided by the commercial code generator**

1. *First case:* High-rate high-priority writer communicating with a low-rate low-priority reader.
   
   - the high rate writer has a period 1 and the low rate reader has period 2.
   - The Reader's goal is to use the first set of values that are produced by the writere.
   - Mechanism needed is to keep constant the values for the period of the reader. This is what the Rate Transition block is providing, it's only a sampling mechanism. This doesnt have a sate, only a set of outputs and the evaluation rule. This block has the *period* of the reader but the task and the *evaluation order* of the writer. So the output update of the Rate Transition block is executed in the same task of the writer right after the writer instance and then executed again with the period of the reader. It's a mechanism that does not need anything from the operating system. It's all code that is executed within the task at application level. it's very simple, simple copies inputs and outputs, it has a small overiding in terms of memory, small or large mostly depends what is being transfered from writer to reader.

2. *Second Case*: Low-rate low-priority writer communicating with a high-rate high-priority reader.
   According to _rate monotonic_, high-rate high-priority is gonna be executed before low-rate. So the order of executions are being violated, in this case, the *Rate Transition* Block for Low-rate to high-rate behaves as a delay, and as any other delay it has a state, so this block has a state update and an output of data port. The values that are produced by the execution of the writer in the previous cycle and then at the first execution of the reader in the following cycle is going to update its output and keep them constant for all the readers in the following writer's cycle. The state update part is executed in the context of the low priority writer task after the writer block and there's an output update that is executed in the context of the high rate task before the implementation of the reader block, sampling the values here and keep them constant. The behaviour is the same as the delay of one cycle of the low rate. ***What's the cost?***:
   
   1. Twice the memory cost (state and output variable)
   2. Additional delay. Delays arent terrible things, but if they are deterministic, they can be considered in the control law as well as in the formal verification and validation of safetyness and a compensation can be added, but no-delay would be better.

The Rate Transition block is included here
![](/home/ckevar/.config/marktext/images/2023-01-19-11-09-03-image.png)     

Because we want this to be Rate Monotonic. And it makes sense to go Rate Monotonic because it makes more efficent the scheduling  

**Limitations of Rate Transition** Keep in mind its advantage, it is implemented at application level and the limitations are:

1. Rate of the comunicating blocks need to be harmonic, otherwise things get complicated or dis-messaged.
2. The best option for multicore systems is doing it by hand, so the Rate Transition Block for this type of hardware isnt enough.

In the current literature there are many solutions to deal the first problem, either when the communication blocks arent harmonic or when they arent even periodic.

The rate transition blocks are useful when the priorities are enforcing the order of execution. If the blocks are in different cores, there's no priority order between the two, priorities are only given in a single core, unless a single priority queue exists for all cores (which is not common)- In a multicore implementation implicit synchronization is needed.

**Absence of Preemption from High to Low priority** the Rate Transition block when going from high to low priority.
When going from Low rate to high rate the rate transition block can be avoided if the low rate writer has a priority higher than the reader. Also when there's a high priority writer the Rate Transition Block can be avoided, this means the the Rate Transition block can be avoided when the reader is executed and complete when the writer is activated again. The condition for the Rate Transition block can be expressed as a timing condition, so if the response time of the reader is less than the period of the writer minus the maximum offset between the activion of the writer and the reader.

**Muticore adaption of RT block** When RT is needed on multicore implementation, there has to be a synchronization between reader and writer. As said before, priority order is not enough in multicore to guarantee the reader is going to be executed after, an explicit signal is needed, this signal can be generated by the writer when it completes. the other option is to compute the worst case execution for the writer and activate the reader with an offset equal to the worse-case execution time.

**Design/Scheduling trade-offs** 

![](/home/ckevar/.config/marktext/images/2023-01-19-11-32-29-image.png)

If the following set of task are a model in **Simulink**, the periods are 4, 1 and, 2. If we need this to be generated as a multitask implmentation by *simulink coded / embeded coder*. Rate Transition blocks are needed for every single link.
Assuming (**the text in red**) no RT is wanted there, and this can be either because it's a link with a lot of data o (so we dont want a memory overhead) or the reader doesnt want a delay there from a low rate to high rate.

- **Is it possible to achieve the fact some RTs have to be kept and other remove?**
- **Is there a way to have Rate Monotonic with a single task?** Remove the assupmtion that all the blocks with the same rate are executed by a single task. So, the task model might be like this: Highest priority task executing block 1 due to Rate Monotonic, the second task is executing the blocks of rate 2 followed by the task that executes a block of rate 4, followed by a task that executes a block of rate 2 and the last task executes the block 2. As you can see block 4 is implemented by a task that has a priority higher than block of rate 2, so there's no need of a Rate Transition block. So this task model is not a Rate Monotonic model that might be feasible saving the usage of Rate Transition Block.

The mapping of blocks into tasks is no more two options (that it has been talked before about how the Rate Transition block was used)

## Task Implementations

Given a set of tasks and a mapping function. Let's assume so far that the output update and state update are merged into a single step function f.
M is implementing a block within a task and may be expressed as a function M(f_j, k, i) where f_j is the step update function of block j mapped into the i task with execution order k.
(***SIDE NOTE***)**What's the execution order?** The order in which the step functions are called by the task. and this order has to be consistent with the partial order of executions.

There will be another functions that express the M functions into cores. and based on these mapping the communication mechanisms are designed that are the extensions of the rate transitions blocks.

**Preserving streams** Let's assume a general system where blocks are not even guarateed to be periodic that can be activated at generic points in time with minimal constraints.

![[Pasted image 20221005175524.png]]

Orange arrows represet the dependency of the blocks, meaning the entry of C is the output of A. But the real implementation turns to be this: 

A mechanism is required in order for B to process the all values produced by A, here is when buffer mechanism is deployed. When having multiple readers, one buffer isn't enough, an array of them is needed, popping many different problems. 

- **How many values will be stored?** There are research on going for this kinda questions.

Assume enough positions are present (no worries about buffer size). The mechanism needed is that assigns an index to the writers when a writer is activated and, the same thing to the reader. The Reader will be assined the index of the user that it will use when activated because the value that needs to be consumed is defined at activation time. This index cannot be given in the task code, it has to be done at activation time. That's why it needs the support of the operating system or something that guarantees the execution before any task in the system (highest priority). Once the index is assigned the actual write and read can be performed, obviously when the reader is reading a certain value, that cannot be overwritten, if the writers are producing other values they can be place somewehre else in the buffer. Not all values produced by the writers have to be stored, so at most, there will be one variable for the eache reader and one more value that's available for the writer. So, one safe bow in case the writer is higher priority than all the readers, number of readers + two (buffer size). If the writer is lower priority you need to account the unit delay plus 2. one way to size the buffer is the number of readers + 1. There's another sizing option

**Temporal Concurrency Control**

This another way to size buffers and based on:

The value will receive an index position in the buffer, this index cannot be reuse if it's being used by any one of the readers but when it's guaranteed this position is not used by any reader then it can be reused, so, a lifetime for this position can be computed.

the

lifetime: $I_{wr}= O_{wr} + max(R_{ri})$

$O_{wr}$ : Offset time between this point in time and activation time of any reader.

$max(R_{ri})$: Worst case time that takes to any reader to complete,

$I_{wr}$: lifetime for this value for anyone of the readers.

Check how many values the writers can produce inside a lifetime and that's the buffer size required. This is called circular buffer. Once the writers reach the last element of the buffer, in the next writing, the writer overwrites the first index (o-based indexation).

But this needs support by the OS at activation time, if the writer and the readers are periodic guaranteed.
