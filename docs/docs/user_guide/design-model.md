#Design Model User Guide

Design Models help to model a software architecture with Patterns.
The existing Patterns in the Pattern Atlas can be used in a Design Model.
Additionally implementations for Patterns, so called Concrete Solutions, can be defined.
Finally these Concrete Solutions of a Design Model can be automatically aggregated to a source code skeleton, expressing the modelled software architecture.

##Introduction

This section provides a brief introduction to users of Pattern Atlas.
It will describe how to manage Design Models, the modelling with Patterns, the selection of a Concrete Solution and the aggregation to a source code skeleton.


##Management


Create a new Design Model or select an existing Design Model to open it in the editor.

![alt_text](../images/numbers/1.png "1:") Choose Design Models in the menu.

![alt_text](../images/numbers/2.png "2:") Add a new Design Model or

![alt_text](../images/numbers/3.png "3:") Select an existing one.

![alt_text](/images/design-model/design-model-management.png){: style="height: 450px; margin-bottom:10px"}
   


##Modelling
Model a software architecture with Patterns.

![alt_text](../images/numbers/1.png "1:") Open a Pattern Language and add a Pattern with drag and drop to the modelling canvas.

![alt_text](../images/numbers/2.png "2:") Patterns can be moved around and have four dots in the middle of each border, to add relationships to other Patterns.

![alt_text](../images/numbers/3.png "3:") Show possible Concrete Solutions for each Pattern in the Design Model.

![alt_text](/images/design-model/design-model-patterns.png){: style="height: 300px; margin-bottom:10px"}


##Concrete Solutions

![alt_text](../images/numbers/1.png "1:") A software architecture modelled with Patterns and their relationship.

![alt_text](../images/numbers/2.png "2:") Possible Concrete Solutions for the Patterns, the preferred one can be selected individually for each Pattern with a simple click.

![alt_text](../images/numbers/3.png "3:") Globally select the preferred Concrete Solutions, e.g. with ``cs.name.indexOf('sync') !== -1`` to exclude the synchronous JMS implementations.

![alt_text](../images/numbers/4.png "4:") Aggregate the selected Concrete Solutions. Pattern Atlas will serve a download with the source code result.

Select Concrete Solutions for a Design Model and aggregate them to a software skeleton representing the software architecture. 


![alt_text](/images/design-model/design-model-concrete-solutions.png){: style=" margin-bottom:10px"}



