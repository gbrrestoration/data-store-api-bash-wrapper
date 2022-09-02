# AdministrationApi

All URIs are relative to **

Method | HTTP request | Description
------------- | ------------- | -------------
[**convertFromCollectionFormatToRoCrate**](AdministrationApi.md#convertFromCollectionFormatToRoCrate) | **POST** /admin/registry/convert/collection-format/ro-crate | Convert Collection Format Rocrate
[**convertFromRoCrateToCollectionFormat**](AdministrationApi.md#convertFromRoCrateToCollectionFormat) | **POST** /admin/registry/convert/rocrate/collection-format | Convert Rocrate Collection Format
[**exportParsed**](AdministrationApi.md#exportParsed) | **GET** /admin/registry/export/parsed | Export Registry Parsed
[**exportUnparsed**](AdministrationApi.md#exportUnparsed) | **GET** /admin/registry/export/unparsed | Export Registry Unparsed
[**importParsed**](AdministrationApi.md#importParsed) | **POST** /admin/registry/import/parsed | Import Registry Parsed
[**importUnparsed**](AdministrationApi.md#importUnparsed) | **POST** /admin/registry/import/unparsed | Import Registry Unparsed



## convertFromCollectionFormatToRoCrate

Convert Collection Format Rocrate

convert_collection_format_rocrate
Given a list of collection format inputs will attempt to return a list 
of freshly generated ro-crate objects. Note that the collection format 
alone is not sufficient since it does not include the registry metadata
such as the s3 location, created time etc. For this reason the input 
type also includes some other helper fields likely sourced from the 
registry item.

Arguments
----------
collection_format_input_list : InputConvertCollectionFormatRocrate
    The list of collection formats

Returns
-------
 : ResponseConvertCollectionFormatRocrate
    The list of outputted possible rocrates.

See Also (optional)
--------

Examples (optional)
--------

### Example

```bash
data-api.sh convertFromCollectionFormatToRoCrate
```

### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **inputConvertCollectionFormatRocrate** | [**InputConvertCollectionFormatRocrate**](InputConvertCollectionFormatRocrate.md) |  |

### Return type

[**ResponseConvertCollectionFormatRocrate**](ResponseConvertCollectionFormatRocrate.md)

### Authorization

[OAuth2PasswordBearer](../README.md#OAuth2PasswordBearer)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)


## convertFromRoCrateToCollectionFormat

Convert Rocrate Collection Format

convert_rocrate_collection_format
Given a list of rocrate items will return a list of equal size with items in the
same order. Each item represents a possible successful conversion into a collection
format object. Each item includes an error field True/False for whether the
conversion succeeds, a collection_format if it does and an error_message if it doesn't.

This method is designed to assist database migrations from the admin tools by providing
the means to generate up to date collection format representations against the current
schema. This can be used in conjunction with imports/exports to perform a quick database
update.

Arguments
----------
rocrate_input_list : InputConvertRocrateCollectionFormat
    The list of rocrate inputs

Returns
-------
 : ResponseConvertRocrateCollectionFormat
    The list of possible collection format outputs

See Also (optional)
--------

Examples (optional)
--------

### Example

```bash
data-api.sh convertFromRoCrateToCollectionFormat
```

### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **inputConvertRocrateCollectionFormat** | [**InputConvertRocrateCollectionFormat**](InputConvertRocrateCollectionFormat.md) |  |

### Return type

[**ResponseConvertRocrateCollectionFormat**](ResponseConvertRocrateCollectionFormat.md)

### Authorization

[OAuth2PasswordBearer](../README.md#OAuth2PasswordBearer)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)


## exportParsed

Export Registry Parsed

export_registry_parsed
Returns all the registry items parsed into the current
RegistryItem format.

Returns
-------
 : RegistryParsedExport
    The export object which has a list of entries.

See Also (optional)
--------

Examples (optional)
--------

### Example

```bash
data-api.sh exportParsed
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**RegistryParsedExport**](RegistryParsedExport.md)

### Authorization

[OAuth2PasswordBearer](../README.md#OAuth2PasswordBearer)

### HTTP request headers

- **Content-Type**: Not Applicable
- **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)


## exportUnparsed

Export Registry Unparsed

export_registry_unparsed
Returns all the registry items without first parsing them as
RegistryItems. This method is useful for a situation in which
the items in the registry are no longer valid under the current
RegistryItem model. You can use this method to dump the db,
then modify it offline to be valid, then upload it using the
parsed import endpoint to validate that the new entries are
valid and are updating old entries as desired.

Returns
-------
 : RegistryUnparsedExport
    The list of unparsed objects in Dict[str,Any] format.

See Also (optional)
--------

Examples (optional)
--------

### Example

```bash
data-api.sh exportUnparsed
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**RegistryUnparsedExport**](RegistryUnparsedExport.md)

### Authorization

[OAuth2PasswordBearer](../README.md#OAuth2PasswordBearer)

### HTTP request headers

- **Content-Type**: Not Applicable
- **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)


## importParsed

Import Registry Parsed

import_registry_parsed
Given a list of registry items (parsed as valid before being
accepted at this endpoint) this method will update the current
registry, according to the rules you set in the other options,
to match your import. This method is much safer than the unparsed
method as it only allows valid RegistryItems in. However there
could be situations where you want to preemptively update the
registry before the API is updated to remove down time after
update.
See the options in ImportResponse, these are critical controls.

Arguments
----------
registry_import : RegistryParsedImport
    The registry import object which contains configuration
    options and the list of items.
protected_roles : ProtectedRole, optional
    _description_, by default Depends( admin_user_protected_role_dependency)

Returns
-------
 : ImportResponse
    The response, which includes status info, statistics and
    other items.

Raises
------
HTTPException
    500 error if write failure occurs
HTTPException
    500 error if delete failure occurs

See Also (optional)
--------

Examples (optional)
--------

### Example

```bash
data-api.sh importParsed
```

### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **registryParsedImport** | [**RegistryParsedImport**](RegistryParsedImport.md) |  |

### Return type

[**ImportResponse**](ImportResponse.md)

### Authorization

[OAuth2PasswordBearer](../README.md#OAuth2PasswordBearer)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)


## importUnparsed

Import Registry Unparsed

import_registry_unparsed
Given a list of unparsed - unvalidated -registry items
this method will update the current registry, according to the
rules you set in the other options, to match your import.
This method is much less safe vs the unparsed method as it
allows any valid dynamodb record as RegistryItems. However there
could be situations where you want to pre-emptively update the
registry before the API is updated to remove down time after
update.
See the options in ImportResponse, these are critical controls.

Arguments
----------
registry_import : RegistryParsedImport
    The registry import object which contains configuration
    options and the list of items.
protected_roles : ProtectedRole, optional
    _description_, by default Depends( admin_user_protected_role_dependency)

Returns
-------
 : ImportResponse
    The response, which includes status info, statistics and
    other items.

Raises
------
HTTPException
    500 error if write failure occurs
HTTPException
    500 error if delete failure occurs

See Also (optional)
--------

Examples (optional)
--------

### Example

```bash
data-api.sh importUnparsed
```

### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **registryUnparsedImport** | [**RegistryUnparsedImport**](RegistryUnparsedImport.md) |  |

### Return type

[**ImportResponse**](ImportResponse.md)

### Authorization

[OAuth2PasswordBearer](../README.md#OAuth2PasswordBearer)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

