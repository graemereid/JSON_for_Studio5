# JSON_for_Studio5
This library contains an Object class (oJSON) that is intended as a substitute for the built-in OJSON found in Studio 8.
It arose from the need to parse and generate JSON in a project for a client that it still running in Studio 5.
This is really cool, so if you're going to pinch it, make sure you acknowledge us ok?

## Usage
The oJSON object contains the following methods:
```omnis
oJSON.$jsontolistorrow(psData[,&psErrorText])
```
Parse the JSON array or object in psData and return a row representing the JSON
* IN: psData - JSON to parse, psErrorText - contains the error if parsing fails
* OUT: vrJSON - row representing the JSON array or object, or NULL if parsing fails
```omnis
oJSON.$listorrowtojson(prJSON)
```
Encodes the row representing the JSON array or object as a character string
* IN: prJSON - row representing the JSON array or object
* OUT: vsData - unformatted JSON
```omnis
oJSON.$formatjson(psData)
```
Parses the JSON in psData and returns a formatted representation
* IN: psData - JSON to format
* OUT: vsData - formatted JSON or error message if parsing fails
```omnis
oJSON.$couldbearray(psData)
```
Returns true if psData could be a JSON array because its first character is [
* IN: psData - JSON to parse
* OUT: kTrue if psData could be a JSON array	
```omnis
oJSON.$couldbeobject(psData)
```
Returns true if psData could be a JSON object because its first character is {
* IN: psData - JSON to parse
* OUT: kTrue if psData could be a JSON object

Note that there are a couple of (hopefully minor) differences between this class and the built-in class in Studio 8.
Most of these are for features that we did not need for our project, so feel free to add them if you need them :-)

In the Studio 8 version:
* the $jsontolistorrow method takes an optional third parameter [bAllowArraysOrRows=kFalse]
* the $listorrowtojson method takes an optional second parameter [iEncoding=kUniTypeUTF8] and third parameter [&cErrorText]
* there is an additional method $arrayarraytolist(vData[,&cErrorText])
* there is an additional method $listtoarrayarray(lList[,iEncoding=kUniTypeUTF8,&cErrorText])
* there is an additional method $objectarraytolist(vData[,&cErrorText])
* there is an additional method $listtoobjectarray(lList[,iEncoding=kUniTypeUTF8,&cErrorText])

The parser is somewhat permissive, so it may successfully parse invalid JSON, and it does not handle escaped quotes within string literals.
Also, it treats every literal as a string, rather than attempting to determine the type from the context.

The library also contains a Code class (TestJSON) with sample code to parse, encode, and format JSON.

## Authors
@graemereid, submitted on behalf of Logical Developments

## Contributing
1. Fork this repository
1. Add a branch for your feature
1. Add the feature and perform a new JSON export
1. Submit a pull request
