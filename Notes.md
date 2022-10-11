# Intro and Requirements

_LINK: https://www.youtube.com/watch?v=Iqc-n6bbGZA&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=1_

## Embedded systems

Special-purpose computer system designed to perform one or a few dedicated functions, sometimes with real-time computing constraints.

It's also important  the model of the physical process (in order to predict the computer behaviour).

Modern language have Predictable timing or a way to handle timing. Old languages such as C or Java (these are general purpose programming languages) does not provide time handling, some libraries were developed later on for such purposes. 

## V-shape development cycle V-model

__User requirements__
        As close to the user language
__Functional specifications__
__Functional modeling__

    The system is modeled using models and parameters of the enviroment.

__Architecture Exploration__
    Defines the architecture that supports the execution of this functionality, such as (microncontroller architecture, peripherals, where the microncontrollers are gonna be purchased from).

    Also it defines the *functionality* over the architecture, where and when the functions will be executed.

__Component Modeling__
        Design the component, model the __behaviour inside them__ and then __implement__ (_Code_) the components either harware or software, accordingly.

__Validation__
        The user confirms the software functionality.

V-model_ allows tracing errors at early stage because the test statements and conditions are written at each level of the development.

# Models

_UML_, _SM_ is a software modeling.

__Why models?__
Sometimes enviroments make a system difficult to test, either due to enviromental conditions or costs, examples of this are space exploration or nuclear reactors. That's why modeling has two goals, _documenting_ and _simulating_.

_UML_ currently and usually is used as a **documenting** tool. Documenting and designing allow reusage and improvement  on the code (sofware costs). This makes the software development effective, fast and errors avoidant, also currently known as __model-driven architecture__. 

Things such as _Simulink_ or _National Instruments_' tools allow us to model in order to know the behaviour of the system, to verify a property on the model, for example, the correct function of a _PID_ controller or the safeness of a _SM_. And this is called __model-driven engineering__

__Model-based design__ traditionally sees the model as a primary artifact for modeling the behavior and properties verification.

## Model-based design

In our case (embedded systems) models are built to test or verify properties (by simulation) or checking.

### Why automatic code generation?

Programmers can introduce errors in the modeling while implementing the code; so, __code generation__ ensures the code is the same as the model.

### RTS and Platform-based Design

The execution plataform. Matches the logical design (HW architecture or OS) into the SW architecture. Using the API of the OS. Time in SW is a property that has to match with the hardware. 

Timing properties such as, period and execution time are parameters that are required but the execution platform will dictate the worst case scenario. 

## REQUIREMENT ANALYSIS

Requirements are linked directly with _validation_ because that's what the user wants or expects. 

1. Good requirements avoid inconsistencies and redundancies.
2. Good requirements tell what the problem is, not the solution. 
3. Good requirements tell what the system is supposed to do.
4. Requirements are (supossely) the starting pointing of the development.
5. Even when the project is built by small cycles (meaning prototypes) in each cycle the set of requirements has to be set.
6. Requirments are generated and coordinated by/with marketing staff, productt specialists and other analysts.
7. Requirements are natural language, therefore, they are unconsistent and misunderstood.
8. The current problem in the industry lays on *How to write* proper requirements or *how to extract* them from the users' speech.
9. It starts with **Requirments Elicitation state**, where the user or stakeholders tells or is being asked what the requirements are.
10. _Z_ language is the _formal_ languge to write requirements.
11. _FSM, ATL_ also can be used to write requirments. But in reality _FSM_ and _ATL_ are not good to write requirements because they are not general language.

### How to write requirements

1. We can start by enumerating the _working_ modes or _states_ of the system. From airplanes to lifts, they all have states or working modes, so _start_ by breaking down the _working mode_ and work in each _working mode_ and the _information_ the system handles if the system or subsystem is a storage data or retriever data. the last obviously won't work for controll based systems.   
2. Then take into account cases of the system and the actors, humans or operatators and external events in the environment (temperature, pressure).
3. Write those working modes in a style of _FSM_ description.
4. Ease definitions of requirenment-driven test cases, to implement SysML.

### REQUIREMENT ANALYSIS - CONTROLLER-CONTROLLED MODEL

In embedded system we have two sides: the system that will control and the enviroment that will be controlled. On the _controller side_ we will found _constraits_ of the system and, on the _plant side_ we will get something called the _assumptions_.
Each requirement should be written as a pair or a contract, a _constrait_ given and an _assumption_, for example:
    __The controller of the boiler should always make sure that the temperature is between +/-1 away from the desired temperature.__
This requirement is missing the *assumption*, it's assumed the _Boiler is full of water, the sensors are working correctly, enough sensors are installed in the region of interest_. Each requirement has two components, the _assertion_, what the controller must provide based on the _assumption_ of the system. Some _assumptions_ should be part of the requirements and some are _forced_ to be.

The structure _assumes_ we have identified a section for our system that is already partioned. For every single macro subsystem:

1. Identify the working modes and, 

2. Then refine those things.  

3. Some reactions aren't isolated in a single subsystem but organized in a protocol escenario. This reaction is called _sequence_ diagram in _UML_ and _interaction_ diagram on _SysML_.
   
   So, the requirements will operate in two modes, at system level and subsystem level: inputs_, _outputs_, _characteristics_ and _parameters_.

