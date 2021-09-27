# List of terms
1. exogenous vs endogenous: advantages and disadvantages
2. Exogenous's frameworks
3. The advantages of BIP and JavaBIP

# To-do list
- What kind of properties will be use?
- Object considered?
- How describe properties, behavior of objects?
- What is the bad situation should be avoid

## List of papers specify safety properties:
### A. Safety properties for a general cloud application
Towards the Formalization of Properties of Cloud-based Elastic Systems [1]
  - **Objective**: three main open issues:
    - How to specify the desired elastic behavior of these systems;
    - How to check whether they manifest or not such an elastic behavior;
    - How to identify when and how they depart from their intended behavior
  - **Workflow**:
    - Provides an overview of cloud-based elastic systems, describing how they operate
    - Introduces CLTLt(D), the temporal logic used later for the formalization
    - Formally defines some general aspects of resources used in cloud-based systems
    - Illustrates the formalization of the properties that we have considered.
  - **Properties**: listed in detail
    - Elasticity
    - Resource Management
    - Quality of Service
  - **Comment**: they specified safety properties in detail and we can apply it into a specific system.
### B. Safety properties for a specific one
1. Formal Design of Dynamic Reconfiguration Protocol for Cloud Applications [2]
  - **Objective**: a novel protocol, which aims to dynamically reconfigure and manage running distributed applications
    - Ensure communication between virtual machines
    - Resolve dependencies by exchanging messages, (dis)connecting,
and starting/stopping components in a specific order.
  - **Workflow**:
    - The interaction between machines is assured via a *Publish-subscribe messaging system*. Each machine reconfigures itself in a decentralized way.
    - Two kinds of properties:
      1. Those allowing to focus on the protocol behavior for
        - Verifying that the final objectives are executed
        - Guaranteeing that the architectural invariants for a reconfigurable application are always satisfied
            - safety: page 25
            - liveness: page 25, 26
      2. Those verify that the progress/ordering constraints are respected
    - Example: LAMP
    - **Comment**:
      - Just a few property is specified (most of them focused on liveness and reachability)
      - LAMP app is not simple (my specification made it look simple)
      - They aims at the application reconfiguration >< we aims to coordination between components of a configuration

2. Modeling and Formal Analysis of Client-Server Application for cloud services [3]
  - **Objective**:
    - Determine the appropriate approach for layout and content adaptation regarding device and network characteristics
    - Describe the client-Cloud interaction by using a formal modeling approach;
    - Validate and verify (model checking of properties) the high-level specifications
  - **Workflow**:
    - CCIM model: integrate various components that are designed in a loosely coupled way
    - Specify some reachability, liveness and safety properties
  - **Comment**: just a few property is specified

3. Home, SafeHome: Ensuring a Safe and Reliable Home Using the Edge [4]
  - **Objective**: design and implement a system to manage and coordinate components inside a smart home
  - **Workflow**:
    - Specify safety properties in a declarative way: p.2
    - Specify routines of commands in an imperative way
  - **Result**:
    - A mechanisms ensure that under concurrent routines and device failures, the smart home behavior is consistent (e.g., serializable) and safety properties are always guaranteed.
  - **Comment**: just a few property is specified
---
## Discussion
1. To specify properties:
  - Determine components of the system
  - Specify how the components interact with others
  - Determine unsafe states of the system, related variables
  - Specify the safety properties to avoid the unsafe states using a declarative language.
2. Next weeks:
  - Understand deeply each properties in the [1] pp
  - Specify safety properties for LAMP applications following the properties in the [1] pp
  - Continue to prove the equivalence
  - Write down definition of these words
