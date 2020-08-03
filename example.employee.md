# REST API - Example - Create Employee

This is an example of creating an employee that can login to the Compliance 360 system and adding them to a manual profile using the [Compliance 360 REST API](overview.html). The metadata used for this example is the Compliance 360 supplied metadata for Compliance 360 version 2011.3. The organization used for this example is named "zonda".

This example is broken down into the following steps:

1. Authenticating with the API
2.
                    Retrieving Related Data Instance IDs

  1. Getting a Job Title Lookup ID
  2. Getting a Division ID
  3. Getting a Company ID
  4. Getting a Workflow Template
  5. Getting an Employee Profile
3. Inserting the Employee Instance

## Authenticating with the API

The first step in creating an employee is authenticating with the REST API using a login which has the permission to create employees. Call [Login](security.html#Login), supplying the organization, user name, and password of the user with permissions to create employees. In this example a user in the organization "zonda" with the login name "mikeh" with the password "mypassword" has permission to create employees. Using those credentials, we retrieve a user context token that is used in subsequent REST API calls.

### Sample Request

GET Security/1.0/Login?organization=zonda&username=mikeh&password=mypassword HTTP/1.1<br>

### Sample Response

HTTP/1.1 200 OK<br>
<Token xmlns="http://www.compliance360.com" xmlns:i="http://www.w3.org/2001/XMLSchema-instance"><br>
<Value>/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ==</Value><br>
</Token><br>
Extract the token value **/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ==** from the response body XML and save it for use in subsequent API calls.

## Retrieving Related Data Instance IDs

We need to retrieve the IDs of related data like selections for lookups such as job title, and other entities like departments.

## Getting a Job Title Lookup ID

Job Title is an example of a relation field which references a lookup value. We need to [Retrieve](data.html#Retrieve) the ID of the lookup value (shown below) or [create](data.html#Create) a lookup value (see the previous link).

### Sample Request

GET /API/2.0/Data/Lookup/Employee/JobTitleId?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ==&take=1&where=Text='Doctor' HTTP/1.1<br>

### Sample Response

HTTP/1.1 200 OK<br>
<Objects><br>
<Object Token="Lookup/Employee/JobTitleId:19430" /><br>
</Objects><br>
We need to parse the response to obtain the desired lookup ID. In this case, the employee we are adding is a "Doctor" so save the lookup ID **19430** for later use.

## Getting a Division ID

For an Employee, we need to specify a primary division to which the Employee instance belongs. We use a call to [Retrieve](data.html#Retrieve) to retrieve the division instance we are linking to the employee and get the division instance ID. The name of the division we are looking for is "My Division". We specify the division name in the criteria.

### Sample Request

GET /API/2.0/Data/EmployeeManagement/EmployeeDivision/Default?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ==&take=1&where=Name='My Division' HTTP/1.1<br>

### Sample Response

HTTP/1.1 200 OK<br>
<Objects><br>
<Object Token="EmployeeManagement/EmployeeDivision/Default:89" /><br>
</Objects><br>
We need to parse the Division ID value **89** out of the response data and save it for later use.

## Getting a Company ID

For an Employee, we can specify a company to which the employee is related through a single reference field where one entity references another entity. In this case, the Company field of the Employee instance field references an EmployeeCompany. We use a call to [Retrieve](data.html#Retrieve) to retrieve the company instance we are linking to the employee and get the company instance ID. The name of company we are looking for is "My Company". We specify the company name we are looking for in the criteria.

### Sample Request

GET /API/2.0/Data/EmployeeManagement/EmployeeCompany/Default?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ==&take=1&where=CompName='My Company' HTTP/1.1<br>

### Sample Response

HTTP/1.1 200 OK<br>
<Objects><br>
<Object Token="EmployeeManagement/EmployeeCompany/Default:123" /><br>
</Objects><br>
We need to parse the company ID value **123** out of the response data and save it for later use.

## Getting a Workflow Template

Employees are associated with workflow so a new employee requires a workflow template to be assigned. For this example we need to find the default workflow template and use its ID to populate the Employee instance's workflow template field. We can retrieve the available workflow templates for an entity using the [Retrieve](data.html#Retrieve) call.

### Sample Request

GET /API/2.0/Data/Global/WorkflowTemplates/Employee?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ==&take=1&where=IsDefault='True' HTTP/1.1<br>

### Sample Response

HTTP/1.1 200 OK<br>
<Objects><br>
<Object Token="Global/WorkflowTemplates/Employee:45116" /><br>
</Objects><br>
We need to parse the workflow template ID of **45116** and save it for later user.

## Getting an Employee Profile

Employees can be associated with multiple employee profiles. We want to add the employee to a manual profile to grant them access to a specific set of modules. We need to retrieve ID of the employee profile to which we want to add the user. In this example, we are using a call [Retrieve](data.html#Retrieve) to find the profile called "Internal Medicine".

### Sample Request

GET /API/2.0/Data/EmployeeManagement/EmployeeProfile/Default?token=/wEFKnpvbmRhfDY1YzJiNTFhLTFhYTMtNGYzZC05YjFhLWY0Njk0NmI2YWU5YQ==&take=1&where=Name='Internal Medicine' HTTP/1.1<br>

### Sample Response

HTTP/1.1 200 OK<br>
<Objects><br>
<Object Token="EmployeeManagement/EmployeeProfile/Default:52" /><br>
</Objects><br>
We need to parse the response and find the instance ID of **52** and save it for later user.

## Inserting the Employee Instance

Once we have retrieved all of the IDs for data we want to associated with the new employee we can insert the Employee instance.
            We include the job title, division, company, workflow template and employee profile we saved from earlier in the request body.  Because an employee's profile is multi-value, we use the keyword "Add" instead of "Set" to associate the selected profile to the new employee.

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
<Field Token="JobTitleId"><br>
<Value action="Set">Lookup/Employee/JobTitleId:19430</Value><br>
</Field><br>
<Field Token="Company"><br>
<Value action="Set">EmployeeManagement/EmployeeCompany/Default:123</Value><br>
</Field><br>
<Field Token="PrimaryDivision"><br>
<Value action="Set">EmployeeManagement/EmployeeDivision/Default:89</Value><br>
</Field><br>
<Field Token="TimeZoneId"><br>
<Value action="Set">-6</Value><br>
</Field><br>
<Field Token="WorkflowTemplate"><br>
<Value action="Set">Global/WorkflowTemplates/Employee:45116</Value><br>
</Field><br>
<Field Token="Profiles"><br>
<Value action="Add">EmployeeManagement/EmployeeProfile/Default:52</Value><br>
</Field><br>
<Field Token="UserName"><br>
<Value action="Set">NewUserName</Value><br>
</Field><br>
<Field Token="Password"><br>
<Value action="Set">NewPassword</Value><br>
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
<Objects><br>
<Object Token="EmployeeManagement/Employee/Default:10325" /><br>
</Objects><br>
This employee has now been created and should be able to login to the application using the given username and password.
