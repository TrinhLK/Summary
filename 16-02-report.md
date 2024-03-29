# To-do list
1. Write down the definition of:
  - configuration
  - specifications
  - model
  - system's state
  - Coordination
  - reconfiguration
  - component's interface
  - adaptation of apps

Resource >< environment
2. Check again the comment part (the comparison)
3. Write some safety properties

# Doing
## A. Definitions
1. Product configuration process  
Configuration consists in deploying the system, i.e. in placing each of its elements at a location, configuring the hosting machine so that the software element can run properly and establishing the connections among the system components.

  - Given:
    1. set of components including: set of *properties*, *ports* for connecting to other components, *constraints* (port constraints and other structural constraints)
    2. description of the desired configuration
    3. possibly some criteria for making optimal selections
  - Build: a configuration that satisfy all the requirements
    - a set of components
    - a description of the connections between the components.


2. Specification: a set of documented requirements to be satisfied

3. Model: is a simplified representation of a software process. Each model represents a process from a specific perspective.

4. Program state:
A computer program stores data in variables, which represent storage locations in the computer's memory. The contents of these memory locations, at any given point in the program's execution, is called the program's state.

5. Process coordination: is the mechanism describe how components interact with others

6. Cloud applications: are distributed applications composed of a set of VMs running a set of interconnected software components.  
After deployment of these applications, some reconfiguration operations are required for setting up new virtual machines, replicating some of them, destroying or adding virtual machines, handling VM failures, and adding or removing components hosted on a VM.

7. Component's interfaces:  
At the lower layer, the system has a pool of components where each component provides some services via its interfaces.

8. The adaptation of apps
An application can be adapted to evolve in the execution environment by  
1) adding or removing components,  
2) changing some of the existing ones,  
3) changing the connections among the components, or  
4) reallocating components to differ- ent execution locations.

9. reconfiguration  
Since the structure of components can be used at run time to discover services or adapt components in order to move and execute them at new locations, correct dynamic recon- figuration becomes an important aspect of the system execution.
System reconfiguration can involve any combination of these four kinds of adaptation in **8**.


## B. Check the comparison
1. Formal Design of Dynamic Reconfiguration Protocol for Cloud Applications [2]  
- **Problem statement**:
  - Existing protocols manage static applications which do not require to be changed after the deployment phase.  
  - Cloud users need protocols that able to modify applications during their execution and take into account the changes that can occur such as the failure of some virtual machine.
- **Purpose**:
  - A novel protocol, which aims to dynamically reconfigure and manage running distributed applications
- **Analysis**:
  - *Self-adaptive* application: Dynamically reconfigure and manage running distributed applications  
  ==> Same as our purpose: correct coordination of access to cloud resources among concurrent cloud application entities.
  - Differences:
  | Their approach| Our approach |
  |---------------|--------------|
  | Dynamically change the configuration at execution time (elasticity) | Coordinate the connection between resources of a specific configuration at execution time (reliability)  |
  |Propose a protocol to reach the purpose| Provide a toolchain supporting developers to write their protocol (and need an Example to prove)|
- **Comment**: If we consider that the resources changing make a new configuration --> the coordination is similar with reconfiguration
- If we provide a fixed number of resources and let the system self-adaptive when some failed, the coordination and reconfiguration are different.
## C. Some safety properties for our research
1. a started component cannot be connected to a stopped component
2. Apache cannot be started before the start-up of the Tomcat provider.
3. Tomcat cannot be started before the MySQL provider.
4. If all the database components are failed, the other components will be inactivated
5. If a component/VM provider is failed, a new component/VM will be created.
6. All the required components/VM of the failed one will connect to new provider.
---
## Other terms  
### 1. Autonomic computing of cloud

A loop with steps:
  1. monitor the system or the infrastructure
  2. analyze the situation according to the monitoring and a set of models
  3. plan and execute actions in consequences

Autonomic Manager (AM)  is based on a constraint solver which aims at finding the optimal configuration for the modeled XaaS

### 2. Reconfiguration  
Need to answer Five questions:
1. why software has to be reconfigured?  
 hardware or software fault tolerance, mobile users, dynamicity of software services, etc
2. what should be reconfigured?  
low-latency applications and systems
3. how should it be reconfigured?
4. where should it be reconfigured?
5. when to reconfigure it?
reconfiguration operations: instantiating/destroying VMs, adding/removing components

### 3. Reconfiguration agents:  
The reconfiguration agent may generate an alternative or a new configuration if it is feasible to adapt the change in requirements or environment.

Each VM embeds a local reconfiguration agent that interacts with the other remote agents. For each component, the VM agent tries to satisfy its required services by connecting them to their providers in order to start the component.

Each component may provide services via exports and require services via imports

### 4. Correct-by-Construction(CbyC):  
Correctness by Construction (CbyC), is a combination of formal methods and incremental developments.  
CbyC is a development style that allows application to progressively evolve by refinement via small steps. The key of the approach is the correctness warranty that the application behaves as specified at each step.

It is proved to be a promising method thanks to the benefits obtained while developing a software, such as a decrease of ambiguity (the major cause of bugs), an avoidance of repetition, management, etc. The method has been applied in industry, demonstrating its effectiveness for reducing defects and increasing productivity, especially in order to develop security and safety-critical applications

---
## Discussion
- A configuration might live in some system's states
- Applications can be dynamically reconfigured and managed using specific protocols (strategies)
- Each protocols can use a specific strategy to communicate components (i.e, publish-subscribe messaging system).
- The communication can be implemented following exogenous or endogenous approach
