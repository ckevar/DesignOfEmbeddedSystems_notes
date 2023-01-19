# Testing

*LINK: [Lesson 3: Intro to testing and Functional testing - YouTube](https://www.youtube.com/watch?v=jhKd3FJM5Cc&list=PLohWCZQwiEVpgTkxTsgSTnDvlz3OvphkP&index=8)*

In the v-model we have left and right side, the left side is refinement and development, right side is verification and testing. Tests should be planned from early in the development, as the requirments are defined the test should be too.

## Functional testing

or black-box testing, turning it into implementation independent. the inputs and outputs are knows as well as the expected properties of the outputs because it was written at requirement definition, what is unknown is what the internal algorithm does, not even the internal structure.
This type of testing is usually used at system level testing, subsystems, unit testing or for individual components.

It's also a requirement-driven testing, so when talking about *coverage*, it's about covering or meeting the requirement, and expected to have 100% coverage, meaning each single requirement has to be checked with the test. The quality of the test can be improved by laveraging information about the function that needs to be performed inside.

A *functional* testing leads to *structural* testing.

### Functional testing

We are gonna assume our program is a function with a given domain of inputs and output variables.
so, it can be represented as a function that takes one input variable from the domain space of interest.
Of course the *inputs* can be represented in a plane xy. the functions operates within a given range of the input variable which huge amount of values between the maximum and the minimum, in this way, it's impossible to test all possible values, because the set of input values is the muplication between all possible input values times all possible input values., in this case the picked values are only the maximums and minimums of each input variable.

### Nominal testing

Given an input domain, a set of values are picked that fall within domain space. This is what is typically done, and if on nominal test is run for each requirement, requirement might be fully covered. Keep in mind, it's not advisable to test a complex function with single input values. because the fact it works correct for a small set does not mean it works for well for all possible values.

Random picking from the domain is not effective, it could be a billion of possible values. by picking 1 or 100 values doesnt make any big change making the coverage rediculously slow. So instead of random picking, it's better to pick the significant ones, at the extreme points., boundary.

### Boundary Testing

This type of testing requires 2 assumptions:

1. the domain consists of independent values, meaning no correlation between the values of the inputs (which is not true).
2. All input values are continuos values, this is a relaxed assumption.
   The concept of testing near the extreme points is a stress testing, it's related to mechanical components testing.

For boundary testing, first, a nominal test is picked, the inputs *a* and *b* and a something that is in the middle. (nominal case is needed). All points are kept in their nominal values but one. pick 4 more values, two that are right at the boundary, near to the max and min within the range. making 4n + 1 number of test-cases.

Always assume that the inputs are independent of each other.

The number of tests is growing linearnly according to the number of input variables.

if we werent given any boundary requirements, we can take as boundaries the machine boundaries or the type-based boundaries (bits length of the type).

Sometimes boundary values and nominal values are the same (most cases). For booleans, doesnt make sense to do this boundary testing.
Sometimes boundary testing is not a good fit, because the specifications might split the range into chuncks (subdomains). So Boundary testing can be applied not over the overall range but the range of the small groups. and the convination among the subdamains within the input variables, this can lead to an even finer partition of the domain.

### Robustness Boundary Value testing

Sometimes, it isnt enough to test the values over the edge of the range and within it, but outside of it (**Arianne Case**). This type of tests are used when a system is dealing with a physical enviroment. It's quite common to see to put a "filter" when someone types on a keyboard the incorrect number and the system pop "INCORRECT NUMBER" than having a system that limits, for example, there's no filter to bound the input temperature.

The same assumptions have to be kept for this test as well, the inputs have to be independent, making the 6n + 1 test-cases.

### Worst-case BV testing

By dropping the assumption that input variables have to be independent but instead they are the combination of a set of input variables in boundary conditions, this is where the number of cases blows, 5^n test-cases, nominal values and boundary condition values.

(**SIDE NOTE**) typical amount of requirements is from hundreds to thousands. i.e, a 300 requirements might have around 140 input variables. not all input variables apply to all requirements.

### Worst-case + Robustness testing

It's a combination among worst case and robustness BV testing. All combinations of 7 values for all variables, making 7^n test-cases.

### Equivalence Classes (Weak)

**Is there any way we can leverage the fact the input domain is composed with subdomains?** Things like age, salary and, sex can be regrouped in order to have a **weak coverage** of the input regions with at least 1 input nominal value test for every input variable in one of the subranges, meaning one possible test for each possible interval. *Test cases* the maximum of the number of regions for every possible input variable max(n,m) where
n is the number of regios for i_1 and m is the ranges.

### Equivalence classes (Strong)

For this test, one nominal test for subregion is required. so the number of test-cases become the product of subranges times the input variables: 
                $\prod_X(\sum_X)$ 

this is a quantity that grows fast as well.

### Weak Robust EC

It isnt enough with at least one test for input variable but it's needed one test below the minimum and one test above the maximum per each input variable.

### Strong Robust EC

Beyond the fact that there's one test for each region, it's also required to have a test case below the minimun of each subrange of each input variable. becoming this way $\prod_X(|\sum_X| + 2)$ test-cases.

### Combination

All tecniques can be combined such as:

- Robust WCT + Robust EC
- Strong EC + Robust BV: $\prod_X4(|\sum_X|+1)$ test-cases. but it's too big for an actual real-life program. in a 5 variables with 5 partitions, the number of tests are 8 millions, which can lead to 3 months of testing if 1 sec is spent per test.

## Structural testing

Or white-box testing. Assume a piece of software needs to be developed based on given specifications followed by another software that is run in the functions, and now we have a program.
Structural test says that everysingle written code has to be executed at least once, this is one criteria for structural coverage. Other criterias can be defined: condition coverage, decision coverage and the mix of both..

**Why do we need structural testing**?

1. When functional testings is performed even at 100% coverage, it only covers a very small input space. Assuming it's needed to write a function that computes the two roots of a second degree function if they exist given *a. b* and, *c*. of course picking all possible values is impossible, it should be taken only a small portion of them.
2. No matter how good the process is, the requirements almost invariable are not gonna meet and arent often going to be up to date with respect to the code, meaning the code is implementing something that is not in the requirements, this could have two reasons, either that requirement was forgotten or the requirement hasnt been updated after another requirement needed to be covered that has just implemented. That's why some sections of the code are never executed when testing exisiting requirements, and the code is executing extra requirements that weren written in the requirements document, so it was never planned.
3. In the code, there still exist some functionality that is not written in the requirement and that is not meant to be written in it. This is called unintendent functionality

**How to solve those issues?** 
(respectively)

1. Check the code and try to understand why some parts aren't being executed and later write that requirement in the requirements document.
2. Everytime that structural testinng is performed and the outputs are not part of the original test plan, it has to be studied why it happens.

In the Aeronatics safety-critical system software, a criteria called MC/DC - *Modified Decision Condition Coverage* - coverage is performed. and Unless the system doesn't reach 100% coverage the system is not gonna be certified.

## Conformance Testing

As times pass by, this testing is being lost.
This test is about the implementation of the model being conformant to the model. like the *SM* and *SM* implementation, either implemented by an automatic code generator or written by hand. 
In many ways, the conformance testing is similar to structural testing because the internals of the system has to be known.
