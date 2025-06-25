# Software Quality
It's the degree to which software **conforms to its requirements** and meets the needs of its users.
- High quality software meets it's requirements which in turn accurately reflect stakeholder needs 
- Quality is about **aligning** the software with both its formal requirements as well as true user needs

## Error 
A human mistake made by a developer
- Eg. misunderstanding a requirement and coding the wrong specification

## Defect 
Flaw or imperfection inserted into software due to an **Error**
- An example is a bug in the code or issues

## Failure
The termination of the software's ability to function as intended.
- Occur when the software executing encounters a Defect
- The user experiences the software failing in some unintended way

## Software Quality Management
- **Quality planning**: Defining quality objectives, requirements, targets and planning of quality assurance
- **Quality control**: Techniques to measure quality characteristics, review work products, and find defects
- **Quality assurance**: Processes to ensure compliance with procedures
- **Quality improvement**: Defect analysis and process enhancements.
- **Resources**: Infrastructure, tools, training that enable quality processes 
- **Standards**: Regulations, models, certifications that guide quality work 
- **Culture**: Values, behaviours that encourage quality mindset

# Software Evaluation
The making of a judgement about the amount, number or value of something
- Assessment, judgement, rating..
## How is software Evaluated
- Points of view:
    - Functionality, Performance, Quality, Usability, Mantainability...
- Approaches:
    - Quantitative, Qualitative...

# Software Metrics
- **Comparability**:
    - Allows comparasions between software systems
    - Metric values can be compared 
- **Intuitive interpretation**
    - What the metric tells you about the system 
    - A metric shold be interpreted also by a non-expert in the domain
- **Simple and efficent computation**
    - Be able to compute the metric with little effort

## Examples 
- **LOC**: Lines of code 
- **KC** Metric suite (Chidamber and Kemerer)
    - **Weighted Methods per Class**: The sum of complexity in a classes methods 
    - **Number of Children**: The number of immediate subclasses a class has
    - **Coupling Between Object Classes**: The number of classes to which a class is coupled
## Examples 
- **LOC**: Lines of code 
- **KC** Metric suite (Chidamber and Kemerer)
    - **Weighted Methods per Class**: The sum of complexity in a classes methods 
    - **Number of Children**: The number of immediate subclasses a class has
    - **Coupling Between Object Classes**: The number of classes to which a class is coupled

- **McCabe Cyclomatic Complexity Metric**
    - A quantitative measure of independent paths in the source code of the software product 
    - An independent path is that path which has at least one edge that has not yet been traversed in any other path 

- **`V(G) = E - N + 2`**
    - `E`: number of edges
    - `N`: number of nodes 

- **McCabe Cyclomatic Complexity Metric**
    - A quantitative measure of independent paths in the source code of the software product 
    - An independent path is that path which has at least one edge that has not yet been traversed in any other path 

- **`V(G) = E - N + 2`**
    - `E`: number of edges
    - `N`: number of nodes 

- Tools for Software Evaluation and Quality Assessment 
    - "Understand"
    - SonarQube

# Quality Attributes
## Performance Efficency 
The degree to which a software performs its functions within the specified time and is efficient in the use of resources under specified conditions

- **Time behaviour**: Degree to which the response time and throughput rates of a software, when performing its funcitons, meet requirements 
- **Resource utilization**: Degree to which the amounts and types of resources used by a software, when performing its functions, meet requirements 
- **Capacity**: Degree to which the maximum limits of a software parameter meet requirements

# Code Smells and Refactoring
Indicators of potential issues in the code over time 
- Results of poor or misguided programming (eg. not conforming to SOLID)
    1. **S**ingle Responsibility
    2. **O**open/Closed
    3. **L**iskov Substitution
    4. **I**nterface Segregation
    5. **D**ependency Inversion

## Examples 
- Large/God Class 
- Long Method 
- Duplicate Code 
- Switch Statement 
- Feature Envy 

## Refactoring 
Performing structureal changes to improve the quality of code while external behaviour remains unchanged

# GRASP Patterns
**G**eneral **R**esponsibility **A**ssignment **S**oftware **P**atterns
- Creator
- Controller 
- Information Expert 
- Low Coupling 
- High Cohesion

*Other patterns*
- Polymorphism
- Pure Fabrication
- Indirection
- Protected Variation


# RAD - Rapid Application Development 
- **Objective**: Produce useful software quickly based on prototyping
- **Main idea**: Software developed in ==increments== where each increment provides new functionality
- Emerged as an alternative to Waterfall in 1980's and 90's 

