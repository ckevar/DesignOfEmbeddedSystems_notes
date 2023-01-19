# SysML and Papyrus

*LINK: https://www.youtube.com/watch?v=1RR8yomqWjE&list=PLohWCZQ0wiEVpgTkxTsgSTnDvlz3OvphkP&index=2*

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

_LINK: https://www.youtube.com/watch?v=YcxYLinFZ3Y&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=3

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

*LINK: https://www.youtube.com/watch?v=YcxYLinFZ3Y&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=4*

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

*LINK: https://www.youtube.com/watch?v=nBqOsobBQig&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=5*

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

*LINK: https://www.youtube.com/watch?v=s8CNB97sWOc&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=6*

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

- Middleware# Intro and Requirements
  
  *LINK: [lesson 1: Intro and Requirements - YouTube](https://www.youtube.com/watch?v=Iqc-n6bbGZA&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=1)*
  
  ## Embedded systems
  
  Special-purpose computer system designed to perform one or a few dedicated functions, sometimes with real-time computing constraints.
  
  It's also important the model of the physical process (in order to predict the computer behaviour).
  
  Modern language have Predictable timing or a way to handle timing. Old languages such as C or Java (these are general purpose programming languages) does not provide time handling, some libraries were developed later on for such purposes.
  
  ## V-shape development cycle V-model
  
  **User requirements** As close to the user language **Functional specifications** **Functional modeling**
  
      The system is modeled using models and parameters of the enviroment.
  
  **Architecture Exploration**     Defines the architecture that supports the execution of this functionality, such as (microncontroller architecture, peripherals, where the microncontrollers are gonna be purchased from).
  
      Also it defines the *functionality* over the architecture, where and when the functions will be executed.
  
  **Component Modeling** Design the component, model the **behaviour inside them** and then **implement** (*Code*) the components either harware or software, accordingly.
  
  **Validation** The user confirms the software functionality.
  
  V-model_ allows tracing errors at early stage because the test statements and conditions are written at each level of the development.
  
  # Models
  
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
  
  ## REQUIREMENT ANALYSIS
  
  Requirements are linked directly with *validation* because that's what the user wants or expects.
  
  1. Good requirements avoid inconsistencies and redundancies.
  2. Good requirements tell what the problem is, not the solution.
  3. Good requirements tell what the system is supposed to do.
  4. Requirements are (supossely) the starting pointing of the development.
  5. Even when the project is built by small cycles (meaning prototypes) in each cycle the set of requirements has to be set.
  6. Requirments are generated and coordinated by/with marketing staff, productt specialists and other analysts.
  7. Requirements are natural language, therefore, they are unconsistent and misunderstood.
  8. The current problem in the industry lays on *How to write* proper requirements or *how to extract* them from the users' speech.
  9. It starts with **Requirments Elicitation state**, where the user or stakeholders tells or is being asked what the requirements are.
  10. *Z* language is the *formal* languge to write requirements.
  11. *FSM, ATL* also can be used to write requirments. But in reality *FSM* and *ATL* are not good to write requirements because they are not general language.
  
  ### How to write requirements
  
  1. We can start by enumerating the *working* modes or *states* of the system. From airplanes to lifts, they all have states or working modes, so *start* by breaking down the *working mode* and work in each *working mode* and the *information* the system handles if the system or subsystem is a storage data or retriever data. the last obviously won't work for controll based systems.
  2. Then take into account cases of the system and the actors, humans or operatators and external events in the environment (temperature, pressure).
  3. Write those working modes in a style of *FSM* description.
  4. Ease definitions of requirenment-driven test cases, to implement SysML.
  
  ### REQUIREMENT ANALYSIS - CONTROLLER-CONTROLLED MODEL
  
  In embedded system we have two sides: the system that will control and the enviroment that will be controlled. On the *controller side* we will found *constraits* of the system and, on the *plant side* we will get something called the *assumptions*.
  Each requirement should be written as a pair or a contract, a *constrait* given and an *assumption*, for example:
   **The controller of the boiler should always make sure that the temperature is between +/-1 away from the desired temperature.** This requirement is missing the *assumption*, it's assumed the *Boiler is full of water, the sensors are working correctly, enough sensors are installed in the region of interest*. Each requirement has two components, the *assertion*, what the controller must provide based on the *assumption* of the system. Some *assumptions* should be part of the requirements and some are *forced* to be.
  
  The structure *assumes* we have identified a section for our system that is already partioned. For every single macro subsystem:
  
  1. Identify the working modes and,
  
  2. Then refine those things.
  
  3. Some reactions aren't isolated in a single subsystem but organized in a protocol escenario. This reaction is called *sequence* diagram in *UML* and *interaction* diagram on *SysML*.
     
     So, the requirements will operate in two modes, at system level and subsystem level: inputs_, *outputs*, *characteristics* and *parameters*.
  
  **Itemized requirements** are more difficult to read but they are more accurate and easy to test or write tests for.
  
  ### Unnecesary description
  
  1. What the system doesn't do
  2. Description of things when the system does not react. If it is a safety requirement, then it's ok, otherwise it's unnecesary.
  3. Don't change or switch back and forth between the working mode names.
  4. If a system has multiple things of the same specie then they have to be named in sequency, but there have to be consistent across the whole desription without changing over time or over the whole description.
  
  ## Type of Requirements
  
  The requirements can be **User requirements**
  
      What the user expects the system does **Functional requirments**    
  
      For mechanisms and procedures needed to achieve the user requirements. timing included. **Safety requirements**    
  
      Possible failure conditions and hazards, based on *assumptions*. **Diagnostic Requirements**
  
      On/off-board diagnostics required. **Para-functional or non-functional Requierements** 
  Features that can be measured: usability, scalability and speed.
  
  In order to complement the requirements some diagrams are needed that will be mentioned later.
  
  *itemization* of requirements is important, to clearly identify them and trace them when tested. 
  A formal repository has to be used to store the variables and parameters (including buttons).
  
  **What's a good test?** To check all the requirements. This is called *functional* test or *requirement* oriented test or *black box* test. Every single requirement has to be test at least once.
  
  *White* box or *structural* test is as well as important as the black box, but it'll be touched later.
  
  ### Ariane Case
  
  It used a software built for the previous version of the rocket, *Ariane 4*, wich had a narrow inclination, but *Ariana 5* was supposed to exceed those values and eventually it happened.
  
  #### Mars Polar Lander Case
  
  Nobody knows what actually happened. A premature shutdown of the engine? or the computer?, the legs deployment didnt happend because the engine shutdown before. There was a requirement untested.
  
  Long list of requirements are difficult to test, and all test conditions have to be written from the begining.
  
  Sometimes when a requirement isnt clear by reading the test, the requirement can be clarify, that's why it's important to write test from the begining.
  
  When writing requirements, some keywords has to be used such as:
   **shall** used in an *assertion*, a promise from the *system* **must** used in for *asumptions*,
   **will** based on the law of physics.
   **should** not required, an optional requirement. *Negative* requirements shall not be written. in safety reasons it can be used, but try to write its complementary positive. A *Negative* requirement means that the system can be in any state or the variable values can be anything, for example if the value is *not* 1 then it could be anything, so the range of values become wide
  
  Requirements shall only stated for *outbound* state transition. For example, *if the temperature sensors break, go to error mode* (this is an outgoing transition) but it's not well to write it again as an *incoming* transition (in general, try to avoid *incoming*), *The error mode occurs when the temperature sensors break*.
  
  This will lead to inconsistency when updating, because, it might happen the case the first requirement is updated and the second no, so, it pops an inconsistency.
  
  ### Styles of writing the requirements
  
  1. there's an assertion and an assumption.
  2. Preconditions/postconditions/invariants
     - Define all properties that are true before the reaction occurs, all the conditions that are true after the behaviour occur. and *invariants* that are not either true or not after the reaction.
  
  ## Data Dictionary
  
  Define the subsystems, define the inputs and outputs, this are formally defined as a model and it's called data dictionary. 
  each input and output needs an identification, a formal name, a description, event association, data type, the range of values accepted, time association (freshness requirement) or update rate, units.
  
  After the develpoing this, we can start writing the itemization of the requirements and remember to use the formal name you gave to the inputs and outputs (otherwise you could get missed or confused). So, *itemization* should be written like this: *Entering mode* -> *While in mode* -> *Exit from mode*.
  
  ## Further Notes
  
  **Ask yourself the following** *what are possible error conditions in a given state, at, in or leaving?*
  
  **Avoid writing** this words, normal, appropiate, suitable or nominal conditions.
  
  **Write** explicitly what to check, when to check, where to check and how to check, what makes it a check.
  
  **Fixed numbers** on a requirement are never allowed, they have to be whithin a range, at least if it were boolean.
  
  Requirments and Test have to be linked not just abstractly but as well in the written documentation. Also they have to be linked along down the *v-shape*. **and why do we do that?** In this way if after sometime a certain requirement has change or a test has been modified, we know what other requirements are affected by that change. So, we keep *track* of all the relations among them.
  
  ## Formal Language
  
  a formal language allows to test in an automatic way. Tests can be written from the *itemized* requirements, which gives *itemized* tests, these aren't test one by one, these are test in a bank test.
  
  .............................................................................................................
  
  # SysML and Papyrus
  
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
  
  *

# OSEK

it's a Standard Operating System that is popular in the automotive industry. It's different than traditional OS. OSEK is static, meaning, all configuration system needs to be known before hand: number of threads, resources, semaphores and so on. No dynamic creation of objects or forking something or dynamically allocating something else. 

Most of automotive system and embedded systems are static. no apps are created during execution, everything is known, and OSEK is attached to this.

it's a real-time system, OSEK Provides support for the implementation of mechanisms for real-tim, _immediate priority ceiling protocol_,

So, __what's a Immediate Priority Ceiling Protocol?__
While using semaphores, there's the problem of _deadlock_. When trying to accesing a resource, and when this accessing is not working properly, the program can get locked for ever.
In real-time systems, it doesnt have to be locked for ever (this could be a meaningful long period of time). There's a a _special_ type of semaphore allows to control how much time the waiting will be in a worst case scenario. so, a Immediate Priority Ceiling Sempahores are a way to achieve predictable deadlock.

## Conformance classes

there are 2 BCC (basic) and ECC (extended), and there are two variations inside each one, so. _ECC_ allows the usage of events that sent from one thread to another who might be waiting for an event. This is called a synchronization mechanism.

__Resources__ 
these are automaticalle protected by a semaphore, by just calling a function _getResource_, the invoked resource gets protected, same as doing a _wait_ in a semaphore and _releaseResource_, same thing as doing _signal_ on a mutex.

__Taks__ are scheduled by priorities.

__Alarm__
Alarms are special objects that are connected with a counter, the last is a variable that is increased by some mechanism, this is usually associated with a timer (a uC peripheral). some counters maybe connect to another harwdware _inputs_. i.e., in a combustion engine, a counter can be related by a revolution, half or quarter one of the engine shaft.
So, an Alarm is another OS object that is associated with a counter, in order to generate an event, execute a callback or activate a Task.

## -> Lab

__Software Architecture Profile__

- Create another profile named "SWArchitectureProfile", also enabling the _UML Profile Diagram_. Tasks or thread concept will be created in here.
- Import the _SysML_ with the usual subprofiles.
- add a _block_ in to the diagram.
- add a _Stereotype_ and name it, "Thread".
- Add anothre _Stereotype_ and name it, "OSEKTASK".
- Add another _Stereotype_ and name it, "OSEKPeriodicTASK".
- The connect them with _generalization_ button to top (_Block_).
- Add properties to the OSEKTAKS, "Priority" as _Int_.
- Add a property to the OSEKPeriodicTASK, "Period" as _Int_.

....................................................
__Physical Architecture of the System__

- Back to the "Elevator" model. under the _Model Explorer_/_Additional Resources_ will be listed the profiles that have been created after importing _ExecutionPlatformComputationProfile_, _ExecutionPlatformCommunicationProfile_ and, _SWArchitectureProfile_.
- On _Model Explorer_, select _SysMLmodel_. on the _Properties_ window, select _Profile_ and under the _Profile application_, click on the _plus_ button. 
- Add the _model.profile.uml_ of _ExectionPlatformCommunicationProfile_, of  _ExecutionPlatformComputationProfile_ and, of _SWArchitecture_.
- Right click on "Platform" package and add a new BDD and name it, "ElevatorSystem", this diagram will be used to define the physical of the entire elevator system.
- Add a block to define the entire system and name it, "System".
- Add another block and name it, "ControllerBoard". This block will be associated using _DirectedComposition_ and there's only one of it.
- Select the _ControllerBoard_, under _Properties_, select _Profile_, click on the _plus_ button of the _Applied stereotypes_ sections and add a _board_ stereotype.
- Add another a couple of blocks, call the first block, and name them, "MotorCtrlBoard" and "CabinCtrlBoard". They are _DirectedComposition_-ed to the _System_. add _Board_ profiles to these blocks as well.
- Inside _Platform_ package, add a packaged and name it, "ControllerBoard". Inside this, there should be a block with the same name as the package. In this block add a _New BDD_, and name it, "ControllerBoardComponents".
- Add a _block_ to the diagram and name it "micro", this is _DirectedComposition_-ed to the _ControllerBoard_ block. and this _micro_ block represets the concept of a _MicroController_. so, add its respective profile.
- Add another block and name it, "mainmemory", and it uses Memory _stereotype_. This is also _DirectedComposition_-ed to the _ControllerBoard_.
- Just below, _Platform_ package, right click on the _System_ block (on _model Explorer_) and add an IBD diagram, for Internal description of the system.
- drang-and-drop the _controllerboard_ that is connected to _cabinctrlboard_ through CAN bus. Add on port to each controller, and name them, "CAN1". link them with a _connector_. this _connector_  represents a CAN bus, so it can be profiled as CAN bus. so properties such as _speed_ can be set.

__Why are we doing this?__

for an end to end schedulability analysis, the involved messages and bus speed by navigatin this model. This model can be navigated from Java API or a language for code generation.

(__SIDE NOTE__) _things to know_

1. How to define a profile
2. How to use and apply a profile.
3. It doesnt matter how specific we have to be defining threads, canvas. (THIS IS NOT STANDARD).
4. Things have to be model, microcontroller, communication buses 
5. _Profiles_ are general and there are number of profiles like this domain specific extensions that have been unknowledge for general use. There are ready-to-use _UML_  profiles for CORBA, testing and other purposes. There's a profile that is a mixture of _UML_ and _SysML_ named MARTE, that's oriented to _Embedded Systems_. MARTE is kinda dissapointing, the standard reference does not match with MARTE profile.

...........................................

__What if the similar _parts_ or instances vary even slightly in the model, such as datalink distance?__
in _SysML_ parts can have multiplicity, so if there are 4 floors, there's no need of draw 4 _floorControllers_. Because the association is the one who has or holds the multiplicity. So in the _IBD_ system, the _floorcontrollerboard_ __part__ or instance represents all 4 _ControllerBoards_. So, the connections buses between them are a generalization. 
Instead if a specific feature has to be modeled for each individual floor component, like, connection length. In that case, an individual part had to be added and tagged with the role it plays in the system, like, \_0, \_1, etc... also the multiplicity has to be 1 on the _association_. The associations need also to indicate the role it plays like ASSOCIATION_1.
Another asociation has to be draw from _System_ block to _FoorCtrlBoard_ and name it as ASSOCIATION_2, and so on. 

- On _Model Explorer_, in the Platform package, there's the _system_ block BDD, on it, create more associantions between the _system_ block and the _FloorCtrlBoard_ with multiplicity 1. 
- Since all this controllers now will be connected to the same CANbus, it would be good to another block called "CAN Bus", profiled as _board_.
- And in the _Internal Block Diagram_ of the system, drag the _CANbus_ _part_ from _Model Explorer_, and add a new standard _port_ on the can bus part and link them using a single _connector_ to the _CANbus_ _part_.

__Thread Modeling__

- Into the mapping _package_ create a new child _package_ called "threads" and inside of it a new BDD diagram is being created called "threads" as well. In here all threads we use will be shown.
- Add a block _diagram_ and name it "ControllerThread", this is _stereotype_-ed as _OSEKPeriodicTASK_, set the period in 200 ms. A bit more of precision will require to add where this thread will be running.
- Again, in the mapping _Package_ create a new BDD call it "MappedSystem". and inside ot this add one block name "MappedSystem" as well. This creates a correspondance between a _Functional_ system model and an _execution platform_ system model. 
- Rename the _System_ model on _Functional_ Package and _Platform_ package by "FunctionalSystem" and "PlatformSystem" respectively. then drag them inside  the BDD of mapping, as well as _ControllerThread_. all these guys are linked to the _MappedSystem_ using _DirectedComposition_ association.
- In the same _Mapping_ _package_, create an _IBD_ diagram, and the _controllerthread_ instance. drag as well the _functionalsystem_. Inside this _part_ drag the _elevator_ from the _Functional_ package / _FunctionalSystem_ / _elevator_. and inside of this drag from Elevator _block_ / _ownattributes_ / _maincontroller_
- From the same Mapping package, create an IBD diagram, from _Platform package_ / _ownedattribute_ / _controllerboard_.  with a _dependency_ link the _controllerthread_ and _maincontroller_ are connected as well as the _controllerthread_ and the _controllerboard_. name this _dependencies_ links as "implements" and "executes" respectively. This looks redudant and it actually is.

# Testing

_LINK: https://www.youtube.com/watch?v=jhKd3FJM5Cc&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=8_

In the v-model we have left and right side, the left side is refinement and development, right side is verification and testing. Tests should be planned from early in the development, as the requirments are defined the test should be too.

## Functional testing

or black-box testing, turning it into implementation independent. the inputs and outputs are knows as well as the expected properties of the outputs because it was written at requirement definition, what is unknown is what the internal algorithm does, not even the internal structure.
This type of testing is usually used at system level testing, subsystems, unit testing or for individual components.

It's also a requirement-driven testing, so when talking about _coverage_, it's about covering or meeting the requirement, and expected to have 100% coverage, meaning each single requirement has to be checked with the test. The quality of the test can be improved by laveraging information about the function that needs to be performed inside. 

A _functional_ testing leads to _structural_ testing. 

### Functional testing

We are gonna assume our program is a function with a given domain of inputs and output variables.
so, it can be represented as a function that takes one input variable from the domain space of interest.
Of course the _inputs_ can be represented in a plane xy. the functions operates within a given range of the input variable which huge amount of values between the maximum and the minimum, in this way, it's impossible to test all possible values, because the set of input values is the muplication between all possible input values times all possible input values., in this case the picked values are only the maximums and minimums of each input variable. 

### Nominal testing

Given an input domain, a set of values are picked that fall within domain space. This is what is typically done, and if on nominal test is run for each requirement, requirement might be fully covered. Keep in mind, it's not advisable to test a complex function with single input values. because the fact it works correct for a small set does not mean it works for well for all possible values.

Random picking from the domain is not effective, it could be a billion of possible values. by picking  1 or 100 values doesnt make any big change making the coverage rediculously slow. So instead of random picking, it's better to pick the significant ones, at the extreme points., boundary.

### Boundary Testing

This type of testing requires 2 assumptions:

1. the domain consists of independent values, meaning no correlation between the values of the inputs (which is not true).
2. All input values are continuos values, this is a relaxed assumption.
   The concept of testing near the extreme points is a stress testing, it's related to mechanical components testing.

For boundary testing, first, a nominal test is picked, the inputs _a_ and _b_ and a something that is in the middle. (nominal case is needed). All points are kept in their nominal values but one. pick 4 more values, two that are right at the boundary, near to the max and min within the range. making $4n + 1$ number of test-cases. 

Always assume that the inputs are independent of each other.

The number of tests is growing linearnly according to the number of input variables.

if we werent given any boundary requirements, we can take as boundaries the machine boundaries or the type-based boundaries (bits length of the type).

Sometimes boundary values and nominal values are the same (most cases). For booleans, doesnt make sense to do this boundary testing.
Sometimes boundary testing is not a good fit, because the specifications might split the range into chuncks (subdomains). So Boundary testing can be applied not over the overall range but the range of the small groups. and the convination among the subdamains within the input variables, this can lead to an even finer partition of the domain.

### Robustness Boundary Value testing

Sometimes, it isnt enough to test the values over the edge of the range and within it, but outside of it (__Arianne Case__). This type of tests are used when a system is dealing with a physical enviroment. It's quite common to see to put a "filter" when someone types on a keyboard the incorrect number and the system pop "INCORRECT NUMBER" than having a system that limits, for example, there's no filter to bound the input temperature.

The same assumptions have to be kept for this test as well, the inputs have to be independent, making the $6n + 1$ test-cases.

### Worst-case BV testing

By dropping the assumption that input variables have to be independent but instead they are the combination of a set of input variables in boundary conditions, this is where the number of cases blows, $5^n$ test-cases, nominal values and boundary condition values. 

(__SIDE NOTE__) typical amount of requirements is from hundreds to thousands. i.e, a 300 requirements might have around 140 input variables. not all input variables apply to all requirements.

### Worst-case + Robustness testing

It's a combination among worst case and robustness BV testing. All combinations of 7 values for all variables, making $7^n$ test-cases.

### Equivalence Classes (Weak)

__Is there any way we can leverage the fact the input domain is composed with subdomains?__
Things like age, salary and, sex can be regrouped in order to have a __weak coverage__ of the input regions with at least 1 input nominal value test for every  input variable in one of the subranges, meaning one possible test for each possible interval.
_Test cases_ the maximum of the number of regions for every possible input variable $max(n,m)$ where
$n$  is the number of regios for $i_1$ and m is the ranges.

### Equivalence classes (Strong)

For this test, one nominal test for subregion is required. so the number of test-cases become the product of subranges times the input variables: 
$\prod_X(\sum_X)$ this is a quantity that grows fast as well.

### Weak Robust EC

It isnt enough with at least one test for input variable but it's needed one test below the minimum and one test above the maximum per each input variable.

### Strong Robust EC

Beyond the fact that there's one test for each region, it's also required to have a test case below the minimun of each subrange of each input variable. becoming this way $\prod_X(|\sum_X| + 2)$  test-cases.

### Combination

All tecniques can be combined such as:

- Robust WCT + Robust EC
- Strong EC + Robust BV: $\prod_X4(|\sum_X|+1)$ test-cases. but it's too big for an actual real-life program. in a 5 variables with 5 partitions, the number of tests are 8 millions, which can lead to 3 months of testing if 1 sec is spent per test.

## Structural testing

Or white-box testing. Assume a piece of software needs to be developed based on given specifications followed by another software that is run in the functions, and now we have a program.
Structural test says that everysingle written code has to be executed at least once, this is one criteria for structural coverage. Other criterias can be defined: condition coverage, decision coverage and the mix of both..

__Why do we need structural testing__?

1. When functional testings is performed even at 100% coverage, it only covers a very small input space. Assuming it's needed to write a function that computes the two roots of a second degree function if they exist given _a. b_ and, _c_. of course picking all possible values is impossible, it should be taken only a small portion of them.
2. No matter how good the process is, the requirements almost invariable are not gonna meet and arent often going to be up to date with respect to the code, meaning the code is implementing something that is not in the requirements, this could have two reasons, either that requirement was forgotten or the requirement hasnt been updated after another requirement needed to be covered that has just implemented. That's why some sections of the code are never executed when testing exisiting requirements, and the code is executing extra requirements that weren written in the requirements document, so it was never planned.
3. In the code, there still exist some functionality that is not written in the requirement and that is not meant to be written in it. This is called unintendent functionality

__How to solve those issues?__ 
(respectively)

1. Check the code and try to understand why some parts aren't being executed and later write that requirement in the requirements document.
2. Everytime that structural testinng is performed and the outputs are not part of the original test plan, it has to be studied why it happens.

In the Aeronatics safety-critical system software, a criteria called MC/DC - _Modified Decision Condition Coverage_ - coverage is performed. and Unless the system doesn't reach 100% coverage the system is not gonna be certified.

## Conformance Testing

As times pass by, this testing is being lost.
This test is about the implementation of the model being conformant to the model. like the _SM_ and _SM_ implementation, either implemented by an automatic code generator or written by hand. 
In many ways, the conformance testing is similar to structural testing because the internals of the system has to be known.

# Simulink Intro

_Link: https://www.youtube.com/watch?v=-8CaGKwRLzQ&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=9_

## -> Lab

- This lab is pretty much built over something that the professor already have.
- In _Simulink_, the blocks are different from what they are in _SysML_, it's called _S-Function_. 
  (__SIDE NOTE__) __S-Function__ is a custom block with a special behaviour.
  This lab's goal is to built a stopwatch that consists of two parts (that will end up in three parts, actually):
- _First part_: the plant, just a front end (no physicis here). Already provided.
- _Second part_: the controller part, that's split into two parts:
  - State of the Stopwatch
  - Managing the condition of the inputs
      This has to be provide by us. How to controll the display of the digits, a mechanism has to be added to translated the _SM_ output, such as: hours, minutes and seconds, tens of a second and, blinking.
  - _Third part_: set of blocks that are required at code generation time to manage the actual IO.

## -> Lab (again)

- by double clicking a susbsystem block it opens its content. The inputs can be: Hours, Minutes and, Seconds, tenths, mode, blinking.  The outputs can be: Row1 and Row2. This subsystem will be named "Row_encoding".
- _Counter Limited_ block will count to 23 for hours, 59 for minutes and seconds and to 99 for tenths of a second.
- "-1" sample time means... Each and everyblock is associated with a sample time, time which the block needs to be evaluated. Discrete Time blocks are usually periodic and that's sample time, but "-1" means inherited from the succesor and if it doesnt have one then it is useless but it means that it will produce the output whenever the consumer needs data. 
- A _Math Function_ block is a generic mathematical function that can be used any several function, such as: _exp_, _log_, _log10_, *__mod__*, etc.
- A _Mux_ is something that is gonna compose a set of single scalars and creates an array out of them. A _Mux_ can also compose array of arrays.
- By right-clicking on the block, the _Format_, _Flip Block_, it flips the selected block.

_Link: https://youtu.be/WGuB5_vwGDs__ ____

## Model Implementation: multi-task

The communication variables need to be protected whenever there's a multi-task system that shares these variables among the task, these variables should be preserved or at least they should have a deterministic behaviour.
    On _Simulink_, the commercial code generator, there's a block that can handle this type of problem and it's called _Rate Transition Blocks_. This block can be added explicitly by the user or the code generation code can add this and other needed blocks in an implicit way (not nice Matlab!). 

__What are Rate Transition Blocks?__
This blocks are need in case, preemption is needed among task executions. These tasks might implement the reader part and the writer part in two different task, if not, and if they dont preempt each other, then, there's no problem.

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

__Mechanism that is provided by the commercial code generator__

1. _First case:_ High-rate high-priority writer communicating with a low-rate low-priority reader.
   
   - the high rate writer has a period 1 and the low rate reader has period 2. 
   - The Reader's goal is to use the first set of values that are produced by the writere.
   - Mechanism needed is to keep constant the values for the period of the reader. This is what the Rate Transition block is providing, it's only a sampling mechanism. This doesnt have a sate, only a set of outputs and the evaluation rule. This block has the _period_ of the reader but the task and the _evaluation order_ of the writer. So the output update of the Rate Transition block is executed in the same task of the writer right after the writer instance and then executed again with the period of the reader. It's a mechanism that does not need anything from the operating system. It's all code that is executed within the task at application level. it's very simple, simple copies inputs and outputs, it has a small overiding in terms of memory, small or large mostly depends what is being transfered from writer to reader. 

2. _Second Case_: Low-rate low-priority writer communicating with a high-rate high-priority reader.
    According to rate monotonic, high-rate high-priority is gonna be executed before low-rate. So the order of executions are being violated, in this case, the _Rate Transition_ Block for Low-rate to high-rate behaves as a delay, and as any other delay it has a state, so this block has a state update and an output of data port. The values that are produced by the execution of the writer in the previous cycle and then at the first execution of the reader in the following cycle is going to update its output and keep them constant for all the readers in the following writer's cycle. The state update part is executed in the context of the low priority writer task after the writer block and there's an output update that is executed in the context of the high rate task before the implementation of the reader block, sampling the values here and keep them constant. The behaviour is the same as the delay of one cycle of the low rate. ___What's the cost?___:
   
   1. Twice the memory cost (state and output variable)
   2. Additional delay. Delays arent terrible things, but if they are deterministic, they can be considered in the control law as well as in the formal verification and validation of safetyness and a compensation can be added, but no-delay would be better.

The Rate Transition block is included here:
![[Pasted image 20221005154029.png]]

Because we want this to be Rate Monotonic. And it makes sense to go Rate Monotonic because it makes more efficent the scheduling 

__Limitations of Rate Transition__
Keep in mind its advantage, it is implemented at application level and the limitations are:

1. Rate of the comunicating blocks need to be harmonic, otherwise things get complicated or dis-messaged.
2. The  best option for multicore systems is doing it by hand, so the Rate Transition Block for this type of hardware isnt enough.

In the current literature there are many solutions to deal the first problem, either when the communication blocks arent harmonic or when they arent even periodic.

The rate transition blocks are useful when the priorities are enforcing the order of execution. If the blocks are in different cores, there's no priority order between the two, priorities are only given in a single core, unless a single priority queue exists for all cores (which is not common)- In a multicore implementation implicit synchronization is needed.

__Absence of Preemption from High to Low priority__
the Rate Transition block when going from high to low priority.
When going from Low rate to high rate the rate transition block can be avoided if the low rate writer has a priority higher than the reader. Also when there's a high priority writer the Rate Transition Block can be avoided, this means the the Rate Transition block can be avoided when the reader is executed and complete when the writer is activated again. The condition for the Rate Transition block can be expressed as a timing condition, so if the response time of the reader is less than the period of the writer minus the maximum offset between the activion of the writer and the reader.

__Muticore adaption of RT block__
When RT is needed on multicore implementation, there has to be a synchronization between reader and writer. As said before, priority order is not enough in multicore to guarantee the reader is going to be executed after, an explicit signal is needed, this signal can be generated by the writer when it completes. the other option is to compute the worst case execution for the writer and activate the reader with an offset equal to the worse-case execution time.

__Design/Scheduling trade-offs__
 ![[Pasted image 20221005162610.png]]

If the following set of task are a model in __Simulink__, the periods are 4, 1 and, 2. If we need this to be generated as a multitask implmentation by _simulink coded / embeded coder_. Rate Transition blocks are needed for every single link.
Assuming (__the text in red__) no RT is wanted there, and this can be either because it's a link with a lot of data o (so we dont want a memory overhead) or the reader doesnt want a delay there from a low rate to high rate. 

- __Is it possible to achieve the fact some RTs have to be kept and other remove?__
- __Is there a way to have Rate Monotonic with a single task?__
  Remove the assupmtion that all the blocks with the same rate are executed by a single task. So, the task model might be like this: Highest priority task executing block 1 due to Rate Monotonic, the second task is executing the blocks of rate 2 followed by the task that executes a block of rate 4, followed by a task that executes a block of rate 2 and the last task executes the block 2. As you can see block 4 is implemented by a task that has a priority higher than block of rate 2, so there's no need of a Rate Transition block. So this task model is not a Rate Monotonic model that might be feasible saving the usage of Rate Transition Block.

The mapping of blocks into tasks is no more two options (that it has been talked before about how the Rate Transition block was used)

## Task Implementations

Given a set of tasks and a mapping function. Let's assume so far that the output update and state update are merged into a single step function $f$.
$M$ is implementing a block within a task and may be expressed as a function $M(f_j, k, i)$ where $f_j$ is the step update function of block $j$ mapped into the $i$ task with execution order $k$.
(___SIDE NOTE___)__What's the execution order?__
The order in which the step functions are called by the task. and this order has to be consistent with the partial order of executions.

There will be another functions that express the $M$ functions into cores. and based on these mapping the communication mechanisms are designed that are the extensions of the rate transitions blocks.

__Preserving streams__
Let's assume a general system where blocks are not even guarateed to be periodic that can be activated at generic points in time with minimal constraints.

![[Pasted image 20221005175524.png]]

Orange arrows represet the dependency of the blocks, meaning the entry of C is the output of A. But the real implementation turns to be this: ![](/home/ckevar/.config/marktext/images/2022-10-12-15-49-46-image.png)

A mechanism is required in order for B to process the all values produced by A, here is when buffer mechanism is deployed. When having multiple readers, one buffer isn't enough, an array of them is needed, popping many different problems. 
![](/home/ckevar/.config/marktext/images/2022-10-12-15-50-26-image.png)

- **How many values will be stored?** There are research on going for this kinda questions.

Assume enough positions are present (no worries about buffer size). The mechanism needed is that assigns an index to the writers when a writer is activated and, the same thing to the reader. The Reader will be assined the index of the user that it will use when activated because the value that needs to be consumed is defined at activation time. This index cannot be given in the task code, it has to be done at activation time. That's why it needs the support of the operating system or something that guarantees the execution before any task in the system (highest priority). Once the index is assigned the actual write and read can be performed, obviously when the reader is reading a certain value, that cannot be overwritten, if the writers are producing other values they can be place somewehre else in the buffer. Not all values produced by the writers have to be stored, so at most, there will be one variable for the eache reader and one more value that's available for the writer. So, one safe bow in case the writer is higher priority than all the readers, number of readers + two (buffer size). If the writer is lower priority you need to account the unit delay plus 2. one way to size the buffer is the number of readers + 1. There's another sizing option

**Temporal Concurrency Control**

This another way to size buffers and based on: 

![](/home/ckevar/.config/marktext/images/2022-10-12-16-52-15-image.png)

The value will receive an index position in the buffer, this index cannot be reuse if it's being used by any one of the readers but when it's guaranteed this position is not used by any reader then it can be reused, so, a lifetime for this position can be computed. 

the 

$lifetime: I_{wr}= O_{wr} + max(R_{ri})$ 

$O_{wr}$ : Offset time between this point in time and activation time of any reader.

$max(R_{ri})$: Worst case time that takes to any reader to complete,

$I_{wr}$: lifetime for this value for anyone of the readers.

Check how many values the writers can produce inside a lifetime and that's the buffer size required. This is called circular buffer. Once the writers reach the last element of the buffer, in the next writing, the writer overwrites the first index (o-based indexation).

But this needs support by the OS at activation time, if the writer and the readers are periodic guaranteedly 

# Simulink Model

they can be many things: network of blocks, other things to considerate to generate code from a model are:

1. Number of workspace variables, The execution of the model may be conditioned to the value or number of variables.

2. Number of type declarations. Each block is the model is carrying a signal, a funtion in time with values in a given range. They can be premitive types predefined by simulink. Keep in mind that complex types can be used in models, possible variable dimensiones, such as arrays, where each element is a structure. In general, whatever language is being used to develop the system, the capability to create custom data types is desired/required. In simulink, this is called bus objects. This custom types are defined outside the model in a separate enviroment.

3. Other part of the system's bheaviour might be descriped with matlab code or external code, that might not be in the graphical description. 

4. Simulation condiguration pages.

## Simulink semantics and flow preservation

The system is a network of functional blocks, for convinience they are labeled as $b_j$. In simulink the blocks can be regular blocks or **dataflow blocks**, these are Stateless (in reality some blocks do have a state). they can be continuous, discrete or triggered.

1. *Continues* means the outputs is update and is valid at any point in time in a continuous  time.

2. *Discrete* means it only updates its output at discrete point in time.

3. *Triggered*, it's kind of a discrete event.

The other type of blocks are **Stateflow** or state machine blocks, this type of blocks are actually managed by a program that in reality is external, it's kind of a plug-ing of external program. In the new versions of simulink the manage of the stateflow blocks is homogeneous to the other blocks.

When generating code out of a model, everything becomes a discrete time block. Everything becomes periodically activated. For embedded systems, out of all those blocks, the most importants are the periodic activated ones. The signals are continues but sample periodically and the output will be periodic as well.

## Simulation Flow

Whenever there's a network of blocks, basically there are two end points, the inicialization stage at the begining and a termination stage at the end.

![](/home/ckevar/.config/marktext/images/2022-10-12-18-03-08-image.png)

Then there is the main simulation cycle that is repeated until the end of the simulation. basically the end of the simulatio is controlled by the user, i.e. _inf_ means the simulation lasts forever.

The model is first compiled before simulation, number of things that have to be done before simulating, as part ot this, each block is assigned with a rate. This is because the user doesnt write explicitly a number for the block's period but it's usually left as inheritance. In this case, the backwards block will dictate the period otherwise, there's a forward search in order to find something that defines a period for the block. Therefore, there's a forward and backwards propagation to assign rate to the blocks. Constant values are also prograpagated at compilation time (to avoid recomputation). As well it initialize the simulation structure, inputs, outputs, states, matrices and variables that are in the system.

Inside the cycle, the next simulatio time is computed specially when there's a variable rate execution, let's step back, there are three types of blocks, continuos, discrete and event.-drive. if everything in the system is discrete, then, the next event in the sysmte is very easy it would be the next activation for any block in the sysmte, and in this case the simulator will do, basically the simulator will compute the base rate, it computes the gratest como divisor among all the periods of all blocks. i.e., if there are two blocks with periods 3 and 10, the the GCM would be 1, meaning the overall period is 1. 

# Simulink - Code Generation and RT blocks

_link: https://www.youtube.com/watch?v=WGuB5_vwGDs&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=10_

## RT Block - Rate Transion

Doesnt need OS, it's application level. It's not an state, but it helps with updating the states.
SOMETHING ELSE ABOUT LOW AND HIGH RATE and PRIORITIES.

## Multicore adaption of RT

there must be a synchronization activation for readers and writers.

## Preserving streams

non periodic tasks

## Temporal cocurrency control

A writer cannot overwrite a buffer while the data is still available for some readers.

# Simulink Model

_link https://www.youtube.com/watch?v=RG7ZBa24wOQ&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=11_

## Simulink semantics

__dataflow__ doesnt have a state, a _dataflow_ block can be cotinue, discrete or periodic.

## Simulation flow

three types of blocks. if everything is discrete time, the next event in the system is any action for the block in the system. The Base rate, common divisor of all periods. if a continues time block will allow to change at same rate or variable time block execution.

Usually it is not solver problem, it just that certain solver would solve something in a prerry long time.

At each $e_j$ the block will compute its own state and/or the inner states.

A stateflow block reacts to a set of events simultaneously.

Simulink can show you what blocks are continuous, discrete and hybrid.

**feedthrough block** where the output depends on the input, and where the output doesnt depende on the input it's called **non-feedthrough**.
The feed through block requieres that the predecessor block provides the input to run/operate, so there's an order of execution, which doesnt happen in non-feedthrough, there's no order of execution.
there's no priority in simulink, there's feedthrough or non-feedthrough blocks and this rules the order of execution.
SOMETHING ELSE
Another interpretation, it's good to fill the values of the variable beforehand. and if you dont know set as uknown, so the outputs will be unknows, however in the following iteration, the values will be progragated from the beginning block to the last one.

## Semantics and Compositionality

systems compositions do not behave according to the semantincs of the component.

The system isnt not sensitive to any delay or jitter between two consecutives executions of task, that's also called synchronous assumption.

## Flow preservation

The implementation of SR(?) model should preserve its semantics so to retain the valiation of the simulation.

Why do we need it? 
consideration: it matters because we have a consistency of the value along the chain of blocks.

# Signal and Systems

_link: https://www.youtube.com/watch?v=abGDF53wJtc&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=12_

We use models to describe how signals behave. Model are usefull even it fails, but it means the model is useful within the boundaries of the values if works.

__concept__ A function identified by four things: name, domain, range, graph or assignment, for example:  Sine, cosine, voice, images. sometimes signals arent over continuo o discrete signal. such as a keyboard, where the inputs key be the sequence of events.

Most of the time we will deal with deterministic state machine.

## System

function whose domain and ranges are signal space, all innput and output pair.

## Memoryless systems

the system isnt affected by the previous values of the system, a integral isn't an example of this type.

## Block diagrams

it's an informal representation of systems

# State Machines

_link: https://www.youtube.com/watch?v=ejXe7w-TXTo&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=13_

a __State__ summarizes the past of the system.
_SM_ are casual, its output only depends on the current state.
There are two states, there are only the current state and the next state. Output and Update are the blocks that SOMETHING...####

## Stuttering

when there's no input, there's no output and the state is supposed to not change.

### Finite State Machine

### Update tables

the update functions can be described as table.

Another way to describe a State Machine is using _state transition diagram_. 

## Shorthand

if no guard then the transition is always executed
if no output symbol, then the stuttering symbol will be the output.

## Determinism

for each possible input there's only one output.

an _FSM_ with no output is called _finite automata_. also used for language composition, parking meter, binary delay, 2-delay

## Mealy machines

generates output during transition.

## Moor machine

generate output while the system is in a particular state.

## Nondeterministic State Machines

it includes _possible update_ in its model.

# Why non determinism?

- Modeling randomness
- Modeling abstraction

# Compostion

_link: https://www.youtube.com/watch?v=ZewkuIbBm7I&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=14_

## Synchrony

_SM_ we are interested are triggered all at the same time. Meaning the compositing _SM_ are being triggered at the same time.

## 1. Cascade Composition

_SM_ reacts to external inputs simultanously and instantaneously.
Simplest composition, casacade (one _SM_ after another _SM_). This is interpreted as the union of _SM_.

Its diagram can be drawn using one state diagram.

#### Example 1

**Explanation** at  _https://youtu.be/ZewkuIbBm7I?list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&t=380_: The output of one machine becomes the input of the another SM
![[Pasted image 20220904112759.png]]

#### Example 2

__a__ state is the initial state. Remeber the output of A is the input of B (this is just in _cascade_ composition) and the output of the composited _SM_ is of tbe B _SM_. 

![[Pasted image 20220904113759.png]]

__Solution__ at: _https://youtu.be/ZewkuIbBm7I?list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&t=990_

![[Pasted image 20220904114125.png]]

### Update function

SOMETHING 

### Reachability

Some states are not reachable based on the input of the first _SM_.

## Hierarchical composition

They are just cascade composition with more than 2 _SM_.

### Fixed point = Feedback

#### Example

number of inputs = new_reclutadores x numero_de_jugarores.

## SM with no external inputs

There's no extermanl input so, it's a self feedbak system, so the outpus are connected to the inputs of the _SM_.

## State-determined Output

All outputs coming out from a state are the same(they are alloed to vary from state to state to state), so this ensures a well-formed feedback composition.

![[Pasted image 20220904120946.png]]

__solution explanation__ at: https://youtu.be/ZewkuIbBm7I?list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&t=2798

![[Pasted image 20220904121046.png]]

It's sufficient but non necessary to have state-determined _SM_.

## Constructive Procedure

at first glance this _SM_ is well-formed composition because it has state-dteremined output on the second output.

![[Pasted image 20220904121753.png]]

# Hierarchical State Machines

_link: https://www.youtube.com/watch?v=u0rvkcLfPm4&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=15_

typical transition follows:

_Event \[ condition\]{condition action}_ / transition_action
the _condition_ is a guard or a binary condition that allows the transition.

## Clustering

The transition can be for the superstate if the arrow ends over the edge of the superstates.

## And-Clustering

this is similar to parallel composition where a superstate has regions and both are active simultaneously.

![[Pasted image 20220904123312.png]]

_ev1_ and _ev2_ are active as well when the substate is active.

_entry_, _during_, _exit_ actions of interest

## Transition junctions

this groups transitions triggere by the same condition and based on a guard it can be redirect to right state, this branches in and out the transition.

## Connective junctions

the joint is a "switch" that can be true or false that can be redirect based on true/false conditions. Meaning this branches out the transition.

## Backtracking on junctions

SOMETHING

## Connective junctions

the transitions can enter/leave to/from regions inside the superstates, and continue with the parallelism that they already have.

# State Machine Behaviour

_link: https://www.youtube.com/watch?v=Xxe4xE0rvDY&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=16_

Two _SM_ are equivalent if they behave the same under the same input, time and return the same outputs

$Time[S_1] = Time[S_2]$

### Refinement

System $S_1$ refines system $S_2$ iff:

1. $Time[S_1] = Time[S_2]$
2. $Inputs[S_1] = Inputs[S_2]$
3. $Outputs[S_1] = Outputs[S_2]$
4. $Behaviour[S_1] = Behaviour[S_2]$

$S_2$ is vaguely described, $S_2$ is an abstraction or property of $S_1$

## Simulation

This can be considered as a matching game. Binary relation $S in States[M_1] States[M_2]$

for deterministic _SM_ simmulation is the same as refinement.

Demostrating a simulation relation is sufficient condition to demostrate abstraction but no necessary, otherwise is unknow, there might be still abstraction.

_no necessary_ for a subset of subset states 

## Behaviour

means the range of outputs of a _SM_, two _SM_ can behave the same, meaning, they range of output or the values of the output are the same non in accordance with the input. the output can match but the input might not.

__output-deterministic__ iff there is only one initial state and for every state and every __input-output__ pair there's only one succesor state. so, if a _SM_ is _output-deterministic_, then a simulation relation is necesarry and sufficient to demostrate _refinement_.

if the _SM_ under test isnt _output-deterministic_ then the _SM_ shoud be cast it into a _output-deterministic_.

# Pattern for C/C++ implementation of FSM

_link: https://www.youtube.com/watch?v=fpuffC17ljk&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=17_

## A C implementation of (some) OO programming

a pseudo-class is declared using structure and regular functions.

Allocate objects dynamically -> *on the heap*
Allocate objects automatically -> on the stack

_C_ has its limitations.

Usage of helper MACROS.

#### Inheritance

Inheritance can be inherited by pointers.
The pointer of the child structure is the same as the parent structure, to extend the parent attributes we need to wrap the parent structure inside the child structure.

A Macro can handle this operation.

This is only possible for single inheritance.

#### Polymorphism

it's trickier because it requires dynamic allocation.

## Design options

Only for flat _SM_, not for hierarchical.

_States_ can be represented as enums.

_init()_ top level initial transition
dispatch() to dispatch an event to the state machine
tran() to make an arbitrary transition
skip from 23 to 

### sync and async SM

two events can occur at the same time on *__sync SM__*. this is for discrete time.
Here _events_ no need to be stored because they are only used when they arrived or when the tick is available after that the events are lost. 

Two events never occur at the same time on __*async SM*__ because time is continuos which makes it non determinisctic, so if the system has to execute one of them, for example, the first, then the second event is lost.
_Events_ here are represented as _queue_.

### Nested switch statement

First level _swtich_ for _state_ variable
Second level _switch_ for _event signals_

No reusable code, everything is wrtten in ROM, very small usage of RAM.
The complexity grows for larger state machine due to nestness.
_swtich()
    case STATE0:
        switch() {
            case SIGNAL0:
                    // do something
                        tran(the_following_table)
        }
__

### State table

In here the signals are listed along columns and states, along rows. Tyically C++ is used to translate this table into code. it's basically a lookup table.
.

##### Dispatch

1. identifies the transition to take as state table lookup
2. Executes the action and changes the state.

The table is the nasty part, because it takes too much memory and for larger _SM_ and also it doesnt work with hierarchical _SM_ .

In this case the pseudo class using structures and macros is used in trhis table implementation.

### Statechart Implementation

_link: https://www.youtube.com/watch?v=sKsEQVH0fxQ&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=18_

## State Pattern

### OO approach

States are represented as subclasses (PanelState). 

Polymorphism makes the transition fast.
it's memory efficient, RAM.
Not fixed types to represent elements.
No encapsulation for the context class.

## Samek's proposal

uses a pseudo-uml.
Classes are for state machine as a whole.
States are represented as function _pointers_.

It also has some disadvantages. All states aren not enumerated. This can handle hierarchical states.

Inside the action has to be implemented SOMETHING
Another option is use ilf-elsi or swtiches.

CODE BUG

_void Fsm::tran(FsmState target){
    (this->*myState)(EXIT_SIG); // EXIT signal to target
    myState = target;
    (this->*myState*)(ENTRY_SIG); // ENTRY signal to source
}_

### Hierarchical Bhaviour Implementation

this means a set of states are active and not only one, and those can be groupped in diferent superstates. This can be handle by a list of pointers inside the class or outside.

Current state and source state is store in a QHSM (_Quantum Hierarchical State Machine_).

Quantum has to type of transition, statically defined and dynamically.

Signals has to be defined by you
and one method for each method.

_WE HAVE TO RE-WATCH THIS VIDEO, WE ARE TOO TIRED RIGHT NOW_

# Lab - Stateflow

_link: https://www.youtube.com/watch?v=dv7sqy3WsMk&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=19_

Events can be rising or falling.
Events are externals to the stateflow

Events to stateflow are wrapped in a vector. so they have to demultiplexed.

transition action is written like this $/transition\_action$

# Lab2 - Code generation

https://www.youtube.com/watch?v=Yfw2W2KiJ2g&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=20
In order to generate model, a couple of things have to be done, because the simulation settings affects on the code generation. 
Simulation -> configuration parameters 
Type : _fixed step_
We dont care about the _solver_
__Real Time Workshop__ 
    Template language or System target file: 
        - _grt_ are simulation purposes, pick _ert_
    - C++ enapsulated is c encapsulated, it's a fake c++. Companies usually generate the code as a subsystem so we need a makefile. If it were the whole system being generated then a make file ready to compile.
    - ANSI C is ok as.
    - Right click on the block we want to generate the code of, Real-Time workshop, buid susbsystem.

- Not all files are necessary, just the main and where the types are generated.
- Functions *__\<susbsystem\>\_step__*
  The inputs and outputs are data structures that they can be defined by hand in the system or a whole can be generated by merging the _SM_ and the data handler.

# Lab 3 - S-Functions in Simulink

_link: https://www.youtube.com/watch?v=91RE6ZYrc-U&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=21_

## What's S-Functions' purpose?

It provides Support at simulation time, in our example it shows (emulation of) the front-end of the system, this part it's not used to generate code.

WTF IS FLEX INTERFACE?

**.mdl** files describe simulink blocks.
**.m** implements the block functionality.
**.fig** shows the interface itself.

**Setup functions** are registering the _start function_ and the _output function_, the first one is called when simulation starts and the second one when the interface needs to be updated. This _setup_ functions also describes block specification, type of block, number of inputs, number of outputs, input types, internal states.
Also global variables are declared in this functions that will be used in the interface.

Matlab _does not_ create a window, it creates a graph, if it's not a graph you can specify it later.

# Lab 4 - Code generation, S-Functions in C and custom generation using TLC.

Some values 

as _solver_ does not make any diference because we dont have continues time on our blocks.

_OPTIMIZATION_ check the following:

1. Conditional input branch execution
2. Implment logic signals as Boolean data (vs. double).
3. _Inline parameters_ (some blocks, as gain block, treat the gain value as a parameter, which is implemented as variaable in RAM) Due to this it's better to check this option because some blocks can be implemented in ROM because they are more efficient. 

_Real-Time Workshop_
in _system target file_ pick **ert.tlc**.
Pick _c_ language

_Custome Code_
You can add your own code in here.

Right click in the block we want to generate -> Real-time workshop -> Build Subsystem.

There are functions in C that remap from S-functions to the board.

## Eclipse

# TLC

it can be used a well to generate C code, in fact, TLC is a text generator. it stands for _Template Language C\<something\>_
They detect patterns in some source model, and for every detection they activate a correspondent generation SOMETHING. Everytime a pattern is found it generates a code in the destination.
The generation commands usually comands of three parts, the beginning, the Template Language directives (identified by the __%__ ) and Text, generated as it is.(black code).

TLC declaration or instruction are recognized by the __%__.

Setup - update - Termination, it can more complicated than this, but in general this wraps up everything.

As same as simulink, all parameters have to be declared in a _setup_ functions.

_Advatange_ additional code needs to be written from the general API to the erika API, that's a couple of lines. The coded generated by simulink is completely portable. while Using TLC it might not be because it's personalised to go from a generic API to an Erika API. 

Simulink uses a TLC bank of codes to generate C codes. 

# Lab 5 - Code Generation using Acceleo

_link: https://www.youtube.com/watch?v=42jkrOWA9RE&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=23_
File -> new -> other -> Acceleo model to text -> Acceleo Project.
__Project Name__: _MyTransformation_
__Metamodel Utils__: __+__ 
*__side note__* SysML is built on top of UML, the base is UML. 
    add _uml2/3.0.0/UML_
    add _papyrus/0.7.0/SysML_
    add _papyrus/0.7.0/SysML/Blocks_

__Type__: _Model_
__Template__
__Generate File__
__Main Template__
-> Finish

## File Template

File _generate.mtl_ is an acceleo template for processing the model and generating text.

this syntax highlighting is similar to _TLC_.
This is a markup language, because each element of the language is contained between two elements (opening marker and closing marker)

    [module generate(<list of metamodels we're using>)]
    [template public generateElement(m : Model)]
    // m is _type_ Model
    [file (m.name, false, 'UTF-8')]
    // (file_name, append mode, character code)
    // What if i dont remember the properties?
    My Model name is [m.name]
    Let me type some free text
    // The _Acceleo Editor_ is very intuitive, when type a command, it lists the available variable in the current scope. (ctrl+ space)
    [/file]
    [/template]

_Steps of configuration_
Right click on the file _generate.mtl_ -> Run As -> Run Configurations -> 

__Main Class__: search for _MyTransformationM2T0.main_
__Generate__

    [module generate(<list of metamodels we're using>)]
    [template public generateElement(m : Model)]
    // m is type Model
    [for(p:Packages | m.eContents(Package))]
    // This is gonna iterate across all the packages.
        [if (p.name = 'functional')]
            [for (c.Class | p.eContents(Class))]
                [generateClassDeclarations(c)/]
            [/for]
        [/if]
    [/for]
    [file (m.name, false, 'UTF-8')]
    // (file_name, append mode, character code)
    // What if i dont remember the properties?
    My Model name is [m.name]
    Let me type some free text
    // The _Acceleo Editor_ is very intuitive, when type a command, it lists the available variable in the current scope.
    [/file]
    [/template]
    [template public generateClassDeclarations(c:Class)]
    [file (c.Name + '.h', false, 'UTF-8')]
    /* My model name is [c.name]
        Let me type some free text    
    */
    class [c.name/] {
        public:
    }
    
    [/file]

*___Templates__* are polymorphic 
*__Scripts__* are used to process the model and return some information from the Model, they can return Model elements, strings or boolean. Acceleo is built according to OCL (Object Contraint Language).
*__Services__* Functions implemented in Java can be called.

### Templates

    // OVERRIDING
    [template public TemplateName() override TemplName]
    // PRECONDITIONS - GUARDS
    [template public TemplName() ? (bool_expr)]
    // POST TREATMENTS
    [template public TemplateName() post(postfun())]
    // VARIABLE INITIALIZATION 
    [template public TemplateName() {var:type = init;}]

## Template statements

- _file_ 
  
    [file (out_file_uri, append_mode, encoding)]
    [/file]

- _for_
    [for (iter_var : type | collection)] ... [/for]
    _modifiers_:
    _before()_ -> what can be done before the foor loop
    _separator()_ -> 
    _after()_ -> what can be done after the foor loop 

- _if_
    [if (condition)] ... [/if]

- _Let_ -> Assignment of final values and it cannot change after init
    [let (var_name = init)] ... [/let]

- _Comments_
    [commet] ... [/comment]

- _Other templates can be called_

__Acceleo Operators and OCL__
all attributes, child's and parent's
OCL is an OMG standard.

_eContents(typestr)_ list of childre of the given type.
_eContainer()_ -> the parent of the object
_eContainer(typeStr)_ -> the parte of the object of the given type if you have more than one parent.

it also has String operators, to upper case, to lower case, to split.

__HERE IT'S MISSING THE LAST PART OF THE VIDEO__

    [template]

One more stereotype can be applied to an element.

# Conformance Testing

_link: https://www.youtube.com/watch?v=dnhr981Eg-E&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=24_

## Model-based testing

o conformance testing or fault detection or machine verification.
$M_s$ known transition diagram.
$M_I$ implementation only behaviour is observable.
 We want to veryfy if $M_I$ correctly implements $M_S$.

We need an input sequence small in number and length. To formal demostrate conformance between the SM and a model. In conformacne testing is succesfull when $M_I$ and $M_S$ behaves the same and they produce the same outputs.

## Asumptions (reqs)

the $M_s$ state machine model is reduced minimal, not two states equivalente.

$M_S$ has to be deterministic.

_strongly connected_ -> every state has to reachable from every state via one or more transitions. A reset button should take us to the initial state from any state.

$M_I$ does not change during testing.

$M_I$ is at its initial state.

$\lambda(S,X)$ output functions, $S$ is state and $X$, the input.
$\sigma(S;X)$ state function: $S$ is the state and $X$, the input.

## Possible faults

_Output_ the transition ($M_S$) produces wrong outputs.
_transfer_ the implementation ($M_I$) goes to the wrong state.

__THIS VIDEO TOPIC SUCKS AS WELL__

## Algorithm for conformance

__This section sucks as well__
It uses graph theory.

- No need to go back to the initial state every time.
- _Transition Tour_ is an input sequence $a_1, a_2, a_3, ..., a_n$
- It's not enough to check the _input_ and _output_ but as well the _status_.
- if it's a symetric _FSM_ then there's always, the transition tour exists.
- for _non-symetric_ FSMs, finding the shortest tour is another graph theory problem (Chinese postman problem). 
- All this algorithm isnt done by hand but by a software tool.

### Transition Tour method

if path touches every state and transition.

_Check the transtion_ means check the output update, and the path touches all transition then it called _transition coverage_

if the tests visits all states (not just transitions) then it's _state coverage_.

Transition coverage is not enough.

## Using Separating Sequences instead of status

first, find the signatures, compute the signatures.
second, ....

## Separating Sequences

## Charazing set

a set of sequences that works as a signature.
it 's an extension of separating sequences

# Lab - Unit test

The additional functions (no regretion test) doest have to afffec the system functionality.

Setting up, prepare the system for the extra component that's gonna be test.
tear down, restore the previous system update.

Checking assertions
Hundred of tests.

## Process

Write the test before writing the code.

## CUnit

it's simple, it's small and easy.
Non mockery.
Works with Assert and it has a bunch of it.

write the test functions.
Write code for the tester:

1. Initializer of the register (suit initialization)

and for each module to be tested write:
3. the setup
4. clean-up
5. a test function to be performed.

The main program for testing. (how and what to perform).
Many registers can be manipulated in one test, because they can be switch as active register by using pointers.

## Behaviour Upon Framework Errors

### Other frameworks

_cpptest_, _gtest_ it might required in the exam.

## Coverage measurement

how much of the code is executed.
it's a black box texting, a code that isnt yours.
Gcov is from _GNU_ foundation.
GCOV is a coverage program, can help with:

1. how often each line of code executes
2. what lines of code are executed.
3. how muc computing times each section of code uses.
   _It better to have a 10% improvement on something that's taking 90% of your execution time than a 90% improvement on something that takes 5% of the execution time_

## GCOV

_gcda_ are the files were all results of tests are stored, this is accumulative.

## Invoking GCOV

// He shows some example.
_gcov [options] sourcefiles_
_options_ can be pretty much anything.

## LCOV

after compilation time, gcov-ing into the compiled program generates some files and _LCOV_ shows you in a fancy way the total coverage.
