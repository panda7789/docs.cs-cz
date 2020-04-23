---
title: Ověřování pomocí knihoven Azure pro .NET
description: Ověření do knihoven Azure pro .NET
ms.date: 08/22/2018
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: f6af813cd1423be8784b769b272756b2c8258392
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "82072149"
---
# <a name="authenticate-with-the-azure-libraries-for-net"></a><span data-ttu-id="eb3b3-103">Ověřování pomocí knihoven Azure pro .NET</span><span class="sxs-lookup"><span data-stu-id="eb3b3-103">Authenticate with the Azure Libraries for .NET</span></span>

## <a name="connect-to-services-with-connection-strings"></a><span data-ttu-id="eb3b3-104">Připojení ke službám pomocí připojovacích řetězců</span><span class="sxs-lookup"><span data-stu-id="eb3b3-104">Connect to services with connection strings</span></span>

<span data-ttu-id="eb3b3-105">Většina knihoven služeb Azure vyžaduje připojovací řetězec nebo klíče pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="eb3b3-105">Most Azure service libraries require a connection string or keys for authentication.</span></span> <span data-ttu-id="eb3b3-106">SQL Database například používá standardní připojovací řetězec SQL:</span><span class="sxs-lookup"><span data-stu-id="eb3b3-106">For example, SQL Database uses a standard SQL connection string:</span></span>

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

<span data-ttu-id="eb3b3-107">Azure Storage používá klíč úložiště:</span><span class="sxs-lookup"><span data-stu-id="eb3b3-107">Azure Storage uses a storage key:</span></span>

```csharp
string storageConnectionString = "DefaultEndpointsProtocol=https;"
        + "AccountName=" + storageName
        + ";AccountKey=" + storageKey
        + ";EndpointSuffix=core.windows.net";

var account = CloudStorageAccount.Parse(storageConnectionString);
// Do things with the account here...
```

<span data-ttu-id="eb3b3-108">Připojovací řetězce služby se používají v jiných službách Azure, jako je [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/), [Azure cache pro Redis](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache)a [Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues).</span><span class="sxs-lookup"><span data-stu-id="eb3b3-108">Service connection strings are used in other Azure services like [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/), [Azure Cache for Redis](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache), and [Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues).</span></span> <span data-ttu-id="eb3b3-109">Tyto řetězce můžete získat pomocí Azure Portal, CLI nebo PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="eb3b3-109">You can get those strings using the Azure portal, CLI, or PowerShell.</span></span> <span data-ttu-id="eb3b3-110">Můžete také použít knihovny pro správu Azure pro .NET k dotazování prostředků na vytváření připojovacích řetězců ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="eb3b3-110">You can also use the Azure management libraries for .NET to query resources to build connection strings in your code.</span></span>

<span data-ttu-id="eb3b3-111">Tento fragment kódu používá knihovny pro správu k vytvoření připojovacího řetězce účtu úložiště:</span><span class="sxs-lookup"><span data-stu-id="eb3b3-111">This snippet uses the management libraries to create a storage account connection string:</span></span>

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