__Itemized requirements__ are more difficult to read but they are more accurate and easy to test or write tests for.

### Unnecesary description

1. What the system doesn't do
2. Description of things when the system does not react. If it is a safety requirement, then it's ok, otherwise it's unnecesary.
3. Don't change or switch back and forth between the working mode names.
4. If a system has multiple things of the same specie then they have to be named in sequency, but there have to be consistent across the whole desription without changing over time or over the whole description.

## Type of Requirements

The requirements can be 
__User requirements__

    What the user expects the system does
__Functional requirments__    

    For mechanisms and procedures needed to achieve the user requirements. timing included.
__Safety requirements__    

    Possible failure conditions and hazards, based on _assumptions_.
__Diagnostic Requirements__

    On/off-board diagnostics required.
__Para-functional or non-functional Requierements__ 
        Features that can be measured: usability, scalability and speed.

In order to complement the requirements some diagrams are needed that will be mentioned later.

_itemization_ of requirements is important, to clearly identify them and trace them when  tested. 
A formal repository has to be used to store the variables and parameters (including buttons).

__What's a good test?__
To check all the requirements. This is called _functional_ test or _requirement_ oriented test or _black box_ test. Every single requirement has to be test at least once.

_White_ box or _structural_ test is as well as important as the black box, but it'll be touched later.

### Ariane Case

It used a software built for the previous version of the rocket, _Ariane 4_, wich had a narrow inclination, but _Ariana 5_ was supposed to exceed those values and eventually it happened.

#### Mars Polar Lander Case

Nobody knows what actually happened. A premature shutdown of the engine? or the computer?, the legs deployment didnt happend because the engine shutdown before. There was a requirement untested.

Long list of requirements are difficult to test, and all test conditions have to be written from the begining. 

Sometimes when a requirement isnt clear by reading the test, the requirement can be clarify, that's why it's important to write test from the begining.

When writing requirements, some keywords has to be used such as:
        __shall__ used in an _assertion_, a promise from the _system_
        __must__ used in for _asumptions_,
        __will__ based on the law of physics.
        __should__ not required, an optional requirement.
_Negative_ requirements shall not be written. in safety reasons it can be used, but try to write its complementary positive. A _Negative_ requirement means that the system can be in any state or the variable values can be anything, for example if the value is _not_ 1 then it could be anything, so the range of values become wide

Requirements shall only stated for _outbound_ state transition. For example, _if the temperature sensors break, go to error mode_ (this is an outgoing transition) but it's not well to write it again as an _incoming_ transition (in general, try to avoid _incoming_), _The error mode occurs when the temperature sensors break_.

This will lead to inconsistency when updating, because, it might happen the case the first requirement is updated and the second no, so, it pops an inconsistency.

### Styles of writing the requirements

1. there's an assertion and an assumption.
2. Preconditions/postconditions/invariants
   - Define all properties that are true before the reaction occurs, all the conditions that are true after the behaviour occur. and _invariants_ that are not either true or not after the reaction.

## Data Dictionary

Define the subsystems, define the inputs and outputs, this are formally defined as a model and it's called data dictionary. 
each input and output needs an identification, a formal name, a description, event association, data type, the range of values accepted, time association (freshness requirement) or update rate, units.

After the develpoing this, we can start writing the itemization of the requirements and remember to use the formal name you gave to the inputs and outputs (otherwise you could get missed or confused). So, _itemization_ should be written like this:
_Entering mode_ -> _While in mode_ -> _Exit from mode_.

## Further Notes

__Ask yourself the following__ _what are possible error conditions in a given state, at, in or leaving?_

__Avoid writing__ this words, normal, appropiate, suitable or nominal conditions.

__Write__ explicitly what to check, when to check, where to check and how to check, what makes it a check.

__Fixed numbers__ on a requirement are never allowed, they have to be whithin a range, at least if it were boolean.

Requirments and Test have to be linked not just abstractly but as well in the written documentation. Also they have to be linked along down the _v-shape_.
__and why do we do that?__ In this way if after sometime a certain requirement has change or a test has been modified, we know what other requirements are affected by that change. So, we keep _track_ of all the relations among them.

## Formal Language

a formal language allows to test in an automatic way. Tests can be written from the _itemized_ requirements, which gives _itemized_ tests, these aren't test one by one, these are test in a bank test.

.............................................................................................................

# SysML and Papyrus

_LINK: https://www.youtube.com/watch?v=1RR8yomqWjE&list=PLohWCZQ0wiEVpgTkxTsgSTnDvlz3OvphkP&index=2_

## SysML as an OMG standard

SysML is a modeling language created by the OMG consortium, this is an open standard. 
__System Engineering__ _SysML_ was created to represent systems, this involves, the software, the electronics, the mecanics, the control plant. On the other hand, _UML_ was built to model Object-Oriented software.

_SysML_, as _UML_, is a graphical (visual) modeling language. Even all these diagrams, including _Simulink_, look the same, they mean different things either in subtle ways or way too different. Because the models can be used in order to documeting things or in other cases, such as, _code generation_ they mean the behaviour of the system.

in _SysML_ and _UML_, the model is different and the views or diagrams are snapshots of specific elements of the model and their relationship. While in _Simulink_ everything you are seeing is part of the model somewhere, this is called one-to-one correspondace between the model and the view. 

