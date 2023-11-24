# Lab 18 - Defender for Cloud Apps Access and Session Policies

## Lab scenario

Microsoft Defender for Cloud Apps  allows us to create additional Conditional Access policies specific to the cloud apps that we are monitoring.  Creating these policies can be done from within the Control menu within the Microsoft Defender for Cloud Apps  portal.

## Lab objectives

After completing this lab, you will be able to complete the following exercises:

+ Exercise 1 - Create and test the Conditional Access App Contol policy
+ Exercise 2 - Setup alerts in Microsoft Defender for Cloud Apps

## Estimated time: 30 minutes

## Architecture Diagram

   ![](./media/arch18.png)

### Exercise 1 - Create and test the Conditional Access App Contol policy
  
  In this lab, you will learn to create and test a Conditional Access App Control policy. 

#### Task 1 - Confirm that PradeepG has unconditional access to FORMS

1. Open a Microsoft Edge browser, launch a new **InPrivate** browsing window, and browse to [https://forms.microsoft.com](https://forms.microsoft.com).

   ![Screen image displaying the Azure resources discovery page with the subscription and manage resource highlighted](./media/signin.png)

1. Select **Sign in** and log in as Pradeep Gupta.
    
   | **Setting**| **Value**|
   | :--- | :--- |
   | Username | pradeep.gupta@`your domain name.com`|
   | Password| Enter the password for Pradeep Gupta|

4. To find the username for **Pradeep Gupta**, login to the Azure portal using the credentials given in the **Environment Details** page navigate to the Users section of the Microsoft Entra ID, and copy the user name.

5. From the Microsoft Entra ID **Users** section, click on **Pradeep Gupta** user, and from the top navigation pane click on **Reset Password** and copy the temporary password and login  and reset the password to **Pa55w.rd@123**

    ![Screen image displaying the New Group page with Group type, Group name, Owners, and Members highlighted](./media/pradeep.png)

   >**Note:** Copy the username and password of Pradeep in a notepad file because you will be needing it for further tasks.
    
7. Confirm that Microsoft Forms opens and that you do not get any warning messages.

   >**Note:** You will not have access to Microsft Forms.

8. Close the InPrivate browsing window.

#### Task 2 - Configure Microsoft Entra ID to work with Defender for Cloud Apps

1. Navigate to Azure Portal, in **Search resources, services and docs (1)** search and select for **Microsoft Entra ID (2)**.

   ![Screen image displaying the Azure resources discovery page with the subscription and manage resource highlighted](./media/MicrosoftentraID.png)

2. From the left-hand navigation pane, under **Manage**, select **Security**.

3. From the left-hand navigation pane, under **Protect**, select **Conditional Access**.

4. Select **+ Create new policy**.

5. Enter a policy name, **Monitor Pradeep using Forms**.

6. Under **Users**, select **0 users and groups selected**, under **Include**, select **Select users and groups**, and select **Users and groups**.
Choose the **Pradeep Gupta** account for the lab tenant and select **Select**.

8. Under Target resources, select **No target resources selected**, under **Include**, select **Select apps**,under **Select** choose **None**, and then choose **Microsoft Forms**, and select **Select**. 

9. Under **Access controls**, under **Session**, select **0 controls selected**.

10. Select the **Use Conditional Access App Control** box, select the drop-down and select **Monitor only (Preview)**, and select **Select**.

11. Under **Enable policy**, select **On**, and select **Create**.

#### Task 3 - Log into Forms and validate that conditional access is monitoring

1. Launch a new InPrivate browsing window, and browse to [https://forms.microsoft.com](https://forms.microsoft.com).

2. Select **Sign in** and log in as Pradeep Gupta.

   | **Setting**| **Value**|
   | :--- | :--- |
   | Username | pradeep.gupta@`your domain name.com`|
   | Password| Pa55w.rd@123|
    
   >**Note:** Copy the username for Pradeep from the notepad file as mentioned in the previous task.
   
3. Confirm  that you get a new message as shown below:

   - Access to Microsoft Forms is monitored.
   
     ![Screen image displaying the Azure resources discovery page with the subscription and manage resource highlighted](./media/access.png)

4. Close the InPrivate browsing window.

### Exercise 2 - Setup alerts in Microsoft Defender for Cloud Apps

Registering your application establishes a trust relationship between your app and the Microsoft identity platform. The trust is unidirectional: Your app trusts the Microsoft identity platform—not the other way around.

#### Task 1 - Access Microsoft Defender for Cloud Apps and create Conditional Access App Control

1. Open a new tab, and browse to the [https://security.microsoft.com](https://security.microsoft.com).

   >**Note:** If you get  **Your new endpoint protection home** page close it.

1. From the left-hand navigation pane, scroll to the bottom and select **More resources**.

1. In the **More resources** window, locate and select **Open** under **Microsoft 365 Defender**.  This will take you to the **Microsoft 365 Defender** portal.

1. In the **Microsoft 365 Defender** portal menu, from the left-hand navigation pane, under **Cloud apps** select **Policies** drop-down, and select **Policy management**.

1. Select **+ Create policy**. Select **Access policy**.

1. Enter a name for the policy, **Monitor Microsoft Forms access**.

1. Leave the **Category** as **Access control**.

1. Under **Activities matching all of the following**, select the drop-down for **Intune compliant, Hybrid Azure AD joined** and unselect **Hybrid Azure AD joined**.

   ![Screen image displaying the Azure resources discovery page with the subscription and manage resource highlighted](./media/365defender.png)

1. Select the drop-down for **Select apps**, select **Microsoft Forms**.

1. Leave **Actions** as **Test**.

1. Under **Alerts**, leave **Create an alert...** checked and select **Send alert as email**.

1. Enter and select **<inject key="AzureAdUserEmail"></inject>**.

1. Select **Create** to create the access policy.

#### Task 2 - Log in as Pradeep to Forms to trigger activity

1. Launch a new InPrivate browsing window, and browse to [https://forms.microsoft.com](https://forms.microsoft.com).

1. Select **Sign in** and log in as Pradeep Gupta.

   | **Setting**| **Value**|
   | :--- | :--- |
   | Username | pradeep.gupta@`your domain name.com`|
   | Password| Pa55w.rd@123|
    
   >**Note:** Copy the username for Pradeep from the notepad file as mentioned in the previous task.

1. Confirm  that you get a new message as shown below:

   - Access to Microsoft Forms is monitored.

     ![Screen image displaying the Azure resources discovery page with the subscription and manage resource highlighted](./media/access.png)

1. Close the InPrivate browsing window.

#### Task 3 - Review the Activity in Defender for Cloud Apps

1. Return to the browswer running Microsoft 365 Defender.

2. Refresh the browser to ensure the most recent data is downloaded.

3. From the left-hand navigation pane, under **Cloud apps**, select **Activity log**.

4. Using the **App: filter** pick **Microsoft Forms** from the list.

5. Notice the sign-on records for Pradeep.

   ![Screen image displaying the Azure resources discovery page with the subscription and manage resource highlighted](./media/msforms2.png)

### Review

In this lab, you have completed the following exercises:
- Created and tested the Conditional Access App Contol policy
- Setup alerts in Microsoft Defender for Cloud Apps

### You have successfully completed the lab
