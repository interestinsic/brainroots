# Software Testing 
The process in which you execute your program using data that simulate user inputs

## Types 
There exist multiple types of testing that check different characteristic of the system
### Functional Testing

Structured in a cycle of 4 testing elements
1. Unit testing: Check software units in isolation, developed by the programmer.
2. Feature testing: Units are integrated into features.
3. System testing: elements are combined into a working version of the total system, checking the interactions between features.
4. Release testing: when the system is packaged for release to consumers, that is tested to check if it works as expected.

### User Testing 
No more mention in the slides
### Performance and load Testing 
No more mention in the slides
### Security Testing 
No more mention in the slides

## Approaches
### Black-box testing 

#### Equivalence partitioning
This involves the identification of sets of inputs that will be treated in the same way by the program.
- Check things that are the same, with multiple combinations. 
- Check combinations that are supposed to give the same result
#### Boundary value analysis 
Testing boundary values for invalid partitions 
- The behaviour at the edge of the equivalence partition is more likely to be incorrect than the behaviour within the partition 
- We check all edge cases that should be checked for correct input 
> [!Example]
> Consider a system that accepts ages from 18 to 58
> We check the minimum value 18, Just below the minimum value: 17
> Maximum value: 56...


### White-box testing 

#### Statement Coverage
- **Definition:** Measures the percentage of executable statements in the code that have been executed by the test suite.  
- **Goal:** Ensure every line of code runs at least once.  
- **Limitation:** May miss untested decision outcomes or logical paths.

#### Branch Coverage
- **Definition:** Measures the percentage of control-flow branches (e.g., `if`/`else`, `case`, loops) that have been exercised by the tests.  
- **Goal:** Ensure each possible branch (true/false, each `case`, loop entry/exit) is tested.  
- **Advantage:** Catches untested decision logic that statement coverage can overlook.
 
## Test automation
Automated testing is based on the idea that tests should be executable 
- An executable test has *input data* to the unit being tested, *expected result* and a *check* that the expected result is returned.
    - **Arrange**, **Action**, **Assert**
> [!Example]
> 
> ```python
> def test_zeroprincipal(self):
>     #Arrange
>     p = 0; r = 3; n = 31
>     result_should_be = 0
>     #Action
>     interest = interest_calculator(p, r, n)
>     #Assert
>     self.assertEqual(result_should_be,
> ```

## Test-driven development 
TDD is an approach to program development that is based around the general idea that **you should write an executable test for code that you write** before you write the code.
- Works best for development of individual program units 