in _SysML_ and _UML_, the model is a tree (data structure), organized in a structural way with their respective relationships, this tree is more a graph.
This is considered a strength of _SysML_ because you dont to represent everything in a view when the system is very large.

__Metamodel__ set of rules that tell you the legal compositions for the elements, this tells us, if a model is feasible or not.

## Available diagrams

__Requirements Diagrams__
__Behaviour Diagram__: How the system evolves in time, what are the systems' reactions. It has the following diagrams: 
        _Activity_, State, Sequence and Use case

__Structure Diagram__: Relationship among the elements of the model. if a communication between two subsystem is required, then it's here where this communication has to be modeled as _structure diagram_, this communication end ports. but it's not stablished when or how the communication will be executed, because this is a behaviour. 

In _UML_ the core diagram is called the class diagram that's available from anywhere, while in _SysML_, this is called _Block Definition Diagram_. it describes the relationship among _blocks_. 
Again, in _UML_ there exists the _Structure diagram_, in _SysML_ this is called, _Internal Block Diagram_. It has to be only used in order to describe the internal structure of a _block_ in _terms of its compoments_ and the topology of communication among these components.
Both _Internal Block_ and _Block_ diagrams are gonna deal maily with block, which is an extensio of a _class_ in _UML_.
Block is an element of the design, can be _anything_.

__Parametric Diagram__ and __Requirement Diagrams__ do not exist in _UML_. 

## SysML v UML

in _UML_, there's the posibility to create profiles, _Stereotypes_. in _SysML_ there's no modeling element for _CPU_ or _Threads_, these Modeling tools are for generic description, not specific. 
in _UML_ this is done by extending the concept of a class, called restricted class, meaning, the class is restrict to a certain type of description, _CPU_ or _thread_.

### Requirement Diagram

It allow to place a requirement in its own box with certain properties, such as label (to item) and plain text. Two requirements can be connected, or/and design elements.
Documents can be generated out from _SysML_.
Keep in mind, the _SM_ in _SysML_ or _UML_ are not runnable and the _SysML_ tool and the _Standard_ are two different things.

## SysML diagrams

Each _SysML_ diagram is contained in a diagram frame, with headers, contents and Diagram description

## Papyrus

Make sure to set in _Eclipse_ to _UML/SysML_ perspective.

## -> LAB

- Let's start with _Block Definition_ diagram.
- Three files are created, they are all _XML_: the model, the diagrams and information about wich diagrams are open currently.
- In the bottom left, the model tree is seen with the current diagram.
- We can operate on the _model tree_ or in the _palette_ (on the far right of the window).
- Create a child model, then a package, the package has names such as, the name, _Functtional_, _Platform_, and _Mapping_.
- The already created diagram is place inside the _Functional_ package, and rename it as _System_.
- Inside functional, create a new _diagram_, a _block definition_ one.

## An embedded Model

it is a composition of three sides, the _functional description_, the _execution platform_ (hardware + OS + drivers + communication stack) and _mapping_ (Semaphores, thread and executables).So, that's why three packages has been created in the _SysML_ model.
The _functional_ view is independent, has to be, the algorithm has to be _independent_ from where the commands are coming or executed. Same thing with the _platform_, it has to be independent, for example, the communication protocol can change from CAN to Ethernet or viceversa. but _Mapping_ tells how the _functional_ and _platform_ are linked togheter.

### Package diagram

it's like a folder, in a way to organize the model elements or can be seen as well as namespace.

Thses packages can be organized many ways or the best to adjust to your project: what they contain. structure, behavior.
    _Hierarchy_ Logica design, physical design
    _IPT_ purpose of the elements, what things are needed for the verification.

no matter your style of _packaging_, after the macro view, some _subpackages_ can be create to describe the subsystem.

_SysML_ is used to trace relationships, not to describe the physical behaviour, this can be a box.

a __block__ has properties, operations, constraints, (not implemented in the tool) _allocation_, _requirements_ 

__Operations__  is similar as _UML_, the operations that the block or class has.

__Constraint__ compartment label.

__Values__ is the same as _attributes_ in object oriented programming, specifying its type, or either if they are public or private.

A _block_ cannot be "built" by other _blocks_, but it might referencing to another _block_. In programming it's seen as a class that is independent but reference by pointer to this class.

The hierarchy can be built as deep as necessary.

### BDD - Block Defintion Diagram

__Generic Association__ Simple relationship, two blocks cooperate in some way. The _association_ can be named, additional names such as _Role_ and _Multiplicity_ can be added.  _Role_ means what role the involved blocks play in the relationship, and _Multiplicity_ means, how many elements of certain _Role_ are involved in the relatioship.

__Composition Association__ represented by a filled diamon in the arrow, this is a children class, created from a father class, and it will be destroyed when the father class is destroyed. Talking at _block_ leve, one _block_ is created from a parent _block_ and destroyed when the parent _block_ is destroyed.

__Aggregation Association__ is the class referencing to another class that exists independently. While this is _block_ referencing.

__Generalization/Specialization__ inherits everything from the parent _block_ and it can override some.

### IBD - Internal Block Diagram

Defines the use of _Block_ in a composition.

## ->LAB

