# Factories

When	creation	of	an	entire,	internally	consistent	aggregate,	or	a	large	value	object,	becomes	
complicated	or	reveals	too	much	of	the	internal	structure,	factories	provide	encapsulation.

Creation	of	an	object	can	be	a	major	operation	in	itself,	but	complex	assembly	operations	do	
not	fit	the	responsibility	of	the	created	objects.	Combining	such	responsibilities	can	produce	
ungainly	designs	that	are	hard	to	understand.	Making	the	client	direct	construction	muddies	
the	design	of	 the	client,	breaches	encapsulation	of	 the	assembled	object	or	aggregate,	and	
overly	couples	the	client	to	the	implementation	of	the	created	object.
## Therefore:

Shift	 the	 responsibility	 for	 creating	 instances	 of	 complex	 objects	 and	 aggregates	 to	 a	
separate	 object,	 which	 may	 itself	 have	 no	 responsibility	 in	 the	 domain	 model	 but	 is	 still	
part	of	the	domain	design.	Provide	an	interface	that	encapsulates	all	complex	assembly	and	
that	 does	 not	 require	 the	 client	 to	 reference	 the	 concrete	 classes	 of	 the	 objects	 being	
instantiated.	 Create	 an	 entire	 aggregate	 as	 a	 piece,	 enforcing	 its	 invariants.	 Create	 a	
complex	value	object	as	a	piece,	possibly	after	assembling	the	elements	with	a	builder.	

## Source

Page 18 of the [DDD reference](http://domainlanguage.com/wp-content/uploads/2016/05/DDD_Reference_2015-03.pdf). Remixed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/legalcode).
