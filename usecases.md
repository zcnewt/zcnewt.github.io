---
title: NoSQL Use Cases
---
# NoSQL Use Cases

## General Use Cases

* Bigness. NoSQL is seen as a key part of a new data stack supporting: big data, big numbers of users, big numbers of computers, big supply chains, big science, and so on. When something becomes so massive that it must become massively distributed, NoSQL is there, though not all NoSQL systems are targeting big. Bigness can be across many different dimensions, not just using a lot of disk space. 
* Massive write performance. This is probably the canonical usage based on Google's influence. High volume. Facebook needs to store 135 billion messages a month. Twitter, for example, has the problem of storing 7 TB/data per day with the prospect of this requirement doubling multiple times per year. This is the data is too big to fit on one node problem. At 80 MB/s it takes a day to store 7TB so writes need to be distributed over a cluster, which implies key-value access, MapReduce, replication, fault tolerance, consistency issues, and all the rest. For faster writes in-memory systems can be used.
* Fast key-value access. This is probably the second most cited virtue of NoSQL in the general mind set.  When latency is important it's hard to beat hashing on a key and reading the value directly from memory or in as little as one disk seek. Not every NoSQL product is about fast access, some are more about reliability, for example. but what people have wanted for a long time was a better memcached and many NoSQL systems offer that.
* Flexible schema and flexible datatypes.  NoSQL products support a whole range of new data types, and this is a major area of innovation in NoSQL. We have: column-oriented, graph, advanced data structures, document-oriented, and key-value. Complex objects can be easily stored without a lot of mapping. Developers love avoiding complex schemas and ORM frameworks. Lack of structure allows for much more flexibility. We also have program and programmer friendly compatible datatypes likes JSON. 
* Schema migration. Schemalessness makes it easier to deal with schema migrations without so much worrying. Schemas are in a sense dynamic, because they are imposed by the application at run-time, so different parts of an application can have a different view of the schema.
* Write availability. Do your writes need to succeed no mater what? Then we can get into partitioning, CAP, eventual consistency and all that jazz.
* Easier maintainability, administration and operations. This is very product specific, but many NoSQL vendors are trying to gain adoption by making it easy for developers to adopt them. They are spending a lot of effort on ease of use, minimal administration, and automated operations. This can lead to lower operations costs as special code doesn't have to be written to scale a system that was never intended to be used that way.
* No single point of failure. Not every product is delivering on this, but we are seeing a definite convergence on relatively easy to configure and manage high availability with automatic load balancing and cluster sizing. A perfect cloud partner.
* Generally available parallel computing. We are seeing MapReduce baked into products, which makes parallel computing something that will be a normal part of development in the future.
* Programmer ease of use. Accessing your data should be easy. While the relational model is intuitive for end users, like accountants, it's not very intuitive for developers. Programmers grok keys, values, JSON, Javascript stored procedures, HTTP, and so on. NoSQL is for programmers. This is a developer led coup. The response to a database problem can't always be to hire a really knowledgeable DBA, get your schema right, denormalize a little, etc., programmers would prefer a system that they can make work for themselves. It shouldn't be so hard to make a product perform. Money is part of the issue. If it costs a lot to scale a product then won't you go with the cheaper product, that you control, that's easier to use, and that's easier to scale?
* Use the right data model for the right problem. Different data models are used to solve different problems. Much effort has been put into, for example, wedging graph operations into a relational model, but it doesn't work. Isn't it better to solve a graph problem in a graph database? We are now seeing a general strategy of trying find the best fit between a problem and solution.
* Avoid hitting the wall. Many projects hit some type of wall in their project. They've exhausted all options to make their system scale or perform properly and are wondering what next? It's comforting to select a product and an approach that can jump over the wall by linearly scaling using incrementally added resources.  At one time this wasn't possible. It took custom built everything, but that's changed. We are now seeing usable out-of-the-box products that a project can readily adopt.
* Distributed systems support. Not everyone is worried about scale or performance over and above that which can be achieved by non-NoSQL systems. What they need is a distributed system that can span datacenters while handling failure scenarios without a hiccup. NoSQL systems, because they have focussed on scale, tend to exploit partitions, tend not use heavy strict consistency protocols, and so are well positioned to operate in distributed scenarios.
* Tunable CAP tradeoffs. NoSQL systems are generally the only products with a "slider" for choosing where they want to land on the CAP spectrum. Relational databases pick strong consistency which means they can't tolerate a partition failure. In the end this is a business decision and should be decided on a case by case basis. Does your app even care about consistency? Are a few drops OK? Does your app need strong or weak consistency? Is availability more important or is consistency? Will being down be more costly than being wrong? It's nice to have products that give you a choice.

