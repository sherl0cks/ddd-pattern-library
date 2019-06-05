# [Domain] Services
Sometimes,	it	just	isn’t	a	thing.

Some	 concepts	 from	 the	 domain	 aren’t	 natural	 to	 model	 as	 objects.	 Forcing	 the	 required	
domain	 functionality	 to	 be	 the	 responsibility	 of	 an	 entity	 or	 value	 either	 distorts	 the	
definition	of	a	model-based	object	or	adds	meaningless	artificial	objects.	

## Therefore:
When	a	significant	process	or	transformation	in	the	domain	is	not	a	natural	responsibility	
of	 an	 entity	 or	 value	 object,	 add	 an	 operation	 to	 the	 model	 as	 a	 standalone	 interface	
declared	as	a	service.	Define	a	service	contract,	a	set	of	assertions	about	interactions	with	
the	service.	(See	assertions.)	State	these	assertions	in	the	ubiquitous	language	of	a	specific	
bounded	 context.	 Give	 the	 service	 a	 name,	 which	 also	 becomes	 part	 of	 the	 ubiquitous	
language.

## Source

Page 14 of the [DDD reference](http://domainlanguage.com/wp-content/uploads/2016/05/DDD_Reference_2015-03.pdf). Remixed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/legalcode).
