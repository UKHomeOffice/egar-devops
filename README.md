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



## Continuous delivery
We will aim to have the code merged several time a day to catch merge conflict as early as possible.

Smaller the change, faster delivery and faster overall product progress.

Every commit produces artifact via automated build triggered from VCS.

All artifacts are stateless




## Continuous deployment

### Environments 
There are 4 environments with different use cases.

##### PRD
Live Environment
Blue/Green deployments:
- via code merge from UAT by User Researcher
- DNS switch after all E2E tests passed

Currently no canary deployments make sense due to lack of users.
Possible for future use.


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

Branching out:
- Developer starts working on code which is branched out from PRD branch. 
- In case PRD is behind in terms of latest features (it should not last longer than 1 sprint), UAT should be the base for developemnt.
- SIT is considered unstable and should not be the base for any development.

Each developer works locally. Ideally whole stack is brought up on the local development machine.

If not possible, any non offensive/non destructive integrations will reach relevant parts of UAT environment.

If not possible, any offensive/destructive integrations will reach relevant parts of SIT environment.


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

### Functional testing

##### Unit testing
Each function should have unit tests written covering as many edge cases as possible.
100% code test coverage is not possible in real world, byt we are aiming for it.

##### Integration testing
E2E tests.
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

