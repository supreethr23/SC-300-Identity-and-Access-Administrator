# Lab 22: Create and manage a catalog of resources in Azure AD entitlement management

## Lab scenario

A catalog is a container of resources and access packages. You create a catalog when you want to group related resources and access packages. Whoever creates the catalog becomes the first catalog owner. A catalog owner can add additional catalog owners. You must create and configure a catalog in your organization.

## Lab objectives
In this lab, you will complete the following tasks:

+ Task 1 - Create a catalog
+ Task 2 - Create a groups
+ Task 3 - Add resources to a catalog
+ Task 4 - Add additional catalog owners
+ Task 5 - Edit a catalog
+ Task 6 - Create Access reviews for guest users
+ Task 7 - Delete a catalog

## Estimated time: 15 minutes

## Architecture diagram

### Exercise 1 - Building out resources in Entitlement Management

#### Task 1 - Create a catalog

1. In **Search, resources, services and docs**, search and select for **Microsoft Entra ID**.

    ![Screen image displaying the Azure resources discovery page with the subscription and manage resource highlighted](./media/MicrosoftID.png)

1. Under **Manage** section, select **Identity Governance**.

    ![Screen image displaying the Azure resources discovery page with the subscription and manage resource highlighted](./media/Identitygovernance.png)

1. From the left-hand navigation menu, under **Entitlement management**, select **Catalogs**.

1. On the top menu, select **+ New Catalog**.

    ![Screen image displaying the Identity governance catalog page with the New catalog menu highlighted ](./media/catalog.png)

1. In the New catalog pane, in the **Name** box, enter **Marketing (1)**.

1. In the **Description** box, enter **For marketing department users (2)**. Users will see this information in an access package's details.

1. Under **Enabled**, select **No (3)**.

1. You may choose to enable the catalog for immediate use or disable if you intend to stage it or keep it unavailable until you intend to use it. For this exercise, the catalog does not need to be enabled.

1. Select **Create (4)**.

    ![Screen image displaying the New catalog pan with the Name, Description, Enabled, and Create options highlighted](./media/create.png)

#### Task 2 - Create a groups

1. In **Search, resources, services and docs**, search and select for **Microsoft Entra ID**.

    ![Screen image displaying the Azure resources discovery page with the subscription and manage resource highlighted](./media/MicrosoftID.png)

1. From the left-hand navigation pane, select **Groups**. On **Groups | All groups**, select **New Group**.

1. Now, follow these instruction to create a groups:-

    | Settings | Value |
    | -------- | ------ |
    | Group type | **Security** |
    | Group name | **Retail** |
    | Group description | **Groups and Teams** |

1. Select **Create**.

1. On **Groups | All groups**, select **New Group**.

1. Now, follow these instruction to create a groups:-

    | Settings | Value |
    | -------- | ------ |
    | Group type | **Security** |
    | Group name | **Box** |
    | Group description | **Applications** |

1. Select **Create**.

1. On **Groups | All groups**, select **New Group**.

1. Now, follow these instruction to create a groups:-

    | Settings | Value |
    | -------- | ------ |
    | Group type | **Security** |
    | Group name | **Salesforce** |
    | Group description | **Applications** |

1. Select **Create**.

1. On **Groups | All groups**, select **New Group**.

1. Now, follow these instruction to create a groups:-

    | Settings | Value |
    | -------- | ------ |
    | Group type | **Security** |
    | Group name | **Salesforce** |
    | Group description | **Applications** |

1. Select **Create**.

1. On **Groups | All groups**, select **New Group**.

1. Now, follow these instruction to create a groups:-

    | Settings | Value |
    | -------- | ------ |
    | Group type | **Security** |
    | Group name | **SharePoint sites** |
    | Group description | **SharePoint** |

1. Select **Create**.

#### Task 3 - Add resources to a catalog

To include resources in an access package, the resources must exist in a catalog. The types of resources you can add are groups, applications, and SharePoint Online sites. The groups can be cloud-created Microsoft 365 Groups or cloud-created Azure AD security groups. The applications can be Azure AD enterprise applications, including both SaaS applications and your own applications federated to Azure AD. The sites can be SharePoint Online sites or SharePoint Online site collections.

