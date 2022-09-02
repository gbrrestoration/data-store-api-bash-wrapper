# AccessCheckApi

All URIs are relative to **

Method | HTTP request | Description
------------- | ------------- | -------------
[**checkAdminAccess**](AccessCheckApi.md#checkAdminAccess) | **GET** /check-access/check-admin-access | Check Admin Access
[**checkGeneralAccess**](AccessCheckApi.md#checkGeneralAccess) | **GET** /check-access/check-general-access | Check General Access
[**checkReadAccess**](AccessCheckApi.md#checkReadAccess) | **GET** /check-access/check-read-access | Check Read Access
[**checkWriteAccess**](AccessCheckApi.md#checkWriteAccess) | **GET** /check-access/check-write-access | Check Write Access



## checkAdminAccess

Check Admin Access

Function Description
--------------------

A check point for the data store which responds if any authentication 
is present and valid. Checks the the user is an admin.

Arguments
----------
user : User, optional
    The authenticated user - may or may not have the correct roles. 

Returns
-------
User
    Returns user information



See Also (optional)
--------

Examples (optional)
--------

### Example

```bash
data-api.sh checkAdminAccess
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**User**](User.md)

### Authorization

[OAuth2PasswordBearer](../README.md#OAuth2PasswordBearer)

### HTTP request headers

- **Content-Type**: Not Applicable
- **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)


## checkGeneralAccess

Check General Access

Function Description
--------------------

A check point for the data store which responds if any authentication 
is present and valid. Does not check role authorisation.

Used to distinguish between 'general' and 'protected' access for this API. 


Arguments
----------
user : User, optional
    The authenticated user - may or may not have the correct roles. 

Returns
-------
User
    Returns user information



See Also (optional)
--------

Examples (optional)
--------

### Example

```bash
data-api.sh checkGeneralAccess
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**User**](User.md)

### Authorization

[OAuth2PasswordBearer](../README.md#OAuth2PasswordBearer)

### HTTP request headers

- **Content-Type**: Not Applicable
- **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)


## checkReadAccess

Check Read Access

Function Description
--------------------

A check point for the data store front end to validate authorisation.

Only allows read users (or read and write).


Arguments
----------
protected_roles : ProtectedRole, optional
    The protected role dependency, by default Depends( kc_auth.get_any_protected_role_dependency([usage_role]))

Returns
-------
User
    Returns user information


See Also (optional)
--------

Examples (optional)
--------

### Example

```bash
data-api.sh checkReadAccess
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**User**](User.md)

### Authorization

[OAuth2PasswordBearer](../README.md#OAuth2PasswordBearer)

### HTTP request headers

- **Content-Type**: Not Applicable
- **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)


## checkWriteAccess

Check Write Access

Function Description
--------------------

A check point for the data store front end to validate authorisation.

Only allows read-write users.


Arguments
----------
protected_roles : ProtectedRole, optional
    The protected role dependency, by default Depends( kc_auth.get_any_protected_role_dependency([usage_role]))

Returns
-------
User
    Returns user information



See Also (optional)
--------

Examples (optional)
--------

### Example

```bash
data-api.sh checkWriteAccess
```

### Parameters

This endpoint does not need any parameter.

### Return type

[**User**](User.md)

### Authorization

[OAuth2PasswordBearer](../README.md#OAuth2PasswordBearer)

### HTTP request headers

- **Content-Type**: Not Applicable
- **Accept**: application/json

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

