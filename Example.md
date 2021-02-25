# LAMP example
1. Description
2. Structure
3. Properties

### 1. Description

### 2. Structure
2.1. Virtual Machine  
At the IaaS layer, Virtual machines are used to host the application following below proposition:  
VM.start(.) - VM.boot(.) - VM.ready(.) - VM.stop(.)



2.2. Applications' components  

### 3. Properties
Variables and Parameters:  
R = number of running virtual machines  
L = value of the system load  
T_e: eagerness time  
T_rtx: resource thrashing time
số lượng tomcat connect tới 1 database
3.1. Properties for VM
- When a proposition is requested, all the other requests for this machine cannot occur until the request for the next proposition end. For example, when G(VM.start(1) -> (~VM.start(1) ^ ~VM.ready(1) ^ ~VM.stop(1) ^ ~VM.end(1)) U VM.boot(1))

- The value of R must not change if neither VM.start(.) nor VM.stop(.) occur

- If L increase/decrease in T_e time, R will increase/decrease