- in the _Functional_ package add a _SysML_ child, _new block_.
- Rename this _block_ as _System_.
- We're assuming it's a system elevator. 
- Blocks can also be dragged and dropped from the _Palette_ (ModelElements).
- Rename this as _Elevator_.
- on, _Associations_ pick, _directComposition_ and link _System block_ and _Elevator block_, name this association _itsElevator_.
- Scrolling down, search for _multiplicity_, in _System_ with _1_ is enough and on _Elevator_ side write 4.
- *__Keep in mind__*: _Delete_ means truly _delete_ and _Hide_ just, delete from view. at higher level the names are different for _Delete_ and _Hide_,  "Delete from _model_" and "Delete from _view_".
- Delete the _diagram_ because everything is in _System_ and already _associated_ in the model.
- _Drag_ and _drop_ another _block_ and call it _floorController_.
- _Drag_ and _drop_ another _block_ and call it _mainController_.
- Associate with _directComposition_ the _floorController_ and the _System_. _Multiplicity_ in the _floorControler_, _n_.
- Associate with _directComposition_ the _mainController_ and the _System_ with _multiplicity_, 1:1.
- The _floorController_ will call the _mainController_ when the _elevator_ is called. and the _mainController_ close or open the door, as well as the _floorController_ opens or closes the door.

## Port

_Standard Port_ already existing in _UML_, it was meant to represent software, so, it is an interaction point. in OOP, this ports are used by using operation whithin an interface.
_Flow Port_ are a _SysML_ concept, Things dont work in here by calling operation, values, signals, currents, water can be exchanged, whatever physical thing.

- from _PortAndFlows_ in Palette, dran a _FlowPort_ and placed in _floorController_ and call it _Request_. in _SysML_ properties, selects the direction as _Out_.
- Add another _FlowPort_ and place in _mainController_ and name it, "floorRequest", in _directions_, select it as _In_.
- These ports have to be typed. in _UML_, select _type_, select _additional resources_, _UML primivite types_

### Describing Internal Behaviour

_LINK: https://www.youtube.com/watch?v=YcxYLinFZ3Y&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=3

- in _model exploring_ click, new _diagram_, new _internal block_ diagram.
- Name it as _Elevator_. This diagrama already starts with a frame diagram. The _attributes_ or _blocks_ that are associated with the _Elevator_ are already included in the _model explorer_.
- fomr Model explorer, _drag_ and _drop_ the _port_, in both, mainController and floorController.
- from _Edges_ on the Palette, pick _connector_ and link the two ports, and you can even name the connection.
- the _mainController_ also have to dictate if the door is Locked or not.
- __The ports can be added graphically__ in the _diagram_ by _drag_ and _drop_
- from the _palette_, section _Nodes_, drag and drop the _flowPort (IN)_, name it as _doorloock_, type it as _boolean_.

.......................

### Add types that arent listed - primitive types

- in the _model explorer_, right click, _import_, _register packages_. in here there are additional types.
  ...............................
- from the _palette_, drag and drop, _FlowPort (OUT)_, name it, DoorLockCmd, type it as boolean.
- in the _FloorController_ package, create a new _Block Definition Diagram_ and name it as _FloorControllerBB_. The purpose of this diagram is only to show the _FloorController_ and its components.
- Drag and drop a _block_ and name it as _FloorDoorController_. Drag and drop another _block_ and name it as _ButtonLightController_.
- This two last _blocks_ are associated to the _FloorController_ as _DirectComposition_.
- Select _FloorController_ block and add an _Internal Block Diagram_ and name it _FloorController_.
- Bring the _FloorDoorController_ and _ButtonLightController_ inside the _FloorController_ _Internal Block Diagram_.
- Add a _flowport_ to the _FloorDoorController_, name it as _DoorLock_ and type it as _boolean_.
- then Link the _input_ port of the _FloorController_ with a _connectior_, this is called a delegation, because the input coming on that port is handled by _FloorController_'s inner component.

..................................

### What if the port has to handle a _structure_ type of data or _array_.

