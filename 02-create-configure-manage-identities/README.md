# Create Configure and Manage Identities in Azure

## Goal

The goal of this exercise was to understand how user creation, grouping, licensing and managment works in Microsoft Entra ID (Azure Active Directory). This included assigning licenses directly to users and seeing how licensing impacts access to Microsoft services.

---

## Exercise: Users, Groups, Licensing (Conceptual), Deleting and Restoring users

### User and Group Creation

To begin working with identity and access management, I created two users within Microsoft Entra ID.

The first user, **Admin Lab**, was created to act as an internal account with administrative privileges. This was necessary because my original account (signed in with Gmail) was an external user (`#EXT#`) and did not have full control over tenant resources. The Admin Lab account was intended to be used as a Global Administrator for managing users, groups, and licensing.

The second user, **Chris Green**, was created as a standard user to simulate a typical employee within an organization.

After setting up users, I created a **security group** called **Marketing**. This group represents a department-based grouping that can be used for access control and license assignment at scale.

- **Admin Lab** and my external account were assigned as **group owners**
- **Chris Green** was added as a **member** of the group

This setup reflects a common real-world structure where administrators manage groups, and users inherit access and configurations through group membership.

---

### Licensing (Conceptual Implementation)

The next step in the exercise involved assigning a license to the Marketing group, which would automatically apply to all members (in this case, Chris Green).

Due to limitations in my lab environment (no Microsoft Entra ID Premium licensing or Microsoft 365 licenses available), this step could not be completed directly. However, the process was reviewed and understood conceptually.

If licenses were available, the assignment would be performed through the Microsoft 365 admin center by:

- Navigating to **Billing -> Licenses**
- Selecting an available license
- Switching to the **Groups** tab within the license
- Assigning the license to the **Marketing** group
- Confirming the assignment and verifying that members inherit the license

---

### Delete and Restore User
 
In the next step, I worked with the user lifecycle by deleting and restoring a user account within Microsoft Entra ID.

The user **Chris Green** was deleted from the **Users (All users)** page. This simulates a real-world scenario where a user may leave the organization or no longer require access.

After deletion, I verified that the account was not permanently removed by navigating to the **Deleted users** tab, where Chris Green appeared. This confirmed that the account was in a soft-deleted state and could still be recovered.

I then restored the user from the **Deleted users** section. Once restored, I confirmed that Chris Green reappeared in the **All users** list with the account intact.

---