1. In **Search, resources, services and docs**, search and select for **Microsoft Entra ID**.

    ![Screen image displaying the Azure resources discovery page with the subscription and manage resource highlighted](./media/MicrosoftID.png)

1. Under **Manage** section, select **Identity Governance**.

    ![Screen image displaying the Azure resources discovery page with the subscription and manage resource highlighted](./media/Identitygovernance.png)

1. On the Identity Governance page, select **Catalogs**.

1. In the **Catalogs** list, select **Marketing**.

1. From the left-hand navigation pane, under **Manage**, select **Resources**.

1. On the menu, select + **Add resources**.

1. Select **+ Groups and Teams**.

1. In the Add resources to catalog page, review the available options.  Add the following items: **Box**, **Retail**, **Salesforce**, and **SharePoint sites**.

1. For this exercise, it is okay to choose any resource you may have available.

    ![Add resources to a catalog](./media/resources.png)

1. When finished, Select **Add**. These resources can now be included in access packages within the catalog.

#### Task 4 - Add additional catalog owners

The user that created a catalog becomes the first catalog owner. To delegate management of a catalog, you add users to the catalog owner role. This helps share the catalog management responsibilities.

1. If necessary, in the Azure portal, browse to **Microsoft Entra ID**, from the left-hand navigation pane, select **Identity Governance** and select **Catalogs** and then select **Marketing**.

2. In the Marketing catalog page, from the left-hand navigation pane, select **Roles and administrators (1)**.

3. On the top menu, review the available roles and then select **+ Add catalog owner (2)**.

    ![Screen image displaying the Roles and administrators page for the Marketing catalog](./media/catalog-owner.png)

4. In the Select members pane, select your **Adele Vance** and then select **Select**.

5. Review the newly added role in the Roles and administrators list.

#### Task 5 - Edit a catalog

You can edit the name and description for a catalog. Users see this information in an access package's details.

1. On the Marketing page, from the left-hand navigation pane, select **Overview (1)**.

2. On the top menu, select **Edit**.

3. Review the setting and, under **Properties** > **Enabled**, select **Yes (2)**.

    ![Screen image displaying the properties being enabled.](./media/overview.png)

4. Select **Save (3)**.

#### Task 6 - Create Access reviews for guest users

1. Navigate back to the **Identity Governance**.

1. Access reviews can manage the access lifecycle.  Azure AD Identity Governance provides an overview dashboard showing the status of access reviews. From the left-hand navigation pane, select **Access reviews** under **Access reviews**.

1. Select **+ New access review** to create your guest user access review.  The tile will open to configure the access review for guest users.

1. Select **Teams + Groups** for **Select what to review**.

1. Under **Review scope**, select **All Microsoft 365 groups with guest users**

1. Under **Scope**, select **Guest users only**.

1. Select **Next: Reviews**.

1. The next tile is where you configure who reviews and approves access, how often access will be reviewed, and when access will expire.

1. Under **Select reviewers**, select **Group owners** as these reviewers. 

    >**Note**: Guest users should not be allowed to review their own access as a good identity governance practice.

1. Enter a **Duration (in days)**, default is 3, choose a **Review recurrence** and **Start date** for the review.

1. Select **Next: Settings** and configure the settings for how the review will take place and what happens when the guest user responds or does not respond.  A good practice is to select **Auto apply results to resource** and select **Remove access** for **If reviewers don't respond**. 

1. Select **Next: Review + create**, and select **Create** to create the new **Access review**.


#### Task 7 - Delete a catalog

You can delete a catalog, but only if it does not have any access packages.

1. In the Marketing catalog’s Overview page, on the top menu, select Delete.

2. In the Delete dialog box, review the information and then select **No**.

    **Note** - we are keeping the catalog for use in the next lab.

### Review
In this lab, you have completed:
- Created a catalog
- Create a groups
- Added resources to a catalog
- Added additional catalog owners
- Edited a catalog
- Created Access reviews for guest users
- Deleted a catalog

### You have successfully completed the lab