# REST API - History Documentation

The history resource is used to retrieve history information for business objects that support an audit trail.

## Retrieve

Retrieve the historical audit entries for the given entity.

### Syntax

GET /API/version/History/module/component/type?token=token &for=for &select=select &where=where &order=order &skip=skip &take=take HTTP/1.1

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| token | string | Yes | The user context token obtained using [Login](security.html#Login). |
| module | string | Yes | The token of the module to restrict the results to.  This token can be obtained using [Metadata](meta.html). |
| component | string | Yes | The token of the component to restrict the results to.  This token can be obtained using [Metadata](meta.html). |
| type | string | Yes | The token of the type to restrict the results to.  This token can be obtained using [Metadata](meta.html). |
| for | object identifier | Yes | The object identifier to retrieve the history records for.  See [Identifier syntax](syntax.html#Identifier) for more information. |
| select | field selection | No | The comma separated list of field tokens to return. See [Selection syntax](syntax.html#Selection) for more information. |
| where | filter criteria | No | The criteria used to filter the entities. See [Filter syntax](syntax.html#Filter) for more information. |
| order | order by | No | The collection of fields used to sort or order the entities. See [Order syntax](syntax.html#Order) for more information. |
| skip | int | No | The number of records to skip from the beginning. Indexes are zero-based. |
| take | int | No | The number of records to return. |

### Sample Request

GET /API/2.0/History/History/EntityAudit/Default?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ==&for=EmployeeManagement/Employee/Default:20&select=AuditDate,Message&where=Message~'Name'&order=AuditDate&skip=0&take=10 HTTP/1.1<br>

### Sample Response

HTTP/1.1 200 OK<br>
<Objects><br>
<Object Token="History/EntityAudit/Default:423134"><br>
<Field Token="Message"><br>
<Value>Field: UserName was changed from "" to "guest"</Value><br>
</Field><br>
<Field Token="AuditDate"><br>
<Value>2013-01-29T19:48:46.703</Value><br>
</Field><br>
</Object><br>
</Objects><br>
