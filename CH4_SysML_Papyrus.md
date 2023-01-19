# # SysML and Papyrus

*LINK: [Lesson 2: SysML and Topcased/Papyrus: part A - YouTube](https://www.youtube.com/watch?v=1RR8yomqWjE&list=PLohWCZQ0wiEVpgTkxTsgSTnDvlz3OvphkP&index=2)*

## SysML as an OMG standard

SysML is a modeling language created by the OMG consortium, this is an open standard. **System Engineering** *SysML* was created to represent systems, this involves, the software, the electronics, the mecanics, the control plant. On the other hand, *UML* was built to model Object-Oriented software.

*SysML*, as *UML*, is a graphical (visual) modeling language. Even all these diagrams, including *Simulink*, look the same, they mean different things either in subtle ways or way too different. Because the models can be used in order to documeting things or in other cases, such as, *code generation* they mean the behaviour of the system.

in *SysML* and *UML*, the model is different and the views or diagrams are snapshots of specific elements of the model and their relationship. While in *Simulink* everything you are seeing is part of the model somewhere, this is called one-to-one correspondace between the model and the view.

in *SysML* and *UML*, the model is a tree (data structure), organized in a structural way with their respective relationships, this tree is more a graph.
This is considered a strength of *SysML* because you dont to represent everything in a view when the system is very large.

**Metamodel** set of rules that tell you the legal compositions for the elements, this tells us, if a model is feasible or not.

## Available diagrams

**Requirements Diagrams** **Behaviour Diagram**: How the system evolves in time, what are the systems' reactions. It has the following diagrams: *Activity*, State, Sequence and Use case

**Structure Diagram**: Relationship among the elements of the model. if a communication between two subsystem is required, then it's here where this communication has to be modeled as *structure diagram*, this communication end ports. but it's not stablished when or how the communication will be executed, because this is a behaviour.

In *UML* the core diagram is called the class diagram that's available from anywhere, while in *SysML*, this is called *Block Definition Diagram*. it describes the relationship among *blocks*. 
Again, in *UML* there exists the *Structure diagram*, in *SysML* this is called, *Internal Block Diagram*. It has to be only used in order to describe the internal structure of a *block* in *terms of its compoments* and the topology of communication among these components.
Both *Internal Block* and *Block* diagrams are gonna deal maily with block, which is an extensio of a *class* in *UML*.
Block is an element of the design, can be *anything*.

**Parametric Diagram** and **Requirement Diagrams** do not exist in *UML*.

## SysML v UML

in *UML*, there's the posibility to create profiles, *Stereotypes*. in *SysML* there's no modeling element for *CPU* or *Threads*, these Modeling tools are for generic description, not specific. 
in *UML* this is done by extending the concept of a class, called restricted class, meaning, the class is restrict to a certain type of description, *CPU* or *thread*.

### Requirement Diagram

It allow to place a requirement in its own box with certain properties, such as label (to item) and plain text. Two requirements can be connected, or/and design elements.
Documents can be generated out from *SysML*.
Keep in mind, the *SM* in *SysML* or *UML* are not runnable and the *SysML* tool and the *Standard* are two different things.

## SysML diagrams

Each *SysML* diagram is contained in a diagram frame, with headers, contents and Diagram description

## Papyrus

Make sure to set in *Eclipse* to *UML/SysML* perspective.

## -> LAB

- Let's start with *Block Definition* diagram.
- Three files are created, they are all *XML*: the model, the diagrams and information about wich diagrams are open currently.
- In the bottom left, the model tree is seen with the current diagram.
- We can operate on the *model tree* or in the *palette* (on the far right of the window).
- Create a child model, then a package, the package has names such as, the name, *Functtional*, *Platform*, and *Mapping*.
- The already created diagram is place inside the *Functional* package, and rename it as *System*.
- Inside functional, create a new *diagram*, a *block definition* one.

## An embedded Model

it is a composition of three sides, the *functional description*, the *execution platform* (hardware + OS + drivers + communication stack) and *mapping* (Semaphores, thread and executables).So, that's why three packages has been created in the *SysML* model.
The *functional* view is independent, has to be, the algorithm has to be *independent* from where the commands are coming or executed. Same thing with the *platform*, it has to be independent, for example, the communication protocol can change from CAN to Ethernet or viceversa. but *Mapping* tells how the *functional* and *platform* are linked togheter.

### Package diagram

it's like a folder, in a way to organize the model elements or can be seen as well as namespace.

Thses packages can be organized many ways or the best to adjust to your project: what they contain. structure, behavior.
 *Hierarchy* Logica design, physical design
 *IPT* purpose of the elements, what things are needed for the verification.

no matter your style of *packaging*, after the macro view, some *subpackages* can be create to describe the subsystem.

*SysML* is used to trace relationships, not to describe the physical behaviour, this can be a box.

a **block** has properties, operations, constraints, (not implemented in the tool) *allocation*, *requirements*

**Operations** is similar as *UML*, the operations that the block or class has.

**Constraint** compartment label.

**Values** is the same as *attributes* in object oriented programming, specifying its type, or either if they are public or private.

A *block* cannot be "built" by other *blocks*, but it might referencing to another *block*. In programming it's seen as a class that is independent but reference by pointer to this class.

The hierarchy can be built as deep as necessary.

### BDD - Block Defintion Diagram

**Generic Association** Simple relationship, two blocks cooperate in some way. The *association* can be named, additional names such as *Role* and *Multiplicity* can be added. *Role* means what role the involved blocks play in the relationship, and *Multiplicity* means, how many elements of certain *Role* are involved in the relatioship.

**Composition Association** represented by a filled diamon in the arrow, this is a children class, created from a father class, and it will be destroyed when the father class is destroyed. Talking at *block* leve, one *block* is created from a parent *block* and destroyed when the parent *block* is destroyed.

**Aggregation Association** is the class referencing to another class that exists independently. While this is *block* referencing.

**Generalization/Specialization** inherits everything from the parent *block* and it can override some.

### IBD - Internal Block Diagram

Defines the use of *Block* in a composition.

## ->LAB

- in the *Functional* package add a *SysML* child, *new block*.
- Rename this *block* as *System*.
- We're assuming it's a system elevator.
- Blocks can also be dragged and dropped from the *Palette* (ModelElements).
- Rename this as *Elevator*.
- on, *Associations* pick, *directComposition* and link *System block* and *Elevator block*, name this association *itsElevator*.
- Scrolling down, search for *multiplicity*, in *System* with *1* is enough and on *Elevator* side write 4.
- ***Keep in mind***: *Delete* means truly *delete* and *Hide* just, delete from view. at higher level the names are different for *Delete* and *Hide*, "Delete from *model*" and "Delete from *view*".
- Delete the *diagram* because everything is in *System* and already *associated* in the model.
- *Drag* and *drop* another *block* and call it *floorController*.
- *Drag* and *drop* another *block* and call it *mainController*.
- Associate with *directComposition* the *floorController* and the *System*. *Multiplicity* in the *floorControler*, *n*.
- Associate with *directComposition* the *mainController* and the *System* with *multiplicity*, 1:1.
- The *floorController* will call the *mainController* when the *elevator* is called. and the *mainController* close or open the door, as well as the *floorController* opens or closes the door.

## Port

*Standard Port* already existing in *UML*, it was meant to represent software, so, it is an interaction point. in OOP, this ports are used by using operation whithin an interface. *Flow Port* are a *SysML* concept, Things dont work in here by calling operation, values, signals, currents, water can be exchanged, whatever physical thing.

- from *PortAndFlows* in Palette, dran a *FlowPort* and placed in *floorController* and call it *Request*. in *SysML* properties, selects the direction as *Out*.
- Add another *FlowPort* and place in *mainController* and name it, "floorRequest", in *directions*, select it as *In*.
- These ports have to be typed. in *UML*, select *type*, select *additional resources*, *UML primivite types*

### Describing Internal Behaviour

_LINK: [Lesson 2: SysML and Papyrus, Part C - YouTube](https://www.youtube.com/watch?v=YcxYLinFZ3Y&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=3)

- in *model exploring* click, new *diagram*, new *internal block* diagram.
- Name it as *Elevator*. This diagrama already starts with a frame diagram. The *attributes* or *blocks* that are associated with the *Elevator* are already included in the *model explorer*.
- fomr Model explorer, *drag* and *drop* the *port*, in both, mainController and floorController.
- from *Edges* on the Palette, pick *connector* and link the two ports, and you can even name the connection.
- the *mainController* also have to dictate if the door is Locked or not.
- **The ports can be added graphically** in the *diagram* by *drag* and *drop*
- from the *palette*, section *Nodes*, drag and drop the *flowPort (IN)*, name it as *doorloock*, type it as *boolean*.

.......................

### Add types that arent listed - primitive types

- in the *model explorer*, right click, *import*, *register packages*. in here there are additional types.
  ...............................
- from the *palette*, drag and drop, *FlowPort (OUT)*, name it, DoorLockCmd, type it as boolean.
- in the *FloorController* package, create a new *Block Definition Diagram* and name it as *FloorControllerBB*. The purpose of this diagram is only to show the *FloorController* and its components.
- Drag and drop a *block* and name it as *FloorDoorController*. Drag and drop another *block* and name it as *ButtonLightController*.
- This two last *blocks* are associated to the *FloorController* as *DirectComposition*.
- Select *FloorController* block and add an *Internal Block Diagram* and name it *FloorController*.
- Bring the *FloorDoorController* and *ButtonLightController* inside the *FloorController* *Internal Block Diagram*.
- Add a *flowport* to the *FloorDoorController*, name it as *DoorLock* and type it as *boolean*.
- then Link the *input* port of the *FloorController* with a *connectior*, this is called a delegation, because the input coming on that port is handled by *FloorController*'s inner component.

..................................

### What if the port has to handle a *structure* type of data or *array*.

- Go to root, create a new *package* and name it, *Types*.
- Go inside *Types* package, create a new *Block Definition Diagra - BDD*, name it, *Types*.
- On *Palette* -> DataTypes, drag and drop *DataType* and name it, *Coord3D*.
- From *Palette* -> ModelElement, drag and drop *Property* and name it, *X*, and type it as *double*.
- Add another two *Properties* and name them, *Y*, and *Z*, as type, *double*. **This is for an structure_**.
- for **Enum**, drag and drop *DataTypes* -> *Enumeration*, name it as *SemapphoreTypes* (Not your typical *mutex* type).
- Drag and drop *EnumerationLiteral* and name, *RED*, *YELLOW*, and *GREEN*.
- for **Something else_**, drag and drop *PrimitiveType* and name it, *my32bitInteger*. **For arrays** go to the port itself and scroll down until you find *multiplicity*. (but this is not how you are supposed to do it.
  ..................................

*LINK: [Lesson 2: SysML and Papyrus, Part C - YouTube](https://www.youtube.com/watch?v=YcxYLinFZ3Y&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=4)*

## ->LAB

- Go to *System* diagram, and add one more *block*, name it, *MotorController*, Associate this *block* with the *Elevator* *block*.
- Still inside *Functional*, create a new *package*, called *MotroController*, name it as *MotorController*, the place the *MotorController* block inside its package and add a new *Block Definition Diagram* and name it, *MotorControllerBB* (MotorController Black Box).
- Add a new *FlowPort* and name it, *MotionCommand*, in the *Properties* window or tab, select *SysML* and in Direction, select *Input*.
- Add a new *FlowPort* and name it, *Speed*, type it as *Real*.
- in the *Types* *package*, rename *SemaphoreType* as *MotionCmdType*. rename the *EnumerationLiteral* as well, as: *UP*, *DOWN* or *STOP*.
- So go back to the model, where the *FlowPort* is listed, go to *types* and select *MotionCmdType*.
- ........................................
- go to *Functional* package again, add a new *Package* called *MainController*.
- in this package ad *Block Definition Diagram* named *MainControllerBB*.
- Drag and drob the *MainCtronller* block inside the *MainControllerBB*.
- Add a *FlowPort* named *MotorCmd*, which is gonna be an *output* port, and pick its type as *MotorCmdType*.
- Add another *FlowPort* named *MotorSpeed*, type it as *Real* and it's an *input* port.
- Go back to *Elevator* and drag and drop the *MotorController*, this will be imported with its own port.
- Add the ports of *MotorCmd* and *MotorSpeed* that has being just created for the *MainController* and connect them..

**Next step** is to extend the *SysML* language in order to describe those *SysML* port according to our *System*. So, a *domain extension* has to be created.

## -> Lab

- Create a new project and call it, *FunctionalPortProfile* and among the available languages, select *Profile*.

The goal is to create *Stereotypes*, a custome *domain* specific extensions. It's also possible to add our own types that define the *profile*. This is done by specifying a custome behaviour of a functional port.

- Drag and drop a *Stereotype* from *Palette/Classifiers* and name it, *FunctionalFlowPort*.

**What a Functional Flow Port does?** It's a custome *FlowPort*.

- on *Model Explorer*, Select *profile*, right click, *Import*, *Import Register Profile*, *SysML*.

For Papyrus, *SysML* is a profile in *UML*. That's why when creating a custom *FlowPort*, a *SysML* element, *SysML* has to be imported.

- *OK*, just select: *ModelElements*, *Blocks*, *PortAndFlows*. then click *OK*.
- from *Model Explorer* Window, drag and drop, *FlowPort*, on top of *FunctionalFlowPort* and linked them togheter using *Generatlzation* *Relationships*, found on *Palette*.

**What if we want to extend a (UML) Port?**

A port is a metaclass, so:

- On *Palette*/*Classifiers*, *Import Metaclass*, *Port*. In this case, there's no *generalization* relationship but *Extension* because it's coming from a *Metaclass*.

Let's go back to the *FunctionalFlowPort* block, and add a new *Porperty*, name it, *min* and, type it, *Real*. In order to use *Types* in this *profiling*, a package needs to be imported, as follows: on *Model Explorer*, *Import*, *Import Register Packages*, and select *JavaPrimitiveTypes* and *SysMLPrimitiveTypes*.

- Add also *max* and *validity_time* and type them as *Reals*.
- Rename the package, *FunctionalPortProfile* and save it.

This *mechanism* can be used also to define a custome *electronic board*, a *communication network* or a *CPU*.

**How is it imported in a project?**

- Open the project,
- on *Model Explorer*, *SysMLmodel*. right click, and select *Import*, *Import Package From Workspace*. and select your *package*.
- On *Properties* window, select *Profile* tab and click on the *plus* button. In this window, the custome package will be listed, and by deploying it you can your custom *profile* model (not the name of the port).

**How to use it?**

- Let's go to the *MainController* which has the two ports, select the *MotorSpeed* port and on the *Window* below, *Properties*, select the *Profile* tab, click on *plus* button and move from left to side the *FunctionalFlowPort*.
- by expanding this profile, all properties added can be seen and their respective values can be added.

**Why should we have custom elements or ports?**

1. Minimal and Maximum values are, as said, it's good information to extract. So, a document can be generated out of this description to generate a software specifcation.

(**SIDE NOTE**) Eclipse can translate this *UML*/*SysML* diagram into a text. and *Code* are just text, so under the *OMG*, a code generator is part of the *model-to-text* translator, *code* is just a special type of *text*.
2. This extension features can be used in *Code generation* as well.

**How would you use your code capabilites based on this definition?**

1. Simple way of extending nominal test that provides requirement coverage is boundary and robustness testing.
2. There's a price to pay, the number of tests grow, first, linearly and then grows exponentially. Huge numbers of test cases, but if we have a boundary conditions in the model, those test can be generate automatically (because it's also a text generator)

## Operations

Assuming the *MotorController* is a piece of software,

## ->LAB

- open the *MotorController* block
- From *Palette*/*ModelElements*, drag and drop an *Operation* on *operations* of the *Block* *MotorController*, name it, *MotorCmd*
- Scroll down and add *Owned parameters*. Name: *direction*, Direction: *in*, and type: *MotionCmdType* (custom one).

(*SIDE NOTE*) in order to see the operation in the block, it's important to bring the Ports inside the *block*.

- Keep adding *Owned Parameters*, this time, name it, *return*, Direction: *return* and type it as *boolean*.
  This is a classical way of how *OOP* was seeing until *interface* has arrived. so, an *interface* is to provide operations in a list as part of the *public* interface of the class. *interface* is a list of methods for which the class is to provide an implementation and identify a set of coherent methods by functionality. For example, *MotorController* may have a list of operations that are actually related with the motor operation, but another set of operations can be related to maintenance. It's a good practice to have these in two different interfaces for usability purposes. Another reason is: if someone is calling this *MotorCmd* operation (this isnt a single command, it's a list of operations), and if its indicated that another component in the system will use some of those operations, if they are left as operations, there are two ways to say those other components will need this operation, either **association** by usage of stereotype or in **behaviour diagram** where the sequence of operations is actually shown. The thrid method is somewhere in between, the operation are partioned according to the interface, so, it can be indicated that the remote component only requires those operations that are part of that interface. This can lead to a bad requirement of dependancy of re-use.

An **interface** is a type defintion, the package where this *type* is created depends on the level of re-use is desired. if it will be at *system* level then it has to bre create inside *Type* package.

## -> LAB

- on *Model Explore*, on *Type* package, add a new *BDD* named *interfaces*.
- from *Palette*, under *PortAndFlows*, drag and drop *Interface*, name it, *MotorOps*, as it were a *block*, an *interface* can have *properties* and *operations*.
- fomr *Palette*, under *ModelElements*, drag and drop *Operation*, call it, *MotorCmd*, as any other operation, *parameters* can be added, i.e.: *Direction* and *return*.
- ..............
- Let's go to the *MotorController*. A way to say the motor is providing some operations is by saying it's proving an implementation of the *interface* and this can be done by the usage of a *port*.
- Drag and drop a regular *port* and name it, *MotorOperations*, scroll down to *type* and from the package *Type* select *MotorOps*.
- Let's go the *Elevator*, main diagram. On *Model* window, under *MotorController*, look for the port that has just been created, *MotorOperations* and drag-and-drop into the *motorController* block in the diagram. Given the fact in our system, the *mainController* is the one will commad the *motor*.
- In the *MainController*, add a "regular" (*standard*) *port* that will be called *MotorClient*.
- By typing this port as *MotorOps*, it's saying that the *mainController* is providing the implementation of this interface, instead what's desired is that the *MainController* calls this implementation.
- .............
- Go to *Type* package, in the *interfaces* diagram, drag-and-drop another *block* and named it, *MotorClientIf*.
- On *Palette*, under *PortAndFlows*, drag-and-drop *usage* and associate it to *MotorOps* interface.
- Go back to *MainController*, select the port *MotorClient* and type it, as *MotorClientIf*, in the box next to this, **Required** interfaces list, it shows that *MotorOps* is required. This is tool based, on *Rhapsody*, the requirement is added direclty without the creation of another type.
- Go back to *Elevator*, drag-and-drop the *MotorClient* port and connect with *Connector*.

(**SIDE NOTE**) Everything is done with *Internal Diagrams* and *Definition Diagrams*.

## SysML Ports

As seen there are two types of ports, the *standard* ones and the *Flow* ones. The first one is operation oriented, for software description, ans for required or provided interface as well. On the other hand, the *FlowPorts* are used for signals and physical signals, like flow of water of flow of electrical current.

Both ports can be typed as *interfaces* or *blocks*.

- A *port* is a property, so it has a type.
  In other softwares when a *Port* is proving an interface is shown with an specific diagram.

### FlowPort with flow specification

An flow port can be *in* or *out* or *both*: *inout*, the last means that the port is undecided yet, or it can mean a complex structure of relation such as: RS232, which is a bunch of wires. so in this way a *flow* port can describe that inside the communication will be held in different directions, *duplex* or *simplex*.
A *flow* specification indicates a set of flows so over this port different flows are gonna occur. This type of port can be only connected to the same type of port and its direction has to be complementary

## Structure Diagrams

*LINK: [Lesson2 behavior - YouTube](https://www.youtube.com/watch?v=nBqOsobBQig&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=5)*

In this last part, Parametric Diagrams will be picked topic, as well as Activities, Sequence and State.

### Parametric Diagrams

These are used to express constraints between value properties. The parametric diagram is created and then associated to the input and output pins. This can be used for accelerations, velocities, breaking force. However this type of diagram is barely or never used. that ones studied are more than enough. In practice, *transformation* of diagrams is used in *SysML*.
While in *Simulink*, a similar behaviour can be expressed using diagrams, but the blocks are equations, keep in mind, equations are constraints as well, which make a "parametric" diagram into something executable, in real life, this type of diagrams arent executable neither simulator. Parametric Diagram is a type of structure diagram

## Behaviour Diagram

### Activity Diagram

Specifies a sequence of steps that transform a set of inputs into a set of output through a control sequence of actions. Similar to data flows but activies have additional features.
In *SysML*, there are two types of data flows: *streaming* and *nonstreaming*.

**Streaming Data Flows** All inputs and ports represent signals, functions or set values that progress over time, like in *Simulink*, where input ports don't represent *tokens*, they represent *signals*, so there's alwaysa a value wheever a block is triggered for its computation. This trigger can be any event, without waiting for a *token* availability.

**Nonstreaming Data Flows** The input and ports are *tokens*, single value items that are processed and produce another single value output, *queue*.

Each Action in *SysML* can be associated with a number of possible refinements. An action can be an instance of an operation behaviour, meaning the action is described in a general form, it can be a written sentence. **Formal definition of actions** so an action maybe a function signature
It's pretty much an operation, with input and output arguments (as return value).
In activity diagrams, the operations of the *blocks* can be organized and defined how these operations get togheter to produce outputs, the *how* is dictated by a **Control Flow** that allows the operations to go parallel or sequential.

*Tokens* are available on all the controll inputs and outputs.
An action can be represented hierarchical defined by another activity diagram, this way building hierarchical description of complex behaviours.

**Common Actions** 
Typical example of an event is a clock rising edge, so a periodic clock generates a train or sequence of events. 
Another example shaft positions.

### Notation

- *Fork* duplicates input tokens from its input flow.
- *Join* waits for an input token on **all** input flows and then places all on the outgoing flow.
- *Decision* waits for an input *token* on its input flow and places it on one outgoing flow based on guards.
- *Merge* waits for an input token on **any** input flows and then places it on the outgoing flow

### Input/Output streams

When set as *optional*, we dont need to wait until this activity has value ready, this is a signal, it's a continuos set of values. usually this a flow, water or current (it's a pin that can be sampled all the time).

## Sequence Diagrams (part of Behaviour Diagrams)

*Interaction* diagrams and they are seen as data flows or control flows, they are used to represent complex computations or behaviours at system or subsystem level thant it might involve cooperation and/or conditions of actions. These diagrams are similar to state diagrams.

(SIDE NOTE) everytime users wants more and more features, so at the end there's a significant overlap of significant capabilities.

**Sequence Diagrams** it's protocol oriented in order to fix something. This is not for complex combinations, but this are for linear protocols, to represent scenarios in a given order: startup or error handling or communication protocols.
How the objects in the system are cooperating with one another, actors such as operators, the customer can be added next to the objects. The interactions among objects are represented as set of messages that are exchanged horizontally and define how the control is flowing from object to object.

Actions are expressed in the vertical domain. i.e.: A message arrives requesting an operation, and as part of its execution another request has to be done. in here synchronous and asynchronous flow of control can be performed.
![[Pasted image 20220915180902.png]]

Another thing in here is the capability to define *time constraints* make it ideal for Real-Time System specification.
It's not limited to a single diagram or one time execution, subdiagrams can be deployed, even conditional executions can be added.

## State Machine

this defines the state of each individual object or subsystem in the model. While *Activity diagrams* are about the *Emerging* from cooperation of *more* operations no matter if those operations are in a same class object or different ones. *Sequence* diagrams are about cooperation of *different* objects. 
So, *State Machine diagrams* focus on a single object or subsystem. How this single subsystem will react to events and its state will change. so, it's about single reactions to events and the object's state.

the *End state* of an object means the object is *destroyed*.
An *State* description can be associated to the Entire system or to one block or to one subsystem or to one operation.

Let's assume the whole *Elevator* will be described:

**Creating States**

- On *Model Explorer*, block *Elevator*, right click, select *New Diagram*, new *StateMachine* diagram.Name this diagram as *ElevatorModes*.
- From *Palette*/*Nodes*, drag-and-drop *Initial* psudo state, and keep drag-and-drop-ing *states* according to the *Elevator*'s behaviour.
- From *Palette*/*Transition*, drag-and-drop *Transition* to link *states* and *nodes*.

**Creating super states**

- By drag-and-drop-ing from *Palette* a state inside another *state* it can create a *super state*.
- or by drag-and-drop-ing from *Model Explorer* states have been already created inside a *state* in the diagram, can make the *state* a *super state*.

**Setting-up Transitions**

- By selecting a *transition* it's possible to see its property such as: *Name*, *Trigger*, *Guard* and *Effect* (action that is performed when this transition takes place).
- By clicking on the *plus* button on *Trigger* section, it pops a window where the trigger that's been created will be set-up. Things like *Name* and *Event* to be linked to are required.

**Create Events**

- on *Model Explorer*, select *Functional* package and add *new SignalEvent*, name it, *StartupComplete_ElevAt0*. Singal it as under *Functional*. Name this Signal as *startupcomplete*.
- Back in the *State* diagram, with a *transition* element selected, by double clicking the *trigger* already created, in the *plus* button, select the Event created.

**Adding Guards**

- Under the *transition* properties, click on the *plus* button and name it, *current_on*.
- on *Constraint Element* section, click on the *plus* button and *OpaqueExpression*, name it, *current_on*.
- On the laguage section, click on the *plus* button, and select *Natural Language* and write as *body*, "the current is on, power is on".

**What can be fount inside a state?**

- it's possible to define the *entry*, *exit* and *do activity*.

## Requirements Diagrams

These are boxes with identifiers and texted lines to connect them together, this way defining relationships among them, derivation, refinement from high level to low lever. The most important thing in here is the capability to trace requirements to design objects, to activities, to state diagrams and shit.

*LINK: [Lesson 2: SysML - Profiles and stereotypes for platform and SW - YouTube](https://www.youtube.com/watch?v=s8CNB97sWOc&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=6)*

So, the controllers and system were the topic of interest and all of them are funtions, so far, the physiical architecture that is gonna support the execution of the *SysML* that has been done.

## Diagraming the physical architecture

The folowing tells things about how the physical architecture will be struct. At each floor there's a board that is connected to the elevator controller using sometype of *datalink*, a CANbus could be the one. There's another board inside the cabin that's also connected to the main *Elevator* controller through CANbus. and there's another board at the top that controls the electric motor.

## -> LAB

- on *Papyrus*, *File*, *New*, *Papyrus Projects*, name it, *ExectutionPlatformComputationProfile*, select *Profile* as Diagram Language.
- From *Palette*/*Classifiers*, drag-and-drop an *stereoptype*, name it *board*.
- In order to work with *SysML* features we need to impot *SysML* profile. (Already done previously but just in case, here it goes again):

**Import SysML profile**

- On *Model Explorer*, right click on *profile*, *Import*, *Import Registerd Profile*, *SysML*, and select: *ModelElements*, *Blocks*, *PortAndFlows*.

**To Make** ***Board*** **a special type of block**

- From *Model Explorer*, drag-and-drop *Board*, and connect them from *Board* to *Block* as a *generalization*.

There are several levels of how we can push this description, should the all other caracterics of board such as: type of microcontroller, the amount of memory, number of IO connections, speed of the microcontroller.
Addional stereotypes can be created, for example:

- *MicroController*, as a type of *block*.
- *Memory*, as a type of *block*.
- *NetAdapter*, as a type of *block*.
- *GenericIO*, as a type of block.

*Enumerations* to be added:

- *MemoryType*
  
  - *RAM* (Enumeration Literal).
  - *ROM* (Enumeratio Literal).

- Into the *StereoTypes* Block for "Memory", add *Properties*: "size" and "type", and type them "Int" and "MemoryType".

- Add to the "MicroController" type, the following properties, "Maker", "model" as *String* and, "speed" as *Integer*.

- Add another *Enumeration*, name it, "MicroMakerType", and add *EnumerationLiterals* and name them as, "ARM", "Toshiba", "Microchip".

- Back into "MicroController", under the property "Maker", type it as, *MicroMakerType*.

- Save the Profile.

**Execution Platform Comm Profile**

- Create a new papyrus project and name it "ExecutionPlatformCommunicationProfile".

- Click on next and select *UML Profile Diagram* (check this always when creating a profile).

- Create a *Stereotype* named "SerialLink", this has to be associated to point-to-point connections or broadcast networks.
  (**SIDE NOTE**) for a point-to-point, it could be good to use a connector, instead for a network, it's better to use a *block*, because a network is a complex communication system.

- Import *SysML* (the classical subprofiles).

- From *Palette*/*Classifiers*, *Import Metaclass* and selecta *Connector.*

- So this "SerialLink" can be an extension of *Connector* or a generalization of *Block*.

- To this "SerialLink" add a property, and name it, "speed".

- Add different *Stereotypes* and name them, "Ethernet" and, "CAN bus". These two are *Generalization* associated with "SerialLink".

As part of the *ExecutionPlatform*, the followings also have to be added:

- Operating System
- Device Drivers
- Communication Stack
- Middleware
