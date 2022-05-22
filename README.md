# Cloud File Storage Manager

Provides complete implementation to handle easily cloud file storage operations like get informations about files, reading, downloadURL generation, file update, file append and delete. Primarily for `Azure (Azure Blob Storage)` right now.

### Configuration

Let's add a section to the `appsettings.json`

```
"AzureStorageSettings": {
    "ConnectionString": "",
    "ContainerName": ""
}
```
In the application, configure this settings part

```cs
services.AddSingleton<ICloudFileStorageManager, AzureCloudFileStorageManager>(services => new AzureCloudFileStorageManager(new AzureCloudFileStorageManagerOptions()
{
    ConnectionString = config.GetSection("AzureStorageSettings").GetValue<string>("ConnectionString"),
    ContainerName = config.GetSection("AzureStorageSettings").GetValue<string>("ContainerName")
}));  

```
