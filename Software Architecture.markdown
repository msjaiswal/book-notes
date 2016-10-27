# Software Architecture 

- Working Software  >  Documentation
- Responding to change  >  Having a plan 
- How can we make irreversible things reversible. Exp :Migrations of database
- Example ares of the code. 
- Part of your responsibility to review commits. 

# Continuous Delivery 
- Your software is deployable throughout its lifecycle. 
- Your team priorities keeping the software deployable over feature development. 
- Anybody can get quick, automated feedback about production readiness of their systems anytime somebody makes a change to them. 
- You can do push button deployments of any version of the software to any environment on demand. 


- Automate everything that can be automated. 
- Solid configuration management. Go to any version anytime. 
    - Database schema, deployment scripts, absolutely everything has to go version control.
- Devops - lot of collaboration between ops team. 

# Continues Integration
- Every developer commits to main trunk
- Solid battery of test to find any bug to find bugs
- In case of prod failure, can you fix in 10 20 mins.
    - Always ready to rollback to previous version 
