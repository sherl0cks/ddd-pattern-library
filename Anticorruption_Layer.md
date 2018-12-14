# Anticorruption	Layer

Translation	 layers	 can	 be	 simple,	 even	 elegant, when	 bridging	 well-designed	 bounded	
contexts	with	cooperative	teams.	But	when	control	or	communication	is	not	adequate	to	pull	
off	 a	 shared	 kernel,	 partner	 or	 customer/supplier	 relationship,	 translation	 becomes	 more	
complex.	The	translation	layer	takes	on a	more	defensive	tone.	

A	 large	 interface	 with	 an	 upstream	 system	 can	 eventually	 overwhelm	 the	 intent	 of	 the	
downstream	 model	 altogether,	 causing	 it	 to	 be	 modified	 to	 resemble	 the	 other	 system’s	
model	in	an	ad	hoc	fashion.	The	models	of	legacy	systems	are usually	weak	(if	not	big	balls	of	
mud),	and	even	 the	exception	 that	is	clearly	designed	may	not	 fit	 the	needs	of	 the	current	
project,	making	it	impractical	to	conform	to	the	upstream	model.	Yet	the	integration	may	be	
very	valuable	or	even	required	for	the downstream	project.

## Therefore:

As	a	downstream	client,	create	an	isolating	layer	to	provide	your	system	with	functionality	
of	the	upstream	system	in	terms	of	your	own	domain	model.	This	layer	talks	to	the	other	
system	through	its	existing	interface,	requiring	little	or	no	modification	to	the	other	system.	
Internally,	 the	 layer	 translates	 in	 one	 or	 both	 directions	 as	 necessary	 between	 the	 two	
models.

## Source

Page 34 of the [DDD reference](http://domainlanguage.com/wp-content/uploads/2016/05/DDD_Reference_2015-03.pdf). Remixed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/legalcode).
