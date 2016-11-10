The table below captures all the issues found and the fix provided

Issues Found | Fix Done
------------ | -------------
Headers Parameters of type array caused error during the conversion | Enhanced the assert to allow repeat flag for headers. The default value set to csv which is supported by all arrays in parameters
Empty schema in body parameter. Schema is mandatory as per [Open API spec](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#parameterObject) for body parameters | An schema of type object added in case the schema is empty or undefined
$schema present in items node of parameters/properties of type array | The $schema deleted from items node of parameter, properties of type array.
definitions present inside the schema element which is not supported by Open API Specification | The definitions inside the schema in the Open API Spec has been renamed to x-defintions so that no information is not resolved.
inner definitions at schema level can't be referenced internally within Open API specification| The inner definitions has been copied into the root of the defintions of the Open API Specifications.
'oneOf' property is not supported by Swagger 2.0 | Resolve 'oneOf' to object in resulting Swagger spec.
Conversion will fail if there's an empty array provided for "required" | Will remove required attribute when empty array is provided.
Schema within definitions that are declared with $schema will break conversion | Will delete inner schema from definitions and reference to it instead.
Internal links that already have a http scheme (are a URI) would still have a '#/definitions/' put in front. | Fix will leave the link as is and not add the '#/definitions/' in front.
References that already are defined with '#/definitions/' will still get a '#/definitions/' put in front. | Just don't add '#/definitions/' to it again.
'additionalProperties' are not supported by Swagger 2.0 and therefor break conversion. | Resolve 'additionalProperties' to object.
Header with "collectionFormat: 'multi'" are not supported | Change the 'multi' to 'csv' so it accepts comma separated lists.
Schemas that don't have a title will override other schemas without a title | Introduce a sequence number to anonymously name them and make them reference-able. User should be able to spot and change definitions after this change now.