- Go to root, create a new _package_ and name it, _Types_.
- Go inside _Types_ package, create a new _Block Definition Diagra - BDD_, name it, _Types_.
- On _Palette_ -> DataTypes, drag and drop _DataType_ and name it, _Coord3D_.
- From _Palette_ -> ModelElement, drag and drop _Property_ and name it, _X_, and type it as _double_.
- Add another two _Properties_ and name them, _Y_, and _Z_, as type, _double_. __This is for an structure___.
- for __Enum__, drag and drop _DataTypes_ -> _Enumeration_, name it as _SemapphoreTypes_ (Not your typical _mutex_ type).
- Drag and drop _EnumerationLiteral_ and name, _RED_, _YELLOW_, and _GREEN_.
- for __Something else___, drag and drop _PrimitiveType_ and name it, _my32bitInteger_.
  __For arrays__
  go to the port itself and scroll down until you find _multiplicity_. (but this is not how you are supposed to do it.
  ..................................

_LINK: https://www.youtube.com/watch?v=YcxYLinFZ3Y&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=4_

## ->LAB

- Go to _System_ diagram, and add one more _block_, name it, _MotorController_, Associate this _block_ with the _Elevator_ _block_. 
- Still inside _Functional_, create a new _package_, called _MotroController_, name it as _MotorController_, the place the _MotorController_ block inside its package and add a new _Block Definition Diagram_ and name it, _MotorControllerBB_ (MotorController Black Box).
- Add a new _FlowPort_ and name it, _MotionCommand_, in the _Properties_ window or tab, select _SysML_ and in Direction, select _Input_.
- Add a new _FlowPort_ and name it, _Speed_, type it as _Real_.
- in the _Types_ _package_, rename _SemaphoreType_ as _MotionCmdType_. rename the _EnumerationLiteral_ as well, as: _UP_, _DOWN_ or _STOP_.
- So go back to the model, where the _FlowPort_ is listed, go to _types_ and select _MotionCmdType_.
- ........................................
- go to _Functional_ package again, add a new _Package_ called _MainController_. 
- in this package ad _Block Definition Diagram_ named _MainControllerBB_.
- Drag and drob the _MainCtronller_ block inside the _MainControllerBB_.
- Add a _FlowPort_ named _MotorCmd_, which is gonna be an _output_ port, and pick its type as _MotorCmdType_. 
- Add another _FlowPort_ named _MotorSpeed_, type it as _Real_ and it's an _input_ port.
- Go back to _Elevator_ and drag and drop the _MotorController_, this will be imported with its own port.
- Add the ports of _MotorCmd_ and _MotorSpeed_ that has being just created for the _MainController_ and connect them..

__Next step__ is to extend the _SysML_ language in order to describe those _SysML_ port according to our _System_. So, a _domain extension_ has to be created.

## -> Lab

- Create a new project and call it, _FunctionalPortProfile_ and among the available languages, select _Profile_.

The goal is to create _Stereotypes_, a custome _domain_ specific extensions. It's also possible to add our own types that define the _profile_. This is done by specifying a custome behaviour of a functional port.

- Drag and drop a _Stereotype_ from _Palette/Classifiers_ and name it, _FunctionalFlowPort_.

__What a Functional Flow Port does?__
It's a custome _FlowPort_.

- on _Model Explorer_, Select _profile_, right click, _Import_, _Import Register Profile_, _SysML_.

For Papyrus, _SysML_ is a profile in _UML_. That's why when creating a custom _FlowPort_, a _SysML_ element, _SysML_ has to be imported.

- _OK_, just select: _ModelElements_, _Blocks_, _PortAndFlows_. then click _OK_.
- from _Model Explorer_ Window, drag and drop, _FlowPort_, on top of _FunctionalFlowPort_ and linked them togheter using _Generatlzation_ _Relationships_, found on _Palette_.

__What if we want to extend a (UML) Port?__

A port is a metaclass, so:

- On _Palette_/_Classifiers_, _Import Metaclass_, _Port_. In this case, there's no _generalization_ relationship but _Extension_ because it's coming from a _Metaclass_.

Let's go back to the _FunctionalFlowPort_ block, and add a new _Porperty_, name it, _min_ and, type it, _Real_. In order to use _Types_ in this _profiling_, a package needs to be imported, as follows: on _Model Explorer_, _Import_, _Import Register Packages_, and select  _JavaPrimitiveTypes_ and _SysMLPrimitiveTypes_.

- Add also _max_ and _validity\_time_   and type them as _Reals_.
- Rename the package, _FunctionalPortProfile_ and save it.

This _mechanism_ can be used also to define a custome _electronic board_, a _communication network_ or a _CPU_.

__How is it imported in a project?__

- Open the project,
- on _Model Explorer_, _SysMLmodel_. right click, and select _Import_, _Import Package From Workspace_. and select your _package_.
- On _Properties_ window, select _Profile_ tab and click on the _plus_ button. In this window, the custome package will be listed, and by deploying it you can your custom _profile_ model (not the name of the port).

__How to use it?__

- Let's go to the _MainController_ which has the two ports, select the _MotorSpeed_ port and on the _Window_ below, _Properties_, select the _Profile_ tab, click on _plus_ button and move from left to side the _FunctionalFlowPort_.
- by expanding this profile, all properties added can be seen and their respective values can be added.

__Why should we have custom elements or ports?__

1. Minimal and Maximum values are, as said, it's good information to extract. So, a document can be generated out of this description to generate a software specifcation.

(__SIDE NOTE__) Eclipse can translate this _UML_/_SysML_ diagram into a text. and _Code_ are just text, so under the _OMG_, a code generator is part of the _model-to-text_ translator, _code_ is just a special type of _text_.
2. This extension features can be used in _Code generation_ as well.  

__How would you use your code capabilites based on this definition?__

1. Simple way of extending nominal test that provides requirement coverage is boundary and robustness testing.
2. There's a price to pay, the number of tests grow, first, linearly and then grows exponentially. Huge numbers of test cases, but if we have a boundary conditions in the model, those test can be generate automatically (because it's also a text generator)

## Operations

Assuming the _MotorController_ is a piece of software,

## ->LAB

- open the _MotorController_ block
- From _Palette_/_ModelElements_, drag and drop an _Operation_ on _operations_  of the _Block_ _MotorController_, name it, _MotorCmd_
- Scroll down and add _Owned parameters_. Name: _direction_, Direction: _in_, and type: _MotionCmdType_ (custom one). 

(_SIDE NOTE_) in order to see the operation in the block, it's important to bring the Ports inside the _block_.

