# DevOps
Unites development and operations teams to automate and accelerate the build, test, and release of software.
- **Developers**: Programmers managing and adding features to the code repository ("don't consider deoployment environment")
- **Operators**: Managing the release, testing for errors, maintenance, uptime ("don't know how the system works")

DevOps is a combination of cultural philosophies, practices,
and tools
It is about anything that makes the process of releasing software fast and with high quality
Devs and Ops should work together more often
## Software release process
1. Plan
2. Code 
3. Test 
4. build
5. Deploy 
6. Operate & Monitor 

## Release Process 
**Challenges**
- Can include a lot of manual works
    - Testing 
    - Release creation 
    - Deployment and configuration

## Benefits

- Faster deployment 
- Reduced risk
- Faster repair
- Higher productivity

## DevOps Automation 
### Continuous Integration
Each time a change is pushed to the main repository: the system is executed and tested 
Benefits:
- Faster to fix/find bugs
- Changes shared with the whole team (?)
- Might create a "quality culture" in the development team (?)
### Continuous Delivery
Builds on CI by automatically packaging every successful build into a deployable artifact and pushing it to one or more staging (or pre-production) environments
### Continuous Deployment 
A new release is made every time a change is made to the main repository, and after running CI and Continuous Delivery correctly.
(Aka. Do Continuous delivery **and** automatically deploy every successful build)

### Benefits
- Faster customer feedback
- Faster problem solving
- Reduced costs 

### Drawbacks (business reasons)
- Incomplete features, and the competitors shouldn't know about it 
- Customers may get irritated by many changes 
- Synchronization of releases with business cycles 

### Infrastructure as Code 
Infrastructure model written in a machine-processable language

- Visibility
- Reproducibility
- Reliability
- Recovery

(aka. a config file that defines the settings of the server/deployment environment)


