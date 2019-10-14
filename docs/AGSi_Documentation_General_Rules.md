# General rules and conventions

!!! note
    This is a working title for this part

## Case sensitivity

!!! note
    DO WE AGREE WITH THIS?
    .. I initially went the other way, then changed my mind!

All text in an AGSi file, however encoded, is deemed to be **case sensitive**. This includes object and attribute names as well as values.

Particular care must be exercised when using and referencing identifiers or Codes.


## Identifiers

!!! todo
    complete section

## Arrays (lists)

Some attributes are of **array** type. An array is a list. The way that an array is expressed in AGSi output will depend on the method of encoding. For the purposes of the examples shown, JSON encoding has been assumed. In this case, an array is expressed using square brackets and commas as follows:

    :::JSON
    ["List item 1" ,  "List item 2" , "List item 3"]

The above example shows a list of strings which require enclosing quotemarks. Lists of numbers do not require quotemarks.

In addition, the above includes White space added for readablity. This would be ignored in processing.

## Coordinates

Input of coordinates uses arrays as follows:

    :::JSON
    [x coordinate , y coordinate, z coordinate]

This is known as a coordinate triple. In some cases only x and y coordinates are required, i.e a coordinate pair.

Coordinates should be numeric so quotemarks are not required for JSON encoding, e.g.

    :::JSON
    [100, 200, 300]

For spatial coordinates, x, y and z correspond to the spatial coordinate grid defined, e.g. x = Easting or project grid X, y = Northing or Y and z = Elevation or Z

In a few cases, x and y may be used differently. This will be defined in the attribute description.

## Profiles or arrays (lists) of coordinates

Some attributes require an array of coordinates to define a line or profile, e.g. design lines, section lines. In such cases the coordinate pairs or triples are themselves the items in a parent list. For example:

    :::JSON
    [[x1,y1], [x2,y2], [x3,y3]]

The line will be formed by joining the points in the order that they are listed.
A polygon is formed when the first and last coordinates are identical. For AGSi it does not matter whether the points are ordered clockwise or anticlockwise. This format is similar to that used for linestrings and polygons in GEOJSON and OGC Simple Features.