- Keep adding  _Owned Parameters_, this time, name it, _return_, Direction: _return_ and type it as _boolean_.
  This is a classical way of how _OOP_ was seeing until _interface_ has arrived. so, an _interface_ is to provide operations in a list as part of the _public_ interface of the class.
  _interface_ is a list of methods for which the class is to provide an implementation and identify a set of coherent methods by functionality. For example, _MotorController_ may have a list of operations that are actually related with the motor operation, but another set of operations can be related to maintenance. It's a good practice to have these in two different interfaces for usability purposes. Another reason is: if someone is calling this _MotorCmd_ operation (this isnt a single command, it's a list of operations), and if its indicated that another component in the system will use some of those operations, if they are left as operations, there are two ways to say those other components will need this operation, either __association__ by usage of stereotype or in __behaviour diagram__ where the sequence of operations is actually shown. The thrid method is somewhere in between, the operation are partioned according to the interface, so, it can be indicated that the remote component only requires those operations that are part of that interface. This can lead to a bad requirement of dependancy of re-use.

An __interface__ is a type defintion, the package where this _type_ is created depends on the level of re-use is desired. if it will be at _system_ level then it has to bre create inside _Type_ package.

## -> LAB

- on _Model Explore_, on _Type_ package, add a new _BDD_ named _interfaces_.
- from _Palette_, under _PortAndFlows_, drag and drop _Interface_, name it, _MotorOps_, as it were a _block_, an _interface_ can have _properties_ and _operations_.
- fomr _Palette_, under _ModelElements_, drag and drop _Operation_, call it, _MotorCmd_, as any other operation, _parameters_  can be added, i.e.: _Direction_ and _return_.
- ..............
- Let's go to the _MotorController_. A way to say the motor is providing some operations is by saying it's proving an implementation of the _interface_ and this can be done by the usage of a _port_.
- Drag and drop a regular _port_ and name it, _MotorOperations_, scroll down to _type_ and from the package _Type_ select _MotorOps_.
- Let's go the _Elevator_, main diagram. On _Model_ window, under _MotorController_, look for the port that has just been created, _MotorOperations_ and drag-and-drop into the _motorController_ block in the diagram. Given the fact in our system, the _mainController_ is the one will commad the _motor_. 
- In the _MainController_, add a "regular" (_standard_) _port_ that will be called _MotorClient_.
- By typing this port as _MotorOps_, it's saying that the _mainController_ is providing the implementation of this interface, instead what's desired is that the _MainController_ calls this implementation. 
- .............
- Go to _Type_ package, in the _interfaces_ diagram, drag-and-drop another _block_ and named it, _MotorClientIf_.
- On _Palette_, under _PortAndFlows_, drag-and-drop _usage_ and associate it to _MotorOps_ interface.
- Go back to _MainController_, select the port _MotorClient_ and type it, as _MotorClientIf_, in the box next to this, __Required__ interfaces list, it shows that _MotorOps_ is required. This is tool based, on _Rhapsody_, the requirement is added direclty without the creation of another type.
- Go back to _Elevator_, drag-and-drop the _MotorClient_ port and connect with _Connector_.

(__SIDE NOTE__) Everything is done with _Internal Diagrams_ and _Definition Diagrams_.

## SysML Ports

As seen there are two types of ports, the _standard_ ones and the _Flow_ ones. The first one is operation oriented, for software description, ans for required or provided interface as well. On the other hand, the _FlowPorts_ are used for signals and physical signals, like flow of water of flow of electrical current. 

Both ports can be typed as _interfaces_ or _blocks_.

- A _port_ is a property, so it has a type.
  In other softwares when a _Port_ is proving an interface is shown with an specific diagram.

### FlowPort with flow specification

An flow port can be _in_ or _out_ or _both_: _inout_, the last means that the port is undecided yet, or it can mean a complex structure of relation such as: RS232, which is a bunch of wires. so in this way a _flow_ port can describe that inside the communication will be held in different directions, _duplex_ or _simplex_.
A _flow_ specification indicates a set of flows so over this port different flows are gonna occur. This type of port can be only connected to the same type of port and its direction has to be complementary

## Structure Diagrams

_LINK: https://www.youtube.com/watch?v=nBqOsobBQig&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=5_

In this last part, Parametric Diagrams will be picked topic, as well as Activities, Sequence and State.

### Parametric Diagrams

These are used to express constraints between value properties.  The parametric diagram is created and then associated to the input and output pins. This  can be used for accelerations, velocities, breaking force. However this type of diagram is barely or never used. that ones studied are more than enough. In practice, _transformation_ of diagrams is used in _SysML_.
While in _Simulink_, a similar behaviour can be expressed using diagrams, but the blocks are equations, keep in mind, equations are constraints as well, which make a "parametric" diagram into something executable, in real life, this type of diagrams arent executable neither simulator. Parametric Diagram is a type of structure diagram

## Behaviour Diagram

### Activity Diagram

Specifies a sequence of steps that transform a set of inputs into a set of output through a control sequence of actions. Similar to data flows but activies have additional features.
In _SysML_, there are two types of data flows: _streaming_ and _nonstreaming_.

__Streaming Data Flows__ All inputs and ports represent signals, functions or set values that progress over time, like in _Simulink_, where input ports don't represent _tokens_, they represent _signals_, so there's alwaysa a value wheever a block is triggered for its computation. This trigger can be any event, without waiting for a _token_ availability.

__Nonstreaming Data Flows__ The input and ports are _tokens_, single value items that are processed and produce another single value output, _queue_.

