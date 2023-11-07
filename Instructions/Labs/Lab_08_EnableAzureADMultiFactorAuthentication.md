
# Lab 08 - Enable Azure AD multi-factor authentication

## Lab scenario

To improve security in your organization, you've been directed to enable multi-factor authentication for Azure Active Directory.

## Lab Objectives

After completing this lab, you will be able to complete the following exercises:

- Exercise 1 - Review and enable Multi-factor Authentication in Azure
- Exercise 2 - Configure MFA to be required for login

## Architecture Diagram

![Screen image displaying the New Group page with Group type, Group name, Owners, and Members highlighted](./media/arch08.png)

#### Estimated time: 30 minutes

>**IMPORTANT** - A Microsoft Entra ID Premium license is required for this exercise.

### Exercise 1 - Review and enable Multi-factor Authentication in Azure

  In this exercise, you will learn how to  enhance security, and ensure Multi-factor Authentication (MFA) is configured and enabled in your Azure environment, adding an extra layer of protection for your accounts and data.

#### Task 1 - Review Azure Multi-Factor Authentication options

1. In the Azure portal, use the search feature and search for **multi-factor**.

2. In the search results, select **Multi-Factor Authentication**.

3. On the Getting started page, under **Configure**, select **Additional cloud-based MFA settings**.

    ![Screenshot showing MFA options in the dashboard](./media/multifactor1.png)

4. In the new browser page, you can see the MFA options for Azure users and service settings.

    ![Screenshot showing MFA configuration](./media/mfa-settings.png)

5. This is where you would select the supported authentication methods, in the screen above, all of them are selected.

6. You can also enable or disable app passwords here, which allow users to create unique account passwords for apps that don't support multi-factor authentication. This feature lets the user authenticate with their Microsoft Entra ID identity using a different password specific to that app.

#### Task 2 - Setup conditional access rules for MFA for Delia Dennis

Next, let's examine how to set up Conditional Access policy rules that would enforce MFA for guest users accessing specific apps on your network.

1. Switch back to the Azure portal, search for and select **Microsoft Entra ID**, then  navigate to **Security** under the Manage section, and then subsequently select **Conditional access**.

2. From the menu, click on **Create new policy**.

    ![creenshot highlighting the New Policy button in the Azure portal](./media/createnewpolicy1.png)

3. Name your policy, for example **MFA_for_Delia**

4. Under Assignments:

    - Select **0 users and groups selected**  
    - On the right side screen, select **Select users and groups** check box to configure.
    - Check **Users and groups** (available users will be populated to the right)
    - Choose **Delia Dennis** from the list of users then choose **Select** button.

5. Under **Target Resources** click on **No target resources selected**

   - In the dropdown, make sure **Cloud apps** is selected.
   - Under Include, mark **All cloud apps** and note the warning the pops up about possibly locking yourself out. 
   - Now under Include, change your choice to **Select apps** item and then under Select click on **None**.
   - In the newly opened dialog, choose **Office 365**.
   - Choose **Select**.

6. Review the Conditions section.

   - Under **Conditions** click on **0 conditions selected** then under **Locations** click on **Not Configured** and then under  **Configure** toggle  it to **Yes**  and ensure that under **Include** ,**Any location** is selected.

      ![Screenshot highlighting the New Policy button in the Azure portal](./media/sc-300loc.png)

7. Under **Access Controls** click on  **0 controls selected** and verify **Grant access** is selected.

8. Select the **Require multi-factor authentication** check box to enforce MFA.

9. Ensure that **Require all the selected controls** is selected.

10. Select **Select**.

11. Set **Enable policy** to **On**.

12. Hit **Create** to create the policy.

    ![Screenshot showing the complete Add Policy dialog](./media/policy-complete.png)

13. MFA is now enabled for your selected user and application(s). The next time a guest tries to sign into that app they will be prompted to register for MFA.

     > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
     > - Navigate to the Lab Validation Page, from the upper right corner in the lab guide section.
     > - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
     > - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
     > - If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help

#### Task 3 - Test Delia's login

1. Open a new **InPrivate** browsing window.
2. Connect to https://www.office.com.
3. Select the sign-in option.
4. Enter **DeliaD@** `<<your domain address>>`.

   >**Note:** You can find the username for **Delina** from the Azure portal in the **Microsoft Entra ID** Users section.

5. To find the password, in the Microsoft Entra ID **Users** section, click on **Delia Dennis** user, and from the top navigation pane  click on **Reset Password** and copy the temporary password.

    ![Screen image displaying the New Group page with Group type, Group name, Owners, and Members highlighted](./media/azureaad.png)

6. Sign in with the temporary password
 
   >**Note:** There is a chance that you might get a login failure message with several options on how to proceed.  Select the **Try Again** option in this case.

7. Click on **Next**

8. You can see that because of the Conditional Access rule we created for Delia, MFA is required to launch Office 365 home page.

   ![Screenshot showing the complete Add Policy dialog](./media/mfa.png)

### Exercise 2 - Configure MFA to be required for login

   By enforcing MFA, you significantly reduce the risk of unauthorized access and data breaches, enhancing the overall security of your Azure environment.

#### Task 1 - Configure Azure AD Per-User MFA

Finally, let's look at how to configure MFA for user accounts. This is another way to get to the multi-factor auth settings.

1. Switch back to the **Microsoft Entra ID** dashboard in the Azure portal.

2. Select **Users**.

3. At the top of the Users pane, select **Per-user MFA**.

   ![Screenshot showing the MFA option](./media/mfauuser.png)

4. A new browser tab/window will open with a multi-factor authentication user settings dialog.

   ![Screenshot showing the MFA options](./media/and-users.png)

5. Select **Adele Vance** with a check-mark.
6. Select the **Enable** option under quick steps.
7. Read the notification popup if you get it, then select **enable multi-factor auth** button.
8. Select **Close**.
9. Notice that Adele now has **Enabled** as her MFA status.
10. Close the MFA setting tab.

## Review

In this lab you have completed the following tasks:
- Reviewed and enabled Multi-factor Authentication in Azure
- Configured MFA to be required for login

## You have successfully completed the lab

