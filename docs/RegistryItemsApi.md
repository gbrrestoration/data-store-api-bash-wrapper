# RegistryItemsApi

All URIs are relative to **

Method | HTTP request | Description
------------- | ------------- | -------------
[**fetchDataset**](RegistryItemsApi.md#fetchDataset) | **GET** /registry/items/fetch-dataset | Fetch Dataset
[**listAllDatasets**](RegistryItemsApi.md#listAllDatasets) | **GET** /registry/items/list-all-datasets | List All Datasets



## fetchDataset

Fetch Dataset

fetch_dataset
Given a unique Handle ID, this function searches the data registry for 
the data associated with this handle and will return a RegistryFetchResponse 
containing as RegistryItem as an attribute for the queried 
dataset.

Arguments
----------
handle_id : str
    The unique handle ID for searching the data-registry with.

Returns
-------
 : RegistryFetchResponse
    Containing the response status and registry_item.

Raises
------
HTTPException
    If fails to source item from the registry.

See Also (optional)
--------

Examples (optional)
--------

### Example

```bash
data-api.sh fetchDataset  handle_id=value
```

### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **handleId** | **string** |  | [default to null]

### Return type

[**RegistryFetchResponse**](RegistryFetchResponse.md)

### Authorization

[OAuth2PasswordBearer](../README.md#OAuth2PasswordBearer)

### HTTP request headers

- **Content-Type**: Not Applicable
- **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)


## listAllDatasets

List All Datasets

list_all_datasets
Lists all data in the data registry. Returns a ListRegistryResponse with a registry_items attribute 
which is a python list of RegistryItem objects, one object per entry to the registry.

Returns
-------
 : ListRegistryResponse
    An object containing the responses status and a registry_items python list containing a RegistryItem for 
    each item in the the database.

See Also (optional)
--------

Examples (optional)
--------

### Example

```bash
data-api.sh listAllDatasets
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**ListRegistryResponse**](ListRegistryResponse.md)

### Authorization

[OAuth2PasswordBearer](../README.md#OAuth2PasswordBearer)

### HTTP request headers

- **Content-Type**: Not Applicable
- **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

