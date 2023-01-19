# OSEK

it's a Standard Operating System that is popular in the automotive industry. It's different than traditional OS. OSEK is static, meaning, all configuration system needs to be known before hand: number of threads, resources, semaphores and so on. No dynamic creation of objects or forking something or dynamically allocating something else.

Most of automotive system and embedded systems are static. no apps are created during execution, everything is known, and OSEK is attached to this.

it's a real-time system, OSEK Provides support for the implementation of mechanisms for real-tim, *immediate priority ceiling protocol*,

So, **what's a Immediate Priority Ceiling Protocol?** While using semaphores, there's the problem of *deadlock*. When trying to accesing a resource, and when this accessing is not working properly, the program can get locked for ever.
In real-time systems, it doesnt have to be locked for ever (this could be a meaningful long period of time). There's a a *special* type of semaphore allows to control how much time the waiting will be in a worst case scenario. so, a Immediate Priority Ceiling Sempahores are a way to achieve predictable deadlock.

## Conformance classes

there are 2 BCC (basic) and ECC (extended), and there are two variations inside each one, so. *ECC* allows the usage of events that sent from one thread to another who might be waiting for an event. This is called a synchronization mechanism.

**Resources** 
these are automaticalle protected by a semaphore, by just calling a function *getResource*, the invoked resource gets protected, same as doing a *wait* in a semaphore and *releaseResource*, same thing as doing *signal* on a mutex.

**Taks** are scheduled by priorities.

**Alarm** Alarms are special objects that are connected with a counter, the last is a variable that is increased by some mechanism, this is usually associated with a timer (a uC peripheral). some counters maybe connect to another harwdware *inputs*. i.e., in a combustion engine, a counter can be related by a revolution, half or quarter one of the engine shaft.
So, an Alarm is another OS object that is associated with a counter, in order to generate an event, execute a callback or activate a Task.

## -> Lab

**Software Architecture Profile**

- Create another profile named "SWArchitectureProfile", also enabling the *UML Profile Diagram*. Tasks or thread concept will be created in here.
- Import the *SysML* with the usual subprofiles.
- add a *block* in to the diagram.
- add a *Stereotype* and name it, "Thread".
- Add anothre *Stereotype* and name it, "OSEKTASK".
- Add another *Stereotype* and name it, "OSEKPeriodicTASK".
- The connect them with *generalization* button to top (*Block*).
- Add properties to the OSEKTAKS, "Priority" as *Int*.
- Add a property to the OSEKPeriodicTASK, "Period" as *Int*.

.................................................... **Physical Architecture of the System**

