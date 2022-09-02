# FastAPI Bash client

## Overview

This is a Bash client script for accessing FastAPI service.

The script uses cURL underneath for making all REST calls.

## Usage

```shell
# Make sure the script has executable rights
$ chmod u+x data-api.sh

# Print the list of operations available on the service
$ ./data-api.sh -h

# Print the service description
$ ./data-api.sh --about

# Print detailed information about specific operation
$ ./data-api.sh <operationId> -h

# Make GET request
./data-api.sh --host http://<hostname>:<port> --accept xml <operationId> <queryParam1>=<value1> <header_key1>:<header_value2>

# Make GET request using arbitrary curl options (must be passed before <operationId>) to an SSL service using username:password
data-api.sh -k -sS --tlsv1.2 --host https://<hostname> -u <user>:<password> --accept xml <operationId> <queryParam1>=<value1> <header_key1>:<header_value2>

# Make POST request
$ echo '<body_content>' | data-api.sh --host <hostname> --content-type json <operationId> -

# Make POST request with simple JSON content, e.g.:
# {
#   "key1": "value1",
#   "key2": "value2",
#   "key3": 23
# }
$ echo '<body_content>' | data-api.sh --host <hostname> --content-type json <operationId> key1==value1 key2=value2 key3:=23 -

# Make POST request with form data
$ data-api.sh --host <hostname> <operationId> key1:=value1 key2:=value2 key3:=23

# Preview the cURL command without actually executing it
$ data-api.sh --host http://<hostname>:<port> --dry-run <operationid>

```

## Docker image

You can easily create a Docker image containing a preconfigured environment
for using the REST Bash client including working autocompletion and short
welcome message with basic instructions, using the generated Dockerfile:

```shell
docker build -t my-rest-client .
docker run -it my-rest-client
```

By default you will be logged into a Zsh environment which has much more
advanced auto completion, but you can switch to Bash, where basic autocompletion
is also available.

## Shell completion

### Bash

The generated bash-completion script can be either directly loaded to the current Bash session using:

```shell
source data-api.sh.bash-completion
```

Alternatively, the script can be copied to the `/etc/bash-completion.d` (or on OSX with Homebrew to `/usr/local/etc/bash-completion.d`):

```shell
sudo cp data-api.sh.bash-completion /etc/bash-completion.d/data-api.sh
```

#### OS X

On OSX you might need to install bash-completion using Homebrew:

```shell
brew install bash-completion
```

and add the following to the `~/.bashrc`:

```shell
if [ -f $(brew --prefix)/etc/bash_completion ]; then
  . $(brew --prefix)/etc/bash_completion
fi
```

### Zsh

In Zsh, the generated `_data-api.sh` Zsh completion file must be copied to one of the folders under `$FPATH` variable.

## Documentation for API Endpoints

All URIs are relative to **

