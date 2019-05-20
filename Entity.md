# Entities

Many	objects	represent	a	thread	of	continuity	and	identity,	going	through	a	lifecycle,	though	
their	attributes	may	change.

Some	objects	are	not	defined	primarily	by	their	attributes.	They	represent	a	thread	of	identity	
that	runs	through	time	and	often	across	distinct	representations.	Sometimes	such	an	object	
must	 be	 matched	 with	 another	 object	 even	 though	 attributes	 differ.	 An	 object	 must	 be	
distinguished	from	other	objects	even	though	they	might	have	the	same	attributes.	Mistaken	
identity	can	lead	to	data	corruption.

## Therefore:

When	an	object	is	distinguished	by	its	identity,	rather	than	its	attributes,	make	this	primary	
to	 its	 definition	 in	 the	 model.	 Keep	 the	 class	 definition	 simple	 and	 focused	 on	 life	 cycle	
continuity	and	identity.

Define	a	means	of	distinguishing	each	object	 regardless	of	its	 form	or	history.	Be	alert	 to	
requirements	 that	 call	 for	 matching	 objects	 by	 attributes.	 Define	 an	 operation	 that	 is	
guaranteed	to	produce	a	unique	result	for	each	object,	possibly	by	attaching	a	symbol	that	
is	guaranteed	unique.	This	means	of	identification	may	come	from	the	outside,	or	it	may	be	
an	arbitrary	identifier	created	by	and	for	the	system,	but	it	must	correspond	to	the	identity	
distinctions	in	the	model.

The	model	must	define	what	it	means	to	be	the	same	thing.

## Source

Page 11 of the [DDD reference](http://domainlanguage.com/wp-content/uploads/2016/05/DDD_Reference_2015-03.pdf). Remixed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/legalcode).
