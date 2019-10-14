# agsiDataCode

agsiDataCode is a dictionary for the property and parameter codes referenced by other objects. It also includes the units applicable for each property/parameter.

Use of codes from a standard list is recommended. Replication of the standard codes in agsiDataCode is optional provided that the standard dictionary used is identified in agsiData (codeDictionary). If standard codes are replicated here, only those used in the data set should be included. Any user defined (non standard) codes must be included, with isNonStandard flagged as TRUE.

The parent object of agsiDataCode is agsiData

agsiDataCode has associations (reference links) with the the following objects:

* agsiDataPropertyValue
* agsiDataParameterValue

blockdiag {
  default_shape = roundedbox;
  default_fontsize = 10;
  edge_layout = flowchart;
  agsiDataCode [color = pink];

  agsiData -> agsiDataParameterSet -> agsiDataParameterValue;
  agsiData -> agsiDataPropertySet -> agsiDataPropertyValue;
  agsiData -> agsiDataCase;
  agsiData -> agsiDataCode;
  agsiDataCode -- agsiDataParameterValue [style = dashed];
  agsiDataCode -- agsiDataPropertyValue [style = dashed];
}

agsiDataCode has the following additional attributes:

### codeID

Identifying code for a property or parameter. Use of codes from standard dictionary, such as the AGSi code list, is recommended. Referenced by agsiDataParameterValue and/or agsiData PropertyValue

- *Type:* string. Identifier
- *Condition:* Required
- *Example:* ``CU``


### description

Short description of what the code represents.

- *Type:* string. Text
- *Condition:* Required
- *Example:* ``Undrained shear strength``

### units

Units of measurement for this property or parameter, if applicable.

- *Type:* string. Text (standard units term)
- *Condition:* Recommended
- *Example:* ``kPa``

### isNonStandard

TRUE if code is not from standard library, i.e user defined.

- *Type:* boolean
- *Example:* ``False``

### remarks

Additional remarks, if required

- *Type:* string. Text
- *Example:* ``Some remarks if required``
