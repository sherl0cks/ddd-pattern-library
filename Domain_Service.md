# Domain Services
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

NOTE: Domain has been added to the title for clarity, as a common issue is handling the overloaded terms of [Domain vs Application Service](https://enterprisecraftsmanship.com/2016/09/08/domain-services-vs-application-services/)


# This section is copied verbatim from the original blue book because I don't think the reference communicates the idea quite right.
Forgive me if you ever see this Eric.

Sometimes, it just isn't a thing.
In some cases, the clearest and most pragmatic design includes operations that do not
conceptually belong to any object. Rather than force the issue, we can follow the natural contours
of the problem space and include `SERVICES` explicitly in the model.

--- 

There are important domain operations that can't find a natural home in an `ENTITY` or `VALUE`
`OBJECT`. Some of these are intrinsically activities or actions, not things, but since our modeling
paradigm is objects, we try to fit them into objects anyway.
Now, the more common mistake is to give up too easily on fitting the behavior into an appropriate
object, gradually slipping toward procedural programming. But when we force an operation into an
object that doesn't fit the object's definition, the object loses its conceptual clarity and becomes
hard to understand or refactor. Complex operations can easily swamp a simple object, obscuring
its role. And because these operations often draw together many domain objects, coordinating
them and putting them into action, the added responsibility will create dependencies on all those
objects, tangling concepts that could be understood independently.
Sometimes services masquerade as model objects, appearing as objects with no meaning beyond
doing some operation. These "doers" end up with names ending in "Manager" and the like. They
have no state of their own nor any meaning in the domain beyond the operation they host. Still, at
least this solution gives these distinct behaviors a home without messing up a real model object.

**Some concepts from the domain aren't natural to model as objects. Forcing the
required domain functionality to be the responsibility of an ENTITY or VALUE either
distorts the definition of a model-based object or adds meaningless artificial objects.**

A `SERVICE` is an operation offered as an interface that stands alone in the model, without
encapsulating state, as `ENTITIES` and `VALUE OBJECTS` do. `SERVICES` are a common pattern in technical
frameworks, but they can also apply in the domain layer.
The name service emphasizes the relationship with other objects. Unlike `ENTITIES` and `VALUE
OBJECTS`, it is defined purely in terms of what it can do for a client. A `SERVICE` tends to be named for
an activity, rather than an entity—a verb rather than a noun. A `SERVICE` can still have an abstract,
intentional definition; it just has a different flavor than the definition of an object. A `SERVICE` should
still have a defined responsibility, and that responsibility and the interface fulfilling it should be
defined as part of the domain model. Operation names should come from the `UBIQUITOUS
LANGUAGE` or be introduced into it. Parameters and results should be domain objects.
`SERVICES` should be used judiciously and not allowed to strip the `ENTITIES` and `VALUE OBJECTS` of all
their behavior. But when an operation is actually an important domain concept, a `SERVICE` forms a
natural part of a `MODEL-DRIVEN DESIGN`. Declared in the model as a `SERVICE`, rather than as a
phony object that doesn't actually represent anything, the standalone operation will not mislead
anyone.

A good `SERVICE` has three characteristics.
1. The operation relates to a domain concept that is not a natural part of an `ENTITY` or `VALUE OBJECT`.
2. The interface is defined in terms of other elements of the domain model.
3. The operation is stateless.

Statelessness here means that any client can use any instance of a particular `SERVICE` without
regard to the instance's individual history. The execution of a `SERVICE` will use information that is
accessible globally, and may even change that global information (that is, it may have side
effects). But the `SERVICE` does not hold state of its own that affects its own behavior, as most
domain objects do.

**When a significant process or transformation in the domain is not a natural
responsibility of an `ENTITY` or `VALUE OBJECT`, add an operation to the model as a
standalone interface declared as a `SERVICE`. Define the interface in terms of the
language of the model and make sure the operation name is part of the `UBIQUITOUS
LANGUAGE`. Make the `SERVICE` stateless.**

---

## `SERVICES` and the Isolated Domain Layer

This pattern is focused on those `SERVICES` that have an important meaning in the domain in their
own right, but of course `SERVICES` are not used only in the domain layer. It takes care to
distinguish `SERVICES` that belong to the domain layer from those of other layers, and to factor
responsibilities to keep that distinction sharp.

Most `SERVICES` discussed in the literature are purely technical and belong in the infrastructure
layer. Domain and application `SERVICES` collaborate with these infrastructure `SERVICES`. For
example, a bank might have an application that sends an e-mail to a customer when an account
balance falls below a specific threshold. The interface that encapsulates the e-mail system, and
perhaps alternate means of notification, is a `SERVICE` in the infrastructure layer.

It can be harder to distinguish application `SERVICES` from domain `SERVICES`. The application layer is
responsible for ordering the notification. The domain layer is responsible for determining if a
threshold was met—though this task probably does not call for a `SERVICE`, because it would fit the
responsibility of an "account" object. That banking application could be responsible for funds
transfers. If a SERVICE were devised to make appropriate debits and credits for a funds transfer,
that capability would belong in the domain layer. Funds transfer has a meaning in the banking
domain language, and it involves fundamental business logic. Technical `SERVICES` should lack any
business meaning at all.

Many domain or application `SERVICES` are built on top of the populations of `ENTITIES` and `VALUES`,
behaving like scripts that organize the potential of the domain to actually get something done.
`ENTITIES` and `VALUE OBJECTS` are often too fine-grained to provide a convenient access to the
capabilities of the domain layer. Here we encounter a very fine line between the domain layer and
the application layer. For example, if the banking application can convert and export our
transactions into a spreadsheet file for us to analyze, that export is an application `SERVICE`. There
is no meaning of "file formats" in the domain of banking, and there are no business rules involved.

On the other hand, a feature that can transfer funds from one account to another is a domain
`SERVICE` because it embeds significant business rules (crediting and debiting the appropriate
accounts, for example) and because a "funds transfer" is a meaningful banking term. In this case,
the `SERVICE` does not do much on its own; it would ask the two Account objects to do most of the
work. But to put the "transfer" operation on the Account object would be awkward, because the
operation involves two accounts and some global rules.

We might like to create a Funds Transfer object to represent the two entries plus the rules and
history around the transfer. But we are still left with calls to `SERVICES` in the interbank networks.
What's more, in most development systems, it is awkward to make a direct interface between a
domain object and external resources. We can dress up such external `SERVICES` with a `FACADE` that
takes inputs in terms of the model, perhaps returning a Funds Transfer object as its result. But
whatever intermediaries we might have, and even though they don't belong to us, those `SERVICES`
are carrying out the domain responsibility of funds transfer.

### Partitioning Services into Layers
#### **Application**: Funds Transfer App Service
- Digests input (such as an XML request).
- Sends message to domain service for fulfillment.
- Listens for confirmation.
- Decides to send notification using infrastructure service.
#### **Domain**: Funds Transfer Domain Service
- Interacts with necessary Account and Ledger objects, making appropriate debits and credits.
- Supplies confirmation of result (transfer allowed or not, and so on).
#### **Infrastructure**: Send Notification Service
- Sends e-mails, letters, and other communications as directed by the
application.

## Granularity

Although this pattern discussion has emphasized the expressiveness of modeling a concept as a
`SERVICE`, the pattern is also valuable as a means of controlling granularity in the interfaces of the
domain layer, as well as decoupling clients from the `ENTITIES` and `VALUE OBJECTS`.

Medium-grained, stateless `SERVICES` can be easier to reuse in large systems because they
encapsulate significant functionality behind a simple interface. Also, fine-grained objects can lead
to inefficient messaging in a distributed system.

As previously discussed, fine-grained domain objects can contribute to knowledge leaks from the
domain into the application layer, where the domain object's behavior is coordinated. The
complexity of a highly detailed interaction ends up being handled in the application layer, allowing
domain knowledge to creep into the application or user interface code, where it is lost from the
domain layer. The judicious introduction of domain services can help maintain the bright line
between layers.

This pattern favors interface simplicity over client control and versatility. It provides a medium
grain of functionality very useful in packaging components of large or distributed systems. And
sometimes a `SERVICE` is the most natural way to express a domain concept.

## Access to `SERVICES`

Distributed system architectures, such as J2EE and CORBA, provide special publishing mechanisms
for `SERVICES`, with conventions for their use, and they add distribution and access capabilities. But
such frameworks are not always in use on a project, and even when they are, they are likely to be
overkill when the motivation is just a logical separation of concerns.

The means of providing access to a `SERVICE` is not as important as the design decision to carve off
specific responsibilities. A "doer" object may be satisfactory as an implementation of a `SERVICE`'s
interface. A simple `SINGLETON` (Gamma et al. 1995) can be written easily to provide access. Coding
conventions can make it clear that these objects are just delivery mechanisms for `SERVICE`
interfaces, and not meaningful domain objects. Elaborate architectures should be used only when
there is a real need to distribute the system or otherwise draw on the framework's capabilities.
