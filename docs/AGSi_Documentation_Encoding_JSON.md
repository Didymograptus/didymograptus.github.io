# Encoding AGSi in JSON format

!!! todo
    eventually weave JSON Schema into this


## Introduction

JSON (JavaScript Object Notation) is

* a lightweight data-interchange format
* easy for humans to read and write
* easy for machines to parse and generate
* based on a subset of the JavaScript Programming Language
* a text format that is completely language independent
* but it uses conventions that are familiar to programmers of the C-family of languages, including C, C++, C#, Java, JavaScript, Perl, Python, and many others
* very easy to parse in Javascript (for web apps), Python (and probably others)

JSON is now considered by many to be the best format for data transfer
applications.

!!! todo
    ADD REF AND LINK TO STD

## JSON basics

JSON Comprises two basic constructs:

1.   Object = { Name : value } pair

    { “my property” : “its value” }

An object can have several properties:

    { “my property” : “its value” ,    “another property” : “another value” }


2.   Array = [ Ordered list of values ]

This is an array:

    [ “Item 1” , “Item 2” ,  "Item 3” ]

Arrays are one dimensional, but can be nested:

    [ "Main list item 1", [ "Sublist item 1", "Sublist item 2" ], "Main list item 3" ]

A few other JSON rules to note:

{ "Objects use" : "curly brackets" }

[ "Arrays use" : "square brackets" ]

Commas are used to separate object name : value pairs and list items.

JSON recognises the following data types:

* String: must be enclosed in "double quotes"
* Number: quotes not required
* Boolean: *true* or *false*
* null: *null*
* JSON object
* JSON array

Object names must be enclosed in double quotes:

    { "Object name" : "its value" }

JSON data can be written in one line, or spread over many lines, and white space may be added for readability.

Lines breaks and white space (not within object names or value strings) will be ignored in parsing.

Line breaks and a small number of reserved control characters must be escaped when these are required in strings (further details below).

## AGSi as JSON overview

AGSi objects shall be represented as JSON objects, and AGSi arrays as JSON arrays.

The AGSi schema includes nested objects. JSON encoding of AGSi shall also follow a nested approach, i.e. objects within objects where required by the schema.

JSON data types shall be the same as the AGSi schema data types.

## AGSi Objects

AGSi objects shall be encoded as JSON objects with the attribute names and values mapping to JSON object names and values:

    { "attribute1" : "value1" , "attribute2" : "value2" }

For object classes at the root level of the AGSi schema, all objects within the root level object class shall be contained within a JSON object named after the root level class:

    { "RootObjectName" : { "attribute1" : "value1" , "attribute2" : "value2" } }

For AGSi objects that are embedded within other objects (child within parent) the child object becomes the value for the relevant parent object attribute.

The convention adopted in AGSi naming is such that the parent attribute name should be the child object class name:

    :::JSON
    { "ParentObjectName" :
        { "OtherParentAttribute" : "a value" ,
          "ChildObjectName" :
              { "childAttribute1" : "a value" , "childAttribute2" : "a value"}
         }
     }

## AGSi arrays

All AGSi arrays, which may comprise values, objects or other arrays, shall
be encoded as JSON arrays:

    :::JSON
    { "listAttribute" : [ "this" , "is", "a", "list", "of", 7, "values" ] },
    { ChildObjectName" :
        [
              { "childAttributeID" : "1st child object" } ,
              { "childAttributeID" : "2nd child object" } ,
              { "childAttributeID" : "3rd child object" }
         ]
    }

## Other rules

!!! todo
    escape characters

## Examples

!!! todo
    may just be a link - or maybe another page?