Class | Method | HTTP request | Description
------------ | ------------- | ------------- | -------------
*AccessCheckApi* | [**checkAdminAccess**](docs/AccessCheckApi.md#checkadminaccess) | **GET** /check-access/check-admin-access | Check Admin Access
*AccessCheckApi* | [**checkGeneralAccess**](docs/AccessCheckApi.md#checkgeneralaccess) | **GET** /check-access/check-general-access | Check General Access
*AccessCheckApi* | [**checkReadAccess**](docs/AccessCheckApi.md#checkreadaccess) | **GET** /check-access/check-read-access | Check Read Access
*AccessCheckApi* | [**checkWriteAccess**](docs/AccessCheckApi.md#checkwriteaccess) | **GET** /check-access/check-write-access | Check Write Access
*AdministrationApi* | [**convertFromCollectionFormatToRoCrate**](docs/AdministrationApi.md#convertfromcollectionformattorocrate) | **POST** /admin/registry/convert/collection-format/ro-crate | Convert Collection Format Rocrate
*AdministrationApi* | [**convertFromRoCrateToCollectionFormat**](docs/AdministrationApi.md#convertfromrocratetocollectionformat) | **POST** /admin/registry/convert/rocrate/collection-format | Convert Rocrate Collection Format
*AdministrationApi* | [**exportParsed**](docs/AdministrationApi.md#exportparsed) | **GET** /admin/registry/export/parsed | Export Registry Parsed
*AdministrationApi* | [**exportUnparsed**](docs/AdministrationApi.md#exportunparsed) | **GET** /admin/registry/export/unparsed | Export Registry Unparsed
*AdministrationApi* | [**importParsed**](docs/AdministrationApi.md#importparsed) | **POST** /admin/registry/import/parsed | Import Registry Parsed
*AdministrationApi* | [**importUnparsed**](docs/AdministrationApi.md#importunparsed) | **POST** /admin/registry/import/unparsed | Import Registry Unparsed
*DefaultApi* | [**root**](docs/DefaultApi.md#root) | **GET** / | Root
*MetadataApi* | [**getDatasetSchema**](docs/MetadataApi.md#getdatasetschema) | **GET** /metadata/dataset-schema | Get Dataset Schema
*MetadataApi* | [**validateMetadata**](docs/MetadataApi.md#validatemetadata) | **POST** /metadata/validate-metadata | Validate Metadata
*RegisterDatasetApi* | [**mintDataset**](docs/RegisterDatasetApi.md#mintdataset) | **POST** /register/mint-dataset | Mint Dataset
*RegisterDatasetApi* | [**updateMetadata**](docs/RegisterDatasetApi.md#updatemetadata) | **POST** /register/update-metadata | Get Dataset Schema
*RegistryCredentialsApi* | [**generateReadAccessCredentials**](docs/RegistryCredentialsApi.md#generatereadaccesscredentials) | **POST** /registry/credentials/generate-read-access-credentials | Generate Read Access Credentials
*RegistryCredentialsApi* | [**generateWriteAccessCredentials**](docs/RegistryCredentialsApi.md#generatewriteaccesscredentials) | **POST** /registry/credentials/generate-write-access-credentials | Generate Write Access Credentials
*RegistryItemsApi* | [**fetchDataset**](docs/RegistryItemsApi.md#fetchdataset) | **GET** /registry/items/fetch-dataset | Fetch Dataset
*RegistryItemsApi* | [**listAllDatasets**](docs/RegistryItemsApi.md#listalldatasets) | **GET** /registry/items/list-all-datasets | List All Datasets


## Documentation For Models

 - [CollectionFormat](docs/CollectionFormat.md)
 - [CollectionFormatAuthor](docs/CollectionFormatAuthor.md)
 - [CollectionFormatConversion](docs/CollectionFormatConversion.md)
 - [CollectionFormatDatasetInfo](docs/CollectionFormatDatasetInfo.md)
 - [CollectionFormatOrganisation](docs/CollectionFormatOrganisation.md)
 - [CredentialResponse](docs/CredentialResponse.md)
 - [Credentials](docs/Credentials.md)
 - [CredentialsRequest](docs/CredentialsRequest.md)
 - [HTTPValidationError](docs/HTTPValidationError.md)
 - [ImportResponse](docs/ImportResponse.md)
 - [ImportStatistics](docs/ImportStatistics.md)
 - [InputConvertCollectionFormatRocrate](docs/InputConvertCollectionFormatRocrate.md)
 - [InputConvertRocrateCollectionFormat](docs/InputConvertRocrateCollectionFormat.md)
 - [ListRegistryResponse](docs/ListRegistryResponse.md)
 - [LocationInner](docs/LocationInner.md)
 - [MintResponse](docs/MintResponse.md)
 - [PossibleCollectionFormat](docs/PossibleCollectionFormat.md)
 - [PossibleRocrate](docs/PossibleRocrate.md)
 - [RegistryFetchResponse](docs/RegistryFetchResponse.md)
 - [RegistryItem](docs/RegistryItem.md)
 - [RegistryParsedExport](docs/RegistryParsedExport.md)
 - [RegistryParsedImport](docs/RegistryParsedImport.md)
 - [RegistryUnparsedExport](docs/RegistryUnparsedExport.md)
 - [RegistryUnparsedImport](docs/RegistryUnparsedImport.md)
 - [ResponseConvertCollectionFormatRocrate](docs/ResponseConvertCollectionFormatRocrate.md)
 - [ResponseConvertRocrateCollectionFormat](docs/ResponseConvertRocrateCollectionFormat.md)
 - [S3Location](docs/S3Location.md)
 - [Schema](docs/Schema.md)
 - [Status](docs/Status.md)
 - [UpdateMetadataResponse](docs/UpdateMetadataResponse.md)
 - [User](docs/User.md)
 - [ValidationError](docs/ValidationError.md)


## Documentation For Authorization


## OAuth2PasswordBearer


- **Type**: OAuth
- **Flow**: password
- **Token URL**: token
- **Scopes**: N/A

