# Creating an Azure User Account

## Objective:
Get hands-on experience with Azure by setting up a user account.

## Steps:

1. **Go to the [Azure Portal](https://portal.azure.com) and sign in with your account provided by the proctor.**

2. **Use the search menu to find and go to Entra ID.**
   - From the left-hand menu click Users

   ![Entra ID](../pics/entrahomepage.png)

3. **Click New User and then Create new user**
    - Give your user a name and a display name 
    - Click next and fill in as many fields as you want 
    - On the assignments page leave it blank and click next 
    - At Review + create click create

    ![New User](../pics/newusers.png)

## Bonus Step: Creating an Entra User with PowerShell

### Objective:
Learn how to create a new user in Entra ID using PowerShell.

### Steps:

1. **Install the AzureAD module for PowerShell:**
    - Open PowerShell as an administrator.
    - Run the following command to install the AzureAD module:
    ```powershell
    Install-Module -Name AzureAD
    ```

2. **Connect to Azure AD:**
    - Run the following command and sign in with your Azure account:
    ```powershell
    Connect-AzureAD
    ```

3. **Create a new user:**
    - Use the following script to create a new user. Replace the placeholder values with the actual user details.
    ```powershell
    $PasswordProfile = New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
    $PasswordProfile.Password = "YourSecurePassword123"

    New-AzureADUser -DisplayName "John Doe" `
                    -PasswordProfile $PasswordProfile `
                    -UserPrincipalName "johndoe@yourdomain.onmicrosoft.com" `
                    -AccountEnabled $true `
                    -MailNickName "johndoe"
    ```

    - Replace the following values:
      - `"YourSecurePassword123"` with a secure password.
      - `"John Doe"` with the display name of the user.
      - `"johndoe@yourdomain.onmicrosoft.com"` with the user's principal name (UPN).
      - `"johndoe"` with a mail nickname.

### Helpful Resources:
- [Azure AD PowerShell Documentation](https://docs.microsoft.com/en-us/powershell/azure/new-azureaduser?view=azureadps-2.0)
- [PowerShell Scripting](https://docs.microsoft.com/en-us/powershell/scripting/overview?view=powershell-7.1)

## Exploration:
Take a few minutes to navigate through the Azure portal. Familiarize yourself with the dashboard, menus, and available services.

## Helpful Resources:
- [Azure Documentation](https://docs.microsoft.com/en-us/azure/)
- [Azure YouTube Channel](https://www.youtube.com/user/windowsazure)

