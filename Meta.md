# API - Metadata Documentation

Metadata is used to describe the business objects within the Compliance 360 system. The metadata access methods allow a caller to read the definitions of the business data and how it relates to other elements of data.

## GetAllModules

Get a list of all the modules, components, types and fields in the Compliance 360 metadata system to which the authenticated user has access.

### Syntax

GET /API/version/Meta?token=token

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| token | string | Yes | The user context token obtained using [Authenticate](security.html#Authenticate). |

### Sample Request
```
GET /API/2.0/Meta?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ==
```
### Sample Response
```
HTTP/1.1 200 OK
&lt;Modules><br>
&nbsp;&nbsp;&nbsp;&nbsp;&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement"><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Components><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee"><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Types><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" IsReadOnly="False"><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;IdentityField Token="InstanceId" QualifiedToken="EmployeeManagement/Employee/Default/InstanceId" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Fields><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Field Token="InstanceId" QualifiedToken="EmployeeManagement/Employee/Default/InstanceId" FieldType="Relation" IsMultiValue="False" IsReadOnly="True" IsRequired="True"><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;RelatedComponent Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;RelatedType Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;/Field><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Field Token="WorkflowTemplate" QualifiedToken="EmployeeManagement/Employee/Default/WorkflowTemplate" FieldType="Relation" IsMultiValue="False" IsReadOnly="False" IsRequired="True"><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;RelatedComponent Token="WorkflowTemplates" QualifiedToken="Global/WorkflowTemplates" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;RelatedType Token="Employee" QualifiedToken="Global/WorkflowTemplates/Employee" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;/Field><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Field Token="FirstName" QualifiedToken="EmployeeManagement/Employee/Default/FirstName" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;/Field><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Field Token="LastName" QualifiedToken="EmployeeManagement/Employee/Default/LastName" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;/Field><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Field Token="Password" QualifiedToken="EmployeeManagement/Employee/Default/Password" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;/Field><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Field Token="PrimaryDivision" QualifiedToken="EmployeeManagement/Employee/Default/PrimaryDivision" FieldType="Relation" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;RelatedComponent Token="EmployeeDivision" QualifiedToken="EmployeeManagement/EmployeeDivision" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;RelatedType Token="Default" QualifiedToken="EmployeeManagement/EmployeeDivision/Default" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;/Field><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Field Token="Profiles" QualifiedToken="EmployeeManagement/Employee/Default/Profiles" FieldType="Relation" IsMultiValue="True" IsReadOnly="False" IsRequired="False"><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;RelatedComponent Token="EmployeeProfile" QualifiedToken="EmployeeManagement/EmployeeProfile" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;RelatedType Token="Default" QualifiedToken="EmployeeManagement/EmployeeProfile/Default" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;/Field><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Field Token="UserName" QualifiedToken="EmployeeManagement/Employee/Default/UserName" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;/Field><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;!-- SNIP --><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;/Fields><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Operations><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Operation Token="Delete" QualifiedToken="EmployeeManagement/Employee/Default/Delete"><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;Validator Token="CanDelete" QualifiedToken="EmployeeManagement/Employee/Default/CanDelete" /><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;/Operation><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;!-- SNIP --><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;/Operations><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;/Type><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;!-- SNIP --><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;/Types><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;/Component><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;!-- SNIP --><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;/Components><br>
&nbsp;&nbsp;&nbsp;&nbsp;&lt;/Module><br>
&nbsp;&nbsp;&nbsp;&nbsp;&lt;!-- SNIP --><br>
&lt;/Modules><br>
```
## GetModule

Get a list of all the components, types and fields in the given module.

### Syntax

GET /API/version/Meta/module?token=token

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| token | string | Yes | The user context token obtained using [Login](security.html#Login). |
| module | string | Yes | The token of the module to retrieve. |

### Sample Request

GET /API/2.0/Meta/EmployeeManagement?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ==

### Sample Response

HTTP/1.1 200 OK<br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement"><br>
&lt;Components><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Types><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" IsReadOnly="False"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;IdentityField Token="InstanceId" QualifiedToken="EmployeeManagement/Employee/Default/InstanceId" /><br>
&lt;Fields><br>
&lt;Field Token="InstanceId" QualifiedToken="EmployeeManagement/Employee/Default/InstanceId" FieldType="Relation" IsMultiValue="False" IsReadOnly="True" IsRequired="True"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;RelatedComponent Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;RelatedType Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;/Field><br>
&lt;Field Token="WorkflowTemplate" QualifiedToken="EmployeeManagement/Employee/Default/WorkflowTemplate" FieldType="Relation" IsMultiValue="False" IsReadOnly="False" IsRequired="True"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;RelatedComponent Token="WorkflowTemplates" QualifiedToken="Global/WorkflowTemplates" /><br>
&lt;RelatedType Token="Employee" QualifiedToken="Global/WorkflowTemplates/Employee" /><br>
&lt;/Field><br>
&lt;Field Token="FirstName" QualifiedToken="EmployeeManagement/Employee/Default/FirstName" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;/Field><br>
&lt;Field Token="LastName" QualifiedToken="EmployeeManagement/Employee/Default/LastName" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;/Field><br>
&lt;Field Token="Password" QualifiedToken="EmployeeManagement/Employee/Default/Password" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;/Field><br>
&lt;Field Token="PrimaryDivision" QualifiedToken="EmployeeManagement/Employee/Default/PrimaryDivision" FieldType="Relation" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;RelatedComponent Token="EmployeeDivision" QualifiedToken="EmployeeManagement/EmployeeDivision" /><br>
&lt;RelatedType Token="Default" QualifiedToken="EmployeeManagement/EmployeeDivision/Default" /><br>
&lt;/Field><br>
&lt;Field Token="Profiles" QualifiedToken="EmployeeManagement/Employee/Default/Profiles" FieldType="Relation" IsMultiValue="True" IsReadOnly="False" IsRequired="False"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;RelatedComponent Token="EmployeeProfile" QualifiedToken="EmployeeManagement/EmployeeProfile" /><br>
&lt;RelatedType Token="Default" QualifiedToken="EmployeeManagement/EmployeeProfile/Default" /><br>
&lt;/Field><br>
&lt;Field Token="UserName" QualifiedToken="EmployeeManagement/Employee/Default/UserName" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;/Field><br>
&lt;!-- SNIP --><br>
&lt;/Fields><br>
&lt;Operations><br>
&lt;Operation Token="Delete" QualifiedToken="EmployeeManagement/Employee/Default/Delete"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;Validator Token="CanDelete" QualifiedToken="EmployeeManagement/Employee/Default/CanDelete" /><br>
&lt;/Operation><br>
&lt;!-- SNIP --><br>
&lt;/Operations><br>
&lt;/Type><br>
&lt;!-- SNIP --><br>
&lt;/Types><br>
&lt;/Component><br>
&lt;!-- SNIP --><br>
&lt;/Components><br>
&lt;/Module><br>

## GetComponent

Get a list of all the types and fields in the given component.

### Syntax

GET /API/version/Meta/module/component?token=token

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| token | string | Yes | The user context token obtained using [Login](security.html#Login). |
| module | string | Yes | The token of the module to retrieve. |
| component | string | Yes | The token of the component to retrieve. |

### Sample Request

GET /API/2.0/Meta/EmployeeManagement/Employee?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ==

### Sample Response

HTTP/1.1 200 OK<br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Types><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" IsReadOnly="False"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;IdentityField Token="InstanceId" QualifiedToken="EmployeeManagement/Employee/Default/InstanceId" /><br>
&lt;Fields><br>
&lt;Field Token="InstanceId" QualifiedToken="EmployeeManagement/Employee/Default/InstanceId" FieldType="Relation" IsMultiValue="False" IsReadOnly="True" IsRequired="True"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;RelatedComponent Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;RelatedType Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;/Field><br>
&lt;Field Token="WorkflowTemplate" QualifiedToken="EmployeeManagement/Employee/Default/WorkflowTemplate" FieldType="Relation" IsMultiValue="False" IsReadOnly="False" IsRequired="True"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;RelatedComponent Token="WorkflowTemplates" QualifiedToken="Global/WorkflowTemplates" /><br>
&lt;RelatedType Token="Employee" QualifiedToken="Global/WorkflowTemplates/Employee" /><br>
&lt;/Field><br>
&lt;Field Token="FirstName" QualifiedToken="EmployeeManagement/Employee/Default/FirstName" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;/Field><br>
&lt;Field Token="LastName" QualifiedToken="EmployeeManagement/Employee/Default/LastName" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;/Field><br>
&lt;Field Token="Password" QualifiedToken="EmployeeManagement/Employee/Default/Password" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;/Field><br>
&lt;Field Token="PrimaryDivision" QualifiedToken="EmployeeManagement/Employee/Default/PrimaryDivision" FieldType="Relation" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;RelatedComponent Token="EmployeeDivision" QualifiedToken="EmployeeManagement/EmployeeDivision" /><br>
&lt;RelatedType Token="Default" QualifiedToken="EmployeeManagement/EmployeeDivision/Default" /><br>
&lt;/Field><br>
&lt;Field Token="Profiles" QualifiedToken="EmployeeManagement/Employee/Default/Profiles" FieldType="Relation" IsMultiValue="True" IsReadOnly="False" IsRequired="False"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;RelatedComponent Token="EmployeeProfile" QualifiedToken="EmployeeManagement/EmployeeProfile" /><br>
&lt;RelatedType Token="Default" QualifiedToken="EmployeeManagement/EmployeeProfile/Default" /><br>
&lt;/Field><br>
&lt;Field Token="UserName" QualifiedToken="EmployeeManagement/Employee/Default/UserName" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;/Field><br>
&lt;!-- SNIP --><br>
&lt;/Fields><br>
&lt;Operations><br>
&lt;Operation Token="Delete" QualifiedToken="EmployeeManagement/Employee/Default/Delete"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;Validator Token="CanDelete" QualifiedToken="EmployeeManagement/Employee/Default/CanDelete" /><br>
&lt;/Operation><br>
&lt;!-- SNIP --><br>
&lt;/Operations><br>
&lt;/Type><br>
&lt;!-- SNIP --><br>
&lt;/Types><br>
&lt;/Component><br>

## GetType

Get a list of all the fields in the given type.

### Syntax

GET /API/version/Meta/module/component/type?token=token

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| token | string | Yes | The user context token obtained using [Login](security.html#Login). |
| module | string | Yes | The token of the module to retrieve. |
| component | string | Yes | The token of the component to retrieve. |
| type | string | Yes | The token of the type to retrieve. |

### Sample Request

GET /API/2.0/Meta/EmployeeManagement/Employee/Default?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ==

### Sample Response

HTTP/1.1 200 OK<br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" IsReadOnly="False"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;IdentityField Token="InstanceId" QualifiedToken="EmployeeManagement/Employee/Default/InstanceId" /><br>
&lt;Fields><br>
&lt;Field Token="InstanceId" QualifiedToken="EmployeeManagement/Employee/Default/InstanceId" FieldType="Relation" IsMultiValue="False" IsReadOnly="True" IsRequired="True"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;RelatedComponent Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;RelatedType Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;/Field><br>
&lt;Field Token="WorkflowTemplate" QualifiedToken="EmployeeManagement/Employee/Default/WorkflowTemplate" FieldType="Relation" IsMultiValue="False" IsReadOnly="False" IsRequired="True"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;RelatedComponent Token="WorkflowTemplates" QualifiedToken="Global/WorkflowTemplates" /><br>
&lt;RelatedType Token="Employee" QualifiedToken="Global/WorkflowTemplates/Employee" /><br>
&lt;/Field><br>
&lt;Field Token="FirstName" QualifiedToken="EmployeeManagement/Employee/Default/FirstName" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;/Field><br>
&lt;Field Token="LastName" QualifiedToken="EmployeeManagement/Employee/Default/LastName" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;/Field><br>
&lt;Field Token="Password" QualifiedToken="EmployeeManagement/Employee/Default/Password" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;/Field><br>
&lt;Field Token="PrimaryDivision" QualifiedToken="EmployeeManagement/Employee/Default/PrimaryDivision" FieldType="Relation" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;RelatedComponent Token="EmployeeDivision" QualifiedToken="EmployeeManagement/EmployeeDivision" /><br>
&lt;RelatedType Token="Default" QualifiedToken="EmployeeManagement/EmployeeDivision/Default" /><br>
&lt;/Field><br>
&lt;Field Token="Profiles" QualifiedToken="EmployeeManagement/Employee/Default/Profiles" FieldType="Relation" IsMultiValue="True" IsReadOnly="False" IsRequired="False"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;RelatedComponent Token="EmployeeProfile" QualifiedToken="EmployeeManagement/EmployeeProfile" /><br>
&lt;RelatedType Token="Default" QualifiedToken="EmployeeManagement/EmployeeProfile/Default" /><br>
&lt;/Field><br>
&lt;Field Token="UserName" QualifiedToken="EmployeeManagement/Employee/Default/UserName" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;/Field><br>
&lt;!-- SNIP --><br>
&lt;/Fields><br>
&lt;Operations><br>
&lt;Operation Token="Delete" QualifiedToken="EmployeeManagement/Employee/Default/Delete"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;Validator Token="CanDelete" QualifiedToken="EmployeeManagement/Employee/Default/CanDelete" /><br>
&lt;/Operation><br>
&lt;!-- SNIP --><br>
&lt;/Operations><br>
&lt;/Type><br>

## GetField

Get details for the given field.

### Syntax

GET /API/version/Meta/module/component/type/field?token=token

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| token | string | Yes | The user context token obtained using [Login](security.html#Login). |
| module | string | Yes | The token of the module to retrieve. |
| component | string | Yes | The token of the component to retrieve. |
| type | string | Yes | The token of the type to retrieve. |
| field | string | Yes | The token of the field to retrieve. |

### Sample Request

GET /API/2.0/Meta/EmployeeManagement/Employee/Default/FirstName?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ==

### Sample Response

HTTP/1.1 200 OK<br>
&lt;Field Token="FirstName" QualifiedToken="EmployeeManagement/Employee/Default/FirstName" FieldType="String" IsMultiValue="False" IsReadOnly="False" IsRequired="False"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;/Field><br>

## GetOperation

Get details for the given operation.

### Syntax

GET /API/version/Meta/module/component/type/operation?token=token

### Parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| token | string | Yes | The user context token obtained using [Login](security.html#Login). |
| module | string | Yes | The token of the module to retrieve. |
| component | string | Yes | The token of the component to retrieve. |
| type | string | Yes | The token of the type to retrieve. |
| operation | string | Yes | The token of the operation to retrieve. |

### Sample Request

GET /API/2.0/Meta/EmployeeManagement/Employee/Default/Delete?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ==

### Sample Response

HTTP/1.1 200 OK<br>
&lt;Operation Token="Delete" QualifiedToken="EmployeeManagement/Employee/Default/Delete"><br>
&lt;Module Token="EmployeeManagement" QualifiedToken="EmployeeManagement" /><br>
&lt;Component Token="Employee" QualifiedToken="EmployeeManagement/Employee" /><br>
&lt;Type Token="Default" QualifiedToken="EmployeeManagement/Employee/Default" /><br>
&lt;Validator Token="CanDelete" QualifiedToken="EmployeeManagement/Employee/Default/CanDelete" /><br>
&lt;/Operation><br>
