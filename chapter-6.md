### Chapter 6 - Building Evolvable Architecture

> Architectures that evolve with the real world

### Mechanics

1. Identify Dimensions Affected by Evolution
	- Always consider the "-ilities" that are important
2. Define Fitness Function(s) for Each Dimension
	- Automated or manual: documented decisions that deserve ongoing attention
3. Use Deployment Pipelines to Automate Fitness Functions
	- Make sure developers can deploy and verify fitness functions
	- Cycle time length has an impact on how fast a project can evolve
	- Delivering new generations affects evolvability

### Greenfield Projects

Much easier to build evolutionary architecture with a new project versus and
existing

### Retrofitting Existing Architectures

#### Appropriate Coupling and Cohesion

The functional cohesion determines the ultimate granularity of restructured
components. That doesn't mean architects can't decompose components to a
ridiculous level, but rather that components should have an appropriate size
based on the problem context.

Trying to build an extremely decoupled architecture that is counter to the
problem is unproductive.

*Understand the business problem before choosing an architecture*

#### Engineering Practices

Make sure deployment is easy for developers so the feedback cycle is not
hampered. Creating a better feedback loop encourages improvements

#### Fitness Functions

Think about all the different kinds of fitness functions that are needed. What
can be automated?

### COTS Implications

Avoid commercial off-the-shelf and other packaged enterprise software when
possible. Incremental change, appropriate coupling, and developing fitness

### Migrating Architectures

Make sure you think about other dimensions affected by evolution. Not just
coupling characteristics of classes and components. Transactional coupling is as
real as coupling between classes, and just as insidious to eliminate when
restructuring architecture.

Avoid slaving away on plumbing, building custom infrastructure and web
frameworks, instead of innovating on building better applications.

*Don't build an architecture just because it will be fun meta-work*

#### Migration Steps

When decomposing a monolith, the architect must take coupling and cohesion into
account to find the appropriate balance. Find the correct service granularity.
Identify the service boundaries to break a large service into smaller services.
Rinse and repeat when necessary. Consider all affected dimensions.

Too-fine-grained components lead to too much orchestration, communication
overhead, and interdependency between components.

1. Business functionality groups
	- Use Conway's Law to build software that mimics existing business
	- ...communication hierarchy
2. Transactional boundaries
	- Transactional coupling can be broken up if done right (e.g. chapter 5)
3. Deployment goals
	- Provide incremental change to developers to selectively release and test

### Guidelines for Building Evolutionary Architectures

#### Remove Needless Variability

Use immutable infrastructure. Building software systems that evolve means
controlling as many unknown factors as possible. Developers strive to replace
variables in code with constants to reduce vectors of change. DevOps introduced
this concept to operations, making it more declarative. Infrastructure as code
comes to mind.

Building immutable development environments is one example of applying
changeable things to constants. Capturing the development environment as
immutable infrastructure, developers always work on the same foundation

This also allows useful tools to spread throughout projects. By building a
single source for developer systems, it becomes easy to add useful tools to all
systems at once: docker comes to mind here.

#### Make Decisions Reversible

Many DevOps practices exist to allow reversible decisions -- decisions that need
to be undone. blue/green deployments is an example of one. If the current
production system is running on blue, green is the staging area for the next
release. When the green release is ready, it becomes the production system and
blue temporarily shifts to backup status. If something goes awry with green,
operations can go back to blue without too much pain. If green is fine, blue
becomes the staging area for the next release.

Feature toggles are another common way developers make decisions reversible.
Allowing developers to release features to a small subset of users to vet a
change (canary releasing).

> Make as many decisions as possible reversible (without over-engineering)

#### Make Decisions Reversible

Architects cannot design for unknown unknowns. If projects can easily
incorporate changes, architects don't need a crystal ball. Architecture is not a
solely upfront activity --projects constantly change in both explicit and
unexpected ways.

#### Build Anti-Corruption Layers

See pg. 111 for full example. Because the architect put an anti-corruption layer
in place with an interface, replacing one piece of functionality became a
mechanical exercise. Isolating an original solution behind an interface makes it
easier to transition to a new implementation without disrupting other
developers' work on the project.

#### Build Sacrificial Architectures

> The management question, therefore, is not whether to build a pilot system and
> throw it away. You will do that. [...] Hence plan to throw one away; you will,
> anyhow. --Fred Brooks

Choosing the correct architecture means building a proof of concept. Many
companies like eBay, twitter, and others built sacrificial architectures to
achieve a minimum viable product to prove a market exists.

While this is a good strategy, the team must eventually allocate time and
resources to build a more robust architecture. This also means removing
technical debt that has accumulated. Removing historical design compromises that
manifest itself in a never decommissioned system. 

#### Mitigate External Change

When relying on code from a third-party, developers must create their own
safeguards against unexpected occurrences: breaking changes, unannounced removal,
and so on. Node modules comes to mind with the 2016 incident that left many
deployments broken because a core package was removed from the community. Make
sure the benefits justify the cost. Don't allow external forces to affect the
stability of your builds.

The book discusses a pull model that can be used to mitigate this effort. In
summary, building a system that has an internal version control to act as a
third-party component store, and treat changes from the outside world as pull
requests to that repository. See pg. 117 for more details.


#### Updating Libraries Versus Framework

Its much easier to change a library that is included inside your application
because its swappable versus a framework that is coupled with your application.

> A developers code calls library whereas the framework calls a developers code

Because frameworks are a fundamental part of applications, teams must be
aggressive about pursuing updates. Libraries generally form less brittle coupling
points than frameworks do, allowing teams to be more casual about upgrades.
While updating may time and effort, the time spent early is a fraction of the
cost if the team perpetually procrastinates on the update.

#### Version Services Internally

When versioning services, prefer internal versioning (build logic into the
endpoint to determine the context of the caller, returning the correct version);
support only two versions at a time.
