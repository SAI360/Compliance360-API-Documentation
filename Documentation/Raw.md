# REST API - Raw Documentation

The raw resource is used to retrieve and update binary file contents for business objects such as attachments or documents.

## GetStream

Retrieve the binary file contents for the given field on a specific entity.
 _Note:_ To retrieve the file contents as a PDF, include the "Accept" header with a value of "application/pdf".

### Syntax

GET /API/version/Raw/module/component/type/id/field?token=token HTTP/1.1

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| token | string | Yes | The user context token obtained using [Authenticate](Security.md#authenticate). |
| module | string | Yes | The token of the module the entity belongs to.  This token can be obtained using [Metadata](Meta.md). |
| component | string | Yes | The token of the component the entity belongs to.  This token can be obtained using [Metadata](Meta.md). |
| type | string | Yes | The token of the type the entity belongs to.  This token can be obtained using [Metadata](Meta.md). |
| id | int | Yes | The id of the entity to retrieve. This value can be obtained using [Create](data.html#Create) or [Retrieve](Data.md#retrieve). |
| field | string | Yes | The token of the field to retrieve. This token can be obtained using [Metadata](Meta.md). |

### Sample Request
```
GET /API/2.0/Raw/Documents/MetaDocument/Default/30/FileContent?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ==<br>
Accept: */*
```
### Sample Response
```
HTTP/1.1 200 OK
Content-Type: image/jpeg
Content-Disposition: attachment; filename=example.jpg
Content-Length: 13598
<...binary data...>
```
## SetStream

Update the binary file contents for the given field on a specific entity.

### Syntax

POST /API/version/Raw/module/component/type/id/field?token=token

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| token | string | Yes | The user context token obtained using [Authenticate](Security.md#authenticate). |
| module | string | Yes | The token of the module the entity belongs to.  This token can be obtained using [Metadata](Meta.md). |
| component | string | Yes | The token of the component the entity belongs to.  This token can be obtained using [Metadata](Meta.md). |
| type | string | Yes | The token of the type the entity belongs to.  This token can be obtained using [Metadata](Meta.md). |
| id | int | Yes | The id of the entity to update. This value can be obtained using [Create](data.html#Create) or [Retrieve](Data.md#retrieve). |
| field | string | Yes | The token of the field to update. This token can be obtained using [Metadata](Meta.md). |

### Sample Request
```
POST /API/2.0/Raw/Documents/MetaDocument/Default/30/FileContent?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ==
Content-Type: image/jpeg
Content-Disposition: attachment; filename=example.jpg
Content-Length: 13598
<...binary data...>
```
### Sample Response
```
HTTP/1.1 200 OK<br>
```
