# Azure Role-Based Access Control (RBAC) Project Documentation

## Project Overview

This project aims to configure and test user roles in Azure to understand the principles of Azure Role-Based Access Control (RBAC). We created two users with different roles to observe their permissions and limitations within an Azure environment. This documentation outlines the steps taken, user configurations, and the outcomes of the tests conducted.

## Objectives

- Create two users in Microsoft Entra ID with different roles.
- Assign Azure RBAC roles to demonstrate permissions.
- Test the capabilities of each user to verify their assigned roles.

## Users Created

### User1: Reader Role
- **Role in Azure**: Reader
- **Role in Microsoft Entra ID**: User Administrator
- **Capabilities**:
  - Can view resources and their properties.
  - Can access Azure Activity Logs and metrics.
  - Cannot create, modify, or delete resources.

### User2: Contributor Role
- **Role in Azure**: Contributor
- **Role in Microsoft Entra ID**: Conditional Access Administrator
- **Capabilities**:
  - Can create, modify, and delete resources.
  - Can access and update resource metrics and logs.
  - Cannot manage user roles or permissions.

## Steps Undertaken

### 1. User Creation in Microsoft Entra ID
- Created two users:
  - **User1**: Assigned the **User Administrator** role.
  - **User2**: Assigned the **Conditional Access Administrator** role.
- Both users were successfully created and are visible in both Microsoft Entra ID and Azure.

### 2. Assigning Azure RBAC Roles
- **User1** was assigned the **Reader** role at the Resource Group level.
- **User2** was assigned the **Contributor** role at the Resource Group level.

### 3. Testing User Permissions

#### Testing with User1 (Reader Role)
- **Logged in as User1**:
  - Accessed the Azure Portal and navigated to the Resource Group.
  - Successfully viewed all resources within the Resource Group, including properties and configurations.
  - Accessed the Activity Log and could view logs of actions taken on resources.
  - **Attempted to create or delete a resource**:
    - **Outcome**: User1 was **not allowed** to perform these actions, confirming the limitations of the Reader role.

#### Testing with User2 (Contributor Role)
- **Logged in as User2**:
  - Accessed the Azure Portal and navigated to the Resource Group.
  - Successfully viewed all resources and properties.
  - **Attempted to create a new resource** (e.g., a virtual machine):
    - **Outcome**: User2 was **allowed** to create resources, demonstrating the capabilities of the Contributor role.
  - **Attempted to delete a resource**:
    - **Outcome**: User2 was also **allowed** to delete resources, confirming their permissions.

## Conclusion
The project successfully demonstrated the differences in capabilities between the Reader and Contributor roles in Azure RBAC. User1 was limited to viewing resources and logs, while User2 had full permissions to manage resources within the Resource Group.

### Next Steps
- Explore additional Azure roles and permissions.
- Consider implementing Conditional Access policies once a Premium license is acquired.
- Document further tests and findings in future iterations.

### Repository Structure
- `README.md`: Overview of the project.
- `docs/`: Detailed documentation and logs of tests performed.
- `scripts/`: Any scripts or automation related to user management (if applicable).
