# Lab 16 - Using Azure Key Vault for Managed Identities

**Note** - This lab requires an Azure Pass. Please see lab 00 for directions.

## Lab scenario

When you use managed identities for Azure resources, your code can get access tokens to authenticate to resources that support Azure AD authentication.  However, not all Azure services support Azure AD authentication. To use managed identities for Azure resources with those services, store the service credentials in Azure Key Vault, and use the managed identity to access Key Vault to retrieve the credentials.

## Lab objectives
In this lab, you will complete the following tasks:

+ Task 1 - Create a Windows Virtual Machine
+ Task 2 - Create a Key Vault
+ Task 3 - Create a secret
+ Task 4 - Grant access to Key Vault
+ Task 5 - Access data with Key Vault secret with PowerShell

## Estimated time: 20 minutes

## Architecture diagram

### Exercise 1 - Use Azure Key Vault to manage Virtual Machine identities

#### Task 1 - Create a Windows Virtual Machine

1. Select **+ Create a resource**.

    ![Screen image displaying the Azure resources discovery page with the subscription and manage resource highlighted](./media/createaresoruces.png)

1. In **Search services and marketplace**, type and search for **Windows Client (1)**.

1. On the **Marketplace** page, under **Windows Client**, select **Create (2)** drop-down and from the plan dropdown choose **Windows 10 Enterprise N x64 (3)**.

    ![Screen image displaying the Azure resources discovery page with the subscription and manage resource highlighted](./media/windowsclient.png)

1. On the **Create a virtual machine** page, follow the instruction to create a virtual machine, after filling all the details, select **Next : Disks >**:-

    | Settings | Values |
    | -------- | ------ |
    | Resource group | **sc-300-rg-<inject key="DeploymentID" enableCopy="false"/>** |
    | Virtual machine name | **VM-<inject key="DeploymentID" enableCopy="false"/>** |
    | Region | **<inject key="Region" enableCopy="false"/>** |
    | Availbility options | **No infrastructure redundancy required** |
    | Security type | Keep it as default |
    | Image | see all images > Microsoft windows 10 > choose **Select** drop-down > select **Windows 10 Enterprise, version 22H2 - x64 Gen 1** |
    | Size | **see all sizes > Standard_B2s - 2 vcpus, 4 GiB memory** |
    | Username | **azureuser** |
    | Password | **Password@..!!** |
    | Confirm Password | **Password@..!!** |
    | Licensing | check the box |

1.  On disk page, follow the instruction, after this select **Next : Networking >**:-

    | Settings | Values |
    | -------- | ------ |
    | OS disk type | **Standard HDD (locally-redundant storage)** |

1. Select **Next : Management >**.

1. On the **Management** tab, check the box to **Enable system assigned managed identity**.

1. Select **Review + Create**.

1. Select **Create**.

#### Task 2 - Create a Key Vault

1. Select **+ Create a resource**.

    ![Screen image displaying the Azure resources discovery page with the subscription and manage resource highlighted](./media/createaresoruces.png)

1. In **Search services and marketplace**, type and search for **Key Vault**.  

1. Select **Create > Key vault**.

    ![Screen image displaying the Azure resources discovery page with the subscription and manage resource highlighted](./media/keyvault.png)

1. Fill out all required information as shown below. Select **Next**.

    | Settings | Values |
    | -------- | ------ |
    | Resource group | **sc-300-rg-<inject key="DeploymentID" enableCopy="false"/>** |
    | Key vault name | **keyvault-<inject key="DeploymentID" enableCopy="false"/>** |
    | Region | **<inject key="Region" enableCopy="false"/>** |
    | Access Configuration | select the **Vault Access Policy** radio button. |

1. Select **Review + create**.

1. Select **Create**.


#### Task 3 - Create a secret

1. Navigate to your newly created Key Vault.

1. From the left-hand navigation pane, under **Objects**, select **Secrets**.

1. Select **+ Generate/Import**.

1. On the Create a secret page, follow the instruction:-

    | Settings | Values |
    | -------- | ------ |
    | Upload | **Manual** |
    | Name | **secret-<inject key="DeploymentID" enableCopy="false"/>** |
    | Secret value | **123456789** |
    | Enabled | **Yes** |

1. Select **Create** to create the secret.

#### Task 4 - Grant access to Key Vault

1. On the **keyvault-<inject key="DeploymentID" enableCopy="false"/> | Secrets**, from the left-hand navigation pane, select **Access policies**.

1. Select **+ Create**.

1. On the **Create an access policy**, under Configure from template, choose Secret Management from the drop-down. Select **Prinicpal**.

1. On the **Principal** page, in the search field enter the name **VM-<inject key="DeploymentID" enableCopy="false"/>**, and select it. Select **Next**.

1. On the **Application (optional) page**, select **Next**.

1. On the **Review + Create** page, select **Create**.

#### Task 5 - Access data with Key Vault secret with PowerShell

1. In the lab virtual machine, in **Type here to search** search and select for **Windows PowerShell**.  

    ![Screen image displaying the Azure resources discovery page with the subscription and manage resource highlighted](./media/powershell.png)

1. In PowerShell, invoke the web request on the tenant to get the token for the local host in the specific port for the VM.  

    ```
    $Response = Invoke-RestMethod -Uri 'http://169.254.169.254/metadata/identity/oauth2/token?api-version=2018-02-01&resource=https%3A%2F%2Fvault.azure.net' -Method GET -Headers @{Metadata="true"}
    ```

1. Next, extract the access token from the response.  

    ```
    $KeyVaultToken = $Response.access_token
    ```

1. Use PowerShell’s Invoke-WebRequest command to retrieve the secret you created earlier in the Key Vault, passing the access token in the Authorization header.  You’ll need the URL of your Key Vault, which is in the Essentials section of the Overview page of the Key Vault.  Reminder - URI for Key Vault is on the Overview tab.

    ```
    Invoke-RestMethod -Uri https://<your-key-vault-URI>/secrets/<secret-name>?api-version=2016-10-01 -Method GET -Headers @{Authorization="Bearer $KeyVaultToken"}
    ```
1. You should receive a response that looks like the following: 
    ```
    'My Secret' https://mi-lab-vault.vault.azure.net/secrets/mi-test/50644e90b13249b584c44b9f712f2e51 @{enabled=True; created=16…
    ```
1. This secret can be used to authenticate to services that require a name and password.

### Review
In this lab, you have completed:
- Created a Windows Virtual Machine
- Created a Key Vault
- Created a secret
- Granted access to Key Vault
- Accessed data with Key Vault secret with PowerShell

### You have successfully completed the lab