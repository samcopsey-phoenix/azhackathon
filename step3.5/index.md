# Deploy a Linux Application to your WebApp

## Objective:
In this step, we will follow a guide to upload a Python web application to your Azure Web App.

#### What is Python?
Python is a popular programming language known for its simplicity and versatility. It is widely used for web development, data analysis, artificial intelligence, and more.

#### What is Git?
Git is a version control system that helps you track changes to your code and collaborate with others. It allows you to manage your code efficiently and deploy it to various environments.

#### Steps:

1. **Sample Application:**
   - First, you'll get a sample Python application that you will upload to your web app. The sample application is a simple web application built using the Django framework.

2. **Set up your development environment:**
   - You need to install Python and Git on your computer if you don't have them already.
   - Use Windows Package Manager (winget) to install both:
     - Open PowerShell as an administrator.
     - Run the following commands to install Python and Git:
       ```powershell
        winget install -e --id Python.Python.3.12
        winget install -e --id Git.Git
        winget install -e --id Microsoft.AzureCLI
       ```

3. **Clone the sample application:**
   - Open a terminal or command prompt.
   - Run the following command to clone the sample application from GitHub:
     ```bash
     git clone https://github.com/Azure-Samples/msdocs-python-django-webapp-quickstart
     cd djangoapp
     ```

4. **Deploy the sample application to Azure:**
   - Use the Azure CLI to deploy your application.
   - Open a terminal or command prompt in the root of your project folder.
   - Run the following commands to deploy the app:
     ```bash
     az webapp deploy --resource-group <resource-group-name> --name <webapp-name> --src-path .
     ```
   - Replace `<your-app-name>` with the name of your web app and `<your-resource-group>` with the name of your resource group.

5. **Access your deployed app:**
   - Once the deployment is complete, you can access your web application by navigating to the URL provided by Azure.

#### Bonus Step
You can stream your applications logs directly to the CLI by following these steps. Log streaming can be extermely useful for your development stage to see what your application is doing and it can also help you troubleshoot any issues the application may be experiencing

1. Using your open AzCLI instance run the following command:
    ```powershell
     az webapp log config --web-server-logging 'filesystem' --name <webapp-name> --resource-group <resource-group-name>
    ```
    - Replace `<your-app-name>` with the name of your web app and `<your-resource-group>` with the name of your resource group.

2. Run the following command to strat streaming the logs:
    ```powershell
     az webapp log tail --name <webapp-name> --resource-group <resource-group-name>
    ```
    - Replace `<your-app-name>` with the name of your web app and `<your-resource-group>` with the name of your resource group.
    - Now try interacting with your webapp to see the logs entries start streaming. Try refreshing the page and entering and submitting your name and seeing what happens.

## Helpful Resources:
- [Azure Documentation](https://docs.microsoft.com/en-us/azure/)
- [Azure App Service Documentation](https://docs.microsoft.com/en-us/azure/app-service/)
- [Quickstart: Create a Python web app - Azure App Service](https://learn.microsoft.com/en-us/azure/app-service/quickstart-python?tabs=django%2Cwindows%2Cazure-cli%2Clocal-git-deploy%2Cdeploy-instructions-azportal%2Cterminal-bash%2Cdeploy-instructions-zip-azcli#1---sample-application)