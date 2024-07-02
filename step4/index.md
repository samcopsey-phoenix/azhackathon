# Understanding Storage in Azure

## Objective:
Learn about Azure storage options and how to use them.

## Steps:

1. **Navigate to "Storage Accounts" in the Azure portal.**
   - Click on "Create a Resource" and select "Storage Account".

2. **Create a new storage account:**
   - **Name:** Choose a unique name for your storage account.
   - **Region:** Select the region closest to you.
   - **Performance:** Choose "Standard".
   - **Replication:** Select "Locally-redundant storage (LRS)" for this exercise.
   - Click "Review + Create" and then "Create".

3. **Explore Blob storage:**
   - Go to your newly created storage account.
   - Click on "Containers" and then "+ Container" to create a new container.
   - Name your container (e.g., "mycontainer") and set the public access level to "Container (anonymous read access)".

4. **Upload a file to Blob storage:**
   - Inside your container, click "+ Upload" to upload a file from your computer.
   - Select the file and click "Upload".

5. **Retrieve and view the file from Blob storage:**
   - After uploading, you can see the file listed in your container.
   - Click on the file to view its URL, which you can use to access the file from a web browser.

![Azure Blob Storage](https://example.com/azure-blob-storage.png)

## Helpful Resources:
- [Quickstart: Upload, download, and list blobs with the Azure portal](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-quickstart-blobs-portal)
- [Azure Storage Documentation](https://docs.microsoft.com/en-us/azure/storage/)
