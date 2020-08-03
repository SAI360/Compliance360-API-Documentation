# REST API Documentation

The Compliance 360 API adheres to [REST](http://en.wikipedia.org/wiki/REST) standards. You reference particular resources by means of the URL path (the part of the URL after the host name). The response from the Compliance 360 API includes IDs that tie related entities together.

You use standard HTTP verbs to access the Compliance 360 API with different methods. To retrieve information, use the GET verb. The POST verb is used to insert, update and delete information.

## Calling REST Resources

REST resources are called using standard HTTP methods. The Compliance 360 REST API sources are split into five distinct categories. All REST API resources have a version as part of the URL which determines which version of the API to use. API versions do not correspond to releases of the Compliance 360 application and is only incremented to preserve backward compatibility within the API.

| Category | URL | Description |
| --- | --- | --- |
| [Security](security.html) | http://secure.compliance360.com/API/2.0/Security/ | Provides the ability to log in with a username and password |
| [Metadata](meta.html) | http://secure.compliance360.com/API/2.0/Meta/ | Provides metadata information about the entities and fields exposed by the other APIs |
| [Data](data.html) | http://secure.compliance360.com/API/2.0/Data/ | Provides CRUD (create, retrieve, update and delete) operations for entities and fields |
| [Raw](raw.html) | http://secure.compliance360.com/API/2.0/Raw/ | Provides streaming functionality for uploading and downloading files |
| [History](history.html) | http://secure.compliance360.com/API/2.0/History/ | Provides retrieve operation for entities that track history |

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
