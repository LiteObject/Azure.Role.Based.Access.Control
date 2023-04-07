# Azure Role Based Access Control
* Role assignment = Security Principal + Role Definition + Scope

* Security Principals (Who)
  * User
  * Group
    * A collection of users.
  * Service Principal
	* Grant applications access resources.
  * Managed Identity
	* Provide an identity for applications to use when connected to resources that support Azure AD authentication
	* A managed identity is actually just a special type of Service Principal

* Role Definitions (What)
  * A collection of permission
  * Lists the operatons that can be performed
  * Effective Permission = Actions - NotActions
  * Operations
    * {Company}.{ProviderName}/{resourceType}/{action}
      * e.g. Microsoft.CostManagement/export/*
    * Actions
      * \*
      * Read
      * Write
      * Action (Example: Restart a VM)
    * Management Operations
      * Specified in the Actions and NotActions properties of a role definition
	  * Example: Managing access to storage account, creating/updating/deleting blob container, or deleting a resource group
      * Not same as Data Access
    * Data Operations
      * Specified in the DataAction and NotDataAction properties of a role definition
      * Example: Retrieve a list of blobs, write to a blob, reading messages on a queue

    * ![Role definition](/images/rbac-role-definition.png)

    * Builr-in Roles
      * Owner
        * Full access
	      * Manages everything including access to resources
        * Ability to assign roles in Azure RBAC
      * Contributor
        * Manages everything except access to the resources
        * Does not have ability to assign roles in Azure RBAC
      * Reader
        * Read-only access to everything
      * User Access Administrator
        * Manage user access to resources
      * [For more RBAC...](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles)

* Scope (Where)
  * The set of resources that access appliies to
  * Four levels of scope:
  * ![Four levels of scope](/images/rbac-scope.png)

## Built-in Azure RBAC Roles
* Owner
  * Full access
  * Manages everything including access to resources
  * Ability to assign roles in Azure RBAC
* Contributor
  * Manages everything except access to the resources
  * Does not have ability to assign roles in Azure RBAC
* Reader
  * Read-only access to everything
* User Access Administrator
  * Manage user access to resources
* [For more RBAC...](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles)

![image](https://user-images.githubusercontent.com/10944397/230610712-b094a869-a933-4952-bd91-39f39b300f3f.png)

* Deny Assignments
  * Block users from performing specific actions
  * Cannot be created directly by users
  * Created by Azure Blueprints and Azure managed apps
* Azure AD roles only grant access to Azure AD resources, NOT to Azure resources
  * Except AD Global Administrator who can be elevated to access all subscriptions and management groups within the tenant
* Assign roles to groups rather than to users 
  * This reduces the number of role assignments
  * This makes managing and auditing a lot simpler 

---
## Links
* [What is Azure role-based access control (Azure RBAC)?](https://learn.microsoft.com/en-us/azure/role-based-access-control/overview)

