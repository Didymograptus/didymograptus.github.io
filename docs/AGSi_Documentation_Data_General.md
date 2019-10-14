
# Data (properties and parameters)


## Overview

The 'Data' part of the schema is intended to be the repository for
property and parameter data associated with model features or elements.

The data contained here will be linked to the relevant agsiFeatures,
agsiModelElements or agsiReportElements by reference.

!!! note
    This structure has been adopted because real life data can be extensive and may require complex data structures to express it correctly and efficiently. Simply incorporating the data as attributes to the feature or element objects is not feasible. In addition, this structure allows the same data to be referenced from both the Model and Report parts of the schema.

For the purposes of the schema, a distinction between properties and
parameters has been made as follows:

### Property

A value reported from an observation or test (directly measured, or based on interpreted measurement), as typically reported in a factual GI report. Properties are likely to be (Eurocode 7) measured or derived values.

### Parameter

An interpreted single value, or a profile of values related to an independent variable, that is to be used in design and/or analysis. Parameters are most likely to be (Eurocode 7) characteristic values.

!!! note
    AGSi supports the reporting of summaries of the property data including basic statistical data. There is also limited support for reporting of individual test results where this is required for the model.

   However, it is not the intent of AGSi to include full factual data as this is covered by the AGS (factual) format

!!! note
    Properties and parameters are dealt with separately for the following reasons:

    * The use cases are different. AGSi parameters data is expected to be used directly by analysis software, whereas the summary property data is only likely to be used for reporting. The property and parameter objects require different attributes.

### Summary of schema

agsiData is a container for all of the other objects described below.

The values of individual parameters are included as agsiDataParameterValue objects. These parameter values are then collected into sets of parameters in agsiDataParameterSet objects. To achieve this, agsDataParameterValue objects are embedded within agsiDataParameterSet, i.e. this is a heirarchical parent-child relationship. Each agsiDataParameterSet object will likely have many agsiDataParameterValue objects embedded within it.

agiDataPropertyValue and agsiDataPropertySet operate in identical manner to agsiDataParameterValue and agsiDataParameterSet but are used for properties instead of parameters.

Other parts of the AGSi schema link to data via agsiDataParameterSet and agsiDataPropertySet, i.e. model elements, features or report elements link to sets of data that are applicable to that element or feature. Refer to the guidance on usage for examples.

The properties and parameters are referenced using codes. The codes are
defined using agsiDataCode objects linked from agsDataParameterValue or agiDataPropertyValue.

Properties and parameters can also be assigned to a 'case' using the relevant attributes in agsDataParameterValue or agiDataPropertyValue Codes may be assigned for cases which can be defined using agsiDataCase objects.

For more guidance on how to use this part of the schema, see

!!! todo
    add link

Diagrams illustrating this part of the schema are shown below (links to
other parts of the schema not included here).

!!! todo
    Need to sort out images
