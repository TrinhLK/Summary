# LAMP example
1. Description
2. Structure
3. Properties

### 1. Description

### 2. Structure
***2.1. Virtual Machine***  
At the IaaS layer, Virtual machines are used to host the application following below proposition:  
VM.start(.) - VM.boot(.) - VM.ready(.) - VM.stop(.) - VM.delete(.)

States:
- Starting
- Active
- Running
- Stopped
- Shutdown
- Deleted
- Suspended, Error


Properties: *Status*: percentage of the usage

***2.2. Systems' components***  
Components:  
- Database: MySQL
- Tomcat
- Apache
- Applications

Components states:  
- Undeployed
- Deployed
- Inactive
- Active
- Failure

Components behaviors:  
- deploy, undeploy
- start, stop
- configure
- fail

***2.3. Coordinator***  
aims:
- Coordinate the execution among VMs and components for allocating the resources
- Track the VM's status

### 3. Properties

Variables and Parameters:  
R = number of running virtual machines  
L = value of the system load  
T_e: eagerness time  
T_rtx: resource thrashing time
T_bru: time for bounded resource usage.
số lượng tomcat connect tới 1 database


***3.1. Properties for VM***  
**Structural properties**
1. When a proposition is requested, all the other requests for this machine cannot occur until the request for the next proposition end. For example, when G(VM.start(1) -> (~VM.start(1) ^ ~VM.ready(1) ^ ~VM.stop(1) ^ ~VM.end(1)) U VM.boot(1))

2. The value of R must not change if neither VM.start(.) nor VM.stop(.) occur

3. If a component/VM provider is failed, a new component/VM will be created.

4. All the required components/VM of the failed one will connect to new provider.

**Behaviors properties**
1. if any VM is overloaded then the jobs will be passed to the under-utilized VM.
2. If there are more than one VMs for a component types, new executions will be distributed to a less status VMs.
3. If L increase/decrease in T_e time, R will increase/decrease correspondingly

***3.2. Properties for Components***

**Structural properties**

1. Apache cannot be started before the start-up of the Tomcat provider.
2. Tomcat cannot be started before the MySQL provider.
3. If all the database components fail, the other components will be stopped

**Behaviors properties**

1. Active components cannot be connected to inactive components
2. After configuring, the components will eventually start.
3. An application cannot be deployed in two or more different Apache servers.
