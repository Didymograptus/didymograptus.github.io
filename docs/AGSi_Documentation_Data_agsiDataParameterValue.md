
# agsiDataParameterValue

Each agsiDataParameterValue objects provides the data for a single defined parameter. The parameter value conveyed may be numeric, a profile of numeric values (e.g. a design line) or text. See overview for definition of parameter.

The parent object of agsiDataParameterValue is [agsiDataPropertySet](/AGSi_Documentation_Data_agsiPrepertySet#agsiDataPropertySet)

agsiDataParameterValue has associations (reference links) with the the following objects:

* [agsiDataCode](/AGSi_Documentation_Data_agsiDataCode#agsiDataCode)
* [agsiDataCase](/AGSi_Documentation_Data_agsiDataCase#agsiDataCase)


blockdiag {
  default_shape = roundedbox;
  default_fontsize = 10;
  edge_layout = flowchart;
  agsiDataParameterValue [color = pink];

  agsiData -> agsiDataParameterSet -> agsiDataParameterValue;
  agsiData -> agsiDataPropertySet -> agsiDataPropertyValue;
  agsiData -> agsiDataCase;
  agsiData -> agsiDataCode;
}

agsiDataParameterValue has the following additional attributes:

### codeID

Code that identifies the parameter. Codes should be defined in either the agsiDataCode object, or in the code dictionary (see agsiData/codeDictionary).

- *Type:* string. Reference to agsiDataCode codeID (or code dictionary)
- *Condition:* Required
- *Example:* ``CU``


### caseID

Code (or text) that identifies the use case for a parameter. For example, different values of the same parameter may be defined corresponding to different design/analysis methods. May also be used to define sets of parameters for sensitivity analysyes. If the input is a code, this should be defined in the agsiDataCase object. May be left blank, but the combination of codeID and caseID should be unique for each agsiDataParameter Value object , i.e. required if codeID is duplicated.

- *Type:* string. Reference to agsiDataCase caseID (or code dictionary), or text
-   *Condition:* Required if codeID duplicated within an agsiDataParameterSet object
-   *Example:* ``EC7PILE``


### valueNumeric

Numeric value of parameter, if applicable.

- *Type:* number
-   *Example:* ``75``

### valueText

Text based value of parameter, if applicable. For a profile (see below), this should be a concise description or represenation of the profile. Unless specified otherwise, this attribute should only be used when the value is not numeric, i.e valueNumeric not used.

- *Type:* string
-   *Example:* ``100 + 6z (z=0 @ +6.0mOD)``


### valueProfileIndVarCodeID

Code that identifies the independent variable for a profile, i.e what the parameter value varies against. Codes should be defined in either the agsiDataCode object, or in the code dictionary (see agsiData/codeDictionary).

- *Type:* string. Reference to agsiDataCode codeID (or code dictionary)
-   *Example:* ``ELEV``


### valueProfileCoordinates

Coordinates that define the profile, as an ordered list of coordinates pair (independent variable value, parameter value).

- *Type:* array. See special guidance on required format.
-   *Example:* ``[[6,100],[-24,280]]``


### remarks

Additional remarks, if required

- *Type:* string
