# agsiDataParameterSet

agsiDataParameterSet objects are containers for subsets of parameter data, with each subset typically corresponding to the property data for a particular agsModelElement or agsFeature object.

The parent object of agsiDataParameterSet is [agsiData](/AGSi_Documentation_Data_agsiData#agsiData)

agsiDataParameterSet contains the following embedded child objects:

* [agsiDataParameterValue](/AGSi_Documentation_Data_agsiDataParameterValue#agsiDataParameterValue)


blockdiag {
  default_shape = roundedbox;
  default_fontsize = 10;
  edge_layout = flowchart;
  agsiDataParameterSet [color = pink];

  agsiData -> agsiDataParameterSet -> agsiDataParameterValue;
  agsiData -> agsiDataPropertySet -> agsiDataPropertyValue;
  agsiData -> agsiDataCase;
  agsiData -> agsiDataCode;
}

agsiDataParameterSet has the following additional attributes:

### parameterSetID

Identifier for this set of data. This will be referenced by other objects such as agsModelElement and agsFeature as required. Use of a simple code is recommended, such as the geology code if no further subdivision of the data is required.

- *Type:* string. Identifier
- *Condition:* Required
- *Example:* ``LC``


### description

Short description identifying the data set.

- *Type:* string. Text
- *Example:* ``London Clay``


### remarks

Additional remarks, if required

- *Type:* string. Text
- *Example:* ``Some remarks if required``


### agsiDataParameterValue

See [agsiDataParameterValue](/AGSi_Documentation_Data_agsiDataParameterValue#agsiDataParameterValue)

- *Type:* array. agsiDataParameterValue object(s)
