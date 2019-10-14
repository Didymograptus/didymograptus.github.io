# agsiDataPropertyValue


Each agsiDataPropertyValue object provides the data for a single defined property. The property data conveyed may be a simple statistical summary and/or a text based summary. See overview for definition of property.

The parent object of agsiDataPropertyValue is agsiDataPropertySet

agsiDataPropertyValue has associations (reference links) with the the following objects:

* *agsiDataCode*
* *agsiDataCase*


blockdiag {
  default_shape = roundedbox;
  default_fontsize = 10;
  edge_layout = flowchart;
  agsiDataPropertyValue [color = pink];

  agsiData -> agsiDataParameterSet -> agsiDataParameterValue;
  agsiData -> agsiDataPropertySet -> agsiDataPropertyValue;
  agsiData -> agsiDataCase;
  agsiData -> agsiDataCode;
}

agsiDataPropertyValue has the following additional attributes:

### codeID

Code that identifies the property. Codes should be defined in either the agsiDataCode object, or in the code dictionary (see agsiData/codeDictionary).

- *Type:* string. Reference to agsiDataCode codeID (or code dictionary)
- *Condition:* Required
- *Example:* ``CUtrix``

### caseID

Code that identifies the meaning or usage of property. For example, an alternative statistical summary that excludes outliers. If the input is a code, this should be defined in the agsiDataCase object. May be left blank, but the combination of codeID and caseID should be unique for each agsiDataProperty Value object , i.e. required if codeID is duplicated.

- *Type:* string. Reference to agsiDataCase caseID (or code dictionary), or text
- *Condition:* Required if codeID duplicated within an agsiDataPropertySet object
- *Example:* ``EXCLOUTLIER``

### valueMin

Minimum value

- *Type:* number
- *Example:* ``78``

### valueMax

Maximum value

- *Type:* number
- *Example:* ``345``

### valueMean

Mean value

- *Type:* number
- *Example:* ``178.2``

### valueStdDev

Standard deviation

- *Type:* number
- *Example:* ``36.4``

### valueCount

Number of results in data set

- *Type:* number
- *Example:* ``58``

### valueText

Alternative text based summary, if required or prefered. May be needed when limiting values are not numeric (<0.001) or could be used to provide a list of results for very small data sets.

- *Type:* string
- *Example:* ``<0.01 to 12.57, mean 3.21, (16 results)``

### valueProfileIndVarCodeID

Code that identifies the independent variable for a profile, i.e what the property value varies against. Codes should be defined in either the agsiDataCode object, or in the code dictionary (see agsiData/codeDictionary).

- *Type:* string. Reference to agsiDataCode codeID (or code dictionary)
- *Example:* ``ELEV``

### valueProfileCoordinates

Coordinates that define the profile, as an ordered list of coordinates pair (independent variable value, parameter value).

- *Type:* array. See special guidance on required format.
- *Example:* ``[[6,100],[-24,280]]``

### remarks

Additional remarks, if required

- *Type:* string
