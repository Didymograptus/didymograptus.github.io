# agsiData

The agsiData object is a wrapper for all of the data for a root dataset. It is required in all cases where data is provided. There should be only one agsiData object per root dataset. All other objects in the Data part of the schema are embedded within agsiData.

The parent object of agsiData is *root*

[agsiData](/AGSi_Documentation_Data_agsiData#agsiData) contains the following embedded child objects:

* [agsiDataParameterSet](/AGSi_Documentation_Data_agsiDataParameterSet)
* [agsiDataPropertySet](/AGSi_Documentation_Data_agsiDataPropertySet)
* [agsiDataCase](/AGSi_Documentation_Data_agsiDataCase)
* [agsiDataCode](/AGSi_Documentation_Data_agsiDataCode)

blockdiag {
  default_shape = roundedbox;
  default_fontsize = 10;
  edge_layout = flowchart;
  agsiData [color = pink];

  agsiData -> agsiDataParameterSet -> agsiDataParameterValue;
  agsiData -> agsiDataPropertySet -> agsiDataPropertyValue;
  agsiData -> agsiDataCase;
  agsiData -> agsiDataCode;
}

[agsiData](/AGSi_Documentation_Data_agsiData#agsiData) has the following additional attributes:



### dataSetID

Identifier, possibly a UUID. This is optional and is not referenced anywhere else in the schema, but there may be cases where it is may be beneficial to include this to help with data control and integrity.

- *Type:* string. Identifier
- *Example:* ``40b785d0-547c-41c5-9b36-3cd31126ecb0``

### description

Similar usage to dataSetID but intended to be a more verbose description.

- *Type:* string. Text
- *Example:* ``My Project Name GIR interpreted data``

### codeDictionary

URI link to the dictionary/vocabulary used for the code list. This should by default be the AGSi standard code list, but it can be changed to an alternate list, e.g. lists published by other agencies (UK or overseas) or major projects/clients. If this is populated, then use of agsiDataCode is optional.

- *Type:* string. URI
- *Condition:* Recommended
- *Example:* ``https://gitlab.com/AGS-DFWG-Web/ASGi/agsCodeList.htm``

### agsiDataParameterSet

See [agsiDataParameterSet](/AGSi_Documentation_Data_agsiDataParameterSet)

- *Type:* array. agsiDataPropertySet object(s)

### agsiDataPropertySet

See [agsiDataPropertySet](/AGSi_Documentation_Data_agsiDataPropertySet)

- *Type:* None. agsiDataParameterSet object(s)

### agsiDataCase

See [agsiDataCase](/AGSi_Documentation_Data_agsiDataCase)

- *Type:* array. agsiDataCase object(s)

### agsiDataCode

See [agsiDataCode](/AGSi_Documentation_Data_agsiDataCode)

- *Type:* array. agsiDataCode object(s)
- *Condition:* Required if codeDictionary is null
