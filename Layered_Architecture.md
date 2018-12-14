# Layered Architecture


In	 an	 object-oriented	 program,	 UI,	 database,	 and	 other	 support	 code	 often	 gets	 written	
directly	into	the	business	objects.	Additional	business	logic	is	embedded	in	the	behavior	of	UI	
widgets	and	database	scripts.	This	happens	because	it	is the	easiest	way	to	make	things	work,	
in	the	short	run.	

  When	 the	 domain-related	 code	 is	 diffused	 through	 such	 a	 large	 amount	 of	 other	 code,	 it	
becomes	 extremely	 difficult	 to	 see	 and	 to	 reason	 about.	 Superficial	 changes	 to	 the	 UI	 can	
actually	change	business	logic.	To	change	a	business	rule	may	require	meticulous	tracing	of	UI	
code,	 database	 code,	 or	 other	 program	 elements.	 Implementing	 coherent,	 model-driven	
objects	 becomes	 impractical.	 Automated	 testing	 is	awkward.	With	all	 the	 technologies	and	
logic	involved	in	each	activity,	a	program	must	be	kept	very	simple	or	it	becomes	impossible	
to	understand.

## Therefore:
  Isolate	 the	 expression	 of	 the	 domain	 model	 and	 the	 business	 logic,	 and	 eliminate	 any	
dependency	on	infrastructure,	user	interface,	or	even	application	logic	that	is	not	business	
logic.	Partition	a	 complex	program	into	layers.	Develop	a	design	within	 each	layer	 that	is	
cohesive	and	that	depends	only	on	the	layers	below.	Follow	standard	architectural	patterns	
to	 provide	 loose	 coupling	 to	 the	 layers	 above.	 Concentrate	 all	 the	 code	 related	 to	 the	
domain	 model	 in	 one	 layer	 and	 isolate	 it	 from	 the	 user	 interface,	 application,	 and	
infrastructure	code.	The	domain	objects,	free	of	the	responsibility	of	displaying	themselves,	
storing	themselves,	managing	application	tasks,	and	so	forth,	can	be	focused	on	expressing	
the	 domain	model.	This	allows	a	model	 to	 evolve	 to	 be	 rich	 enough	and	 clear	 enough	 to	
capture	essential	business	knowledge	and	put	it	to	work.	

The	key	goal	here	is	isolation.	Related	patterns,	such	as	“Hexagonal	Architecture”	may	serve	
as	 well	 or	 better	 to	 the	 degree	 that	 they	 allow	 our	 domain	 model	 expressions	 to	 avoid	
dependencies	on	and	references	to	other	system	concerns.
