<img src="chapters/media/image4.png" width="300" style="margin: 0 auto; text-align: center" />

# Skyve Enterprise Platform
## Developer Guide

![](chapters/media/image5.png)

### Contents

* [Section 1: Introduction](#introduction)
  * **[Chapter 1: Architectural Overview](#architectural-overview)**
    * [1.1: Technical description](#technical-description)
    * [1.2: General Approach and Design Principles](#general-approach-and-design-principles)
    * [1.3: Use of SQL](#use-of-sql)
    * [1.4: Multi-tenant & Mass-Customisation](#multi-tenant--mass-customisation)
    * [1.5: “Open-source” Inclusions ](#open-source-inclusions)
  * [Chapter 2: Concepts](chapters/concepts.md)
  * [Chapter 3: Identifying the Skyve Version](chapters/concepts.md)
  * [Chapter 4: Security, Persistence and Access control](chapters/security-persistence-and-access-control.md)
  * [Chapter 5: Exception Handling](chapters/exception-handling.md)
* [Section 2: Building Applications](chapters/customers.md)
  * [Chapter 6: Customers](chapters/customers.md)
  * [Chapter 7: Modules](chapters/modules.md)
  * [Chapter 8: Documents](chapters/documents.md)
  * [Chapter 9: Converters](chapters/converters.md)
  * [Chapter 10: Bizlets](chapters/bizlets.md)
  * [Chapter 11: Views](chapters/views.md)
  * [Chapter 12: Actions](chapters/actions.md)
  * [Chapter 13: Reports](chapters/reports.md)
  * [Chapter 14: Jobs](chapters/jobs.md)
  * [Chapter 15: Utility Classes](chapters/utility-classes.md)
  * [Chapter 16: Common Patterns](chapters/common-patterns.md)
* [Section 3: Persistence](chapters/skyve-persistence-mechanisms.md)  
  * [Chapter 17: Skyve Persistence Mechanisms](chapters/skyve-persistence-mechanisms.md)
* [Section 4: Platform Tools](chapters/ant-utilities.md)
  * [Chapter 18: Ant Utilities](chapters/ant-utilities.md)
  * [Chapter 19: Content Repository Tools](chapters/content-repository-tools.md)
  * [Chapter 20: Bizport](chapters/bizport.md)
  * [Chapter 21: WILDCAT Conversion Tool](chapters/wildcat-conversion-tool.md)
  * [Chapter 22: Automated Unit Testing](chapters/automated-unit-testing.md)
* [Section 5: Appendix](chapters/appendix.md)
  * [Appendix 1: Deploying a Skyve Application](chapters/appendix.md)
  * [Appendix 2: Installing and configuring the Skyve Development Environment](chapters/appendix.md)
  * [Appendix 3: Example Deployment Instructions with Single Sign-on](chapters/appendix.md)
  * [Appendix 4: Example Deployment Problems caused by problems in the .json file](chapters/appendix.md)
  * [Appendix 5: Installing Skyve in Production](chapters/appendix.md)

# Introduction

## Architectural Overview

Skyve is an open-source low-code Enterprise Platform both for
development and runtime.

Skyve integrates more than 50 other open-source frameworks and libraries
as well as our own original intellectual property (now also open-source)
and we are regularly adding more and updating those included. Skyve
provides a high level abstraction API of all of these to the developer,
giving them the ability to create high quality applications spanning
technologies which they would be unlikely to gain enough expertise in to
use in a robust solution. This means that Skyve enables smaller
development teams to match the output of large teams with specific
expertise groupings.

As a runtime engine, Skyve enforces a declarative security model,
performant persistence interactions, optimises packet sizes for
interactions, thread-safe types and provides a pluggable rendering
architecture, routing control and sophisticated administration and data
maintenance tools.

As a low-code platform, for most applications Skyve requires only small
amounts of very high level Java code, compared to traditional
development platform - for example most applications developers will not
need to create any SQL, HTML or Javascript - but will be able to create
enterprise scale applications which automatically render for most
devices and browsers, include mapping and spatial queries, allow
attachment and uploading of various files and content, provide federated
text searching across both modelled database rows and file attachments.

In many cases, significant proportions of capability can be created
declaratively - with no programming code and Skyve automatically has a
declarative approach to security, menus and navigation,
create-read-update-delete activities, sophisticated n-level
transactional demarcation, automatic database creation and manipulation
along with the usual searching, filtering and reporting capabilities.

Behaviours required for navigation and to maintain, filter and report
data are created automatically by Skyve but can be extended and
customised where necessary. To extend the application, actions
(behaviours) can be written in Java or Groovy, hooking into a predefined
event lifecycle.

Skyve provides a high level programming interface (API), incorporating
thread-safe business types, a simple binding mechanism and persistence
utilities - significantly reducing the amount and complexity of
Developer code and avoiding common security and threading issues.

For example, Skyve has the ability to automatically generate a
consistent and highly usable UI layout to suit the domain model and user
interactions. Even where a more tailored layout is required, this is
done at a high level of abstraction so that the UI can be interpreted
and rendered for phones and tablets and support resizing and zoom for
accessibility.

Uniquely, skyve provides thorough domain validation on a continual basis
for developers - maintaining the code base in a production ready state
and immediately identifying change impact analysis as the developer
works.

A side benefit of this approach is very rapid development - and always
in a production-ready state - secure, robust and scalable from the very
first build.

Skyve applications are developed independent of any specific operating
system, device, browser or database technology. It is quite common for
Skyve development teams to be using a range of different development
environments while working on the same project - as developers may have
their own preferences for their own development environment.

Skyve also provides a revolutionary database independent backup and
restore facility for the combined relational and "non-SQL" data store -
which means support teams can backup from production instances running
on different operating systems and database technologies and restore to
another environment seamlessly.

Skyve applications may be created from legacy applications using the
WILDCAT Conversion Tool (WCT), which combines Extract-Transform-Load
(ETL) with metadata generation and code generation capabilities.

### Technical description

Technically, Skyve is an open-source ***meta-data driven data-centric
business component application platform*** designed for rapid
development of high-quality, secure Web applications.

***“Meta-data driven”*** means that applications are controlled by
high-level specification of requirements (meta-data) rather than by
programming code.

***“Data-centric”*** reflects an approach which recognises that the
nature of the data being maintained implies the functionality required
to maintain it.

***“Business component platforms”*** organise all information relating
to a business concept in a single location – to reduce the risks arising
from changes or enhancements to the business requirements and to ensure
consistency.

Skyve is developed in Java and integrates a range of open-source
frameworks including Hibernate and Jasper reports.

### General Approach and Design Principles

The Skyve Enterprise Platform was created in reaction to problems
experienced with applications built using traditional approaches, and
Skyve is designed specifically to assist developers avoid these
problems.

Skyve is created from the following design principles:

  Principle | Description | In Simple Terms…
  --------- | ----------- | ----------------
  Parsimony | Only the minimum amount of information required to declare a system should be required to build the system. <br>This principle implies the provision of implicit functionality and features - but with the ability for developers to override these without restriction where required. | Developers shouldn’t need to spend effort to create aspects of the system which are implicit.
  Authority | Each element of system declaration should be authoritative.<br>This principle implies that each element of declaration must be in only one location. | Developers should be able to declare each system concept once, without the possibility of contradiction or confusion.
  Independence | The effort required to build a system should be reusable across different technologies and therefore independent from any specific implementation.<br>This principle implies human-readable platform independent formats for application declaration. | Developers should be able to reuse development effort when technology changes or updates.
  Security | Best-practice security must not be able to be compromised by simple error or omission.<br>This principle implies the provision of transparent security, with user permissions assigned declaratively rather programmatically. | Developers should not be able to accidentally compromise system security.
  Scalability | The declaration of a system should not impact the ability to grow the system.<br>This principle implies the transparent provision of best-practice information techniques. | Developers should be able to devise functionality of systems without limiting future capability.
  Maintainability | The declaration of a system must be able to be changed with minimum effort and risk.<br>In addition to the parsimonious implication that changes be made with the minimum information required to declare the change, this principle implies the provision of extensive validation of the system declaration to mitigate the risk of introducing errors. | Developers should be able to make changes to the system with confidence that the change they are making is conceptually correct and will not result in system failure.   
  Exit | By the principle of independence, the declaration of a system must be reusable at the end-of-life either for replacement or incorporation into other systems.<br>In addition to the implications from parsimony and independence, this principle implies that the format of system declaration correlates clearly and obviously to the requirements of the system. | The system declaration must be self-describing so that it can inform (or be reused in) other systems.<br>Data must be accessible via a range of technologies and always exist in a valid state.

Table 1 Skyve design principles

***Unless an application complies with these principles, it represents a
significant risk to the organisation in terms of usability,
maintainability, scalability, integrity, security, cost, lifetime and/or
ability to exit.***

The implications of these principles, as expressed as high level
requirements, are as follows:

  Principle | Implication
  --------- | -----------
  Parsimony | Skyve shall allow developers to define applications using the smallest amount of information possible. <br>The application specification shall be declared in XML rather than programming code. Skyve shall always refers back to this declaration, reducing the possibility of programming errors and inconsistencies. <br>Skyve metadata shall be comprehensive – covering menus, security roles, queries, reports, document attributes, relationships, textual indexes, enumerations, constraints, conditions and views. <br>Skyve shall offer default functionality and behaviours where these can be implied, i.e. intelligent defaults. Where highly-custom application behaviours are required, default behaviours must be able to be overridden without restriction. <br>Skyve shall provide the ability to customise user experience at all definable levels, e.g. by user, by role, by department, by organisation, even where applications exist in a shared multi-tenant environment.
  Authority | Skyve shall conform to (and encourage developers to conform to) the Business Component design principle of having a single-point of reference for all application concepts, and locating all related artefacts together.
  Independence | Skyve applications shall be independent of platform, device, browser and database technologies - so that organisations are not locked into any particular vendor and can move applications with minimal technical risk and without refactoring.
  Security | Skyve applications shall not allow developers to contravene best-practice security by simple error or omission.
  Scalability | Skyve applications shall support scalability, so that implementation decisions by the developer do not become limiting as applications grow.
  Maintainability | Skyve applications shall be easily maintainable via human-readable metadata and where code is required, using a high level API.<br>Generated code shall never be required to be maintained by developers.
  Exit | Skyve shall maintain a viable exit path for data and modelling so that organisations are not confined by the application. Skyve will use (wherever possible) open human-readable standards and formats.

Skyve has extensive validation routines to ensure applications are
comply with these principles throughout the software development life
cycle.

### Use of SQL

According to the Skyve principles, Skyve applications should avoid the
creation of SQL artefacts (triggers, procedures and views) where
possible. This is because SQL is inevitably implementation-specific.
Depending on approaches, SQL is not strongly typed and without carefully
coding is not thread safe and may expose security vulnerabilities.
Additionally, locating part of the business logic in the data-tier
contravenes the business component principle, and potentially increases
maintenance effort and costs.

Skyve provides an object data source which can be used by application
reports, further reducing the need for SQL.In some situations using
implementation-specific SQL is necessary for performance or to integrate
with 3rd party systems and the Skyve API provides an execute method for
insecure SQL, i.e. SQL which is not within the Skyve security
architecture

Remembering that schema object creation is handled automatically by
Skyve via Hibernate, scripts for table creation are not only unnecessary
but introduce the potential for conflict with the automatic schema
update. However, the Skyve administration module provides facilities for
database scheme comparison and will generate DDL scripts for manual
review if this is preferred to automatic database manipulation.

If SQL artefacts are created, it is recommended that developers locate
creation scripts (or a single creation script) for all SQL artefacts
within the Skyve code package, e.g. in a folder called SQL (or similar).
That way, searches for identifiers within the IDE workspace won’t
inadvertently miss references within SQL artefacts, supporting the
common tasks of refactoring, deprecation and change impact analysis.

### Multi-tenant & Mass-Customisation

Skyve supports multi-tenant applications concepts out of the box- when a
Skyve application is created, it is ready to support multiple customers
(tenants) from a single "production" instance, as a distribution
mechanism for a mass-customised approach to software. Skyve
multi-tenanting supports highly-tailored experiences for each
customer/tenant and with distinct data and security controls.

Skyve also provides sophisticated routing control to allow different
rendering options for each customer.

Customer access to application modules is defined via a `customer.xml`
file declaring which application modules the customer has access to.
User and group security is managed within an administration module
included in the platform.

Skyve is designed around the concept of "Minimum Viable Product" (MVP) -
at a basic level, Skyve supports the minimum application specification
possible and assumes intelligent defaults for the rest until specified.

For example, if no view definition has been provided, Skyve will
generate a default view (applying security and data validation rules).
However, these defaults can be overridden by providing a view
specification. From this point on, the specified view overrides the
default view.

Within Skyve, overriding per customer can also be done for any single
piece of the application specification. The custom piece is located in
the Customer specification folder and is used in place of the generic
piece.

This capability is supported by extensive domain model validation and
compilation which confirms the validity of the application specification
even where this has been overridden. Persistence of the overridden model
is facilitated by type coercion to the broadest type required.

Application code is generated once the overridden domain model has been
thoroughly validated. Once the application code has been deployed, user
interfaces are generated on-the-fly using Web 2.0 with piecemeal
downloads for improved performance. Web, Mobile/PDA or exe type clients
can be generated without additional development effort.

### “Open-source” Inclusions

Skyve takes advantage of a number of open-source and LGPL frameworks
which are either distributed with the platform, required to be present
for operation or deployment, or recommended.

These include:

-   Hibernate™ Object Relational Mapping framework -
    <http://www.hibernate.org/>
-   SmartClient Ajax Framework - <http://www.smartclient.com/>
-   Elastic™ content repository - <https://www.elastic.co/>
-   Google maps - <http://www.google.com>
-   Jasper Reports™ report library -
    <http://www.jaspersoft.com/jasperreports>
-   Apache Lucene™ textual indexing engine - <http://lucene.apache.org/>
-   iText and PDFBox generation and content libraries,
-   Apache POI and JXL office interoperability support,and
-   JBoss™ Wildfly Application Server - <http://www.jboss.org/>
-   Eclipse™ Integrated Development Environment -
    <http://www.eclipse.org/>
-   iReport report designer - <http://jasperforge.org/projects/ireport>
-   Eve lightweight JVM for mobile platforms- <http://www.ewesoft.com>

Customised versions of the Skyve platform can be created to integrate
deeply with other 3rd party packages or custom architectural elements.

**[⬆ back to top](#contents)**

---
**Next [Chapter 2: Concepts](chapters/concepts.md)**  