- Back to the "Elevator" model. under the *Model Explorer*/*Additional Resources* will be listed the profiles that have been created after importing *ExecutionPlatformComputationProfile*, *ExecutionPlatformCommunicationProfile* and, *SWArchitectureProfile*.
- On *Model Explorer*, select *SysMLmodel*. on the *Properties* window, select *Profile* and under the *Profile application*, click on the *plus* button.
- Add the *model.profile.uml* of *ExectionPlatformCommunicationProfile*, of *ExecutionPlatformComputationProfile* and, of *SWArchitecture*.
- Right click on "Platform" package and add a new BDD and name it, "ElevatorSystem", this diagram will be used to define the physical of the entire elevator system.
- Add a block to define the entire system and name it, "System".
- Add another block and name it, "ControllerBoard". This block will be associated using *DirectedComposition* and there's only one of it.
- Select the *ControllerBoard*, under *Properties*, select *Profile*, click on the *plus* button of the *Applied stereotypes* sections and add a *board* stereotype.
- Add another a couple of blocks, call the first block, and name them, "MotorCtrlBoard" and "CabinCtrlBoard". They are *DirectedComposition*-ed to the *System*. add *Board* profiles to these blocks as well.
- Inside *Platform* package, add a packaged and name it, "ControllerBoard". Inside this, there should be a block with the same name as the package. In this block add a *New BDD*, and name it, "ControllerBoardComponents".
- Add a *block* to the diagram and name it "micro", this is *DirectedComposition*-ed to the *ControllerBoard* block. and this *micro* block represets the concept of a *MicroController*. so, add its respective profile.
- Add another block and name it, "mainmemory", and it uses Memory *stereotype*. This is also *DirectedComposition*-ed to the *ControllerBoard*.
- Just below, *Platform* package, right click on the *System* block (on *model Explorer*) and add an IBD diagram, for Internal description of the system.
- drang-and-drop the *controllerboard* that is connected to *cabinctrlboard* through CAN bus. Add on port to each controller, and name them, "CAN1". link them with a *connector*. this *connector* represents a CAN bus, so it can be profiled as CAN bus. so properties such as *speed* can be set.

**Why are we doing this?**

for an end to end schedulability analysis, the involved messages and bus speed by navigatin this model. This model can be navigated from Java API or a language for code generation.

(**SIDE NOTE**) *things to know*

1. How to define a profile
2. How to use and apply a profile.
3. It doesnt matter how specific we have to be defining threads, canvas. (THIS IS NOT STANDARD).
4. Things have to be model, microcontroller, communication buses
5. *Profiles* are general and there are number of profiles like this domain specific extensions that have been unknowledge for general use. There are ready-to-use *UML* profiles for CORBA, testing and other purposes. There's a profile that is a mixture of *UML* and *SysML* named MARTE, that's oriented to *Embedded Systems*. MARTE is kinda dissapointing, the standard reference does not match with MARTE profile.

...........................................

**What if the similar *parts* or instances vary even slightly in the model, such as datalink distance?** in *SysML* parts can have multiplicity, so if there are 4 floors, there's no need of draw 4 *floorControllers*. Because the association is the one who has or holds the multiplicity. So in the *IBD* system, the *floorcontrollerboard* **part** or instance represents all 4 *ControllerBoards*. So, the connections buses between them are a generalization. 
Instead if a specific feature has to be modeled for each individual floor component, like, connection length. In that case, an individual part had to be added and tagged with the role it plays in the system, like, _0, _1, etc... also the multiplicity has to be 1 on the *association*. The associations need also to indicate the role it plays like ASSOCIATION_1.
Another asociation has to be draw from *System* block to *FoorCtrlBoard* and name it as ASSOCIATION_2, and so on.

- On *Model Explorer*, in the Platform package, there's the *system* block BDD, on it, create more associantions between the *system* block and the *FloorCtrlBoard* with multiplicity 1.
- Since all this controllers now will be connected to the same CANbus, it would be good to another block called "CAN Bus", profiled as *board*.
- And in the *Internal Block Diagram* of the system, drag the *CANbus* *part* from *Model Explorer*, and add a new standard *port* on the can bus part and link them using a single *connector* to the *CANbus* *part*.

**Thread Modeling**

- Into the mapping *package* create a new child *package* called "threads" and inside of it a new BDD diagram is being created called "threads" as well. In here all threads we use will be shown.
- Add a block *diagram* and name it "ControllerThread", this is *stereotype*-ed as *OSEKPeriodicTASK*, set the period in 200 ms. A bit more of precision will require to add where this thread will be running.
- Again, in the mapping *Package* create a new BDD call it "MappedSystem". and inside ot this add one block name "MappedSystem" as well. This creates a correspondance between a *Functional* system model and an *execution platform* system model.
- Rename the *System* model on *Functional* Package and *Platform* package by "FunctionalSystem" and "PlatformSystem" respectively. then drag them inside the BDD of mapping, as well as *ControllerThread*. all these guys are linked to the *MappedSystem* using *DirectedComposition* association.
- In the same *Mapping* *package*, create an *IBD* diagram, and the *controllerthread* instance. drag as well the *functionalsystem*. Inside this *part* drag the *elevator* from the *Functional* package / *FunctionalSystem* / *elevator*. and inside of this drag from Elevator *block* / *ownattributes* / *maincontroller*
- From the same Mapping package, create an IBD diagram, from *Platform package* / *ownedattribute* / *controllerboard*. with a *dependency* link the *controllerthread* and *maincontroller* are connected as well as the *controllerthread* and the *controllerboard*. name this *dependencies* links as "implements" and "executes" respectively. This looks redudant and it actually is.
