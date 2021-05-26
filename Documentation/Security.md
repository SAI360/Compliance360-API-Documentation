# API - Security Documentation

Before a client can authenticate with the Compliance 360 API, the client must resolve the correct host that will be servicing requests for the specific organization. Once that host is resolved, all requests should be sent to that specific host including Authenticate requests. To request a user context token, which is required for all data and metadata requests, you must use the Authenticate method on the correct host. 

[SwaggerHub](https://app.swaggerhub.com/api/saiglobal/compliance360-security/2.0.0) [yaml](compliance360-security-api.yaml)

## OrganizationHost

Get the host to use for all subsequent requests (from Login to Logout) for a given organization.

### Syntax

GET /API/version/Security/OrganizationHost?organization=organization

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| organization | string | Yes | The name of the organization to authenticate under. |

### Sample Request
```
GET /API/2.0/Security/OrganizationHost?organization=myorg 
```
### Sample Response
```
HTTP/1.1 200 OK<br>
<OrganizationInfo><br>
<Host>https://secure.compliance360.com</Host><br>
</OrganizationInfo><br>
```
## Authenticate

Authenticate with the Compliance 360 API. The value of the token returned is used for all subsequent calls to the API during the session.

### Syntax

GET /API/version/Security/Authenticate?organization=organization &integrationkey=integrationkey &culture=culture

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| organization | string | Yes | The name of the organization to authenticate under. |
| integrationkey | string | Yes | The Integration Key generated via the C360 Integrations menu. |
| culture | string | No | The culture to use for the session (usually en-us). |

### Sample Request
```
GET /API/2.0/Security/Authenticate?organization=myorg&integrationkey=MPI053EIHLHHTJZUWE8TOJU5HXO53FIIHK1HWGZR2IO&culture=en-us
```
### Sample Response
```
HTTP/1.1 200 OK<br>
<Token><br>
<Value>/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ==</Value><br>
</Token><br>
```
## Login (deprecated)

Authenticate as a user with the Compliance 360 API. The value of the token returned is used for all subsequent calls to the API during the session.

### Syntax

GET /API/version/Security/Login?organization=organization &username=username &password=password &culture=culture

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| organization | string | Yes | The name of the organization to authenticate under. |
| username | string | Yes | The name of the user to authenticate under. |
| password | string | Yes | The password used to authenticate the user. |
| culture | string | No | The culture to use for the session (usually en-us). |

### Sample Request
```
GET /API/2.0/Security/Login?organization=myorg&username=joe&password=password&culture=en-us
```
### Sample Response
```
HTTP/1.1 200 OK<br>
<Token><br>
<Value>/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ==</Value><br>
</Token><br>
```
### Post Syntax

#### Post Syntax with XML

POST /API/version/Security/Login HTTP/1.1<br>
Content-Type: application/xml<br>
<LoginInformation><br>
<Organization>organization </Organization><br>
<Username>username </Username><br>
<Password>password </Password><br>
<Culture>culture </Culture><br>
</LoginInformation><br>

#### Post Syntax with JSON

POST /API/version/Security/Login HTTP/1.1<br>
Content-Type: application/json<br>
{<br>
 "organization": "organization ",<br>
 "username": "username ",<br>
 "password": "password ",<br>
 "culture": "culture "<br>
}

## Logout

End a Compliance 360 API session and invalidate the user context token

### Syntax

GET /API/version/Security/Logout?token=token

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| token | string | Yes | The user context token obtained using [Authenticate](#authenticate). |

### Sample Request
```
GET /API/2.0/Security/Logout?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ==
```
### Sample Response
```
HTTP/1.1 200 OK
```
## GetCulture

Get the current culture of the user context.

### Syntax

GET /API/version/Security/Culture?token=token

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| token | string | Yes | The user context token obtained using [Authenticate](#authenticate). |

### Sample Request
```
GET /API/2.0/Security/Culture?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ==
```
### Sample Response
```
HTTP/1.1 200 OK<br>
<string>en-us</string>
```