## More Specific Use Cases

* Managing large streams of non-transactional data: Apache logs, application logs, MySQL logs, clickstreams, etc.
* Syncing online and offline data. This is a niche CouchDB has targeted. 
* Fast response times under all loads.
* Avoiding heavy joins for when the query load for complex joins become too large for a RDBMS.
* Soft real-time systems where low latency is critical. Games are one example.
* Applications where a wide variety of different write, read, query, and consistency patterns need to be supported. There are systems optimized for 50% reads 50% writes, 95% writes, or 95% reads. Read-only applications needing extreme speed and resiliency, simple queries, and can tolerate slightly stale data. Applications requiring moderate performance, read/write access, simple queries, completely authoritative data. Read-only application which complex query requirements.
* Load balance to accommodate data and usage concentrations and to help keep microprocessors busy.
* Real-time inserts, updates, and queries.
* Hierarchical data like threaded discussions and parts explosion.
* Dynamic table creation.
* Two tier applications where low latency data is made available through a fast NoSQL interface, but the data itself can be calculated and updated by high latency Hadoop apps or other low priority apps.
* Sequential data reading. The right underlying data storage model needs to be selected. A B-tree may not be the best model for sequential reads.
* Slicing off part of service that may need better performance/scalability onto it's own system. For example, user logins may need to be high performance and this feature could use a dedicated service to meet those goals.
* Caching. A  high performance caching tier for web sites and other applications. Example is a cache for the Data Aggregation System used by the Large Hadron Collider.
* Voting.
* Real-time page view counters.
* User registration, profile, and session data.
* Document, catalog management  and content management systems. These are facilitated by the ability to store complex documents has a whole rather than organized as relational tables. Similar logic applies to inventory, shopping carts, and other structured data types.
* Archiving. Storing a large continual stream of data that is still accessible on-line. Document-oriented databases with a flexible schema that can handle schema changes over time.
* Analytics. Use MapReduce, Hive, or Pig to perform analytical queries and scale-out systems that support high write loads.
* Working with heterogenous types of data, for example, different media types at a generic level.
* Embedded systems. They don’t want the overhead of SQL and servers, so they uses something simpler for storage.
* A "market" game, where you own buildings in a town. You want the building list of someone to pop up quickly, so you partition on the owner column of the building table, so that the select is single-partitioned. But when someone buys the building of someone else you update the owner column along with price.
* JPL is using SimpleDB to store rover plan attributes. References are kept to a full plan blob in S3. 
* Federal law enforcement agencies tracking Americans in real-time using credit cards, loyalty cards and travel reservations.
* Fraud detection by comparing transactions to known patterns in real-time.
* Helping diagnose the typology of tumors by integrating the history of every patient.
* In-memory database for high update situations, like a web site that displays everyone's "last active" time (for chat maybe). If users are performing some activity once every 30 sec, then you will be pretty much be at your limit with about 5000 simultaneous users.
* Handling lower-frequency multi-partition queries using materialized views while continuing to process high-frequency streaming data.
* Priority queues.
* Running calculations on cached data, using a program friendly interface, without have to go through an ORM.
* Unique a large dataset using simple key-value columns.
* To keep querying fast, values can be rolled-up into different time slices.
* Computing the intersection of two massive sets, where a join would be too slow.
* A timeline ala Twitter. 

