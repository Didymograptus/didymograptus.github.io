
# agsiDataCase

agsiDataCase is a dictionary of the case IDs referenced by other objects, if applicable. Case IDs can be used to where the valid usage of a parameter needs to be defined, e.g. for a specific type of analysis. Case IDs may also be used to faciliate alternative reporting of properties, e.g. a statistical summary that ignores outliers.

The parent object of agsiDataCase is agsiData

agsiDataCase has associations (reference links) with the the following objects:

* agsiDataPropertyValue
* agsiDataParameterValue

blockdiag {
  default_shape = roundedbox;
  default_fontsize = 10;
  edge_layout = flowchart;
  agsiDataCase [color = pink];

  agsiData -> agsiDataParameterSet -> agsiDataParameterValue;
  agsiData -> agsiDataPropertySet -> agsiDataPropertyValue;
  agsiData -> agsiDataCase;
  agsiData -> agsiDataCode;
  agsiDataCase -- agsiDataParameterValue [style = dashed];
  agsiDataCase -- agsiDataPropertyValue [style = dashed];

}

agsiDataCase has the following additional attributes:

### caseID

Identifying code for a defined case. Referenced by agsiDataParameterValue and/or agsiData PropertyValue

- *Type:* string. Identifier
- *Condition:* Required
- *Example:* ``EC7PILE``

### description

Short description of the case, e.g. use case for a parameter.

- *Type:* string. Text
- *Condition:* Required
- *Example:* ``EC7 Pile design``

### remarks

Additional remarks, if required

- *Type:* string. Text
- *Example:* ``See alternate cases for LDSA pile design and retaining wall design.``
