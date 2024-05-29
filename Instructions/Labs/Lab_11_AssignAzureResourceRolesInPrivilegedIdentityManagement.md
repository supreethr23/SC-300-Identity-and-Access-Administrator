![image](https://github.com/CloudLabs-MOC/SC-300-Identity-and-Access-Administrator/assets/69720936/7bc6d487-adc7-4449-b967-da73b9761abe)# Lab 11 - Assign Azure resource roles in Privileged Identity Management

## Lab scenario

Microsoft Entra ID Privileged Identity Management (PIM) can manage the built-in Azure resource roles, as well as custom roles, including (but not limited to):

- Owner
- User Access Administrator
- Contributor
- Security Admin
- Security Manager

You need to make a user eligible for an Azure resource role.

## Lab objectives
In this lab, you will complete the following tasks:

- Task 1 - Assign Azure resource roles
- Task 2 - Update or remove an existing resource role assignment

## Estimated time: 10 minutes

## Architecture Diagram

   ![](./media/arch-11.png)

### Exercise 1 - PIM with Azure resources
Using Privileged Identity Management (PIM) with Azure resources enables just-in-time access, auditing, and monitoring of privileged roles to enhance security and compliance.

#### Task 1 - Assign Azure resource roles

1. In **Search resources, services, and docs** search for and then select **Microsoft Entra Privileged Identity Management**.

   ![Screen image displaying the Azure resources discovery page with the subscription and manage resource highlighted](./media/lab11-1.png)

1. on the **Privileged Identity Management | Quick start** page, from the left-hand navigation pane, under **Manage** section, select **Azure resources (1)**.
   ![](./media/lab11-2.png)

1. In the Azure resources – Discovery page, select your **subscription (1)** and then select **Manage resource (2)**.

   ![](./media/g78.png)

1. From the left-hand navigation menu, under **Manage**, select **Roles** to see the list of roles for Azure resources and on the top menu, select + **Add assignments**.

   ![](./media/lab11-6.png)

1. In the **Add assignments** page, for the **Select role** menu, select **API Management Service Contributor.**

   ![](./media/lab11-7.png)

1. Under **Select member(s),** select **No member selected** and Select **Miriam Graham** from your organization that will be assigned the role. Then chose **Select**.
    ![](./media/lab11-8.png)

1. Select **Next >**.

1. On the **Setting** tab, under **Assignment type**, select **Eligible**.

   - **Eligible** assignments require the member of the role to perform an action to use the role. Actions might include performing a multi-factor authentication (MFA) check, providing a business justification, or requesting approval from designated approvers.

   - **Active** assignments do not require the member to perform any action to use the role. Members assigned as active have the privileges always assigned to the role.

1. Specify an assignment duration by changing the start and end dates and times.

1. When finished, select **Assign**.

1. After the new role assignment is created, a status notification is displayed.

     > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
     > - Navigate to the Lab Validation Page, from the upper right corner in the lab guide section.
     > - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
     > - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
     > - If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help


#### Task 2 - Update or remove an existing resource role assignment

Follow these steps to update or remove an existing role assignment.

1. Open **Microsoft Entra Privileged Identity Management**.

2. Select **Azure resources** from the left navigation pane.

3. Select the subscription you want to manage and click on **Manage Resources** to open its overview page.

4. From the left-hand navigation pane, under **Manage**, select **Assignments**.

   ![](./media/lab11-9.png)

6. On the **Eligible assignments** tab, in the Action column, review the available options, and select it.

7. Select **Remove**.
   ![](./media/lab11-10.png)

### Review
In this lab, you have completed:
- Assigned Azure resource roles
- Updated or removed an existing resource role assignment

### You have successfully completed the lab
