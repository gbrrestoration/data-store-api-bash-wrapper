# MetadataApi

All URIs are relative to **

Method | HTTP request | Description
------------- | ------------- | -------------
[**getDatasetSchema**](MetadataApi.md#getDatasetSchema) | **GET** /metadata/dataset-schema | Get Dataset Schema
[**validateMetadata**](MetadataApi.md#validateMetadata) | **POST** /metadata/validate-metadata | Validate Metadata



## getDatasetSchema

Get Dataset Schema

Function Description
--------------------

Returns the json schema Schema object which defines the required dataset metadata. 
Metdata which is uploaded via the mint-dataset endpoint will be validated against this 
schema before being accepted.


Arguments
----------
protected_roles : ProtectedRole, optional
    by default Depends( kc_auth.get_any_protected_role_dependency([usage_role]))

Returns
-------
Schema
    The json schema object


Raises
------
HTTPException
    Raises a 500 internal error if something goes wrong.

See Also (optional)
--------

Examples (optional)
--------

### Example

```bash
data-api.sh getDatasetSchema
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**Schema**](Schema.md)

### Authorization

[OAuth2PasswordBearer](../README.md#OAuth2PasswordBearer)

### HTTP request headers

- **Content-Type**: Not Applicable
- **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)


## validateMetadata

Validate Metadata

validate_metadata
Allows for validation checks without any interaction with external resources.
Used for testing and potentially as an ongoing validation checker on the front end.

Arguments
----------
metadata : CollectionFormat
    The metadata to validate - this validation occurs both in terms of 
    parsing the collection format object at the API level and also by 
    validating the schema against the json schema file.

Returns
-------
 : Status
    The status object - true/false

Raises
------
HTTPException 422
    If the parsing fails at API level then 422 is returned with the 
    shared interface validation exception type.

See Also (optional)
--------

Examples (optional)
--------

### Example

```bash
data-api.sh validateMetadata
```

### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **collectionFormat** | [**CollectionFormat**](CollectionFormat.md) |  |

### Return type

[**Status**](Status.md)

### Authorization

[OAuth2PasswordBearer](../README.md#OAuth2PasswordBearer)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

