# API - Metadata Documentation

Metadata is used to describe the business objects within the Compliance 360 system. The metadata access methods allow a caller to read the definitions of the business data and how it relates to other elements of data.

## GetAllModules

Get a list of all the modules, components, types and fields in the Compliance 360 metadata system to which the authenticated user has access.

### Syntax

GET /API/version/Meta?token=token HTTP/1.1

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| token | string | Yes | The user context token obtained using [Login](security.html#Login). |

### Sample Request

GET /API/2.0/Meta?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ== HTTP/1.1

### Sample Response

HTTP/1.1 200 OK<br>
&lt;Modules><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement"><br>
<Components><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Types><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" IsReadOnly="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<IdentityField Token="InstanceId" QualifiedToken="EmployeeManagement/Employee/Default/InstanceId" /><br>
<Fields><br>
<Field Token="InstanceId" QualifiedToken="EmployeeManagement/Employee/Default/InstanceId" FieldType="Relation" IsMultiValue="False" IsReadOnly="True" IsRequired="True"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
<RelatedComponent Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<RelatedType Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
</Field><br>
<Field Token="WorkflowTemplate" QualifiedToken="EmployeeManagement/Employee/Default/WorkflowTemplate" FieldType="Relation" IsMultiValue="False" IsReadOnly="False" IsRequired="True"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
<RelatedComponent Token="WorkflowTemplates" QualifiedToken="Global/WorkflowTemplates" /><br>
<RelatedType Token="Employee" QualifiedToken="Global/WorkflowTemplates/Employee" /><br>
</Field><br>
<Field Token="FirstName" QualifiedToken="EmployeeManagement/Employee/Default/FirstName" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
</Field><br>
<Field Token="LastName" QualifiedToken="EmployeeManagement/Employee/Default/LastName" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
</Field><br>
<Field Token="Password" QualifiedToken="EmployeeManagement/Employee/Default/Password" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
</Field><br>
<Field Token="PrimaryDivision" QualifiedToken="EmployeeManagement/Employee/Default/PrimaryDivision" FieldType="Relation" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
<RelatedComponent Token="EmployeeDivision" QualifiedToken="EmployeeManagement/EmployeeDivision" /><br>
<RelatedType Token="Default" QualifiedToken="EmployeeManagement/EmployeeDivision/Default" /><br>
</Field><br>
<Field Token="Profiles" QualifiedToken="EmployeeManagement/Employee/Default/Profiles" FieldType="Relation" IsMultiValue="True" IsReadOnly="False" IsRequired="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
<RelatedComponent Token="EmployeeProfile" QualifiedToken="EmployeeManagement/EmployeeProfile" /><br>
<RelatedType Token="Default" QualifiedToken="EmployeeManagement/EmployeeProfile/Default" /><br>
</Field><br>
<Field Token="UserName" QualifiedToken="EmployeeManagement/Employee/Default/UserName" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
</Field><br>
<!-- SNIP --><br>
</Fields><br>
<Operations><br>
<Operation Token="Delete" QualifiedToken="EmployeeManagement/Employee/Default/Delete"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
<Validator Token="CanDelete" QualifiedToken="EmployeeManagement/Employee/Default/CanDelete" /><br>
</Operation><br>
<!-- SNIP --><br>
</Operations><br>
</Type><br>
<!-- SNIP --><br>
</Types><br>
</Component><br>
<!-- SNIP --><br>
</Components><br>
</Module><br>
<!-- SNIP --><br>
</Modules><br>

## GetModule

Get a list of all the components, types and fields in the given module.

### Syntax

GET /API/version/Meta/module?token=token HTTP/1.1

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| token | string | Yes | The user context token obtained using [Login](security.html#Login). |
| module | string | Yes | The token of the module to retrieve. |

### Sample Request

GET /API/2.0/Meta/EmployeeManagement?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ== HTTP/1.1

### Sample Response

HTTP/1.1 200 OK<br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement"><br>
<Components><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Types><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" IsReadOnly="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<IdentityField Token="InstanceId" QualifiedToken="EmployeeManagement/Employee/Default/InstanceId" /><br>
<Fields><br>
<Field Token="InstanceId" QualifiedToken="EmployeeManagement/Employee/Default/InstanceId" FieldType="Relation" IsMultiValue="False" IsReadOnly="True" IsRequired="True"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
<RelatedComponent Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<RelatedType Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
</Field><br>
<Field Token="WorkflowTemplate" QualifiedToken="EmployeeManagement/Employee/Default/WorkflowTemplate" FieldType="Relation" IsMultiValue="False" IsReadOnly="False" IsRequired="True"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
<RelatedComponent Token="WorkflowTemplates" QualifiedToken="Global/WorkflowTemplates" /><br>
<RelatedType Token="Employee" QualifiedToken="Global/WorkflowTemplates/Employee" /><br>
</Field><br>
<Field Token="FirstName" QualifiedToken="EmployeeManagement/Employee/Default/FirstName" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
</Field><br>
<Field Token="LastName" QualifiedToken="EmployeeManagement/Employee/Default/LastName" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
</Field><br>
<Field Token="Password" QualifiedToken="EmployeeManagement/Employee/Default/Password" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
</Field><br>
<Field Token="PrimaryDivision" QualifiedToken="EmployeeManagement/Employee/Default/PrimaryDivision" FieldType="Relation" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
<RelatedComponent Token="EmployeeDivision" QualifiedToken="EmployeeManagement/EmployeeDivision" /><br>
<RelatedType Token="Default" QualifiedToken="EmployeeManagement/EmployeeDivision/Default" /><br>
</Field><br>
<Field Token="Profiles" QualifiedToken="EmployeeManagement/Employee/Default/Profiles" FieldType="Relation" IsMultiValue="True" IsReadOnly="False" IsRequired="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
<RelatedComponent Token="EmployeeProfile" QualifiedToken="EmployeeManagement/EmployeeProfile" /><br>
<RelatedType Token="Default" QualifiedToken="EmployeeManagement/EmployeeProfile/Default" /><br>
</Field><br>
<Field Token="UserName" QualifiedToken="EmployeeManagement/Employee/Default/UserName" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
</Field><br>
<!-- SNIP --><br>
</Fields><br>
<Operations><br>
<Operation Token="Delete" QualifiedToken="EmployeeManagement/Employee/Default/Delete"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
<Validator Token="CanDelete" QualifiedToken="EmployeeManagement/Employee/Default/CanDelete" /><br>
</Operation><br>
<!-- SNIP --><br>
</Operations><br>
</Type><br>
<!-- SNIP --><br>
</Types><br>
</Component><br>
<!-- SNIP --><br>
</Components><br>
</Module><br>

## GetComponent

Get a list of all the types and fields in the given component.

### Syntax

GET /API/version/Meta/module/component?token=token HTTP/1.1

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| token | string | Yes | The user context token obtained using [Login](security.html#Login). |
| module | string | Yes | The token of the module to retrieve. |
| component | string | Yes | The token of the component to retrieve. |

### Sample Request

GET /API/2.0/Meta/EmployeeManagement/Employee?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ== HTTP/1.1

### Sample Response

HTTP/1.1 200 OK<br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Types><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" IsReadOnly="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<IdentityField Token="InstanceId" QualifiedToken="EmployeeManagement/Employee/Default/InstanceId" /><br>
<Fields><br>
<Field Token="InstanceId" QualifiedToken="EmployeeManagement/Employee/Default/InstanceId" FieldType="Relation" IsMultiValue="False" IsReadOnly="True" IsRequired="True"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
<RelatedComponent Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<RelatedType Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
</Field><br>
<Field Token="WorkflowTemplate" QualifiedToken="EmployeeManagement/Employee/Default/WorkflowTemplate" FieldType="Relation" IsMultiValue="False" IsReadOnly="False" IsRequired="True"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
<RelatedComponent Token="WorkflowTemplates" QualifiedToken="Global/WorkflowTemplates" /><br>
<RelatedType Token="Employee" QualifiedToken="Global/WorkflowTemplates/Employee" /><br>
</Field><br>
<Field Token="FirstName" QualifiedToken="EmployeeManagement/Employee/Default/FirstName" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
</Field><br>
<Field Token="LastName" QualifiedToken="EmployeeManagement/Employee/Default/LastName" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
</Field><br>
<Field Token="Password" QualifiedToken="EmployeeManagement/Employee/Default/Password" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
</Field><br>
<Field Token="PrimaryDivision" QualifiedToken="EmployeeManagement/Employee/Default/PrimaryDivision" FieldType="Relation" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
<RelatedComponent Token="EmployeeDivision" QualifiedToken="EmployeeManagement/EmployeeDivision" /><br>
<RelatedType Token="Default" QualifiedToken="EmployeeManagement/EmployeeDivision/Default" /><br>
</Field><br>
<Field Token="Profiles" QualifiedToken="EmployeeManagement/Employee/Default/Profiles" FieldType="Relation" IsMultiValue="True" IsReadOnly="False" IsRequired="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
<RelatedComponent Token="EmployeeProfile" QualifiedToken="EmployeeManagement/EmployeeProfile" /><br>
<RelatedType Token="Default" QualifiedToken="EmployeeManagement/EmployeeProfile/Default" /><br>
</Field><br>
<Field Token="UserName" QualifiedToken="EmployeeManagement/Employee/Default/UserName" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
</Field><br>
<!-- SNIP --><br>
</Fields><br>
<Operations><br>
<Operation Token="Delete" QualifiedToken="EmployeeManagement/Employee/Default/Delete"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
<Validator Token="CanDelete" QualifiedToken="EmployeeManagement/Employee/Default/CanDelete" /><br>
</Operation><br>
<!-- SNIP --><br>
</Operations><br>
</Type><br>
<!-- SNIP --><br>
</Types><br>
</Component><br>

## GetType

Get a list of all the fields in the given type.

### Syntax

GET /API/version/Meta/module/component/type?token=token HTTP/1.1

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| token | string | Yes | The user context token obtained using [Login](security.html#Login). |
| module | string | Yes | The token of the module to retrieve. |
| component | string | Yes | The token of the component to retrieve. |
| type | string | Yes | The token of the type to retrieve. |

### Sample Request

GET /API/2.0/Meta/EmployeeManagement/Employee/Default?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ== HTTP/1.1

### Sample Response

HTTP/1.1 200 OK<br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" IsReadOnly="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<IdentityField Token="InstanceId" QualifiedToken="EmployeeManagement/Employee/Default/InstanceId" /><br>
<Fields><br>
<Field Token="InstanceId" QualifiedToken="EmployeeManagement/Employee/Default/InstanceId" FieldType="Relation" IsMultiValue="False" IsReadOnly="True" IsRequired="True"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
<RelatedComponent Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<RelatedType Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
</Field><br>
<Field Token="WorkflowTemplate" QualifiedToken="EmployeeManagement/Employee/Default/WorkflowTemplate" FieldType="Relation" IsMultiValue="False" IsReadOnly="False" IsRequired="True"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
<RelatedComponent Token="WorkflowTemplates" QualifiedToken="Global/WorkflowTemplates" /><br>
<RelatedType Token="Employee" QualifiedToken="Global/WorkflowTemplates/Employee" /><br>
</Field><br>
<Field Token="FirstName" QualifiedToken="EmployeeManagement/Employee/Default/FirstName" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
</Field><br>
<Field Token="LastName" QualifiedToken="EmployeeManagement/Employee/Default/LastName" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
</Field><br>
<Field Token="Password" QualifiedToken="EmployeeManagement/Employee/Default/Password" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
</Field><br>
<Field Token="PrimaryDivision" QualifiedToken="EmployeeManagement/Employee/Default/PrimaryDivision" FieldType="Relation" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
<RelatedComponent Token="EmployeeDivision" QualifiedToken="EmployeeManagement/EmployeeDivision" /><br>
<RelatedType Token="Default" QualifiedToken="EmployeeManagement/EmployeeDivision/Default" /><br>
</Field><br>
<Field Token="Profiles" QualifiedToken="EmployeeManagement/Employee/Default/Profiles" FieldType="Relation" IsMultiValue="True" IsReadOnly="False" IsRequired="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
<RelatedComponent Token="EmployeeProfile" QualifiedToken="EmployeeManagement/EmployeeProfile" /><br>
<RelatedType Token="Default" QualifiedToken="EmployeeManagement/EmployeeProfile/Default" /><br>
</Field><br>
<Field Token="UserName" QualifiedToken="EmployeeManagement/Employee/Default/UserName" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
</Field><br>
<!-- SNIP --><br>
</Fields><br>
<Operations><br>
<Operation Token="Delete" QualifiedToken="EmployeeManagement/Employee/Default/Delete"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
<Validator Token="CanDelete" QualifiedToken="EmployeeManagement/Employee/Default/CanDelete" /><br>
</Operation><br>
<!-- SNIP --><br>
</Operations><br>
</Type><br>

## GetField

Get details for the given field.

### Syntax

GET /API/version/Meta/module/component/type/field?token=token HTTP/1.1

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| token | string | Yes | The user context token obtained using [Login](security.html#Login). |
| module | string | Yes | The token of the module to retrieve. |
| component | string | Yes | The token of the component to retrieve. |
| type | string | Yes | The token of the type to retrieve. |
| field | string | Yes | The token of the field to retrieve. |

### Sample Request

GET /API/2.0/Meta/EmployeeManagement/Employee/Default/FirstName?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ== HTTP/1.1

### Sample Response

HTTP/1.1 200 OK<br>
<Field Token="FirstName" QualifiedToken="EmployeeManagement/Employee/Default/FirstName" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
</Field><br>

## GetOperation

Get details for the given operation.

### Syntax

GET /API/version/Meta/module/component/type/operation?token=token HTTP/1.1

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| token | string | Yes | The user context token obtained using [Login](security.html#Login). |
| module | string | Yes | The token of the module to retrieve. |
| component | string | Yes | The token of the component to retrieve. |
| type | string | Yes | The token of the type to retrieve. |
| operation | string | Yes | The token of the operation to retrieve. |

### Sample Request

GET /API/2.0/Meta/EmployeeManagement/Employee/Default/Delete?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ== HTTP/1.1

### Sample Response

HTTP/1.1 200 OK<br>
<Operation Token="Delete" QualifiedToken="EmployeeManagement/Employee/Default/Delete"><br>
<Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
<Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
<Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
<Validator Token="CanDelete" QualifiedToken="EmployeeManagement/Employee/Default/CanDelete" /><br>
</Operation><br>