Each Action in _SysML_ can be associated with a number of possible refinements. An action can be an instance of an operation behaviour, meaning the action is described in a general form, it can be a written sentence. 
__Formal definition of actions__ so an action maybe a function signature
It's pretty much an operation, with input and output arguments (as return value).
In activity diagrams, the operations of the _blocks_ can be organized and defined how these operations get togheter to produce outputs, the _how_ is dictated by a __Control Flow__ that allows the operations to go parallel or sequential.

_Tokens_ are available on all the controll  inputs and outputs.
An action can be represented hierarchical defined by another activity diagram, this way building hierarchical description of complex behaviours.

__Common Actions__ 
Typical example of an event is a clock rising edge, so a periodic clock generates a train or sequence of events. 
Another example shaft positions.

### Notation

- _Fork_ duplicates input tokens from its input flow.
- _Join_ waits for an input token on __all__ input flows and then places all on the outgoing flow.
- _Decision_ waits for an input _token_ on its input flow and places it on one outgoing flow based on guards.
- _Merge_ waits for an input token on __any__ input flows and then places it on the outgoing flow

### Input/Output streams

When set as _optional_, we dont need to wait until this activity has value ready, this is a signal, it's a continuos set of values. usually this a flow, water or current (it's a pin that can be sampled all the time).

## Sequence Diagrams (part of Behaviour Diagrams)

_Interaction_ diagrams and they are seen as data flows or control flows, they are used to represent complex computations or behaviours at system or subsystem level thant it might involve cooperation and/or conditions of actions. These diagrams are similar to state diagrams.

(SIDE NOTE) everytime users wants more and more features, so at the end there's a significant overlap of significant capabilities.

__Sequence Diagrams__ it's protocol oriented in order to fix something. This is not for complex combinations, but this are for linear protocols, to represent scenarios in a given order: startup or error handling or communication protocols.
How the objects in the system are cooperating with one another, actors such as operators, the customer can be added next to the objects. The interactions among objects are represented as set of messages that are exchanged horizontally and define how the control is  flowing from object to object. 

Actions are expressed in the vertical domain. i.e.: A message arrives requesting an operation, and as part of its execution another request has to be done. in here synchronous and asynchronous flow of control can be performed.
![[Pasted image 20220915180902.png]]

Another thing in here is the capability to define _time constraints_ make it ideal for Real-Time System specification.
It's not limited to a single diagram or one time execution, subdiagrams can be deployed, even conditional executions can be added.

## State Machine

this defines the state of each individual object or subsystem in the model. While _Activity diagrams_ are about the _Emerging_ from cooperation of _more_ operations no matter if those operations are in a same class object or different ones. _Sequence_ diagrams are about cooperation of _different_ objects. 
So, _State Machine diagrams_ focus on a single object or subsystem. How this single subsystem will react to events and its state will change. so, it's about single reactions to events and the object's state.

the _End state_ of an object means the object is _destroyed_.
An _State_ description can be associated to the Entire system or to one block or to one subsystem or to one operation.

Let's assume the whole _Elevator_ will be described:

__Creating States__

- On _Model Explorer_, block _Elevator_, right click, select _New Diagram_, new _StateMachine_ diagram.Name this diagram as _ElevatorModes_.
- From _Palette_/_Nodes_, drag-and-drop _Initial_ psudo state, and keep drag-and-drop-ing _states_ according to the _Elevator_'s behaviour.
- From _Palette_/_Transition_, drag-and-drop _Transition_ to link _states_ and _nodes_.

__Creating super states__

- By drag-and-drop-ing from _Palette_ a state inside another _state_ it can create a _super state_.
- or by drag-and-drop-ing from _Model Explorer_ states have been already created inside a _state_ in the diagram, can make the _state_ a _super state_.

__Setting-up Transitions__

- By selecting a _transition_ it's possible to see its property such as: _Name_, _Trigger_, _Guard_ and _Effect_ (action that is performed when this transition takes place).
- By clicking on the _plus_ button on _Trigger_ section, it pops a window where the trigger that's been created will be set-up. Things like _Name_ and _Event_ to be linked to are required.

__Create Events__

- on _Model Explorer_, select _Functional_ package and add _new SignalEvent_, name it, _StartupComplete\_ElevAt0_. Singal it as under _Functional_. Name this Signal as _startupcomplete_.
- Back in the _State_ diagram, with a _transition_ element selected, by double clicking the _trigger_ already created, in the _plus_ button, select the Event created.

__Adding Guards__

- Under the _transition_ properties, click on the _plus_ button and name it, _current\_on_. 
- on _Constraint Element_ section, click on the _plus_ button and _OpaqueExpression_, name it, _current\_on_. 
- On the laguage section, click on the _plus_ button, and select _Natural Language_ and write as _body_, "the current is on, power is on".

__What can be fount inside a state?__

- it's possible to define the _entry_, _exit_ and _do activity_.

## Requirements Diagrams

These are boxes with identifiers and texted lines to connect them together, this way defining relationships among them, derivation, refinement from high level to low lever. The most important thing in here is the capability to trace requirements to design objects, to activities, to state diagrams and shit.

_LINK: https://www.youtube.com/watch?v=s8CNB97sWOc&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=6_

So, the controllers and system were the topic of interest and all of them are funtions, so far, the physiical architecture that is gonna support the execution of the _SysML_ that has been done.

## Diagraming the physical architecture

