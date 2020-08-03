# REST API - Data Documentation

The data resource is used to create, retrieve, update, and execute operations for instances of the business objects within the Compliance 360 system. Where the metadata describes the business objects, the data is the actual business data populated into instance of those definitions.

## Create

Create the requested entity in the given module/component/type.  Values for fields are read from the post data.
 _Note:_ Types marked as IsReadOnly="True" in [Metadata](meta.html) cannot be created.

### Syntax

POST /API/version/Data/module/component/type?token=token HTTP/1.1

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| token | string | Yes | The user context token obtained using [Login](security.html#Login). |
| module | string | Yes | The token of the module to create the entity in.  This token can be obtained using [Metadata](meta.html). |
| component | string | Yes | The token of the component to create the entity in.  This token can be obtained using [Metadata](meta.html). |
| type | string | Yes | The token of the type to create the entity in.  This token can be obtained using [Metadata](meta.html). |

### Sample Request

POST /API/2.0/Data/EmployeeManagement/Employee/Default?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ== HTTP/1.1<br>
<Object><br>
<Field Token="FirstName"><br>
<Value action="Set">John</Value><br>
</Field><br>
<Field Token="LastName"><br>
<Value action="Set">Smith</Value><br>
</Field><br>
<Field Token="Email"><br>
<Value action="Set">john.smith@mycompany.com</Value><br>
</Field><br>
<Field Token="HireDate"><br>
<Value action="Set">2011-10-31T00:00:00</Value><br>
</Field><br>
<Field Token="Company"><br>
<Value action="Set">EmployeeManagement/EmployeeCompany/Default:1</Value><br>
</Field><br>
<Field Token="PrimaryDivision"><br>
<Value action="Set">EmployeeManagement/EmployeeDivision/Default:3</Value><br>
</Field><br>
<Field Token="TimeZoneId"><br>
<Value action="Set">-6</Value><br>
</Field><br>
<Field Token="WorkflowTemplate"><br>
<Value action="Set">Global/WorkflowTemplates/Employee:84</Value><br>
</Field><br>
<Field Token="Profiles"><br>
<Value action="Add">EmployeeManagement/EmployeeProfile/Default:59</Value><br>
</Field><br>
<Field Token="UserName"><br>
<Value action="Set">john.smith</Value><br>
</Field><br>
<Field Token="Password"><br>
<Value action="Set">password</Value><br>
</Field><br>
<Field Token="MustChangePassword"><br>
<Value action="Set">false</Value><br>
</Field><br>
<Field Token="CanLogin"><br>
<Value action="Set">true</Value><br>
</Field><br>
</Object><br>

### Sample Response

HTTP/1.1 200 OK<br>
<Object Token="EmployeeManagement/Employee/Default:149"><br>
<Field Token="FirstName"><br>
<Value>John</Value><br>
</Field><br>
<Field Token="LastName"><br>
<Value>Smith</Value><br>
</Field><br>
<Field Token="Email"><br>
<Value>john.smith@mycompany.com</Value><br>
</Field><br>
<Field Token="HireDate"><br>
<Value>2011-10-31T00:00:00</Value><br>
</Field><br>
<Field Token="Company"><br>
<Value>EmployeeManagement/EmployeeCompany/Default:1</Value><br>
</Field><br>
<Field Token="PrimaryDivision"><br>
<Value>EmployeeManagement/EmployeeDivision/Default:3</Value><br>
</Field><br>
<Field Token="TimeZoneId"><br>
<Value>-6</Value><br>
</Field><br>
<Field Token="WorkflowTemplate"><br>
<Value>Global/WorkflowTemplates/Employee:84</Value><br>
</Field><br>
<Field Token="Profiles"><br>
<Value>EmployeeManagement/EmployeeProfile/Default:59</Value><br>
</Field><br>
<Field Token="UserName"><br>
<Value>john.smith</Value><br>
</Field><br>
<Field Token="Password"><br>
<Value>password</Value><br>
</Field><br>
<Field Token="MustChangePassword"><br>
<Value>false</Value><br>
</Field><br>
<Field Token="CanLogin"><br>
<Value>true</Value><br>
</Field><br>
</Object><br>

## Retrieve

Finds the entity instances for the given type with optional selection, filtering, ordering and paging parameters.

### Syntax

GET /API/version/Data/module/component/type?token=token &select=select &where=where &order=order &skip=skip &take=take HTTP/1.1

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| token | string | Yes | The user context token obtained using [Login](security.html#Login). |
| module | string | Yes | The token of the module to restrict the results to.  This token can be obtained using [Metadata](meta.html). |
| component | string | Yes | The token of the component to restrict the results to.  This token can be obtained using [Metadata](meta.html). |
| type | string | Yes | The token of the type to restrict the results to.  This token can be obtained using [Metadata](meta.html). |
| select | field selection | No | The comma separated list of field tokens to return. See [Selection syntax](syntax.html#Selection) for more information. |
| where | filter criteria | No | The criteria used to filter the entities. See [Filter syntax](syntax.html#Filter) for more information. |
| order | order by | No | The collection of fields used to sort or order the entities. See [Order syntax](syntax.html#Order) for more information. |
| skip | int | No | The number of records to skip from the beginning. Indexes are zero-based. |
| take | int | No | The number of records to return. |

### Sample Request

GET /API/2.0/Data/EmployeeManagement/Employee/Default?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ==&select=FirstName,LastName&where=FirstName='John'&order=LastName,FirstName&skip=0&take=10 HTTP/1.1<br>

### Sample Response

HTTP/1.1 200 OK<br>
<Objects><br>
<Object Token="EmployeeManagement/Employee/Default:43"><br>
<Field Token="FirstName"><br>
<Value>John</Value><br>
</Field><br>
<Field Token="LastName"><br>
<Value>Smith</Value><br>
</Field><br>
</Object><br>
<!-- SNIP --><br>
</Objects><br>

## Update

Update the requested entity with the given id in the given module/component/type.  Values for fields are read from the post data.
 _Note:_ Types marked as IsReadOnly="True" in [Metadata](meta.html) cannot be updated.

### Syntax

POST /API/version/Data/module/component/type/id?token=token HTTP/1.1

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| token | string | Yes | The user context token obtained using [Login](security.html#Login). |
| module | string | Yes | The token of the module the entity belongs to. This token can be obtained using [Metadata](meta.html). |
| component | string | Yes | The token of the component the entity belongs to. This token can be obtained using [Metadata](meta.html). |
| type | string | Yes | The token of the type the entity belongs to. This token can be obtained using [Metadata](meta.html). |
| id | int | Yes | The id of the entity to update. This value can be obtained using [Create](data.html#Create) or [Retrieve](data.html#Retrieve). |

### Sample Request

POST /API/2.0/Data/EmployeeManagement/Employee/Default?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ== HTTP/1.1<br>
<Object Token="EmployeeManagement/Employee/Default:149"><br>
<Field Token="FirstName"><br>
<Value action="Set">David</Value><br>
</Field><br>
</Object><br>

### Sample Response

HTTP/1.1 200 OK<br>
<Object Token="EmployeeManagement/Employee/Default:149"><br>
<Field Token="FirstName"><br>
<Value>David</Value><br>
</Field><br>
</Object><br>

## Execute

Execute the requested operation for the requested entity with the given id in the given module/component/type.

### Syntax

POST /API/version/Data/module/component/type/id/operation?token=token HTTP/1.1

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| token | string | Yes | The user context token obtained using [Login](security.html#Login). |
| module | string | Yes | The token of the module the entity belongs to.  This token can be obtained using [Metadata](meta.html). |
| component | string | Yes | The token of the component the entity belongs to.  This token can be obtained using [Metadata](meta.html). |
| type | string | Yes | The token of the type the entity belongs to.  This token can be obtained using [Metadata](meta.html). |
| id | int | Yes | The id of the entity to execute the operation on. This value can be obtained using [Create](data.html#Create) or [Retrieve](data.html#Retrieve). |
| operation | string | Yes | The token of the operation to execute. This token can be obtained using [Metadata](meta.html). |

### Sample Request

POST /API/2.0/Data/EmployeeManagement/Employee/Default/149/Delete?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ== HTTP/1.1<br>

### Sample Response

HTTP/1.1 200 OK<br>
