The table below captures all the issues found and the fix provided

Issues Found | Fix Done
------------ | -------------
Headers Parameters of type array caused error during the conversion | Enhanced the assert to allow repeat flag for headers. The default value set to csv which is supported by all arrays in parameters
Empty schema in body parameter. Schema is mandatory as per [Open API spec](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#parameterObject) for body parameters | An schema of type object added in case the schema is empty or undefined
$schema present in items node of parameters/properties of type array | The $schema deleted from items node of parameter, properties of type array.
definitions present inside the schema element which is not supported by Open API Specification | The definitions inside the schema in the Open API Spec has been renamed to x-defintions so that no information is not resolved.
