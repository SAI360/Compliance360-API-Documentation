# API Documentation

## Common Uses

* Employee Import. Create or Update one or more C360 Employees. See the following sample code for the most efficient manner of doing this. [Compliance 360 Import (batch import)](https://github.com/SAIGlobal/Compliance360-Import)
* Incident Import. Create or Update one or more C360 Incidents. See the following sample code for the most efficient manner of doing this. [Compliance 360 Import (batch import)](https://github.com/SAIGlobal/Compliance360-Import)

## API Support
If you are having a problem with a specific call returning unexpected results, contact SAI30 Support by sending an email to support@sai360.com.
You must provide the following information for your question to be researhced;
* The specific call and arguments being made, redacted of any confidential customer information, such as passwords, and for PHI/PII data.
* What results are being returned.
* What results you expected to be returned.
Please note that without this information, your question cannot be addressed by our technical staff.

## Documentation Organization

The Compliance 360 API uses the GET verb to retrieve information and the POST verb to insert, update and delete information.

The API sources are split into five distinct categories. All API resources have a version as part of the URL which determines which version of the API to use. API versions do not correspond to releases of the Compliance 360 application and is only incremented to preserve backward compatibility within the API.

| Category | Description |
| --- | --- |
| [Security](Security.md) | Provides the ability to log in with a username and password |
| [Metadata](Meta.md) | Provides metadata information about the entities and fields exposed by the other APIs |
| [Data](Data.md) | Provides CRUD (create, retrieve, update and delete) operations for entities and fields |
| [Raw](Raw.md) | Provides streaming functionality for uploading and downloading files |
| [History](History.md) | Provides retrieve operation for entities that track history |

## Basic Terminology

This documentation makes use of the following terms.

| Term | Note |
| --- | --- |
| Organization | An organization is the top level unit of a Compliance 360 customer. All data is owned by the organization. Data from one organization cannot be seen by another organization. |
| User Context Token | A unique identifier created by the Compliance 360 system when you log in to the API. This token is used to identify an API session. Tokens become invalid if they are not used for a period of time. |
| Metadata | The description of the data that is stored in the Compliance 360 system. Metadata describes entities (collections of fields) and fields (data). |
| Module | A group of related functionality within the Compliance 360 system. Entities are organized into modules and users can be granted access to modules independently or other modules. |
| Component | A collection of types that share similar purpose or functionality.  Components are organized within modules. |
| Type | A collection of metdata fields which, when combined, create the description of a unit of business data. Types are organized within components. |
| Field | The definition of a specific piece of data within an entity or the relation to another entity. Metadata about the field includes the name and type. Metadata fields can also describe relations to other entities. |
| Token | A string that identifies an data object or metadata object in the system.  For example: module token, component token, type token or field token. |
| Entity | An instance of an object with corresponding fields (data). |

## Domain Model

The API exposes a domain model or business domain. The following are some of the modules, components and/or types that may be available.  Note that additional modules/components/types may be found using the metadata API.

| Object | Note |
| --- | --- |
| Division | A unit within the organization which can be used to control what an individual user can see. |
| Attachment | An instance of a file, link or data which is connected to an entity instance. |
| Lookup | Used for entity fields where the metadata describes the type as a list of values. Each value in the list is called a lookup. |
| Folder | A collection of objects similar to the folder structure of a file system. |
| Workflow Template | The definition of the workflow steps, actions, and rules which can be applied to a specific entity type. |
