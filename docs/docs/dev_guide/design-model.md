#Design Model Developer Guide


The following section will give a technical introduction into the current state of the Design Model part of Pattern Atlas.


##Architectural overview


For the Design Models the following four components of Pattern Atlas are relevant. The components are linked to their corresponding repository.

![alt_text](/images/design-model/pattern-atlas-architecture-overview.svg){: style=" margin-bottom:10px"}


**Pattern Atlas UI**
The user interface, containing the editor for the Design Models.

**Pattern Atlas API**
Handles the logic for persistence and aggregation of Design Models.

**Relational Database**
Store all data for a Design Model and the metadata for a Concrete Solution, the Concrete Solution Descriptor.

**Git-Repository**
Keeps track of the implementation of a Pattern, the Concrete Solution Artifact.


##Concrete Solutions


Concrete Solutions (CS) are made of two parts.
The Concrete Solutions Descriptor (CSD) contains metadata, like the name of the CS, the relation to the Pattern and similar information.
The other part, the Concrete Solution Artifact (CSA) is the implementation of a Pattern.

**CSD**
Is stored in the database containing the relevant metadata for a CS.
The linked file contains some [examples of a CSD](https://github.com/PatternAtlas/pattern-atlas-content/blob/0f77c1f4788f37edc76fbd709cc298c41775bc28/db-backup-files/2-patternatlas-data-inserts.sql#L37).

**CSA**
Is a implementation, this could be in form of a source code fragment.
The currently implemented aggregators allow the usage of [StringTemplate](https://www.stringtemplate.org/) for conditions, loops and similar things.
This supports for example a [Recipient List](https://github.com/PatternAtlas/pattern-atlas-pattern-implementations/blob/13aec80f745a51f88b776adc1a5d0dd6811d9e69/eip-activemq-xml/recipient-list.st), with an arbitrary number of Patterns consuming it.
While currently all CSAs are stored in one [Git repository](https://github.com/PatternAtlas/pattern-atlas-pattern-implementations).
This Git repository is used as it allows keeping track on changes and provides a workflow, software developers are used to.
CSAs could be stored on other places as well.
The only condition for automated aggregation, is that the CSA is referencable by a URL, which means even local or protected files could be used, if the aggregator can access it.


##Create a new concrete solution


- Create CSA: Write the source code for a new CS.

    - Use plain text or
    - make use of the template features [cheat sheet](https://github.com/antlr/stringtemplate4/blob/master/doc/cheatsheet.md).
    - CSAs which could be used as example can be found in this [Git repository](https://github.com/PatternAtlas/pattern-atlas-pattern-implementations).

- Create CSD: Add a row to the database table ``concrete_solution``.

    - Fill all fields, like name, implemented pattern, aggregation type, ...
    - Examples exist in the database table or as [SQL query](https://github.com/PatternAtlas/pattern-atlas-content/blob/0f77c1f4788f37edc76fbd709cc298c41775bc28/db-backup-files/2-patternatlas-data-inserts.sql#L37).


##Aggregator


An aggregator combines CSs to an integrated artifact.
An artifact could be a source code or configuration fragment or another kind of file.
The aggregator used for an aggregation is selected by the aggregation types of two CSs.
Lets assume, we have two XML configuration snippets as CSs and both aggregation types are ``ActiveMQ-XML``.
Then the [ConcreteSolutionService](https://github.com/PatternAtlas/pattern-atlas-api/blob/8b81dc3a14cd267229953c67a42185508268d504/src/main/java/com/patternpedia/api/service/ConcreteSolutionServiceImpl.java#L139) will search for a match aggregator.
In this case, it would match the [ActiveMQXMLAggregator](https://github.com/PatternAtlas/pattern-atlas-api/blob/d4f478fc197b0e1fb77912a1b01e5284af38801c/src/main/java/com/patternpedia/api/util/aggregator/ActiveMQXMLAggregator.java#L13), which will perform the aggregation.


##Create a new aggregator


- Create a Java class (for example in ``src/main/java/com/patternpedia/api/util/aggregator/``)
- Implement the Aggregator interface or extend the abstract AggregatorImpl class, which already provide some methods to simplify reading files or for template rendering.
- Add the ``@AggregatorMetadata(sourceTypes = {}, targetTypes = {})`` annotation and fill the source and target type arrays with the aggregation types the new aggregator can aggregate.

    - When searching for a matching aggregator, it will be checked, if the aggregation type of the first CS is in the source type array and the aggregation type of the second CS is in the target type array.

- Implement the aggregation logic.