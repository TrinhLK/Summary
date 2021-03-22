
Exercise 8 (Canonical formulæ). Write the LTL formulæ for the following properties (p and q are state
properties):  
***1. (Safety) p holds always.***
(Something bad never happens.)  
**VS5**. "A VM/component cannot be duplicated."  
*never VM_id.isDuplicated()*  
**CB1**. "Active components cannot be connected to inactive components"  
*never active_components.connectTo(inactive_components)*  
- Always have at least one tomcat server available
- It is never the case that the failure of all VMs or all MySQLs


***2. (Guarantee) p will happen.***
(Something good will eventually happen.)  
**CB3**. "After configuring, the components will eventually start."  
*always (component_id.configure() -> eventually! component_id.start())*

***3. (Obligation) If at some point p fails to hold, q will eventually hold.***
(If something bad happens, you will be compensated.)  
**VB4**. "If the VMs load is over a threshold in T_bru time, no new jobs is executed in this VMs until the load down."  
*always (!(VM(id).load <= threshold) -> new_job.wait() until (VM(id).load < threshold))*  
"if load > threshold -> eventually go down"  


***4. (Response) Whenever p happens, it will eventually be followed by q.***
(The system always responds to p by q.)  

**CB2**. "The components disconnect all related components before configuring"   
*related_components.disconnect() after component(id).configure_request()*  

**VB1**. "if any VM is overloaded, and have a new_job then the new_job will be passed to the under-utilized VM."  
*always (VM(id).load > R_max -> next_event  
((VM(id1 != id).load < R_max).isActive()) (new_job.executeOn(VM(id1)).*  

**CS3**. "If all the database components fail, the other components will be stopped"  
*always(!database.active() -> next other_components.stop())*  

***5. (Persistence) If p happens, q will eventually hold forever.***
(An occurence of p forces the system to eventually stabilise at q.)   


***6. (Reactivity) p happens infinitely often, unless from some point on q holds forever.***
(System has two modes: it is responsive unless it permanently switches to another, e.g. standby, mod)  

Whenever the server down, it will restart unless the server is active permanently.

**CS1-2.** "Tomcat cannot be started before connected to a MySQL provider."  
*(always !Tomcat(id).start()) -> next_event (Tomcat(id).connect(MySQL(id))) (Tomcat.start())*
