# Safety properties
What is safety properties?
Why do we need safety properties?
How to determine safety properties?

### 1. What is safety properties?
Safety properties: ensure that "bad things" do not happen.  

System must follow properties to *avoid incorrect behaviors*

To do this, the controller observes all the system events and enforces it to respect the properties, which are regarded as constraints imposed by the system.

Model checking is used to verify that the properties are respected during the protocol execution. (Some properties in p.111)

### 2. Why do we need safety properties?
To verify that the system is safe.  
Steps of the verification:
1. express safety properties using a formal language (i.e, Communicating Sequential Processes (CSP))
2. translate the specification of a safety property to a deterministic Labeled Transition System (LTS) to ensure that all the paths of an LTS with identical traces are ended at the same state.
3. modify this LTS by adding a violation state to detect violations

### 3. How to determine safety properties?
- Determine components of the system
- Specify how the components interact with others
- Determine unsafe states of the system, related variables
- Specify the safety properties to avoid the unsafe states using a declarative language.
