# Aggregates

It	 is	 difficult	 to	 guarantee	 the	 consistency	 of	 changes	 to	 objects	 in	 a	 model	 with	 complex	
associations.	Objects	are	supposed	to	maintain	their	own	internal	consistent	state,	but	they	
can	 be	 blindsided	 by	 changes	 in	 other	 objects	 that	 are	 conceptually	 constituent	 parts.	
Cautious	 database	 locking	 schemes	 cause	 multiple	 users	 to	 interfere	 pointlessly	 with	 each	
other	and	can make	a	system	unusable.	Similar	issues	arise	when	distributing	objects	among	
multiple	servers,	or	designing	asynchronous	transactions.

## Therefore:

Cluster	the	entities	and	value	objects	into	aggregates	and	define	boundaries	around	each.	
Choose	 one	 entity	 to	 be	 the	 root	 of	 each	 aggregate,	 and	 allow	 external	 objects	 to	 hold	
references	 to	 the	 root	 only	 (references	 to	 internal	members	 passed	 out	 for	 use	 within	 a	
single	operation	only).	Define	properties	and	invariants	 for	 the	aggregate	as	a	whole	and	
give	enforcement	responsibility	to	the	root	or	some	designated	framework	mechanism.

Use	the	same	aggregate	boundaries	to	govern	transactions	and	distribution.

Within	 an	 aggregate	 boundary,	 apply	 consistency	 rules	 synchronously.	 Across	 boundaries,	
handle	updates	asynchronously.

Keep	 an	 aggregate	 together	 on	 one	 server.	 Allow	 different	 aggregates	 to	 be	 distributed	
among	nodes.	

When	 these	 design	 decisions	 are	 not	 being	 guided	 well	 by	 the	 aggregate	 boundaries,	
reconsider	 the	 model.	 Is	 the	 domain	 scenario	 hinting	 at	 an	 important	 new	 insight?	 Such	
changes	 often	 improve	 the	 model’s	 expressiveness	 and	 flexibility	 as	 well	 as	 resolving	 the	
transactional	and	distributional	issues

## Source

Page 16 of the [DDD reference](http://domainlanguage.com/wp-content/uploads/2016/05/DDD_Reference_2015-03.pdf). Remixed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/legalcode).
