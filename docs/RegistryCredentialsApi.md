# RegistryCredentialsApi

All URIs are relative to **

Method | HTTP request | Description
------------- | ------------- | -------------
[**generateReadAccessCredentials**](RegistryCredentialsApi.md#generateReadAccessCredentials) | **POST** /registry/credentials/generate-read-access-credentials | Generate Read Access Credentials
[**generateWriteAccessCredentials**](RegistryCredentialsApi.md#generateWriteAccessCredentials) | **POST** /registry/credentials/generate-write-access-credentials | Generate Write Access Credentials



## generateReadAccessCredentials

Generate Read Access Credentials

generate_access_credentials
Given an S3 location, will attempt to generate programmatic access keys
for the storage bucket at this particular subdirectory. 

Note that the permission boundary is restricted by the intersection of 
the preformed role and the created policy based on the location - which is
bounded to the storage bucket.

This produces read level access into the subset of the bucket 
requested in the S3 location object.

TODO currently this does not enforce any ownership of datasets.

Arguments
----------
credentials_request: CredentialsRequest 
    Contains the location + console session URL required flag

Returns
-------
 : CredentialResponse
    The AWS credentials

Raises
------
HTTPException
    500 error code if something goes wrong with STS call or otherwise.

See Also (optional)
--------

Examples (optional)
--------

### Example

```bash
data-api.sh generateReadAccessCredentials
```

### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **credentialsRequest** | [**CredentialsRequest**](CredentialsRequest.md) |  |

### Return type

[**CredentialResponse**](CredentialResponse.md)

### Authorization

[OAuth2PasswordBearer](../README.md#OAuth2PasswordBearer)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)


## generateWriteAccessCredentials

Generate Write Access Credentials

generate_access_credentials
Given an S3 location, will attempt to generate programmatic access keys
for the storage bucket at this particular subdirectory. 

Note that the permission boundary is restricted by the intersection of 
the preformed role and the created policy based on the location - which is
bounded to the storage bucket.

This produces write level access into the subset of the bucket 
requested in the S3 location object.

TODO currently this does not enforce any ownership of datasets.

Arguments
----------
credentials_request: CredentialsRequest 
    Contains the location + console session URL required flag

Returns
-------
 : CredentialResponse
    The AWS credentials

Raises
------
HTTPException
    500 error code if something goes wrong with STS call or otherwise.

See Also (optional)
--------

Examples (optional)
--------

### Example

```bash
data-api.sh generateWriteAccessCredentials
```

### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **credentialsRequest** | [**CredentialsRequest**](CredentialsRequest.md) |  |

### Return type

[**CredentialResponse**](CredentialResponse.md)

### Authorization

[OAuth2PasswordBearer](../README.md#OAuth2PasswordBearer)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

