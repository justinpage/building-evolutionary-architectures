### Chapter 3 - Engineering Incremental Change 

> An evolutionary architecture supports guided,	*incremental* change across
> multiple dimensions

- Microservices architecture that embraces share nothing: isolated 
	- Some services use a rating service
	- New rating service is deployed
	- Some services update their calls to use the new rating service
	- Other services continue to use the existing rating service
	- All services will use the new rating service after some time
	- When original rating service is not in use, it is deactivated
		- Garbage collected because it is unused
- Incremental change:
	- Original service
	- New service
	- Migration to new service
	- Automatic mechanism for removing unused original service

#### Building Blocks 
- Nothing in software is static. 
- We live in a 4-D world
	- Modern architecture must be deployable and changeable
	- Initial architecture diagram involves more dimensions:
		- Software used
		- Software version updates
		- Software changes based on new tools 
	- Evolution of software should be a first class citizen

#### Testable
- Fitness functions that test coupling and develop guidelines
	- These would be automated in a deployment pipeline
	- Would also run continually to maintain quality of architecture

#### Deployment Pipelines
- Encourage developers to split individual tasks into stages:
	- Unit test
	- Functional test
	- Atomic Fitness functions test
	- Holistic Fitness functions test
	- Deploy to integration environment
	- Focuses on production readiness
	- Different from continuous integration (CI) focused only on integration
- Developers may "get by" with just CI but later need a deployment pipeline
	- The need for separation of tasks
	- Feedback necessary for each step
- May include continuous deployment
	- Could fan out to a integration production and staging environment 
	- Successful deploy to both guarantee:
		- Does not affect current state of production
		- Does not affect future state environment
	- Fan in after tasks to consolidate a single thread for deployment
- Allow QA to test in production by controlling access
	- Team can deploy changes to production and toggle them on for only QA
	- You can use production as an environment for exploratory testing
- Having a deployment pipeline can allow us to apply fitness functions:
	- Fitness functions are designed to have objects, quantifiable results
	- Captures all concerns that creates a consistent enforcement mechanism
	- Having a list of fitness functions allows developers to easily design --
		- Deployment pipelines

#### Combining 
- Atomic + Triggered
	- Unit and functional tests ran as part of software development
- Holistic + Triggered
	- Integration tests that are included in a deployment pipeline
- Atomic + Continual 
	- Test one aspect of the architecture but run as part of the overall system
	- e.g. testing REST endpoints support proper verbs
	- e.g. error handling is behaving correctly
	- e.g. Metadata is being handled properly
- Holistic + Continual
	- Test multiple parts of the system all the time
	- An agent that constantly assesses architecture and operations
	- Chaos Monkey from Netflix is an example
	- Simian Army from Netflix is another
	- Take note that these agents don't run on a schedule --it runs continually 
	- This forces developers to build systems that withstand problems
	- Validates solutions continuously 
	- Runs against multiple parts of the architecture (resiliency, scalability)
		- Tests if these characteristics are maintained

#### Case Study: Architectural Restructuring while Deploying 60 Times/Day
- Github: https://githubengineering.com/move-fast/ 
- Example that allows developers to refactor a critical part of their --
	- infrastructure with confidence
- Ran a new version alongside the existing and then testing consistency

#### Conflicting Goals
- Developers may want to deploy more aggressively
- Concerning to database admins as fast changes to code could lessen stability
- Compromises must occur when considering incremental changes

#### Case Study: Adding fitness functions to
#### PenultimateWidgets' Invoicing Service 
- See book for details

#### Hypothesis and Data-Driven Development
- Github's example of using scientist was data-driven development
	- Why? They allowed data to drive changes and focus their efforts
- A similar approach that incorporates the business rather than technical is:
	- Hypothesis-driven development
- Use the scientific method to determine development by experiments
	- If we do A then we hypothesize that it will lead to B
	- Once in place, run A/B testing and tally the results
	- Decision is made by a hypothesis versus conjecture

#### Case Study: What to Port?
- A migration to a new system may be influenced by what features are most used
	- Most used features are obviously migrated
	- Those that are not may be left out thus sun-setting
- Use data analytics to determine what features to port instead of all 
