# Requirement Analysis

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
