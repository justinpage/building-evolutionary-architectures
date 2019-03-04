### Chapter 7 - Evolutionary Architecture Pitfalls and Antipatterns

- Antipattern
	- Initially good but turns into a mistake
	- Better alternatives exist for most antipatterns
- Pitfall
	- Superficially good but immediately reveals itself to be a path

### Technical Architecture

#### Antipattern: Vendor King

> Don't couple your architecture to a vendor king

Avoid building your entire business around a vendor's tools. Doing so leaves
your business limited because the architecture is dependent on tools the vendor
supplies --rarely supporting what must be fully implemented in order to
succeed.

Treat vendor products as just another integration point. This will allow
developers to easily replace behavior that isn't useful without other
integration points.

#### Pitfall: Leaky Abstractions

> All non-trivial abstractions, to some degree, are leaky

We come to trust that abstractions are always accurate, but they often break in
surprising ways. Modern software systems have expanded into more complex
solutions. If one abstraction at the lowest level exhibits a fault, because so
many layers exist, the fault can bubble itself to the top affecting other
services in the stack --like UI. Debugging and troubleshooting is much more
difficult because the stack is more complex. This can lead to a leaky
abstraction because the problem leaks into the other integration points.

>  Always fully understand at least one abstraction layer below the one you
>  normally work in.

This advice becomes more difficult when the solution in place is complex.
Fitness functions can protect the evolutionary architecture by testing key
integration points so they don't start leaking.

> Understand the fragile places within your complex technology stack and
> automate protections via fitness functions


#### Antipattern: Last 10% Trap

Avoid reusable solutions from packages, platforms, and frameworks, that solve
maybe 60% of your problems and the remaining is hacked together to satisfy maybe
90% of your solution. Ultimately, the tool can't solve the problem completely
--last 10%--leaving the project as a disappointment.

While easy to build simple things fast, some reusable solutions do not scale to
meet the demands of the real world. Check out pg. 128 for a discussion around
IBM's San Francisco Project.

#### Antipattern: Code Reuse Abuse

The more effort developers put into making code reusable the harder it is to
use. Making code reusable involves adding additional options and decision points
to accommodate the different users. More reusability may harm basic usability.

> The more reusable code is, the less usable it is

Microservice adopts the philosophy of duplication to coupling. The real end goal
is to isolate entities within domains. This offsets initial coupling that could
harm evolutionary architecture. Make sure you understand the coupling points in
your code and make sure it doesn't conflict with goals in the architecture.

#### Pitfall: Resume-Driven Development

> Don't build architecture for the sake of architecture --you are trying to
> solve a problem

Choose an effective architecture, not because it will look good on your resume,
but because it is the most suited for the problem.

### Incremental Change

#### Antipattern: Inappropriate Governance

It's inappropriate to solve all problems using one technology stack. Using
different stacks to solve the right problem can help avoid inadvertent coupling.
One advantage to choosing a similar technology stack is to have consistent
solutions that can be shared by different staff members. However, a side effect
to this effort is overengineering. While a tech stack may solve the most complex
problems, it becomes inappropriate for smaller projects that don't require the
industrial complexity an existing solution may provide.

Some large organizations use the Goldilocks Governance: pick three technology
stacks for standardization --simple, intermediate, and complex --and allow
individual service requirements drive the stack decisions. This gives the team
the flexibility to choose the appropriate stack while providing the company some
standards.

#### Pitfall: Lack of Speed to Release

> Speed of evolution is a function of cycle time; faster cycle time allows
> faster evolution

Cycle time starts when a developer starts working on a new feature and expires
when that feature is running in production. The reduction of cycle time is key
for Continues Delivery. Faster cycle times means architecture can evolve
quicker.

### Business Concerns

#### Pitfall: Product Customization

Always evaluate the associate cost when it comes to supporting the following:

- Unique builds for each customer
- Permanent feature toggles
- Product-driven customization

The caricature of sales people has them selling any requested before its even
implemented. Evaluate if custom solutions for a customer outweighs the necessary
burden in developing custom tests and fitness functions.

#### Antipattern: Reporting

Separate the behavior, where the isolation of services benefits separation but
not consolidation. Using event streaming and message queues to populate domain
"system of record" databases leads to eventual consistency rather than
transactional behavior.

> https://en.wikipedia.org/wiki/Eventual_consistency

#### Pitfall: Planning Horizons

The more someone invests time or effort into something, the harder it becomes to
abandon it (Sunk Costs). The more time you invest in planning or documenting a
solution, the more likely you are to protect it even when faced with evidence
that the solution is outdated.

> Don't become irrationally attached to handcrafted artifacts

Find ways to keep options open. Avoid technologies that require a significant
upfront investment before the software is actually built and validated to solve
the actual problem.
