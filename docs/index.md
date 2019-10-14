# General

## Overview

The schema is based on an object model, with objects generally representing physical or virtual entities.

Objects have a number of attributes (alternatively: properties) that describe the object in more detail.

The proposed schema is hierarchical, i.e. it includes objects embedded (nested) within other objects. However, this is only done where this accurately reflects real-life relationships.

In other cases, relationships between objects are defined by cross-reference links, i.e. links formed via object attributes.

The objects are organised into the following **Groups** according to function:

* Common
* Model
* Report
* Data
* Geometry

Each group is effectively a standalone subschema within the overall schema.
Links between groups are made by reference as required.

The Model and Report groups may be considered to be the core parts of the schema as these are used to assemble models and reports. The Data and Geometry groups provide resources, i.e. the detailed properties/parameters and geometry respectively, that the core group objects can reference. The Common group provides general metadata. This concept is illustrated below.

![image](images/general_outline.png)


## Family of AGS schemas

The intention is for AGSi to become of one a family of similar AGS schemas covering ground investigation, monitoring and ground related construction.

The current AGS format for factual GI data is not compatible with AGSi, but the aspiration is it to be adapted to this style of schema at its next major revision. None of the other proposed schemas exist at present although some, such as a schema for piling data, are in development.

The current proposal is for all members of this family to share 'common' objects where appropriate. Examples include general metadata such as project/investigation data and file/transmittal information. The AGSi schema presented here includes a 'Common' group which is expected to form the basis of the future AGS Common schema.

## Naming conventions (development notes)

**Object names** use PascalCase except that all are preceded by the prefix *ags* or *agsi* in lower case. Example: **agsiObjectName**

The object name prefix *agsi* is used for objects that are unique to the AGSi schema whereas *ags* is used for objects that are expected to be eventually incorporated in the AGS Common schema (as described above).

!!! note case
    OGC GML standards use PascalCase but with a namespace prefix in lower case (separated by a colon), e.g. gsmlb:GeologicUnit. IFC has names starting with 'Ifc', e.g. IfcPile.*

**Attribute names** use camelCase. Example: *attributeName*

!!! note OGC
    OGC GML standards use camelCase. IFC uses PascalCase.

Object and attribute names should be meaningful. Full words should generally be used, except that reasonable truncation or abbreviation may be used to avoid very long names.  Example: *valueProfileIndVarCodeID*

!!! note
    This is common convention. Applied in OGC GML standards and IFC.

Object names shall incorporate the object name of its top level parent, but should not include any further parent names.
Example: [agsiData](/AGSi_Documentation_Data_agsiData#agsiData) (top level parent); [agsiDataParameterValue](/AGSi_Documentation_Data_agsiDataParameterValue#agsiDataParameterValue) (2nd level child)

!!! note
    Including all parent names would lead to very long and cumbersome object names.

Where one object is embedded (nested) within another (as an attribute), the parent object attribute name shall generally be the child object name. Example: [agsiDataParameterSet](/AGSi_Documentation_Data_agsiDataParameterValue#agsiDataParameterSet) has an attribute [agsiDataParameterValue](/AGSi_Documentation_Data_agsiDataParameterValue#agsiDataParameterValue), which will contain [agsiDataParameterValue](/AGSi_Documentation_Data_agsiDataParameterValue#agsiDataParameterValue) objects.

!!! note
    Adopting this convention ensures that the object name will always appear in the data file (for nested Json encoding).

Where an attribute value is intended to be a reference to an identifier defined elsewhere in the schema, the source and target identifiers should be the same, and should end with 'ID'. Example: *codeID* attribute in [agsiDataParameterValue](/AGSi_Documentation_Data_agsiDataParameterValue#agsiDataParameterValue) references *codeID* attribute in [agsiDataCode](/AGSi_Documentation_Data_agsiDataCode#agsiDataCode) object.

An exception to the above is where clarification of the usage of the identifier is desirable, or required to avoid conflict. In such cases clarifying terms may be added to the source attribute name in front of the
target attribute name.

Example: [valueProfileIndVarCodeID](/AGSi_Documentation_Data_agsiDataParameterValue#valueProfileIndVarCodeID) attribute of [agsiDataParameterValue](/AGSi_Documentation_Data_agsiDataParameterValue#agsiDataParameterValue)
references *codeID* attribute of [agsiDataCode](/AGSi_Documentation_Data_agsiDataCode#agsiDataCode) (clarifies and avoids
clash with *CodeID* attribute of [agsiDataParameterValue](/AGSi_Documentation_Data_agsiDataParameterValue#agsiDataParameterValue))

## Attribute type

Attributes may be one of the following basic types:

* string
* number
* integer
* boolean
* null
* array (list)
* object

!!! note
    This simplified list of types is proposed for now, in order to facilitate Json encoding (compliant with Json Schema). It may be possible to expand this list as we develop the schema. Json Schema allows for some validation rules, that may be worth exploring. However, in order to allow other encodings, it is probably best to keep things simple.

!!! note
    'enumerated' type, i.e. code from a defined list, requires further consideration.

!!! note
    date/time format not recognised by Json, but we can specify a string formatted in accordance with ISO8601, i.e. similar to current AGS factual.
