### Chapter 2 - Fitness Functions

> An architectural fitness function provides an objective integrity assessment
> of some architectural characteristic(s)

- Architectural fitness functions embodies a protection mechanism
	- for the "-ilities" of a given system
- Combining fitness functions together can form the
	- system wide fitness function
		- Allows architects to think about divergent concerns
		- Evaluate tradeoffs when combining fitness functions

#### What is a Fitness Function?
- A fitness function represents each requirement of an architecture
	- Performance
	- Reliability
	- Security
	- Operability
	- Coding Standards
	- Integration
- Developers express fitness functions through tests and metrics
- Testing performance requirements makes good use of fitness functions
- Fitness functions can be automated or a manual process

#### Categories

- Atomic
	- Unit tests are an example
	- But only those that verify architecture characteristics
- Holistic
	- Run against a shared context and combine aspects:
		- Such as security and scalability
	- Running them together may prove that one passes and the other fails
	- This allows us to determine the quality and value of a characteristic
		- Is security and scalability important
		- What trade-offs would we make in adjusting them to both pass
		- See example on pg. 19 discussing caching and security
- Triggered
	- Unit test that are ran during a deployment pipeline
	- Can include traditional, BDD, and also functional testing
	- Triggered fitness functions run on a particular event
- Continual
	- No set schedule, instead are executed constantly
	- Production monitoring to assess both technical and business health
	- Check out MDD: Monitoring-driven development
	- Triggered test provide sparse info about real-world behavior
	- Simulate a transaction in production to verify
	- Verify behavior and gather real data about the system "in the wild."
- Static
	- Fixed result
	- Can think of them as binary
	- Acceptable or average range based on metrics
	- Unit tests are an example
- Dynamic
	- A shifting definition based on extra context
	- Circumstances have an influence on what may be permitted
	- Range of acceptability based on context

- Automated Versus Manual
	- Some fitness functions can, and should, be automated
	- Placed in continuous delivery
	- Developers and DevOps have contributed to this process
	- Not all fitness functions can be automated
	- Some may be manual because of law and or regulations
	- Manual fitness functions should be defined for those characteristics
- Temporal
	- Build a time component for assessing fitness
	- Force re-evaluation overtime to maintain integrity
	- A reminder to check if important updates have been made
- Intentional over Emergent
	- Architects never know all important parts of an architecture -
		- Especially at the beginning
	- As the system evolves, new fitness functions are identified
- Domain-specific
	- Fitness functions can be specific to the domain they live in
	- Identify them early on and develop for them

#### Identify Fitness Functions early
	- This will help support changes that may come later
	- Teams that do not identify their fitness functions face the following:
		- Wrong design leads to software that fails in its environment
		- Design choice that cost time and/or money but are uneccessary
		- Not being able to evolve the system easily when change comes
	- Fitness functions can be classified into three simple categories:
		- Key: critical in making technology or design choices
		- Relevant: Feature level but not guiding architecture choices
		- Not Relevant: How fast a design goes to implementation
	- Be sure to keep key and relevant fitness functions alive by sharing
		- Open chat that notifies others that key functions pass/fail
		- Developers are reminded to consider them in day-to-day coding
#### Review Fitness Functions
	- Review with key business and technical stakeholders
	- Goal is to update fitness functions to meet design goals
	- Check relevancy
	- Determine change in the scale or magnitude
	- Decide if there are better approaches to testing them
	- Discover new ones that the system might need to support
	- Review your fitness functions at least once a year

#### Idea
- Keep a spreadsheet listing your fitness functions
- Test those fitness functions by wiring them to deployment pipelines

> We want our architecture to evolve in a guided way, so we place constraints on
> different aspects of the architecture to reign in undesirable evolutionary
> directions.
