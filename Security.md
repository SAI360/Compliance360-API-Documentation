# API - Security Documentation

Before a client can authenticate with the Compliance 360 API, the client must resolve the correct host that will be servicing requests for the specific organization. Once that host is resolved, all requests should be sent to that specific host including Login requests. To request a user context token, which is required for all data and metadata requests, you must use the Login method on the correct host.

## OrganizationHost

Get the host to use for all subsequent requests (from Login to Logout) for a given organization.

### Syntax

GET /API/version/Security/OrganizationHost?organization=organization HTTP/1.1

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| organization | string | Yes | The name of the organization to authenticate under. |

### Sample Request

GET /API/2.0/Security/OrganizationHost?organization=myorg HTTP/1.1

### Sample Response

HTTP/1.1 200 OK<br>
<OrganizationInfo><br>
<Host>https://secure.compliance360.com</Host><br>
</OrganizationInfo><br>

## Login

Authenticate as a user with the Compliance 360 REST API. The value of the token returned is used for all subsequent calls to the API during the session.

### Syntax

GET /API/version/Security/Login?organization=organization &username=username &password=password &culture=culture HTTP/1.1

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| organization | string | Yes | The name of the organization to authenticate under. |
| username | string | Yes | The name of the user to authenticate under. |
| password | string | Yes | The password used to authenticate the user. |
| culture | string | No | The culture to use for the session (usually en-us). |

### Sample Request

GET /API/2.0/Security/Login?organization=myorg&username=joe&password=password&culture=en-us HTTP/1.1

### Sample Response

HTTP/1.1 200 OK<br>
<Token><br>
<Value>/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ==</Value><br>
</Token><br>

### Post Syntax (Recommended)

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

End a Compliance 360 REST API session and invalidate the user context token

### Syntax

GET /API/version/Security/Logout?token=token HTTP/1.1

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| token | string | Yes | The user context token obtained using [Login](#login). |

### Sample Request

GET /API/2.0/Security/Logout?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ== HTTP/1.1

### Sample Response

HTTP/1.1 200 OK

## GetCulture

Get the current culture of the user context.

### Syntax

GET /API/version/Security/Culture?token=token HTTP/1.1

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| token | string | Yes | The user context token obtained using [Login](#login). |

### Sample Request

GET /API/2.0/Security/Culture?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ== HTTP/1.1

### Sample Response

HTTP/1.1 200 OK<br>
<string>en-us</string>
