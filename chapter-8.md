### Chapter 8 - Putting Evolutionary Architecture into Practice

> Steps required to implement the ideas around evolutionary architecture

### Organizational Factors

#### Cross-Functional Teams

- Domain-centric
	- Has all the roles needed to design, implement, and deploy their service
- Eliminates coordination friction
	- Removes silos by keeping all roles local

#### Finding New Resources via Automating DevOps

By applying modern engineering practices to automate things that humans
shouldn't deal with on a regular basis, frees DevOps up to be better
partners in development efforts

#### Organized Around Business Capabilities

Instead of focusing on shared resources to minimize cost, architects have chosen
open source solutions in order to solve technical architectural problems. Now
that developers have the option of creating custom-made environments and
functionality, the attention can shift towards the domain of the business rather
than the technical aspect.

> Organize teams around business capabilities, not job functions

#### Product over Project

1. Products live forever, projects have a lifespan
2. Each product has an owner who manages and advocates it
3. Products are cross-functional and therefore represented by the team

#### Connections Between Team Members

Many companies have found anecdotally that large development teams don't work
well. J. Richard Hackman offered an explanation why: it's not the number of
people but the number of connections they must maintain.

Creating small teams revolves around the desire to cut down on communication
links. These small teams should be cross-functional to eliminate artificial
friction imposed by coordinating across silos.

> Strive for a low number of connections between development teams

### Team Coupling Characteristics

### Culture

Architects should care about how engineers build their system and watch out for
behaviors their organization rewards. Architects can seek to understand a team's
engineering culture by asking questions like:

- Does everyone know what fitness functions are?
	- How do new tools or products effect fitness functions
- Are teams measuring how well their system is doing by fitness functions?
- Do engineers understand cohesion and coupling?
- Are there conversations around domain and technical concepts?
	- Which components belong together?
- Do teams choose solutions based on its ability to make changes?
	- Not based on what technology they want to use
- How do teams respond to business changes?
	- Do they struggle to incorporate small changes?
	- Are are they spending too much time on small business changes?

Many teams are driven and rewarded most often for delivering new functionality,
with code quality and the evolvable aspect considered only if teams make it a
priority. Architects must find ways to encourage design decisions that
prioritize evolutionary design.

### Culture of Experimentation

- Successful evolution demands experimentation

Organizations can do the following:

- Bringing ideas from outside
	- External advice; consultants
	- Conferences
- Encouraging explicit improvement
	- Seek constant improvement
	- Toyota's culture of kaizen is an example
- Spike and stabilize
	- Generate throw-away solutions to learn and explore
	- Created for learning, not as a well engineered solution
- Creating innovation time
	- Hackathons
	- Google's 20% time is an example
	- Atlassian's shipit is another example
- Following set-based development
	- Explore multiple approaches to a problem
	- Understand the problem better
	- Can create a more robust solution
- Connecting engineers with end-users
	- Experimentation is only successful after understanding its impact
	- Research and understanding how users interact with a solution

### CFO and Budgeting

Architects strive to find the sweet spot between the size of a deployable
component and the corresponding cost. Every company is different. A company in
an aggressive market may need to move faster and therefore desire a smaller
deployable component size of software. Others may find it more pragmatic to
build a service-based architecture because it models common change of the
business.

### Where Do You Start?

#### Low-Hanging Fruit

Find architecture that already is largely decoupled and not on a critical path
with any dependencies. Improving the modularity and deceasing coupling can allow
teams to demonstrate the benefits of evolutionary architecture through fitness
functions and incremental change.

In turn, these types of decoupled components can make it easier to build
deployment pipelines and provide a platform for easier and more robust testing.

#### Highest-Value

Find the most critical part of the system and build evolutionary behavior around
it first. Demonstrate the long term value of this architecture by showing
actionable data around the most valuable parts

#### Testing

Developers should add coarse-grained functional tests around some behavior
before restructuring the code. Allowing you to verify the behavior before
restructuring.

Testing is a critical component to incremental change and fitness functions
leverage tests aggressively.

### Future State

- Fitness Functions Using AI
	- AI can look for anomalous behavior
	- Used to support software development
- Generative Testing
	- Run large number of tests and capture the outcomes
	- Generate statistics and analyze any anomalies
	- Check every possible value and report on edge cases that break
	- Unit tests check known places but are immune to unanticipated edge cases

### Why (or Why Not)

#### Why

- Predictable versus evolvable
	- Highly volatile nature of development means more incremental change
	- Architects may still make plans, but they may be invalidated at any moment
	- React to substantive shifts without rework
- Scale
	- Using microservices to eliminate inappropriate coupling
- Cycle time as a business metric
	- Cycle time has become a business differentiator in some markets
	- Being able to deliver faster has an advantage against competitors
	- Using Continuous Deployment is an example of reducing cycle time
- Isolating architectural characteristics at the quantum level
	- Decoupled components allow different architecture solutions
	- Free to focus on the primary characteristics versus trade-offs

#### Why Not

- Can't evolve a ball of mud
- Other architectural characteristics dominate
	- Other factors may outweigh evolvability
	- Performance may be a core goal that outweighs adaptability
- Sacrificial architecture
	- Designed to be thrown away
	- Experimentation versus replacing existing solution
- Planning on closing the business soon

### Convincing Others
- Demonstrate how these ideas improve by putting them into practice
- Use **Consulting Judo** to find a pain point and fix it as an exemplar

### Business Case

### Move fast without breaking things

All the practices we call incremental change improve automation and efficiency.
Defining top-level enterprise architecture concerns as fitness functions both
unifies a disparate set of concerns under one umbrella and forces developers to
think in terms of objective outcomes.

### Less Risk

Improved engineering practices comes decreased risk. Once developers have
confidence that their practices will allow them to make changes in the
architecture without breaking things, companies can increase their release
cadence.

### New Capabilities 

Being able to support new business capabilities, as a result of evolutionary
architecture, can be an idea to sell. For example, hypothesis-driven
development. Always sell the idea in terms of the business, not just technical
improvements.

### Building Evolutionary Architecture

Relies on many existing things:

- Testing
- Metrics
- Deployment Pipelines
- Supporting infrastructure
- Innovation
- Automation

React and thrive in an ecosystem that has new ideas from unexpected places.
