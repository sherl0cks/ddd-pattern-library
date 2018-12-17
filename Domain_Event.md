# Domain	Events

Something	happened	that	domain experts	care	about.
An	entity is	responsible	 for	 tracking	its	state	and	 the	rules	regulating	its	lifecycle.	But	if	you	
need	to	know	the	actual	causes	of	the	state	changes,	this	is	typically	not	explicit,	and	it	may	
be	difficult	to	explain	how	the	system	got	the	way	it	is.	Audit	trails	can	allow	tracing,	but	are	
not	 usually	 suited	 to	 being	 used	 for	 the	 logic	 of	 the	 program	 itself.	 Change	 histories	 of	
entities	 can	 allow	 access	 to	 previous	 states,	 but	 ignores	 the	meaning	 of	 those	 changes,	 so	
that	any	manipulation	of	the	information	is	procedural,	and	often	pushed	out	of	the	domain	
layer.

A	distinct,	though	related	set	of	issues	arises	in	distributed	systems.	The	state	of	a	distributed	
system	cannot	be	kept	completely	consistent	at	all	times.	We	keep	the	aggregates	internally	
consistent	 at	 all	 times,	 while	making	 other	 changes	 asynchronously.	 As	 changes	 propagate	
across	nodes	of	a	network,	it	can	be	difficult	to	resolve	multiple	updates	arriving	out	of	order	
or	from	distinct	sources.

## Therefore:

Model	information	about	activity	in	 the	 domain	as	a	 series	 of	 discrete	 events.	Represent	
each	event	as	a	domain	object.	These	are	distinct	 from	system	events	that	reflect	activity	
within	 the	 software	 itself,	 although	 often	 a	 system	 event	 is	 associated	 with	 a	 domain	
event,	either	as	part	of	a	response	to	the	domain	event	or	as	a	way	of	carrying	information	
about	the	domain	event	into	the	system.

A	domain	event	is	a	full-fledged	part	of	the	domain	model,	a	representation	of	something	
that	happened	in	 the	domain.	Ignore	irrelevant	domain	activity	while	making	 explicit	 the	
events	 that	 the	 domain	 experts	 want	 to	 track or	 be	 notified	 of,	 or	 which	 are	 associated	
with	state	change	in	the	other	model	objects.

In	 a	 distributed	 system,	 the	 state	 of	 an	 entity	 can	 be	 inferred	 from	 the	 domain	 events	
currently	 known	 to	 a	 particular	 node,	 allowing	 a	 coherent	 model	 in	 the	 absence	 of	 full	
information	about	the	system	as	a	whole.

Domain	events	are	 ordinarily	 immutable,	as	 they	are	a	 record	 of	 something	 in	 the	 past.	In	
addition	to	a	description	of	the	event,	a	domain	event	typically	contains	a	timestamp	for	the	
time	 the	 event	 occurred and	 the	 identity	 of	 entities	 involved	 in	 the	 event.	 Also,	 a	 domain	
event	often	has	a	separate	timestamp	indicating	when	the	event	was	entered	into	the	system	
and	the	identity	of	the	person	who	entered	it.	When	useful,	an	identity	for	the	domain	event	
can	be	based	on	some	set	of	these	properties.	So,	for	example,	if	two	instances	of	the	same	
event	arrive	at	a	node	they	can	be	recognized as	the	same

## Source

Page 13 of the [DDD reference](http://domainlanguage.com/wp-content/uploads/2016/05/DDD_Reference_2015-03.pdf). Remixed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/legalcode).
