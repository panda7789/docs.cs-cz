---
title: Ověření pomocí knihoven Azure pro rozhraní .NET
description: Ověření do knihoven Azure pro rozhraní .NET
ms.date: 08/22/2018
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: f6af813cd1423be8784b769b272756b2c8258392
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "82072149"
---
# <a name="authenticate-with-the-azure-libraries-for-net"></a>Ověření pomocí knihoven Azure pro rozhraní .NET

## <a name="connect-to-services-with-connection-strings"></a>Připojení ke službám pomocí připojovacích řetězců

Většina knihoven služeb Azure vyžaduje pro ověřování připojovací řetězec nebo klíče. Například sql database používá standardní připojovací řetězec SQL:

```csharp
var builder = new SqlConnectionStringBuilder();
builder.DataSource = "example.database.windows.net";
builder.InitialCatalog = "MyDatabase";
builder.UserID = "sampleuser@example"; // Format user ID as "user@server"
builder.Password = password;
builder.Encrypt = true;
builder.TrustServerCertificate = true;

using (var conn = new SqlConnection(builder.ConnectionString))
{
    conn.Open();
    // Do things with the connection...
    // ...
}
```

Azure Storage používá klíč úložiště:

```csharp
string storageConnectionString = "DefaultEndpointsProtocol=https;"
        + "AccountName=" + storageName
        + ";AccountKey=" + storageKey
        + ";EndpointSuffix=core.windows.net";

var account = CloudStorageAccount.Parse(storageConnectionString);
// Do things with the account here...
```

Připojovací řetězce služby se používají v jiných službách Azure, jako je [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/), [Azure Cache for Redis](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache)a [Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues). Tyto řetězce můžete získat pomocí portálu Azure, CLI nebo PowerShellu. Knihovny správy Azure pro rozhraní .NET můžete také použít k dotazování prostředků k vytvoření připojovacích řetězců ve vašem kódu.

Tento fragment fragmentpoužívá knihovny správy k vytvoření připojovacího řetězce účtu úložiště:

```csharp
// Get a storage account
var storage = azure.StorageAccounts.GetByResourceGroup("myResourceGroup", "myStorageAccount");

// Extract the keys
var storageKeys = storage.GetKeys();

// Build the connection string
string storageConnectionString = "DefaultEndpointsProtocol=https;"
        + "AccountName=" + storage.Name
        + ";AccountKey=" + storageKeys[0].Value
        + ";EndpointSuffix=core.windows.net";

// Connect
var account = CloudStorageAccount.Parse(storageConnectionString);

// Do things with the account here...
```

Další knihovny vyžadují, aby aplikace využívala [instanční objekt](https://docs.microsoft.com/azure/active-directory/develop/active-directory-application-objects), který umožňuje spuštění aplikace s udělenými přihlašovacími údaji. Tato konfigurace je podobná níže uvedenému postupu ověřování na základě objektů pro knihovnu pro správu.

## <a name="azure-management-libraries-for-net-authentication"></a><a name="mgmt-auth"></a>Knihovny správy Azure pro ověřování .NET

[!include[Create service principal](../includes/create-sp.md)]

Nyní, když je vytvořen instanční objekt, jsou k dispozici dvě možnosti k ověření instančního objektu pro vytvoření a správu prostředků.

Pro obě možnosti budete muset přidat následující balíčky NuGet do projektu.

```powershell
Install-Package Microsoft.Azure.Management.Fluent
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="authenticate-with-token-credentials"></a>Ověření pomocí pověření tokenu

První metodou je sestavení objektu pověření tokenu v kódu. Pověření byste měli bezpečně ukládat do konfiguračního souboru, registru nebo Azure KeyVault.

```csharp
var credentials = SdkContext.AzureCredentialsFactory
    .FromServicePrincipal(clientId,
    clientSecret,
    tenantId,
    AzureEnvironment.AzureGlobalCloud);
```

Při vytváření instančního objektu použijte hodnoty *clientId*, *clientSecret*a *tenantId* z výstupu JSON.

Potom vytvořte `Azure` objekt vstupního bodu a začněte pracovat s rozhraním API:

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

### <a name="file-based-authentication"></a><a name="mgmt-file"></a>Ověřování založené na souborech

Ověřování založené na souborech umožňuje umístit pověření zaregistrovaný chod do souboru ve formátu prostého textu a zabezpečit je v systému souborů.

[!include[File-based authentication](../includes/file-based-auth.md)]

Přečtěte si obsah souboru a `Azure` vytvořte objekt vstupního bodu, abyste začali pracovat s rozhraním API:

```csharp
// pull in the location of the authentication properties file from the environment
var credentials = SdkContext.AzureCredentialsFactory
    .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```
