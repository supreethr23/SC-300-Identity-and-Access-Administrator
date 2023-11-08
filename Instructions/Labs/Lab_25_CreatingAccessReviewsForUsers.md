# Lab 25 - Creating Access Reviews for Internal and External Users  

## Lab scenario

Privileged user access should be regularly reviewed in a similar manner.  Since these are elevated access assignments, the review of these should be done on a consistent basis as identified by the company.  Unused and unnecessary privileged assignments should be removed.  Automated removal should also be configured for users that are no longer with the company or have changed departments within the company.

## Lab Objectives

After completing this lab, you will be able to:
+ Exercise 1 - Create an internal Access review

#### Estimated time: 5 minutes

### Exercise 1 - Create an internal Access review

#### Task 1 - Create a new Access review

1. Select the **Show portal menu** hamburger icon and then select **Microsoft Entra ID**.

    ![Azure portal menu with Azure Active Directory selected](./media/lab25-1.png)

1. From the left-hand navigation pane, select **Groups**.

1. On **Groups | All groups**, select **New group**. Now, follow the instructions for creating the groups, and select **Create**:
   ![Azure portal menu with Azure Active Directory selected](./media/lab25-2.png)

    |Settings|Value|
    |--------|-----|
    |Group type| **Security**|
    |Group name| **Sales and Marketing**|
    |Group description| **Sales and Marketing**|
    |Owners| click on **No owners selected** > Select **ODL_User <inject key="DeploymentID" enableCopy="false"/>** and click on **select**|

1. Return back to **Microsoft Entra ID** page, from the left-hand navigation pane, under the **Manage** section select **Identity Governance**.

1. On **Identity Goverance** blade, under **Access reviews** section, select **Access reviews** from left panel.
     ![Azure portal menu with Azure Active Directory selected](./media/lab25-3.png)

   **Note**: Access reviews can manage the access lifecycle.

1. On **Identity Governance | Access reviews** blade Select **+ New access review**.
   ![Azure portal menu with Azure Active Directory selected](./media/lab25-4.png)

1. In the **Select what to review** box choose **Teams + Groups** from the dropdown and for **Review scope** select **Select Teams + groups**.
    ![Azure portal menu with Azure Active Directory selected](./media/lab25-5.png)

1. For **Groups** select **+Select group(s)**, on **Select group window** select **Sales and Marketing** group from the list, and hit **Select**.

    ![Azure portal menu with Azure Active Directory selected](./media/lab25-6.png)
   
1. Back on **Access review**, set the **Scope** to **All users** and select **Next: Reviews** option for move forward in the wizard.
   ![Azure portal menu with Azure Active Directory selected](./media/lab25-7.png)

1. The next step is to determine the reviewers. These reviewers can be the member themselves to do a self-review or can be assigned to supervisors if reviewing access for an entire department. You can also set the action when a reviewer does not respond to automatically remove that privileged access from the member.

1. On the **Reviews** page, follow the instruction, and select **Next: Settings**:

    |Settings|Value|
    |--------|-----|
    |Select reviewers| **Selected user(s) or group(s)**|
    |Users or groups| Click on **+ Select reviewers** and select **ODL_User <inject key="DeploymentID" enableCopy="false"/>**|
    |**Specify recurrence of review**| 
    |**Duration in days**| **Keep it as default**|
    |Review recurrence| **Select the options of your choice**|
    |Start date| **Select the options of your choice**|
    
1. The advanced settings allow you to put a message as part of the review. On **Settings** page, keep it as default.

1. Select **Next: Review and Create** to finalize the access review.

1. On the **Review and Create** tab enter **SC300 Access Review Test** for Review name.

  ![Azure portal menu with Azure Active Directory selected](./media/lab25-8.png)

1. Select **Create**.

1. Back on **Identity Governance | Access reviews** page refresh page and the access review list will populate with the roles and owners of the reviews.

1. Members that are being reviewed will receive an email when the review is initiated.

1. Selecting an access review of one of the roles will provide status on these access reviews.

    > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
   > - Navigate to the Lab Validation Page, from the upper right corner in the lab guide section.
   > - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
   > - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
   > - If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help you out.

## Review

In this lab you have completed the following tasks:
- Created an internal Access review.

## You have successfully completed the lab
