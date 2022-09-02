# RegisterDatasetApi

All URIs are relative to **

Method | HTTP request | Description
------------- | ------------- | -------------
[**mintDataset**](RegisterDatasetApi.md#mintDataset) | **POST** /register/mint-dataset | Mint Dataset
[**updateMetadata**](RegisterDatasetApi.md#updateMetadata) | **POST** /register/update-metadata | Get Dataset Schema



## mintDataset

Mint Dataset

Function Description
--------------------

Used by the front end to prepare the data store, the handle service, metadata
etc for a new dataset. Accepts the filled out metadata which must validate 
against the current dataset schema which is provided by the /dataset-schema endpoint.

If the schema validates, then a handle will be minted, a handle endpoint will be formed 
and updated for the handle service, a S3 location will be determined, the metadata updated
with these details and uploaded to that location to seed the folder structure. 

This function returns the MintResponse which includes the status, the handle, the S3 location
information.


Arguments
----------
collection_format : CollectionFormat
    The input pre-parsed using the pydantic input model validation.
    Still is validated using the json schema as well.

Returns
-------
MintResponse
    The mint response object which encodes the result if successful


Raises
------
HTTPException
    400 response if metadata fails to validate
HTTPException
    400 response if the S3 location cannot be uniquely determined

See Also (optional)
--------

Examples (optional)
--------

### Example

```bash
data-api.sh mintDataset
```

### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **collectionFormat** | [**CollectionFormat**](CollectionFormat.md) |  |

### Return type

[**MintResponse**](MintResponse.md)

### Authorization

[OAuth2PasswordBearer](../README.md#OAuth2PasswordBearer)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)


## updateMetadata

Get Dataset Schema

get_dataset_schema
Given the metadata and handle id, will re-parse the metadata
as valid ro crate, then overwrite the registry entry and 
s3 bucket metadata.

Will also update the timestamp of the updated_time to be 
the current time.

Arguments
----------
collection_format : CollectionFormat
    The updated metadata
handle_id : str
    The handle for which to update the metadata

Returns
-------
 : UpdateMetadataResponse
    The updated metadata response

Raises
------
HTTPException
    422 - validation failure against schema at API level
HTTPException
    400 - validation failure against schema at JSON schema level
HTTPException
    400 - failed to transform into ro crate
HTTPException
    500 - failed to update registry 

See Also (optional)
--------

Examples (optional)
--------

### Example

```bash
data-api.sh updateMetadata  handle_id=value
```

### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **handleId** | **string** |  | [default to null]
 **collectionFormat** | [**CollectionFormat**](CollectionFormat.md) |  |

### Return type

[**UpdateMetadataResponse**](UpdateMetadataResponse.md)

### Authorization

[OAuth2PasswordBearer](../README.md#OAuth2PasswordBearer)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