## Redis Use Cases
### Redis is unique in the repertoire as it is a data structure server, with many fascinating use cases that people are excited to share. 

* Calculating whose friends are online using sets. 
* Memcached on steroids.
* Distributed lock manager for process coordination.
* Full text inverted index lookups.
* Tag clouds.
* Leaderboards. Sorted sets for maintaining high score tables.
* Circular log buffers.
* Database for university course availability information. If the set contains the course ID it has an open seat. Data is scraped and processed continuously and there are ~7200 courses.
* Server for backed sessions. A random cookie value which is then associated with a larger chunk of serialized data on the server) are a very poor fit for relational databases. They are often created for every visitor, even those who stumble in from Google and then leave, never to return again. They then hang around for weeks taking up valuable database space. They are never queried by anything other than their primary key.
* Fast, atomically incremented counters are a great fit for offering real-time statistics.
* Polling the database every few seconds. Cheap in a key-value store. If you're sharding your data you'll need a central lookup service for quickly determining which shard is being used for a specific user's data. A replicated Redis cluster is a great solution here - GitHub use exactly that to manage sharding their many repositories between different backend file servers.
* Transient data. Any transient data used by your application is also a good fit for Redis. CSRF tokens (to prove a POST submission came from a form you served up, and not a form on a malicious third party site, need to be stored for a short while, as does handshake data for various security protocols. 
* Incredibly easy to set up and ridiculously fast (30,000 read or writes a second on a laptop with the default configuration)
* Share state between processes. Run a long running batch job in one Python interpreter (say loading a few million lines of CSV in to a Redis key/value lookup table) and run another interpreter to play with the data that’s already been collected, even as the first process is streaming data in. You can quit and restart my interpreters without losing any data. 
* Create heat maps of the BNP’s membership list for the Guardian
* Redis semantics map closely to Python native data types, you don’t have to think for more than a few seconds about how to represent data.
* That’s a simple capped log implementation (similar to a MongoDB capped collection)—push items on to the tail of a ’log’ key and use ltrim to only retain the last X items. You could use this to keep track of what a system is doing right now without having to worry about storing ever increasing amounts of logging information.
* An interesting example of an application built on Redis is Hurl, a tool for debugging HTTP requests built in 48 hours by Leah Culver and Chris Wanstrath. 
* It’s common to use MySQL as the backend for storing and retrieving what are essentially key/value pairs. I’ve seen this over-and-over when someone needs to maintain a bit of state, session data, counters, small lists, and so on. When MySQL isn’t able to keep up with the volume, we often turn to memcached as a write-thru cache. But there’s a bit of a mis-match at work here. 
* With sets, we can also keep track of ALL of the IDs that have been used for records in the system.
* Quickly pick a random item from a set. 
* API limiting. This is a great fit for Redis as a rate limiting check needs to be made for every single API hit, which involves both reading and writing short-lived data.  
* A/B testing is another perfect task for Redis - it involves tracking user behaviour in real-time, making writes for every navigation action a user takes, storing short-lived persistent state and picking random items.
* Implementing the inbox method with Redis is simple: each user gets a queue (a capped queue if you're worried about memory running out) to work as their inbox and a set to keep track of the other users who are following them. Ashton Kutcher has over 5,000,000 followers on Twitter - at 100,000 writes a second it would take less than a minute to fan a message out to all of those inboxes.
* Publish/subscribe is perfect for this broadcast updates (such as election results) to hundreds of thousands of simultaneously connected users. Blocking queue primitives mean message queues without polling.
* Have workers periodically report their load average in to a sorted set.
* Redistribute load. When you want to issue a job, grab the three least loaded workers from the sorted set and pick one of them at random (to avoid the thundering herd problem).
* Multiple GIS indexes. 
* Recommendation engine based on relationships.
* Web-of-things data flows.
* Social graph representation. 
* Dynamic schemas so schemas don't have to be designed up-front. Building the data model in code, on the fly by adding properties and relationships, dramatically simplifies code. 
* Reducing the impedance mismatch because the data model in the database can more closely match the data model in the application.

## VoltDB Use Cases

### VoltDB as a relational database is not traditionally thought of as in the NoSQL camp, but I feel based on their radical design perspective they are so far away from Oracle type systems that they are much more in the NoSQL tradition.

* Application: Financial trade monitoring
** Data source: Real-time markets
** Partition key: Market symbol (ticker, CUSIP, SEDOL, etc.)
** High-frequency operations: Write and index all trades, store tick data (bid/ask)
** Lower-frequency operations: Find trade order detail based on any of 20+ criteria, show TraderX's positions across all market symbols

* Application: Web bot vulnerability scanning (SaaS application)
** Data source: Inbound HTTP requests
** Partition key: Customer URL
** High-frequency operations: Hit logging, analysis and alerting
** Lower-frequency operations: Vulnerability detection, customer reporting

* Application: Online gaming leaderboard 
** Data source: Online game 
** Partition key: Game ID 
** High-frequency operations: Rank scores based on defined intervals and player personal best
** Lower-frequency transactions: Leaderboard lookups

* Application: Package tracking (logistics)
** Data source: Sensor scan
** Partition key: Shipment ID
** High-frequency operations: Package location updates
** Lower-frequency operations: Package status report (including history), lost package tracking, shipment rerouting

* Application: Ad content serving
** Data source: Website or device, user or rule triggered
** Partition key: Vendor/ad ID composite
** High-frequency operations: Check vendor balance, serve ad (in target device format), update vendor balance
** Lower-frequency operations: Report live ad view and click-thru stats by device (vendor-initiated)

* Application: Telephone exchange call detail record (CDR) management
** Data source: Call initiation request
** Partition key: Caller ID
** High-frequency operations: Real-time authorization (based on plan and balance)
** Lower-frequency operations: Fraud analysis/detection

* Application: Airline reservation/ticketing
** Data source: Customers (web) and airline (web and internal systems)
** Partition key: Customer (flight info is replicated)
** High-frequency operations: Seat selection (lease system), add/drop seats, baggage check-in
** Lower-frequency operations: Seat availability/flight, flight schedule changes, passenger re-bookings on flight cancellations

## Analytics Use Cases

### Kevin Weil at Twitter is great at providing Hadoop use cases. At Twitter this includes counting big data with standard counts, min, max, std dev; correlating big data with probabilities, covariance, influence; and research on Big data. Hadoop is on the fringe of NoSQL, but it's very useful to see what kind of problems are being solved with it.

* How many request do we serve each day?
* What is the average latency? 95% latency?
* Grouped by response code: what is the hourly distribution?
* How many searches happen each day at Twitter?
* Where do they come from?
* How many unique queries?
* How many unique users?
* Geographic distribution?
* How does usage differ for mobile users?
* How does usage differ for 3rd party desktop client users?
* Cohort analysis: all users who signed up on the same day—then see how they differ over time.
* Site problems: what goes wrong at the same time?
* Which features get users hooked?
* Which features do successful users use often?
* Search corrections and suggestions (not done now at Twitter, but coming in the feature).
* What can web tell about a user from their tweets?
* What can we tell about you from the tweets of those you follow?
* What can we tell about you from the tweets of your followers?
* What can we tell about you from the ratio of your followers/following?
* What graph structures lead to successful networks? (Twitter’s graph structure is interesting since it’s not two-way)
* What features get a tweet retweeted?
* When a tweet is retweeted, how deep is the corresponding retweet three?
* Long-term duplicate detection (short term for abuse and stopping spammers)
* Machine learning. About not quite knowing the right questions to ask at first. How do we cluster users?
* Language detection (contact mobile providers to get SMS deals for users—focusing on the most popular countries at first).
* How can we detect bots and other non-human tweeters?

## Poor Use Cases

    OLTP. Outside VoltDB, complex multi-object transactions are generally not supported. Programmers are supposed to denormalize, use documents, or use other complex strategies like compensating transactions.
    Data integrity. Most of the NoSQL systems rely on applications to enforce data integrity where SQL uses a declarative approach. Relational databases are still the winner for data integrity.
    Data independence.  Data outlasts applications. In NoSQL applications drive everything about the data. One argument for the relational model is as a repository of facts that can last for the entire lifetime of the enterprise, far past the expected life-time of any individual application.
    SQL. If you require SQL then very few NoSQL system will provide a SQL interface, but more systems are starting to provide SQLish interfaces.
    Ad-hoc queries. If you need to answer real-time questions about your data that you can’t predict in advance, relational databases are generally still the winner. 
    Complex relationships. Some NoSQL systems support relationships, but a relational database is still the winner at relating.
    Maturity and stability. Relational databases still have the edge here. People are familiar with how they work, what they can do, and have confidence in their reliability. There are also more programmers and toolsets available for relational databases. So when in doubt, this is the road that will be traveled.

### Related Articles

<ul>
<li><a href="http://news.ycombinator.com/item?id=1976429">Hacker News</a>&nbsp;and <a href="http://www.reddit.com/r/programming/comments/ehaeq/high_scalability_what_the_heck_are_you_actually/">Reddit</a> thread on this Post. More use case suggestions there.&nbsp;</li>
<li><a href="http://nosql-database.org/">List of NoSQL Systems</a></li>
<li><a href="http://research.yahoo.com/node/90">Pig</a> - infrastructure to support ad-hoc analysis of very large data sets.</li>
<li><a href="http://gigaom.com/2009/06/07/digging-deeper-into-data-with-hadoop/">Digging Deeper Into Data With Hadoop</a>&nbsp;By Gary Orenstein&nbsp;</li>
<li><a href="http://journal.uggedal.com/nosql-east-2009---summary-of-day-1">NoSQL East 2009 - Summary of Day 1</a>&nbsp;by Eivind Uggedal</li>
<li><a href="http://nsaunders.wordpress.com/2010/08/05/the-nosql-approach-struggling-to-see-the-benefits/">The “NoSQL” approach: struggling to see the benefits</a>&nbsp;by Neil Saunders&nbsp;</li>
<li> <a href="http://static.last.fm/johan/nosql-20090611/intro_nosql.pdf ">Design Patterns for DistributedNon-Relational Databases</a> by Todd Lipcon. </li>
<li><a href="http://gigaom.com/2009/10/25/the-future-is-big-data-in-the-cloud/">The Future Is Big Data in the Cloud</a> By Ping Li</li>
<li><a href="http://www.odbms.org/blog/2010/02/document-stores-nosql-databases-odbmss/">One size does not fit all: “document stores”, “nosql databases” , ODBMSs</a>&nbsp;by Roberto V. Zicari</li>
<li><a href="http://www.zdnet.com/blog/open-source/nosql-is-for-niches/6128">NoSQL is for niches</a>&nbsp;By Dana Blankenhorn.</li>
<li><a href="http://www.mongodb.org/display/DOCS/Use+Cases">MongoDB Use Cases</a></li>
<li><a href="http://kylebanker.com/blog/2010/04/30/mongodb-and-ecommerce/">MongoDB and Ecommerce</a>&nbsp;by&nbsp;&nbsp;Kyle Banker</li>
<li><a href="http://blog.mongodb.org/post/1200539426/archiving-a-good-mongodb-use-case">Archiving - a good MongoDB use case?</a></li>
<li><a href="http://facility9.com/2010/09/16/five-reasons-to-use-nosql">Five Reasons to Use NoSQL</a>&nbsp;by&nbsp;Jeremiah Peschka</li>
<li><a href="http://www.itbusinessedge.com/cm/blogs/lawson/the-business-case-for-nosql-noetl-and-noproblems/?cs=40284">The Business Case for NoSQL, NoETL and NoProblems</a>&nbsp;by&nbsp;Loraine Lawson</li>
<li><a href="http://intelligent-enterprise.informationweek.com/blog/archives/2010/03/is_it_time_for.html;jsessionid=3YOYNBBPASI5VQE1GHRSKH4ATMY32JVN">Is It Time For NoETL</a>?&nbsp;by Seth Grimes</li>
<li><a href="http://blog.mongodb.org/post/660037122/holy-large-hadron-collider-batman">Holy Large Hadron Collider, Batman!</a></li>
<li><a href="http://teddziuba.com/2010/03/i-cant-wait-for-nosql-to-die.html">I Can't Wait for NoSQL to Die</a> by Ted Dziuba.</li>
<li><a href="http://intelligent-enterprise.informationweek.com/channels/information_management/showArticle.jhtml;jsessionid=ZLGYK42ZWIZSXQE1GHOSKH4ATMY32JVN?articleID=227701021&amp;pgno=2#">NoSQL Basics, Benefits and Best-Fit Scenarios</a> by Curt Monash&nbsp;</li>
<li><a href="http://simonwillison.net/static/2010/redis-tutorial/">Redis Tutorial</a> by Simon Willison</li>
<li><a href="http://simonwillison.net/2009/Oct/22/redis/ ">Why I Like Redis</a> by Simon Willison</li>
<li><a href="http://www.linux-mag.com/id/7496">Redis: Lightweight key/value Store That Goes the Extra Mile</a> by&nbsp;Jeremy Zawodny</li>
<li><a href="http://www.slideshare.net/ezmobius/redis-remote-dictionary-server">Remote Dictionary Server</a></li>
<li><a href="http://devlicio.us/blogs/hadi_hariri/archive/2010/11/24/is-nosql-for-me-i-m-just-a-small-fish.aspx">Is NoSQL for me? I’m just a small fish</a>&nbsp;by Hadi Hariri</li>
<li><a href="http://s3.amazonaws.com/cimlabs/Oredev-Enterprise-NoSQL.pdf">Why Big Enterprises are Interested in NoSQL</a>&nbsp;by&nbsp;Jon Moore</li>
<li><a href="http://blog.nahurst.com/visual-guide-to-nosql-systems">Visual Guide to NoSQL Systems</a> by Nathan Hurst</li>
<li><a href="http://codahale.com/you-cant-sacrifice-partition-tolerance/">You Can't Sacrifice Partition Tolerance</a> by Coda Hale</li>
<li><a href="http://perfcap.blogspot.com/">NoSQL Netflix Use Case Comparison</a> by Adrian Cockcroft</li>
<li><a href="http://cattell.net/datastores/Datastores.pdf">Comparison guide of horizontally scalable datastores</a> by Rick Cattell</li>
<li><a href="http://www.igvita.com/2010/06/24/weak-consistency-and-cap-implications/">Weak Consistency and CAP Implications</a>&nbsp;by Ilya Grigorik&nbsp;</li>
<li><a href="http://www.igvita.com/2010/03/01/schema-free-mysql-vs-nosql/">Schema-Free MySQL vs NoSQL</a>&nbsp;&nbsp;by Ilya Grigorik&nbsp;</li>
<li><a href="http://www.slideshare.net/peterneubauer/neo4j-5-cool-graph-examples-4473985">Neo4j - 5 Cool Graph Examples</a></li>
<li><a href="http://stackoverflow.com/questions/1000162/have-abyone-used-graph-based-databases-http-neo4j-org">Has anyone used Graph-based Databases</a></li>
<li><a href="http://neotechnology.com/customers">Neotechnology Uses Cases</a></li>
<li><a href="http://www.couchone.com/case-study-ataxo">CouchOne Ataxo Case Study</a></li>
<li><a href="http://blogs.neotechnology.com/emil/2009/11/nosql-scaling-to-size-and-scaling-to-complexity.html">NOSQL: scaling to size and scaling to complexity</a>&nbsp;by Emil Eifrem</li>
<li><a href="http://jeremypinkham.com/post/1587967351/nosql-noproblem-not-really-but-its-still-awesome#">NoSQL, NoProblem (Not Really… but it’s still awesome)</a>&nbsp;by Jeremy Pinkham</li>
<li><a href="http://it.toolbox.com/blogs/oracle-guide/acid-vs-base-25938">An Expert's Guide to Oracle Technology</a>&nbsp;by Lewis Cunningham</li>
<li>N<a href="http://www.cloudbook.net/resources/stories/nosql-vs-sql-why-not-both">oSQL vs SQL, Why Not Both?</a>&nbsp;By Alaric Snell-Pym&nbsp;</li>
<li><a href="http://www.cbsolution.net/roller/ontarget/entry/databases_relational_vs_object_vs">Databases: relational vs object vs graph vs document</a>&nbsp;by On Target&nbsp;</li>
<li><a href="http://blog.membase.com/use-cases-are-driving-divergence-and-convergence-nosql-solutions">Use cases are driving the divergence, and the convergence, of NoSQL solutions</a>&nbsp;by James &nbsp;Phillips</li>
<li><a href="http://blogs.the451group.com/information_management/2010/11/12/the-beginning-of-the-end-of-nosql/">The beginning of the end of NoSQL</a> by&nbsp;Matthew Aslett&nbsp;</li>
<li><a href="http://msdn.microsoft.com/en-us/magazine/ee310029.aspx">Going NoSQL with MongoDB</a>&nbsp;by&nbsp;Ted Neward</li>
<li><a href="http://www.rackspacecloud.com/blog/2009/11/09/nosql-ecosystem/">NoSQL Ecosystem</a> by&nbsp;Jonathan Ellis</li>
<li><a href="http://nosql.mypopescu.com/post/287581423/the-new-dimension-of-nosql-scalability-complexity">The New Dimension of NoSQL Scalability: Complexity</a>&nbsp;by Alex Popescu</li>
<li><a href="http://themindstorms.blogspot.com/2009/05/quick-reference-to-alternative-data.html">Quick Reference to Alternative data storages</a>&nbsp;by Alex Popescu</li>
<li><a href="http://www.havemacwillblog.com/2008/11/6-reasons-why-relational-database-will-be-superseded/">6 Reasons Why Relational Database Will Be Superseded</a>&nbsp;&nbsp;by Robin Bloor</li>
<li><a href="http://www.viget.com/extend/nosql-misconceptions/">NoSQL Misconceptions</a> by Ben Scofield</li>
<li><a href="http://adam.heroku.com/past/2009/7/6/sql_databases_dont_scale/">SQL Databases Don't Scale</a> by Adam Wiggins&nbsp;</li>
<li><a href="http://www.cs.brown.edu/~ugur/fits_all.pdf">“One Size Fits All”: An Idea Whose Time Has Come and Gone</a>&nbsp;by&nbsp;Michael Stonebraker and&nbsp;Uğur Çetintemel</li>
<li><a href="http://www.igvita.com/2009/12/07/future-of-rdbms-is-ram-clouds-ssd/">Future of RDBMS is RAM Clouds &amp; SSD</a>&nbsp;by&nbsp;Ilya Grigorik</li>
<li>
<div id="_mcePaste"></div>
<div id="_mcePaste"><a href="http://www.slideshare.net/uri1803/to-scale-or-not-to-scale-keyvalue-document-sql-jpa-whats-right-for-my-app#">To scale or not to scale: Key/Value, Document, SQL, JPA</a> &nbsp;by Uri Cohen</div>
<div id="_mcePaste"></div>
<div id="_mcePaste"></div>
</li>
</ul>