### Chapter 4 - Architectural Coupling

> How the pieces of the architecture connect and rely on one another

### Modularity

- Modularity describes a logical grouping of related code
- Components are the physical packaging of modules

Modularity focus on logical grouping whereas components focus on physical
grouping.

### Architectural Quanta and Granularity

- Quantum: minimum amount of any physical entity involved in an interaction
	- Architectural Quantum: independently deployable component
	- Includes all structural elements required for the system to function

In monolithic architecture, the quantum is the entire application. Microservices
define physical bounded contexts between elements which allow incremental
change.

### Evolvability of Architectural Styles

Different architectural patterns have different inherent quantum sizes, which
impact their evolvability.

#### Big Ball of Mud

- *Incremental change*: difficult
	- Related code is scattered
	- Fixing breakages will generate more breakages
- *Guided change with fitness functions*: difficult
	- No clear partitioning exists
	- Must identify parts to protect
	- No structure other than low-level functions or classes
- *Appropriate coupling*: inappropriate

#### Monoliths

- Classes talking to other classes. Each having many dependencies on one another
- *Incremental change*: difficult
	- Each component is highly coupled
- *Guided change with fitness functions*: difficult, but not impossible
	- Because this pattern has existed, tools have been made to test it
	- Guided changes, such as performance and scalability, are difficult
	- Easy to understand monoliths, but lose scalability and performance
- *Appropriate coupling*: inappropriate. Just as bad as Big Ball of Mud

##### Layered Architecture

Each layer represents a technical capability. Allows for implementation changes
without affecting other layers. Provides isolation and separation of concerns.

- *Incremental change*: easy if the changes are isolated to an existing layer
	- If change requires multiple layers, this coordination is needed
	- Could be difficult if each team is responsible for each layer
- *Guided change with fitness functions*: easier because structure is more
apparent
- *Appropriate coupling*: understandable
	- evolvability is defined by the structure or layers of the architecture

While developers use layered architectures for separation of concern. The layer
typically exhibits high internal and low external coupling. Within each layer,
the component is cooperating toward a single goal. Developers use interfaces to
lessen coupling between layers.

##### Modular monoliths

If developers are extremely disciplined, then many of the benefits
about microservices --isolation, independence, small unit of change--
can be achieved in monolithic architectures.

Most modern languages allow building strict visibility and connection
rules. Using these rules, developers and architects can have much more
malleable architecture

- *Incremental change*: easy because developers can enforce modularity
	- Components containing the modules may be difficult to deploy
	- The degree of deployability determines the rate of incremental change
- *Guided change with fitness functions*: easier to design and implement
	- Good separation of concern and therefore easier to test
- *Appropriate coupling*: appropriate. Cohesive with good interfaces between
components

##### Microkernel

Plugin architecture. Many IDE utilize this architecture for plugins. Can create
high coupling if plugin components rely on one another. If plugins are isolated,
the coupling is isolated. Offers reasonably good but limited opportunities to
evolve.

- *Incremental change*: once core is built, change comes from plugins
- *Guided change with fitness functions*: Easy to create for core and plugins
	- Core and plugins are separated
	- Mock core to make plugin testing easier
- *Appropriate coupling*: Similar to micro-service architecture

Something to keep in mind is plugin size in relation to coupling

#### Event-Driven Architectures

Integrate several disparate systems together using message queues.

##### Brokers

- Message queues (how messages are transferred
- Initiating event (what started or triggered the event)
- intra-process event (events passed between processors to fulfill request)
- event processors (what components perform the actual business logic)
- *Incremental change*: allows it in multiple forms
	- deployment may be difficult because it relies on async communication
- *Guided change with fitness functions*: Atomic functions should be easy
	- However holistic are necessary and complex
	- Correlation IDs for tracking each request for testing cross-services
- *Appropriate coupling*: low degree of coupling
	- functional cohesion exists between services and the message contracts

##### Mediators

Similar to broker but an additional component appears: a hub that acts as a
coordinator. The mediator posts messages to the queues which in turn trigger the
appropriate event processors. Transactional coordination is an advantage. This
also allows for parallel events to execute and coordinate.

*Incremental change* and *Guided change with fitness functions* are similar to
brokers. *Appropriate coupling* is different in that developers must consider
side effects for the other services in the workflow.

#### Service-Oriented Architectures

##### ESB-driven SOA

Using a service bus as a mediator for complex events and handles a variety of
integrations such as message transformation and choreography. Defining
characteristics are:

- Mediation and routing: knows how to locate and communicate with services
- Process choreography and orchestration:
	- composes services together and manages tasks
- Message enhancement and transformation
	- Can provide an integration hub between different protocols
	- One service is HTTP, another is AMQP, can transform behind-the-scenes
	- Receives message, transforms for service, sends it other service

ESB-driven SOA was never designed to exhibit evolutionary properties:

- *Incremental change*: hampers most common types of changes to business domains
	- Most SOA teams are partitioned as the architecture, requiring...
	- herculean amounts of coordination for common changes
- *Guided change with fitness functions*: testing in general is difficult
	- Testing core behavior is challenging because a portion could lead...
	- to a variety of workflows
	- Large scale holistic functions that do end-to-end testing is necessary
	- Impossible to build atomic fitness functions
- *Appropriate coupling*: Not designed for evolvability, more driven towards...
	- Accounting for all future application development
	- Not possible in the real-world because SOA parts are not evolvable

Software architectures aren't created in a vacuum --they always reflect the
ecosystem in which they were defined. SOA was popular when large enterprise
proprietary systems ruled. Open source has changed how we approach architecture.

##### Microservices

Combining the engineering practices of CD with the logical partitioning of
bounded context (DDD) forms the philosophical basis for microservice-style
architecture.

Some characteristics include:

- Modeled around the business domain
	- business domain, not technical architecture
	- represents business context and/or workflows
- Hide implementation details
	- Encapsulates the service boundary
	- Each domain forms a physical bounded context
	- Services integrate with each other by messages, not exposing databases
- Culture of automation
	- CI/CD by default
	- Embrace automation for tests
- Highly decentralized
	- Share nothing architecture - decrease coupling
	- If one service goes down or changes, doesn't affect the whole system
- Deployed independently
	- Can update and change components without affecting the entire system
- Isolate failure
	- Each service is expected to handle reasonable errors and recover
	- Circuit breaker pattern
	- https://www.reactivemanifesto.org/
- Highly observable
	- Monitoring and logging become first-class citizens

- *Incremental change*: easy
- *Guided change with fitness functions*: supports atomic and holistic
- *Appropriate coupling*: integration coupling and service templates
	- integration coupling is how services talk to each other by messages
	- service templates allow us to manage coupling and outline behavior

##### Service-based architecture

A common architectural pattern for migrating a monolithic service to a more
evolutionary architecture. See pg. 74 for more details.

##### Serverless Architectures

Function as a Service or Backend as a Service rely on the cloud provider to
connect services together. Many handle provisioning infrastructure per request,
automatically handling scaling, provisioning, and a host of other management
duties. All triggered by events.

- *Incremental change*: can fit in deployment pipelines
- *Guided change with fitness functions*: critical to ensure integration points
	- Expect to write more holistic fitness functions to ensure stability
- *Appropriate coupling*: attractive because it simplifies the dimensions
	- While practical for making changes, it can put constraints on clients
	- Offloads coordination to clients which may not be ideal

** Make sure your architecture matches the problem domain. Don't try to force
fit an unsuitable architecture**
