# agsiDataPropertySet


agsiDataPropertySet objects are containers for subsets of property data, with each subset typically corresponding to the property data for a particular agsModelElement or agsFeature object.

The parent object of agsiDataPropertySet is agsiData

agsiDataPropertySet contains the following embedded child objects:

* agsiDataPropertyValue


blockdiag {
  default_shape = roundedbox;
  default_fontsize = 10;
  edge_layout = flowchart;
  agsiDataPropertySet [color = pink];

  agsiData -> agsiDataParameterSet -> agsiDataParameterValue;
  agsiData -> agsiDataPropertySet -> agsiDataPropertyValue;
  agsiData -> agsiDataCase;
  agsiData -> agsiDataCode;
}

agsiDataPropertySet has the following additional attributes:

### propertySetID

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


### agsiDataPropertyValue

See agsiDataPropertyValue

- *Type:* array. agsiDataPropertyValue object(s)
