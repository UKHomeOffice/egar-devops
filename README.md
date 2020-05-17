# egar-devops
The central DevOps repo for the eGAR Beta development


# Dev Manifesto 

### Agile software development
*After [Agile Manifesto](http://agilemanifesto.org)* 

#### Manifesto for Agile Software Development
We are uncovering better ways of developing
software by doing it and helping others do it.

Through this work we have come to value:
- **Individuals and interactions** over processes and tools
- **Working software** over comprehensive documentation
- **Customer collaboration** over contract negotiation
- **Responding to change** over following a plan

That is, while there is value in the items on
the right, we value the items on the left more.


#### Principles behind the Agile Manifesto

*We follow these principles:*

- Our highest priority is to satisfy the customer
through early and continuous delivery
of valuable software.

- Welcome changing requirements, even late in
development. Agile processes harness change for
the customer's competitive advantage.

- Deliver working software frequently, from a
couple of weeks to a couple of months, with a
preference to the shorter timescale.

- Business people and developers must work
together daily throughout the project.

- Build projects around motivated individuals.
Give them the environment and support they need,
and trust them to get the job done.

- The most efficient and effective method of
conveying information to and within a development
team is face-to-face conversation.

- Working software is the primary measure of progress.

- Agile processes promote sustainable development.
The sponsors, developers, and users should be able
to maintain a constant pace indefinitely.

- Continuous attention to technical excellence
and good design enhances agility.

- Simplicity--the art of maximizing the amount
of work not to be done--is essential.

- The best architectures, requirements, and designs
emerge from self-organizing teams.

- At regular intervals, the team reflects on how
to become more effective, then tunes and adjusts
its behavior accordingly. 

-------------------------------------------------------------------------------
# 12 Factor App
Please see [here](https://12factor.net/)

-------------------------------------------------------------------------------
# CI/CD

### Continuous integration
All developers will have the same environment to work on, to minimise integration issues.

All developers are responsible for updating their development environment as often as possible/needed. 

All code is maintained in Version Control System (VCS).

Each task developers are working on should be achievable within 1 day.

If certain task takes longer, it should be split into smaller subtasks. 

Each code merge will contain the following components:

- Code

- Unit tests

- Integration definition(s)

- Documentation

  - Installing / Getting started
  - How to start developing
  - How to build
  - How to publish
  - Configuration 
  - Relevant links

- Pull/Merge request information

  - Description of changes
  - Relevant tickets
  - Tests description
  - Types of review required


-------------------------------------------------------------------------------
## Continuous delivery
We will aim to have the code merged several time a day to catch merge conflict as early as possible.

Smaller the change, faster delivery and faster overall product progress.

Every commit produces artifact via automated build triggered from VCS.

All artifacts are stateless

All artifacts are run as non-elevated user (root is forbidden)


-------------------------------------------------------------------------------
## Continuous deployment

### Environments 
There are 4 environments with different use cases.

##### PRD
Live Environment
Blue/Green deployments:
- via code merge from UAT by User Researcher
- DNS switch after all E2E tests passed


##### UAT
User Acceptance Testing
- stable environment
- receives changes upon User Researcher request


##### SIT
System Integration Testing
- developers merge and test code here
- if code change breaks environment developer reverts changes and works on fix locally
- in rare case it's not possible  
Rebuild nightly

##### DEV
Development environment



-------------------------------------------------------------------------------
## CI/CD Pipeline
Detailed description are available here: [PIPELINE](./PIPELINE.md)


-------------------------------------------------------------------------------
## Development process

#### Foundations
Each developer works locally. Ideally whole stack is brought up on the local development machine.

If not possible, any non offensive/non destructive integrations will reach relevant parts of UAT environment.

If not possible, any offensive/destructive integrations will reach relevant parts of SIT environment.


#### Branching out
- Branch names should have format of <Task-Number>_<short_description> and should be all lower case.
- Developer starts working on code which is branched out from PRD branch. 
- In case PRD is behind in terms of latest features (it should not last longer than 1 sprint), UAT should be the base for developemnt.
- SIT is considered unstable and should not be the base for any development.


#### Versioning
Each artifact will be tagged with unique ID. 
Microservices architecture allows to use various combinations of different versions of artifact to build the final system.

Therefore there will be only the Current Version of the System, with pre-defined microservices' tags.

All previous Version configurations will be stored in Version control for history and legal purposes.


#### Code
The following needs to be defined for code:
- formatting
- linting
- checking for existence of secrets
- etc.

#### Continous Documentation
- All functions have simple explanation 
- All files have information required to pick up code easily (quite fuzzy - define more)
- All parts of the system are documented and documentation is tested (e.g. by real users?)

-------------------------------------------------------------------------------
## Infractructure
All applications will run inside containers on ACP Kubernetes platform.
Databases will be provisioned by ACP


-------------------------------------------------------------------------------
## Technology stack
Deployments:
- AWS cloud (eu-west-2 region)
- Kubernetes (ACP cluster, non-prod & prod)
- Drone (Deployment Tool, ACP provided)
- Containers (Docker v...)
- quay.io (Artifact Storage & Vulnerability Testing)
- Hashicorp Vault (Secret Management)

Application:
- NodeJS v8.11 (Frontend)
- Python v3.7 (Backend)
- Django v... (REST API)

Data storage:
- PostgerSQL v9.6 (Main data storage)
- Redis v... (Frontend cache)
- S3 (attachement storage)
- S3 (backup storage)
- Glacier (historical backup storage)

Testing:
- Cucumber (Unit testing)
- Locust.io (Performance/Load testing)
- SSL Labs (Encryption testing)
- ClamAV (Antivirus scanning)
- OWASP ZAP proxy (security pipeline tool)


-------------------------------------------------------------------------------
## Data

### Storage 

### Backup & Recovery



-------------------------------------------------------------------------------
## Security


### Encryption

##### Encryption in transit
All traffic is performed via encrypted channels

All channels encryption is security approved

##### Encryption at rest
All data are encrypted at rest

All channels encryption is security approved


### Secret Management
No secrets are stored in plain text 

##### Environment variables

##### Secret Management System


### Security testing
Please see `Testing` section 

-------------------------------------------------------------------------------

## Testing
We are aiming for all tests to be automated and build into build pipeline 


### Functional testing


##### Unit testing
Each function should have unit tests written covering as many edge cases as possible.
100% code test coverage is not possible in real world, byt we are aiming for it.

##### Integration testing
E2E tests
When some sort of unit testing is not possible, end-to-end tests should cover the gap.

##### System testing

##### Sanity testing

##### Smoke testing

##### Interface testing

##### Regression testing

##### Beta/Acceptance testing


### Non-functional testing

##### Performance Testing

##### Load testing

##### Stress testing

##### Volume testing

##### Security testing

##### Compatibility testing

##### Install testing

##### Recovery testing

##### Reliability testing

##### Accessibility testing

##### Compliance testing

##### Localization testing




-------------------------------------------------------------------------------
## Operations

### Monitoring
- ACP provided Sysdig

### Logging
- ACP provided ELK
