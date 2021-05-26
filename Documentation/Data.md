# API - Data Documentation

The data resource is used to create, retrieve, update, and execute operations for instances of the business objects within the Compliance 360 system. Where the metadata describes the business objects, the data is the actual business data populated into instance of those definitions.

 [Swaggerhub](https://app.swaggerhub.com/api/saiglobal/compliance360-data/2.0.0) [yaml](compliance360-data-api.yaml)

## Create

Create the requested entity in the given module/component/type.  Values for fields are read from the post data.
 _Note:_ Types marked as IsReadOnly="True" in [Metadata](Meta.md) cannot be created.

### Syntax

POST /API/version/Data/module/component/type?token=token

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| token | string | Yes | The user context token obtained using [Authenticate](Security.md#authenticate). |
| module | string | Yes | The token of the module to create the entity in.  This token can be obtained using [Metadata](Meta.md). |
| component | string | Yes | The token of the component to create the entity in.  This token can be obtained using [Metadata](Meta.md). |
| type | string | Yes | The token of the type to create the entity in.  This token can be obtained using [Metadata](Meta.md). |

### Sample Request
```
POST /API/2.0/Data/EmployeeManagement/Employee/Default?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ== HTTP/1.1
<Object>
    <Field Token="FirstName">
        <Value action="Set">John</Value>
    </Field>
    <Field Token="LastName">
        <Value action="Set">Smith</Value>
    </Field>
    <Field Token="Email">
        <Value action="Set">john.smith@mycompany.com</Value>
    </Field>
    <Field Token="HireDate">
        <Value action="Set">2011-10-31T00:00:00</Value>
    </Field>
    <Field Token="Company">
        <Value action="Set">EmployeeManagement/EmployeeCompany/Default:1</Value>
    </Field>
    <Field Token="PrimaryDivision">
        <Value action="Set">EmployeeManagement/EmployeeDivision/Default:3</Value>
    </Field>
    <Field Token="TimeZoneId">
        <Value action="Set">-6</Value>
    </Field>
    <Field Token="WorkflowTemplate">
        <Value action="Set">Global/WorkflowTemplates/Employee:84</Value>
    </Field>
    <Field Token="Profiles">
        <Value action="Add">EmployeeManagement/EmployeeProfile/Default:59</Value>
    </Field>
    <Field Token="UserName">
        <Value action="Set">john.smith</Value>
    </Field>
    <Field Token="Password">
        <Value action="Set">password</Value>
    </Field>
    <Field Token="MustChangePassword">
        <Value action="Set">false</Value>
    </Field>
    <Field Token="CanLogin">
        <Value action="Set">true</Value>
    </Field>
</Object>
```
### Sample Response
```
HTTP/1.1 200 OK
<Object Token="EmployeeManagement/Employee/Default:149">
    <Field Token="FirstName">
        <Value>John</Value>
    </Field>
    <Field Token="LastName">
        <Value>Smith</Value>
    </Field>
    <Field Token="Email">
        <Value>john.smith@mycompany.com</Value>
    </Field>
    <Field Token="HireDate">
        <Value>2011-10-31T00:00:00</Value>
    </Field>
    <Field Token="Company">
        <Value>EmployeeManagement/EmployeeCompany/Default:1</Value>
    </Field>
    <Field Token="PrimaryDivision">
        <Value>EmployeeManagement/EmployeeDivision/Default:3</Value>
    </Field>
    <Field Token="TimeZoneId">
        <Value>-6</Value>
    </Field>
    <Field Token="WorkflowTemplate">
        <Value>Global/WorkflowTemplates/Employee:84</Value>
    </Field>
    <Field Token="Profiles">
        <Value>EmployeeManagement/EmployeeProfile/Default:59</Value>
    </Field>
    <Field Token="UserName">
        <Value>john.smith</Value>
    </Field>
    <Field Token="Password">
        <Value>password</Value>
    </Field>
    <Field Token="MustChangePassword">
        <Value>false</Value>
    </Field>
    <Field Token="CanLogin">
        <Value>true</Value>
    </Field>
</Object>
```
## Retrieve

Finds the entity instances for the given type with optional selection, filtering, ordering and paging parameters.

### Syntax

GET /API/version/Data/module/component/type?token=token &select=select &where=where &order=order &skip=skip &take=take

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| token | string | Yes | The user context token obtained using [Authenticate](Security.md#authenticate). |
| module | string | Yes | The token of the module to restrict the results to.  This token can be obtained using [Metadata](Meta.md). |
| component | string | Yes | The token of the component to restrict the results to.  This token can be obtained using [Metadata](Meta.md). |
| type | string | Yes | The token of the type to restrict the results to.  This token can be obtained using [Metadata](Meta.md). |
| select | field selection | No | The comma separated list of field tokens to return. See [Selection syntax](Syntax.md#selection) for more information. |
| where | filter criteria | No | The criteria used to filter the entities. See [Filter syntax](Syntax.md#filter) for more information. |
| order | order by | No | The collection of fields used to sort or order the entities. See [Order syntax](Syntax.md#order) for more information. |
| skip | int | No | The number of records to skip from the beginning. Indexes are zero-based. |
| take | int | No | The number of records to return. |

### Sample Request
```
GET /API/2.0/Data/EmployeeManagement/Employee/Default?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ==&select=FirstName,LastName&where=FirstName='John'&order=LastName,FirstName&skip=0&take=10
```
### Sample Response
```
HTTP/1.1 200 OK
<Objects>
    <Object Token="EmployeeManagement/Employee/Default:43">
        <Field Token="FirstName">
            <Value>John</Value>
        </Field>
        <Field Token="LastName">
            <Value>Smith</Value>
        </Field>
    </Object>
    <!-- SNIP -->
</Objects>
```
## Update

Update the requested entity with the given id in the given module/component/type.  Values for fields are read from the post data.
 _Note:_ Types marked as IsReadOnly="True" in [Metadata](Meta.md) cannot be updated.

### Syntax

POST /API/version/Data/module/component/type/id?token=token

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| token | string | Yes | The user context token obtained using [Authenticate](Security.md#authenticate). |
| module | string | Yes | The token of the module the entity belongs to. This token can be obtained using [Metadata](Meta.md). |
| component | string | Yes | The token of the component the entity belongs to. This token can be obtained using [Metadata](Meta.md). |
| type | string | Yes | The token of the type the entity belongs to. This token can be obtained using [Metadata](Meta.md). |
| id | int | Yes | The id of the entity to update. This value can be obtained using [Create](Data.md#create) or [Retrieve](Data.md#retrieve). |

### Sample Request
```
POST /API/2.0/Data/EmployeeManagement/Employee/Default?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ== HTTP/1.1
<Object Token="EmployeeManagement/Employee/Default:149">
    <Field Token="FirstName">
        <Value action="Set">David</Value>
    </Field>
</Object>
```
### Sample Response
```
HTTP/1.1 200 OK
<Object Token="EmployeeManagement/Employee/Default:149">
    <Field Token="FirstName">
        <Value>David</Value>
    </Field>
</Object>
```
## Execute

Execute the requested operation for the requested entity with the given id in the given module/component/type.

### Syntax

POST /API/version/Data/module/component/type/id/operation?token=token

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| token | string | Yes | The user context token obtained using [Authenticate](Security.md#authenticate). |
| module | string | Yes | The token of the module the entity belongs to.  This token can be obtained using [Metadata](Meta.md). |
| component | string | Yes | The token of the component the entity belongs to.  This token can be obtained using [Metadata](Meta.md). |
| type | string | Yes | The token of the type the entity belongs to.  This token can be obtained using [Metadata](Meta.md). |
| id | int | Yes | The id of the entity to execute the operation on. This value can be obtained using [Create](Data.md#create) or [Retrieve](Data.md#retrieve). |
| operation | string | Yes | The token of the operation to execute. This token can be obtained using [Metadata](Meta.md). |

### Sample Request
```
POST /API/2.0/Data/EmployeeManagement/Employee/Default/149/Delete?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ==
```
### Sample Response
```
HTTP/1.1 200 OK
```
