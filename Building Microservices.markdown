# [Building Microservices](https://www.amazon.in/Building-Microservices-Designing-Fine-Grained-Systems-ebook/dp/B00T3N7XB4)
![](https://images-eu.ssl-images-amazon.com/images/I/51e6hCWFZNL.jpg)

Here are the notes that I made while reading the book. These concepts are not something which you can understand and digest all at once. But here is my attempt to make revision of the book easy.

I am not a copyright expert and I am unsure if its ok to copy excerpts from book and publish publicly. Tell me if this is not allowed. Please don't sue me :)

### What are Microservices?
Microservices are small, autonomous services that work together.                   
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
Reuse of functionality. Same microservice can be used for different purpose.                                       

### Shared Libraries                   

### Disadvantages:                   
You loose true heterogeneity               
Unless using dlls, you cannot deploy a new library without deploying the entire process.         
What is ok?
Shared Code that isn't specific to business domain and needs to be reused is fine.                   
What's not ok?
Shared code to communicate between services is NOT good at all.                                       
Modules                   

Talks a bit about module and process level decoupling.                               
TODO
### Evolutionary Architect                   

Architects are incharge of making sure we have a joined-up technical vision, the one that delivers the system customer needs .                   

Architects have a direct impact on the quality of systems, on their organisation's ability to respond to change.                   

Be worried about what happens between the services and be liberal about what happens inside them.                   

### A Principle Approach                   

Making decisions in system design is all about tradeoffs, and microservices architecture gives us a lot of tradeoffs to make.                   

### Principles                   

Principles are the rules you have made to align what you are doing in to some larger goal, and will sometimes change.                   
Example: 12 factor app                   
Fewer than 10 principles are good                                       
Practices                   

Practices sometimes reflect constraints. Example Only Centos is allowed.                   
The key point is that there is value in having overarching ideas that guide how the system evolves, and in having enough detail so that people know how to implement those ideas.                   

### The Required Standard                    

Define what is a "good citizen" service in your system ?                    
"It needs to be a cohesive system made of may small parts with autonomous life cycles but all coming together." - Ben Christensen, Netflix               
Define clear set of attributes that each service should have.                   
Monitoring                   

This has to be a system-wide view and not service-specific view.                   
All services should emit health information in same way - keep it standardised.                                       
Architectural Safety                   

We cannot afford for one badly behaved service to ruin the party for everyone.                   
Services should shield themselves from unhealthy, downstream calls.                   
Governance through code                   

TODO
                   

### Technical Debt                   

Credits for this section: martinfowler.com
Doing things in a quick and dirt way to deliver a project instead of doing it in the right way leads to technical debt.                    
Like a financial debt, the technical debt incurs interest payments, which come in the form of the extra effort that we have to do in future development because of the quick and dirty design choice.                    
We can choose to continue paying the interest, or we can pay down the principal by refactoring the quick and dirty design into the better design.                   
A mess is not a technical debt though. Messy code designed by people ignorant of design principles is just bad code.                    

Sometimes, technical debt is introduced because vision changes.                   

Having some view as to the level of debt, and where to get involved, is important.                                       

### Governance and leading from centre.                   

Architects need to make sure that there is a set of guiding principles that match the organization's strategy.                    
Make sure that these principle do not require working practices that makes developers miserable.                    
How to Model services                   

### What makes a good service - loose coupling and high cohesion.                   
Loose Coupling: Change is one service should not require a change in another.                   
High Cohesion: We want realted code to sit together and unrelated code to sit elsewhere. If we want to change something, we should be making change at one place.                               
Bounded Context                   

In each bounded context, there are things that do no need to be communicated outside that bounded context.                   
Each bounded context decide wha models to share with other contexts.                   
Microservices cleanly align to bounded contexts.                      
Integration                   

Keep you API technology agnostic                   
Make your service simple to consume                   
Hide internal implementation details                                       

### Random Tips:
Shared Database - avoid as much as possible.                                
Synchronous Vs Asynchronous -                    
RPC - :(                   
REST & HTTP :(                   
Async :)                    
Read this book: Enterprise Integration Patterns - (Addison Weasley)        
Services as State Machines      

### DRY and Perils of code sharing in Microservices                   
If your shared code ever leakes outside your service boundary, you have introduced a potential form of coupling.                   
Using common code like logging libraries is fine, as they are internal concepts that are invisible ot the outside world.                    
Don't voilate DRY within a microservice but be relaxed about violating DRY across all services.                               
Client Libraries                   

Netflix client libraries include service discovery, failure modes, logging and other aspects that aren't actually about the nature of the service itself.                   
Make sure that these client libraries do not lead to coupling between services.                   
Clients are incharge of when to update their clint libraries.                   
.... blah blah
He talks about bunch of other stuff that I am still to read and implement in my company. Here is a list:

### TODO (Still to Read)
Splitting a Monolith
Deployment
CI and CD                    
Environments                   
Service Configuration                   
PaaS                   
Containers, vagrant, docker and what not    
