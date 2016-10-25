# [Building Microservices](https://www.amazon.in/Building-Microservices-Designing-Fine-Grained-Systems-ebook/dp/B00T3N7XB4?tag=gludo-21)
![](https://images-eu.ssl-images-amazon.com/images/I/51e6hCWFZNL.jpg)

#### Disclaimer
Following are the notes that I made while reading the book. These concepts are not something which you can understand and digest all at once. But here is my attempt to make revision of the book easy.

### What are Microservices?
Microservices are small, independently deployable, autonomous services that work together.
Small and focussed on doing one thing well.
Microservices takes the approach of Single Responsibility Principle to independent services.

### How small can it go ?
Smaller services => More number of services => more independence => More operational complexity.

### Autonomous
Can be deployed independently
All communications via network calls.
Exposes an API

### Technology Heterogeneity
Different part of systems can use different technology stack if needed for better performance. But multiple technologies comes with an overhead - operational understanding of multiple technology stacks.

### Resilience
Microservices can provide resiliency by introducing redundancy.

### Scaling
One part of the system can move to another machine.

### Ease of Deployment
Individual microservices can be deployed independently in contrast with deploying whole Monolith 

### Organization
Different microservices can be owned by different teams.

### Composability
Reuse of functionality. Same microservice can be used for different purpose. Unix Philosophy.

### Shared Libraries

#### Disadvantages:
- You loose true heterogeneity.
- Unless using dlls, you cannot deploy a new library without deploying the entire process.
- What is ok?
  -  Shared Code that isn't specific to business domain and needs to be reused is fine.
- What's not ok?
  - Shared code to communicate between services is NOT good at all. 

### Modules
- Talks a bit about module and process level decoupling.            
- TODO

### Evolutionary Architect
- Architects are incharge of making sure we have a joined-up technical vision, the one that delivers the system customer needs. 
- Architects have a direct impact on the quality of systems, on their organisation's ability to respond to change.
- Be worried about what happens between the services and be liberal about what happens inside them.

### A Principle Approach
Making decisions in system design is all about tradeoffs, and microservices architecture gives us a lot of tradeoffs to make. 

**Principles**
- Principles are the rules you have made to align what you are doing in to some larger goal, and will sometimes change.
- Example: 12 factor app
- Fewer than 10 principles are good 

**Practices**
- Practices sometimes reflect constraints. Example Only Centos is allowed.
- The key point is that there is value in having overarching ideas that guide how the system evolves, and in having enough detail so that people know how to implement those ideas.

### The Required Standard 
- Define what is a "good citizen" service in your system ? 
- "It needs to be a cohesive system made of may small parts with autonomous life cycles but all coming together." - Ben Christensen, Netflix               
- Define clear set of attributes that each service should have.


### Monitoring

- This has to be a system-wide view and not service-specific view.
- All services should emit health information in same way - keep it standardised. 

### Architectural Safety

- We cannot afford for one badly behaved service to ruin the party for everyone.
- Services should shield themselves from unhealthy, downstream calls.

### Governance through code

- TODO
                  
### Technical Debt

- Credits for this section: martinfowler.com
- It's a metaphor to understand the efffects of writing bad code under certain circumstances.
- Doing things in a quick and dirt way to deliver a project instead of doing it in the right way leads to technical debt.
- Like a financial debt, the technical debt incurs interest payments, which come in the form of the extra effort that we have to do in future development because of the quick and dirty design choice. 
- We can choose to continue paying the interest, or we can pay down the principal by refactoring the quick and dirty design into the better design.
- A mess is not a technical debt though. Messy code designed by people ignorant of design principles is just bad code.
- Sometimes, technical debt is introduced because vision changes.
- Having some view as to the level of debt, and where to get involved, is important. 

### Governance and leading from centre.

- Architects need to make sure that there is a set of guiding principles that match the organization's strategy.   
- Make sure that these principle do not require working practices that makes developers miserable. 

### How to Model services
#### What makes a good service - loose coupling and high cohesion.

**Loose Coupling**: Change is one service should not require a change in another.
**High Cohesion**: We want realted code to sit together and unrelated code to sit elsewhere. If we want to change something, we should be making change at one place.            


### Bounded Context

- In each bounded context, there are things that do no need to be communicated outside that bounded context.
- Each bounded context decide wha models to share with other contexts.
- Microservices cleanly align to bounded contexts.   

### Integration

- Keep you API technology agnostic
- Make your service simple to consume
- Hide internal implementation details 

### Random Tips:
- Shared Database - avoid as much as possible.             
- Synchronous Vs Asynchronous - 
- RPC - :(
- REST & HTTP :(
- Async :) 
- Read this book: Enterprise Integration Patterns - (Addison Weasley)        

### Services as State Machines      

### DRY and Perils of code sharing in Microservices
- If your shared code ever leakes outside your service boundary, you have introduced a potential form of coupling.           
- Using common code like logging libraries is fine, as they are internal concepts that are invisible ot the outside world.
- Don't voilate DRY within a microservice but be relaxed about violating DRY across all services.            
### Client Libraries
- Netflix client libraries include service discovery, failure modes, logging and other aspects that aren't actually about the nature of the service itself.
- Make sure that these client libraries do not lead to coupling between services.
- Clients are incharge of when to update their clint libraries.
- .... blah blah. 



### TODO (Still to Read)
He talks about bunch of other stuff that I am still to read and implement in my company. Here is a list:
- Splitting a Monolith
- Deployment
- CI and CD 
- Environments
- Service Configuration
- PaaS
- Containers, vagrant, docker and what not    


### Microservices at Scale
- Failure is inevitable.
- Instead of trying to avoid failures, design for resiliency. 
- With monolithic systems, health is binary. For MS based architectures, ask yourself "what happens if this service goes down?"
- Embrace and Incite Failures
- Netflix uses Chaos Monkey to simulate failures. 
  - Sweat in peace so that you dont blood in War. 

#### Techniques for Handling Failures:
- Timeouts.
  - Wait too long and you will slow down the system. 
  - Give up too quickly, a working call might appear faulty.
  - Having no timeouts can hang your system!
- Circuit Breakers
- Isolation
- Idempotent

#### Scaling
- Verical Scaling i.e. bigger boxes
- Splitting Workloads
  - Maximum one microservice per box. Preferred Option.
- Load Balancing  
  - Useful when there are multiple boxes serving a single microservice.
- Worker based systems

#### Scaling Database
- Scaling for Reads
  - Most services are read heavy.
  - Caching. Read Replicas.
- Scaling for Writes
  - Sharding
- CQRS - Command Query Responsibility Segregation

#### Caching
- ....

#### Autoscaling
- Reactive or Predictive
- Benefits: Cost Saving

#### CAP Theorem
- Pick any two: consistency, availability, and partition tolerance.
- Sacrificing Consistency
  - These are eventually consistent.
- Sacrificing Availability
  - Distributed consistency is hard. 
  - Distributed transactions, even harder.
- AP systems scale more easily and are simpler to build
- CP system require more work due to the challenges in supporting distributed consistency.

#### Service Discovery
- knowing where on earth everything is
- Gets complicated when we are constantly destroying and deploying new instances of services.
- Strategies: 1. "I am here" .... 
- Common Solutions:
  - DNS
  - Dynamic Service registries
    - Serices registers themselves with some central registry.
    - Zookeeper, Consul 
- Whatever system you pick, make sure you have tools available that let you build reports and dashboards on top of these registries to create displays for humans, not just for computers.

#### The Self-Describing System
- Have a place where humans can record information about the service.
- Getting a picture of our system and how it is behaving is important.
- Making this information readily available is key to managing the complexity at scale.

### Bringing it all together
- Model Around Business Concepts. Use bounded contexts to define potential domain boundaries.
- Adopt a culture of automation. Automated testing.
- Hide implementation details. Services should hide their databases.
- Decentralize All the Things
  - Ensure teams own their services.
  - Use "Internal Open Source", allows people to change services owned by other teams.
  - Align teams to make Conway's law work for you.
  - Embrace Shared governance Model. All teams collectively share responsibility for evolving architecture.
- Independently Deployable
- Isolate Failure
- Highly Observable
  - We need a joined-up view of what is happening.
  - Monitoring, logs and stats. Levarage multiple vantage points to get a view of system.
- Go incrementally. Break your system apart piece by piece, learning as you go. And get used to it: in many ways, the discipline to continually change and evolve our systems is a far more important lesson to learn than any other.

### Miscellaneous:
- Differnce between Microserices and SOA: http://stackoverflow.com/a/33007471/578989
- Martin Fowler on Microservices:
  - (http://www.martinfowler.com/articles/microservices.html)
  - (https://youtu.be/2yko4TbC8cI)
  - (https://youtu.be/wgdBVIX9ifA)

