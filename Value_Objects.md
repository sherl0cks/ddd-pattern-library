# Value	Objects

Some	objects	describe	or	compute	some	characteristic	of	a	thing.

Many	objects	have	no	conceptual	identity.

Tracking	 the	identity	of	entities	is	essential,	but	attaching	identity	 to	other	objects	can	hurt	
system	performance,	add	analytical	work,	and	muddle	the	model	by	making	all	objects	look	
the	same.	Software	design	is	a	constant	battle	with	complexity.	We	must	make	distinctions	so	
that	special	handling	is	applied	only	where	necessary.

However,	 if	 we	 think	 of	 this	 category	 of	 object	 as	 just	 the	 absence	 of	 identity,	 we	 haven’t	
added	much	to	our	toolbox	or	vocabulary.	In	fact,	these	objects	have	characteristics	of	their	
own,	and	their	own	significance	to	the	model.	These	are	the	objects	that	describe	things.	

## Therefore:

When	you	care	only	about	the	attributes	and	logic	of	an	element	of	the	model,	classify	it	as	
a	value	object.	Make	it	express	the	meaning	of	the	attributes	it	conveys	and	give	it	related	
functionality.	 Treat	 the	 value	 object	 as	 immutable.	 Make	 all	 operations	 Side-effect-free	
Functions	 that	don’t	depend	on	any	mutable	state.	Don’t	give	a	value	object	any	identity	
and	avoid	the	design	complexities	necessary	to	maintain	entities.	

## Source

Page 12 of the [DDD reference](http://domainlanguage.com/wp-content/uploads/2016/05/DDD_Reference_2015-03.pdf). Remixed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/legalcode).
