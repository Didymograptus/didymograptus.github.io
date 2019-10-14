# Guidance on usage - Data

## Properties and parameters

For the purposes of the schema, a distinction between properties and parameters has been made as follows:

**Property**

A value reported from an observation or test (directly measured, or based on interpreted measurement), as typically reported in a factual GI report. Properties are likely to be (Eurocode 7) measured or derived values.

In AGSi, a properties can be reported as simple statistical summaries of values, e.g. minimum, maximum, mean, standard deviation and number of results. Alternatively, or in addition, a text based description can be reported. This is intended to support the reporting of summaries of test results as common seen in ground investigation reports. The properties themselves may comprise only factual data, but the process of providing a summary is considered to be part of interpretation.

Alternatively individual properties can be reported, and these may also be reported against some other (independent) variable. One example would be SPT N values reported against elevation in a particular borehole.

It is not the intention for AGSi to carry complete sets of test data as the main AGS (factual) format already does this. However, there are occasions when it is useful to incorporate selected test data in a model as supporting data.

!!! todo
    May be more examples we can add, of other types of data.

Properties are reported using [agsiDataPropertyValue](/AGSi_Documentation_Data_agsiDataPropertyValue#agsiDataPropertyValue) objects collected together in [agsiDataPropertySet](/AGSi_Documentation_Data_agsiDataPropertySet#agsiDataPropertySet) objects.

**Parameter**

An interpreted single value, or a profile of values related to an independent variable, that is to be used in design and/or analysis. Parameters are most likely to be (Eurocode 7) characteristic values.

Parameters are the values or design lines for properties determined from interpretation of the  relevant data. If best practice is being followed then this should also take into account the intended usage.

Parameters are normally intended to be applied in analysis or design, either by a human (reading the report or interrogating the model) or by a machine (direct import to analysis software or indirect import via a script).

For analysis by machine, it is unlikely that the data provided as AGSi will provide all of the input required. In particular there may be other parameters, correlations factors and options that need to be input separately. AGSi has the potential to positively transform workflows but it certainly does not take away the requirement for careful checking of input.

Parameters are reported using [agsiDataParameterValue](/AGSi_Documentation_Data_agsiDataParameterValue#agsiDataParameterValue) objects collected together in [agsiDataParameterSet](/AGSi_Documentation_Data_agsiDataParameterSet#agsiDataParameterSet) objects.

## Sets of data

Data carried within this part of the schema is collected together in sets of properties and parameters.

Data sets are referenced from other objects of the AGSi schema, including:

* agsiModelElement
* agisFeature
* agsiReportElement

These objects are only able to reference one set of property data and one set of parameter data.
However, it is possible for the same set of data to be referenced by many different objects.

The make up of the sets will therefore be dictated by the nature of the object(s) that need to reference the set.

Examples include:

* Set of parameters for an agsiModelElement object representing   a geological unit (or same from an agsiFeature object)
* As above, but a set of properties (statistical summaries) for that geological unit
* Set of SPT N values, as a profile against elevation, for a single exploratory hole referenced by a agsGeometryExpHole object

Sometimes, in a large model, a single geological unit may have interpreted parameters (or reported properties) that vary according to location, i.e. a single unit divided up into different zones with different sets of parameters/properties for each. In this situation it will be necessary to divide the geological unit up into different agsiModelElement objects for each zone, with each object referenced to different [agsiDataParameterSet](/AGSi_Documentation_Data_agsiDataParameterSet#agsiDataParameterSet) and/or [agsiDataPropertySet](/AGSi_Documentation_Data_agsiDataPropertySet#agsiDataPropertySet) objects as required.

!!! note
    An alternative method of achieving the above is to use different cases (described below) for different zones. However, this is not the intended use of case, and this method is not recommended.*

## Use of Case

[agsiDataParameterValue](/AGSi_Documentation_Data_agsiDataParameterValue#agsiDataParameterValue) and [agsiDataPropertyValue](/AGSi_Documentation_Data_agsiDataPropertyValue#agsiDataPropertyValue) objects have the optional attribute **caseID**. This is code (or text) that identifies the use case for a parameter.

Examples of the use of case include:

* Define different values of the same parameter corresponding   to different intended design/analysis methods.
* Define sets of parameters for sensitivity analyses.
* For properties, provide an alternative statistical summary, e.g. excluding outliers.

If the input is a code, this should be defined in the [agsiDataCase](/AGSi_Documentation_Data_agsiData#agsiDataCase) object.

caseID may be left blank, but the combination of codeID and caseID should be unique for each [agsiDataParameterValue](/AGSi_Documentation_Data_agsiDataParameterValue#agsiDataParameterValue) or [agsiDataPropertyValue](/AGSi_Documentation_Data_agsiDataPropertyValue#agsiDataPropertyValue) object, i.e. required if codeID is duplicated for an object.

For AGSi output intended to be used as input to analysis/design software or scripts, it will be necessary to ensure that the analysis/design software/script knows how to interpret caseID. Protocols for the correct use of caseID will need to be established when the data is created, in particular the approach to the following...

In many cases, there will be sets of data where some parameters vary according to case, *e.g. different Young's Modulus (E) of soil for foundations and retaining walls* and some don't *e.g. bulk unit weight (BUW) of the same soil saem for all cases*.

There are two possible approaches to use of case in this scenario:

* E defined twice with different caseID used for E, but BUW defined once with caseID left blank (or use a 'default' caseID)
* Both E and BUW defined twice with different caseID (the values for both cases of BUW would be the same)

This standard adopts a neutral stance on which is the best approach. It is up to the user(s) to define data requirements for their project taking local needs into account.

!!! note
    We may, after consultation, take a different view on the above.
