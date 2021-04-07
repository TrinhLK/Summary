### 06/04/2021
Sau khi gọi Spontaneous port thì chuyển tới state Failing, tạo một transtion từ failing tới Error. Sau đó synchronize makeError of C_MySQL and stop() of Tomcat

Việc chuyển data dạng BIPActor ở bản hiện tại là bug và Larisa đã fixed nó, liên hệ với Larisa để biết chi tiết

Ví dụ hiện tại cho bài báo thuộc dạng quá đơn giản nên ko đáng để được publish, do đó phải làm một cái to - chính là cái hiện tại để chứng minh rằng việc áp dụng cách tiếp cận đc đề xuất là hợp lý.
- Thiết kế ban đầu chỉ có stop, ko có cái trung gian giữa fail và Error --> Chương trình ko chạy
- Sau khi chỉnh sửa có thêm thì nó sẽ chạy

### 31/03/2021
Simon:
Chỉ có configure, không hiện start sau đó là vì DataWise chuyển đồng thời cả Monitor và VM --> không nhận được data --> không check đk được \
stop: cannot be invoked when using data in guard. \
If I follow the image that using Monitor, I can make a synchron between Monitor and MySQL.fail because it's Spontaneous port: No, you can transfer data from this port to other.

engine take value of data parse to component to select. If add a port require some data, provide data not fit -> break.
define both in guard and transition \

failing -> error
ask larisa for fixing bugs
reuse to validate of the example
manner that it can solve the
system has to work with reasonable assumption
Sau khi gọi hàm
### 22/03/2021
- Rewrite the LAMP case study separately (instead of using inheritance)
- Followed the Pub-Sub case study of Simon to make queue commands

I re-designed the system several times but it didn't work as I expected.
- I setup that if MySQL fail, Tomcat should stop before connecting to another MySQL. There is two cases happened:
1. Tomcat auto-connect to another MySQL and ignore Stopping
2. After MySQL fails, Tomcat never reacts again.
- I tried to follow the Pub-Sub example but it seems lack the GlueBuilder file and the MainFile following the design.

Questions:
- Spontaneous port is the actor makes the system environment's change. Thus, it shouldn't appear in the Glue file, which specify how the components interact with each other.
- How to prove by hand the equivalence between a function and the set?

The most important thing in JavaBIP is specifying GlueBuilder.

---
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
