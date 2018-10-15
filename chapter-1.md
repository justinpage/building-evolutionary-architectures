### Chapter 1 - Software Architecture

#### Evolutionary Architecture
- Add a new standard that is "evolvability"
- Containerization couldn't have happen without evolutionary steps before it
	- Linux - OS Free
	- Puppet and Chef - OS Operations free
	- Docker - Portable formats
- What if we build changeability into the architecture?

#### Incremental Change
- Incremental software development that focus on small module changes
- Continuous delivery in software that activates and retires services

#### Guided Change
- Develop fitness functions that evaluate how changes impact:
	- the important characteristics of the architecture
	- and prevent degradation of those characteristics over time
- Fitness functions ensure architecture doesn't change in undesirable ways
- Using metrics, tests, and other verification tools
- Fitness function defines how "fit" each variant is based on what "fit" is

#### Multiple Architecture Dimensions
- Architecture has multi-dimensional perspectives
- Each perspective must be balanced between pros/cons
- Utilizing fitness functions protects their integrity

#### Conway's Law
- Inverse Conway Maneuver
- Cross functional teams that match the purview of the surface
- Companies that build micro-services:
	- Structure their teams around service boundaries instead of tech silos
	- Impact myriad dimensions of software development
	- Reflects the problem size and scope

#### Why Evolutionary
- Architecture that truly evolves and genuinely supports change
- Fit for purpose and survives an ever changing environment
- Architecture that is guided or represents what we want: our end goal
