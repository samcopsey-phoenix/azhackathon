# Understanding Storage in Azure

## Objective:
Learn about Azure storage options and how to use them.

## Describe Azure Storage

<iframe width="560" height="315" src="https://www.microsoft.com/en-us/videoplayer/embed/RE4MAbS?postJsllMsg=true" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

   A storage account provides a unique namespace for your Azure Storage data that's accessible from anywhere in the world over HTTP or HTTPS. Data in this account is secure, highly available, durable, and massively scalable.

   When you create your storage account, you’ll start by picking the storage account type. The type of account determines the storage services and redundancy options and has an impact on the use cases. Below is a list of redundancy options that will be covered later in this module:

   Locally redundant storage (LRS)
   Geo-redundant storage (GRS)
   Read-access geo-redundant storage (RA-GRS)
   Zone-redundant storage (ZRS)
   Geo-zone-redundant storage (GZRS)
   Read-access geo-zone-redundant storage (RA-GZRS)

## Describe redundancy 

   Azure Storage always stores multiple copies of your data so that it's protected from planned and unplanned events such as transient hardware failures, network or power outages, and natural disasters. Redundancy ensures that your storage account meets its availability and durability targets even in the face of failures.

   When deciding which redundancy option is best for your scenario, consider the tradeoffs between lower costs and higher availability. The factors that help determine which redundancy option you should choose include:

   How your data is replicated in the primary region.
   Whether your data is replicated to a second region that is geographically distant to the primary region, to protect against regional disasters.
   Whether your application requires read access to the replicated data in the secondary region if the primary region becomes unavailable.
   Redundancy in the primary region
   Data in an Azure Storage account is always replicated three times in the primary region. Azure Storage offers two options for how your data is replicated in the primary region, locally redundant storage (LRS) and zone-redundant storage (ZRS).

   Locally redundant storage
   Locally redundant storage (LRS) replicates your data three times within a single data center in the primary region. LRS provides at least 11 nines of durability (99.999999999%) of objects over a given year.

   ![LRS](../pics/storage1.png)

   LRS is the lowest-cost redundancy option and offers the least durability compared to other options. LRS protects your data against server rack and drive failures. However, if a disaster such as fire or flooding occurs within the data center, all replicas of a storage account using LRS may be lost or unrecoverable. To mitigate this risk, Microsoft recommends using zone-redundant storage (ZRS), geo-redundant storage (GRS), or geo-zone-redundant storage (GZRS).

   Zone-redundant storage
   For Availability Zone-enabled Regions, zone-redundant storage (ZRS) replicates your Azure Storage data synchronously across three Azure availability zones in the primary region. ZRS offers durability for Azure Storage data objects of at least 12 nines (99.9999999999%) over a given year.

   ![ZRS](../pics/storage2.png)

   With ZRS, your data is still accessible for both read and write operations even if a zone becomes unavailable. No remounting of Azure file shares from the connected clients is required. If a zone becomes unavailable, Azure undertakes networking updates, such as DNS repointing. These updates may affect your application if you access data before the updates have completed.

   Microsoft recommends using ZRS in the primary region for scenarios that require high availability. ZRS is also recommended for restricting replication of data within a country or region to meet data governance requirements.

   Redundancy in a secondary region
   For applications requiring high durability, you can choose to additionally copy the data in your storage account to a secondary region that is hundreds of miles away from the primary region. If the data in your storage account is copied to a secondary region, then your data is durable even in the event of a catastrophic failure that prevents the data in the primary region from being recovered.

   When you create a storage account, you select the primary region for the account. The paired secondary region is based on Azure Region Pairs, and can't be changed.

   Azure Storage offers two options for copying your data to a secondary region: geo-redundant storage (GRS) and geo-zone-redundant storage (GZRS). GRS is similar to running LRS in two regions, and GZRS is similar to running ZRS in the primary region and LRS in the secondary region.

   By default, data in the secondary region isn't available for read or write access unless there's a failover to the secondary region. If the primary region becomes unavailable, you can choose to fail over to the secondary region. After the failover has completed, the secondary region becomes the primary region, and you can again read and write data.

   **Important**

   Because data is replicated to the secondary region asynchronously, a failure that affects the primary region may result in data loss if the primary region can't be recovered. The interval between the most recent writes to the primary region and the last write to the secondary region is known as the recovery point objective (RPO). The RPO indicates the point in time to which data can be recovered. Azure Storage typically has an RPO of less than 15 minutes, although there's currently no SLA on how long it takes to replicate data to the secondary region.

   Geo-redundant storage
   GRS copies your data synchronously three times within a single physical location in the primary region using LRS. It then copies your data asynchronously to a single physical location in the secondary region (the region pair) using LRS. GRS offers durability for Azure Storage data objects of at least 16 nines (99.99999999999999%) over a given year.

   ![GRS](../pics/storage3.png)

   Geo-zone-redundant storage
   GZRS combines the high availability provided by redundancy across availability zones with protection from regional outages provided by geo-replication. Data in a GZRS storage account is copied across three Azure availability zones in the primary region (similar to ZRS) and is also replicated to a secondary geographic region, using LRS, for protection from regional disasters. Microsoft recommends using GZRS for applications requiring maximum consistency, durability, and availability, excellent performance, and resilience for disaster recovery.

   ![GZRS](../pics/storage4.png)

   GZRS is designed to provide at least 16 nines (99.99999999999999%) of durability of objects over a given year.

   Read access to data in the secondary region
   Geo-redundant storage (with GRS or GZRS) replicates your data to another physical location in the secondary region to protect against regional outages. However, that data is available to be read only if the customer or Microsoft initiates a failover from the primary to secondary region. However, if you enable read access to the secondary region, your data is always available, even when the primary region is running optimally. For read access to the secondary region, enable read-access geo-redundant storage (RA-GRS) or read-access geo-zone-redundant storage (RA-GZRS).

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