## Characteristics
- Specification, design and implementation are **interleaved** 
- Software developed as a **series of versions** with s**takeholders involved** in version evaluation
- **User interfaces** are often developed using an **IDE** and **graphical toolset**

# Agile Software development 
## Methods 
- Reduce overhead in software processes (by limiting documentation)
- Respond quicly to changing requirements
- Practical guidelines
    - Focus on code rather than design 
    - Iterative approach to software development 
    - Deliver working software quickly 
    - Evolve software quickly to meet changing requirements 

> [!IMPORTANT]
> **Agile Manifesto**
> We are uncovering better ways of developing software by doing it and helping others do it.
> Through this work we have come to value:
> - **Individuals** and **interactions** over *processes* and *tools* 
> - **Working software** over *comprehensive documentation*
> - **Customer collaboration** over *contract negotiation*
> - **Responding to change** over *following a plan*
> 
> That is, while there is value in the terms on the right, we value the items on the left more.

## Applicability
- Suitable for **small to medium size** software
- Tightly-integrated teams
- Clear commitment from the customer to become involved in the development process 
- Not a lof ot external rules and regulations that affect software (security rules, high-risk products)

## Issues 
- **Keep customers involved in the development process**
- Keep the **team members collaboration high** in the **development process** 
- **Prioritize changes** in presence of multiple stakeholders
- **Maintain simplicity** (avoid extra work)
- **Contracts** may be a problem as with other approaches in iterative development 

## Software Maintenance
- Maintainablity can be more difficult when there is no priority on formal documentation.
- Can agile methods be used effectiely for evolving a system in response to customer change requests?

## Extreme Programming 
The best-known and most widely used **agile method**
- Extreme approach on **iterative development**
    - New versions built several times a day 
    - Increments are delivered every 2 weeks to customers 
    - All tests must be run for every build and the build is only accepted if tests run successfully
### XP & Agile
- Incremental development through small, frequent releases 
- Customer Involvement means full-time customer engagement with team 
- Change supported through regular software releases 
- Maintaining simplicity through constant refactoring of code 

### User Stories 
Informal general explanation of a software feature written from the persective of the end user.
`As a [person], I [want to], [so that]`

### Requirements Scenarios 
- In XP, a customer or user is part of the XP team and is responsible for taking decisions on requirements 
- User requiremens are expressed as scenarios or user stories 
- These are written on cards and the development team break them down into implementation tasks. These tasks are the basis of schedule and cost estimates
- The customer chooses the stories for inclusion in the next release based on their priorities and the schedule estimates 

## Scrum 
A framework based on agile principles 
Structured in 3 phases:
1. **Initial planning phase**: the general objectives of the project are established, and the software architecture is designed
2. **Sprint cycles**: where each cycle develops an increment of the system
3. **Closure phase**: wraps up the project, completes required documentation. System help frames, user manuals and assesses lessons learned from the project 

### Sprint
- Short time period of 1-4 weeks in which an iteration is performed 
- A set amount of work is completed
- Sprints help teams follow the agile principles:
    - "*delivering working software frequently*"
    - "*responding to change over following a plan*"
- The starting point for planning is the product Backlog
- The **selection phase** involves all of the project team, to select the features and functionality developed during the sprint

### Elements 
- **Roles**:
    - Product Owner 
    - Scrum Master:
        - Arranges daily meetings
        - tracks the backlog 
        - records decisions 
        - measures progress 
        - communicates with customers and team
    - Developers
- **Scrum Artifacts**:
    - Product Backlog
    - Sprint Backlog
    - Increment
- **Scrum events**:
    - Sprint, Sprint Planning, Daily goal, Sprint goal, Sprint review, Sprint retrospective
- **Scrum**: A daily meeting with the whole team to share information and describe progress/problems/plans

### Benefits 
- The product is broken down into a set of manageable and understandable chunks 
- Unstable requirements do not stall progress 
- The whole team has visibility of everything -> so team communication improves
- Customers see on-time delivery of increments and gain feedback on how the product works 
- Trust between customers and developers is established and a positive culture is created in which everyone expects the project to succeed

# Plan-driven VS Agile 
- Most processes mix plan-driven and agile
- Deciding the balance depends on multiple factors
    - Detailed specification necessary?: plan-driven 
    - rapid feedback and delivery of software? agile 
    - Team size? 
        - smaller and good communication: agile
        - bigger teams and large systems: plan-driven


