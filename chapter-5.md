### Chapter 5 - Evolutionary Data

> Refusing to refactor schemas or eliminate old data couples your architecture
> to the past, which is difficult to refactor

Developer should treat changes to database structure the same way they treat
source code: tested, versioned, and incremental.

- *Tested*: Add fitness functions to ensure mappings stay with the schemas
	- Ensure stability
- *Versioned*: Version database schemas alongside code
	- Neither functions without the other
- *Incremental*: Automated migration tools should be used instead of manual

Embrace integration patterns that include parallel change. Providing transition
phases that support old and new implementations. Check out pg. 88 for a complete
example. The gist is that we provide a timeline to use deprecated fields and
when to retire them because no one is using them in the database.

### Inappropriate Data Coupling

Databases and DBAs many times they rely on antiquated practices and tools
compared to the development world. Features that are available to developers,
don't exist for DBAs: refactoring support, out-of-container testing, unit
testing, mocking, stubbing, and so on. Some would argue its because of vendor
lock-in and tool choice. Check out pg. 90 for more details.

### Two-Phase Commit Transactions

While systems often cannot avoid transactions, architects should try to limit
transactional contexts as much as possible because they form tight coupling.
When developing microservices, or migrating a monolith, keep the bounded context
useful, not necessarily small. Make sure the level of granularity matches the
problems developers are trying to to solve.

### Age and Quality of Data
End of the chapter illustrates the main motive behind this chapter:

While it's true that schemas change less frequently than code, database schemas
still represent an abstraction of the real world. DBAs who believe that schemas
never change ignore reality. 

Developers and DBAs must embrace effective data practices alongside other modern
engineering practices