<span data-ttu-id="eb3b3-112">Další knihovny vyžadují, aby aplikace využívala [instanční objekt](https://docs.microsoft.com/azure/active-directory/develop/active-directory-application-objects), který umožňuje spuštění aplikace s udělenými přihlašovacími údaji.</span><span class="sxs-lookup"><span data-stu-id="eb3b3-112">Other libraries require your application to run with a [service principal](https://docs.microsoft.com/azure/active-directory/develop/active-directory-application-objects) authorizing the application to run with granted credentials.</span></span> <span data-ttu-id="eb3b3-113">Tato konfigurace je podobná níže uvedenému postupu ověřování na základě objektů pro knihovnu pro správu.</span><span class="sxs-lookup"><span data-stu-id="eb3b3-113">This configuration is similar to the object-based authentication steps for the management library listed below.</span></span>

## <a name="azure-management-libraries-for-net-authentication"></a><a name="mgmt-auth"></a><span data-ttu-id="eb3b3-114">Knihovny pro správu Azure pro ověřování .NET</span><span class="sxs-lookup"><span data-stu-id="eb3b3-114">Azure management libraries for .NET authentication</span></span>

[!include[Create service principal](../includes/create-sp.md)]

<span data-ttu-id="eb3b3-115">Nyní, když je objekt služby vytvořen, jsou k dispozici dvě možnosti pro ověření objektu služby pro vytváření a správu prostředků.</span><span class="sxs-lookup"><span data-stu-id="eb3b3-115">Now that the service principal is created, two options are available to authenticate to the service principal to create and manage resources.</span></span>

<span data-ttu-id="eb3b3-116">Pro obě možnosti budete muset do svého projektu přidat následující balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="eb3b3-116">For both options you will need to add the following NuGet packages to your project.</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Fluent
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="authenticate-with-token-credentials"></a><span data-ttu-id="eb3b3-117">Ověřování pomocí přihlašovacích údajů tokenu</span><span class="sxs-lookup"><span data-stu-id="eb3b3-117">Authenticate with token credentials</span></span>

<span data-ttu-id="eb3b3-118">První metodou je vytvořit objekt přihlašovacích údajů tokenu v kódu.</span><span class="sxs-lookup"><span data-stu-id="eb3b3-118">The first method is to build the token credential object in code.</span></span> <span data-ttu-id="eb3b3-119">Přihlašovací údaje byste měli bezpečně ukládat do konfiguračního souboru, registru nebo úložiště klíčů Azure.</span><span class="sxs-lookup"><span data-stu-id="eb3b3-119">You should store the credentials securely in a configuration file, the registry, or Azure KeyVault.</span></span>

```csharp
var credentials = SdkContext.AzureCredentialsFactory
    .FromServicePrincipal(clientId,
    clientSecret,
    tenantId,
    AzureEnvironment.AzureGlobalCloud);
```

<span data-ttu-id="eb3b3-120">Při vytváření instančního objektu použijte hodnoty *ClientID*, *clientSecret*a *tenantId* z výstupu JSON.</span><span class="sxs-lookup"><span data-stu-id="eb3b3-120">Use the *clientId*, *clientSecret*, and *tenantId* values from the JSON output when you created the service principal.</span></span>

<span data-ttu-id="eb3b3-121">Pak vytvořte objekt vstupního bodu `Azure` , abyste mohli začít pracovat s rozhraním API:</span><span class="sxs-lookup"><span data-stu-id="eb3b3-121">Then create the entry point `Azure` object to start working with the API:</span></span>

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

### <a name="file-based-authentication"></a><a name="mgmt-file"></a><span data-ttu-id="eb3b3-122">Ověřování na základě souborů</span><span class="sxs-lookup"><span data-stu-id="eb3b3-122">File-based authentication</span></span>

<span data-ttu-id="eb3b3-123">Ověřování na základě souborů umožňuje umístit přihlašovací údaje instančního objektu do souboru prostého textu a zabezpečit ho v systému souborů.</span><span class="sxs-lookup"><span data-stu-id="eb3b3-123">File-based authentication allows you to put the service principal credentials in a plain text file and secure it within the file system.</span></span>

[!include[File-based authentication](../includes/file-based-auth.md)]

<span data-ttu-id="eb3b3-124">Přečtěte si obsah souboru a vytvořte objekt vstupního bodu `Azure` , abyste mohli začít pracovat s rozhraním API:</span><span class="sxs-lookup"><span data-stu-id="eb3b3-124">Read the contents of the file and create the entry point `Azure` object to start working with the API:</span></span>

```csharp
// pull in the location of the authentication properties file from the environment
var credentials = SdkContext.AzureCredentialsFactory
    .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```