The folowing tells things about how the physical architecture will be struct. At each floor there's a board that is connected to the elevator controller using sometype of _datalink_, a CANbus could be the one. There's another board inside the cabin that's also connected to the main _Elevator_ controller through CANbus. and there's another board at the top that controls the electric motor.

## -> LAB

- on _Papyrus_, _File_, _New_, _Papyrus Projects_, name it, _ExectutionPlatformComputationProfile_, select _Profile_ as Diagram Language.
- From _Palette_/_Classifiers_, drag-and-drop an _stereoptype_, name it _board_. 
- In order to work with _SysML_ features we need to impot _SysML_ profile. (Already done previously but just in case, here it goes again):

__Import SysML profile__

- On _Model Explorer_, right click on _profile_, _Import_, _Import Registerd Profile_, _SysML_, and select: _ModelElements_, _Blocks_, _PortAndFlows_. 

__To Make__ *__Board__* __a special type of block__

- From _Model Explorer_, drag-and-drop _Board_, and connect them from _Board_ to _Block_ as a _generalization_.

There are several levels of how we can push this description, should the all other caracterics of board such as: type of microcontroller, the amount of memory, number of IO connections, speed of the microcontroller.
Addional stereotypes can be created, for example:

- _MicroController_, as a type of _block_.
- _Memory_, as a type of _block_.
- _NetAdapter_, as a type of _block_.
- _GenericIO_, as a type of block.

_Enumerations_ to be added:

- _MemoryType_
  
  - _RAM_ (Enumeration Literal).
  - _ROM_ (Enumeratio Literal).

- Into the _StereoTypes_ Block for "Memory", add _Properties_: "size" and "type", and type them "Int" and "MemoryType".

- Add to the "MicroController" type, the following properties, "Maker", "model" as _String_ and, "speed" as _Integer_.

- Add another _Enumeration_, name it, "MicroMakerType", and add _EnumerationLiterals_ and name them as, "ARM", "Toshiba", "Microchip".

- Back into "MicroController", under the property "Maker", type it as, _MicroMakerType_.

- Save the Profile.

__Execution Platform Comm Profile__

- Create a new papyrus project and name it "ExecutionPlatformCommunicationProfile".

- Click on next and select _UML Profile Diagram_ (check this always when creating a profile).

- Create a _Stereotype_ named "SerialLink", this has to be associated to point-to-point connections or broadcast networks.
  (__SIDE NOTE__) for a point-to-point, it could be good to use a connector, instead for a network, it's better to use a _block_, because a network is a complex communication system.

- Import _SysML_ (the classical subprofiles).

- From _Palette_/_Classifiers_, _Import Metaclass_ and selecta _Connector._

- So this "SerialLink" can be an extension of _Connector_ or a generalization of _Block_.

- To this "SerialLink" add a property, and name it, "speed".

- Add different _Stereotypes_ and name them, "Ethernet" and, "CAN bus". These two are _Generalization_ associated with "SerialLink".

As part of the _ExecutionPlatform_, the followings also have to be added:

- Operating System
- Device Drivers
- Communication Stack
- Middleware

# OSEK

it's a Standard for operating system that is popular in the automitve industry. It's different than traditional OS. OSEK is static, meaning, all configuration system needs to be known before hand, number of threads, resources, semaphores and so on. No dynamic creation of objects or forking something or dynamically allocating something else. 

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

Orange arrows represet the dependency of the blocks, meaning the entry of C is the output of A. But the real implementation turns to be this: 
![[Pasted image 20221005175730.png]]

A mechanism is required in order for B to process the all values produced by A, here is when buffer mechanism is deployed. When having multiple readers, one buffer isn't enough, an array of them is needed, popping many different problems. 

- How many values will be stored?
- 

## Testing

_link: https://www.youtube.com/watch?v=jhKd3FJM5Cc&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=8_

in the _V cycle_, left wing is refinement and development and right wing is verification and testing and blue lines lines (the horizontal ones the goes from left wing to the right one) are the planned verification and testing.

### Testing

should be a black-box, only known the inputs and the expected outputs accoriding to the requirements.  all requests should be cover (100% coverage).

### Instruction testing

is to make sure every single line of code has to be executed at least in one testing.

### Unintended Functionality

.....

### Functional Testing

A program is seen as functions that has inputs in a range and its respective output.
Impossible to test all possible inputs.

### Nominal testing

For each input a value is selected from the given range, they could be random or significants.

### Boundary testing

Values at the boundary of the range are most likely to produce errors, like a mechanical component and the test cases are: _4n + 1_, where n is number of input variables.

#### Robustness BV testing

sometimes it's better to take values even outside the range, like the Arianne 5 which wasnt supposed to go over a certaing variable. And now the number of test cases are _6n + 1_.

### Worst-case BV testing

test cases $5^n$ 

#### Worst-case + Robust BV testing.

test cases $7^n$

### Equivalence Classes

it's a weak test 

test cases: $\prod_X(\sum_X)$

### Weak Robust EC

test case: $(\max_x|\sum_X|) + 2n$

### Strong Robust EC

test case: $\prod_X(|\sum_x| + 2)$

### Combined with BV

text cases: $\prod_x4(|\sum_X| + 1)$

# Simulink Intro

_link: https://www.youtube.com/watch?v=-8CaGKwRLzQ&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=9_

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
