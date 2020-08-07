---
title: Principy ověřování v knihovnách Azure pro .NET
description: Vysvětluje různé způsoby ověřování pomocí sady Azure SDK pro .NET.
ms.date: 06/19/2020
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: e588499a789fc5e7da7eb51009f97090ca75e562
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916614"
---
# <a name="authenticate-with-the-azure-sdk-for-net"></a><span data-ttu-id="e5da7-103">Ověřování pomocí sady Azure SDK pro .NET</span><span class="sxs-lookup"><span data-stu-id="e5da7-103">Authenticate with the Azure SDK for .NET</span></span>

## <a name="recommended-azureidentity"></a><span data-ttu-id="e5da7-104">Doporučené: Azure. identity</span><span class="sxs-lookup"><span data-stu-id="e5da7-104">Recommended: Azure.Identity</span></span>

<span data-ttu-id="e5da7-105">Nejnovější balíčky v sadě Azure SDK pro .NET používají pro ověření, že se používá společný ověřovací balíček `Azure.Identity` .</span><span class="sxs-lookup"><span data-stu-id="e5da7-105">The latest packages in the Azure SDK for .NET use a common authentication package to authenticate, `Azure.Identity`.</span></span> <span data-ttu-id="e5da7-106">Použití `Azure.Identity` se doporučuje u jiných ověřovacích mechanismů popsaných dále v tomto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="e5da7-106">Using `Azure.Identity` is recommended over other authentication mechanisms described later in this document.</span></span> <span data-ttu-id="e5da7-107">Balíčky podporující přihlašovací údaje, které poskytuje, `Azure.Identity` jsou postavené na začátku `Azure.Core` a mají identifikátory balíčků počínaje *Azure.*</span><span class="sxs-lookup"><span data-stu-id="e5da7-107">Packages supporting the credentials provided by `Azure.Identity` are built on top of `Azure.Core` and have package identifiers starting with *Azure.*</span></span> <span data-ttu-id="e5da7-108">[Prohlédněte si seznam balíčků](packages.md) pro inventarizaci balíčků, které používají `Azure.Core` .</span><span class="sxs-lookup"><span data-stu-id="e5da7-108">[See the package list](packages.md) for an inventory of packages that use `Azure.Core`.</span></span>

<span data-ttu-id="e5da7-109">Podrobné pokyny k použití `Azure.Identity` v projektu najdete v dokumentaci ke [službě Azure identity Client pro .NET](/dotnet/api/overview/azure/identity-readme).</span><span class="sxs-lookup"><span data-stu-id="e5da7-109">For complete instructions on using `Azure.Identity` in your project, see the documentation for [Azure Identity client for .NET](/dotnet/api/overview/azure/identity-readme).</span></span>

> [!TIP]
> <span data-ttu-id="e5da7-110">Příklady použití identity Azure ke správě a přístupu k prostředkům Azure najdete v [ukázce Azure identity, Resource Management a Storage](/samples/dotnet/samples/azure-identity-resource-management-storage/) .</span><span class="sxs-lookup"><span data-stu-id="e5da7-110">See the [Azure Identity, Resource Management, and Storage sample](/samples/dotnet/samples/azure-identity-resource-management-storage/) for examples of using Azure Identity to manage and access Azure resources.</span></span>

<span data-ttu-id="e5da7-111">K ověřování pomocí knihoven, které nepodporují Azure. identity, se podívejte na zbývající část tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="e5da7-111">To authenticate with libraries that don't support Azure.Identity, see the rest of this topic.</span></span>

## <a name="access-azure-resources"></a><span data-ttu-id="e5da7-112">Přístup k prostředkům Azure</span><span class="sxs-lookup"><span data-stu-id="e5da7-112">Access Azure resources</span></span>

<span data-ttu-id="e5da7-113">K interakci s prostředky Azure, jako je například načítání tajného klíče z Key Vault nebo ukládání objektu blob do úložiště, mnoho knihoven služeb Azure vyžaduje připojovací řetězec nebo klíče pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="e5da7-113">To interact with Azure resources, such as retrieving a secret from Key Vault or storing a blob in Storage, many Azure service libraries require a connection string or keys for authentication.</span></span> <span data-ttu-id="e5da7-114">SQL Database například používá [standardní připojovací řetězec SQL](https://docs.microsoft.com/azure/azure-sql/database/connect-query-dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="e5da7-114">For example, SQL Database uses a [standard SQL connection string](https://docs.microsoft.com/azure/azure-sql/database/connect-query-dotnet-core).</span></span> <span data-ttu-id="e5da7-115">Připojovací řetězce služby se používají v jiných službách Azure, jako je [CosmosDB](/azure/cosmos-db/), [Azure cache pro Redis](/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache)a [Service Bus](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues).</span><span class="sxs-lookup"><span data-stu-id="e5da7-115">Service connection strings are used in other Azure services like [CosmosDB](/azure/cosmos-db/), [Azure Cache for Redis](/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache), and [Service Bus](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues).</span></span> <span data-ttu-id="e5da7-116">Tyto řetězce můžete získat pomocí Azure Portal, CLI nebo PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="e5da7-116">You can get those strings using the Azure portal, CLI, or PowerShell.</span></span> <span data-ttu-id="e5da7-117">Můžete také použít knihovny pro správu Azure pro .NET k dotazování prostředků na vytváření připojovacích řetězců ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="e5da7-117">You can also use the Azure management libraries for .NET to query resources to build connection strings in your code.</span></span>

<span data-ttu-id="e5da7-118">Metody pro použití připojovacího řetězce se liší podle produktu.</span><span class="sxs-lookup"><span data-stu-id="e5da7-118">The methods for using a connection string vary by product.</span></span> <span data-ttu-id="e5da7-119">[Informace najdete v dokumentaci k produktu Azure](/azure/?product=featured).</span><span class="sxs-lookup"><span data-stu-id="e5da7-119">[Refer to the documentation for your Azure product](/azure/?product=featured).</span></span>

## <a name="manage-azure-resources"></a><span data-ttu-id="e5da7-120">Správa prostředků Azure</span><span class="sxs-lookup"><span data-stu-id="e5da7-120">Manage Azure resources</span></span>

[!include[Create service principal](includes/create-sp.md)]

<span data-ttu-id="e5da7-121">Nyní, když je objekt služby vytvořen, jsou k dispozici dvě možnosti pro ověření objektu služby pro vytváření a správu prostředků.</span><span class="sxs-lookup"><span data-stu-id="e5da7-121">Now that the service principal is created, two options are available to authenticate to the service principal to create and manage resources.</span></span>

<span data-ttu-id="e5da7-122">Pro obě možnosti budete muset do svého projektu přidat následující balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="e5da7-122">For both options you will need to add the following NuGet packages to your project.</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Fluent
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="authenticate-with-token-credentials"></a><span data-ttu-id="e5da7-123">Ověřování pomocí přihlašovacích údajů tokenu</span><span class="sxs-lookup"><span data-stu-id="e5da7-123">Authenticate with token credentials</span></span>

<span data-ttu-id="e5da7-124">První metodou je vytvořit objekt přihlašovacích údajů tokenu v kódu.</span><span class="sxs-lookup"><span data-stu-id="e5da7-124">The first method is to build the token credential object in code.</span></span> <span data-ttu-id="e5da7-125">Přihlašovací údaje byste měli bezpečně ukládat do konfiguračního souboru, registru nebo úložiště klíčů Azure.</span><span class="sxs-lookup"><span data-stu-id="e5da7-125">You should store the credentials securely in a configuration file, the registry, or Azure KeyVault.</span></span>

```csharp
var credentials = SdkContext.AzureCredentialsFactory
    .FromServicePrincipal(clientId,
        clientSecret,
        tenantId,
        AzureEnvironment.AzureGlobalCloud);
```

<span data-ttu-id="e5da7-126">Při vytváření instančního objektu použijte hodnoty *ClientID*, *clientSecret*a *tenantId* z výstupu JSON.</span><span class="sxs-lookup"><span data-stu-id="e5da7-126">Use the *clientId*, *clientSecret*, and *tenantId* values from the JSON output when you created the service principal.</span></span>

<span data-ttu-id="e5da7-127">Pak vytvořte objekt vstupního bodu `Azure` , abyste mohli začít pracovat s rozhraním API:</span><span class="sxs-lookup"><span data-stu-id="e5da7-127">Then create the entry point `Azure` object to start working with the API:</span></span>

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

<span data-ttu-id="e5da7-128">Doporučuje se explicitně zadat *SubscriptionId* z výstupu JSON do `Azure` objektu:</span><span class="sxs-lookup"><span data-stu-id="e5da7-128">It is recommended that you explicitly provide the *subscriptionId* from the JSON output to the `Azure` object:</span></span>

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithSubscription(subscriptionId);
```

### <a name="file-based-authentication"></a><a name="mgmt-file"></a><span data-ttu-id="e5da7-129">Ověřování na základě souborů</span><span class="sxs-lookup"><span data-stu-id="e5da7-129">File-based authentication</span></span>

<span data-ttu-id="e5da7-130">Ověřování na základě souborů umožňuje umístit přihlašovací údaje instančního objektu do souboru prostého textu a zabezpečit ho v systému souborů.</span><span class="sxs-lookup"><span data-stu-id="e5da7-130">File-based authentication allows you to put the service principal credentials in a plain text file and secure it within the file system.</span></span>

[!include[File-based authentication](includes/file-based-auth.md)]

<span data-ttu-id="e5da7-131">Přečtěte si obsah souboru a vytvořte objekt vstupního bodu `Azure` , abyste mohli začít pracovat s rozhraním API:</span><span class="sxs-lookup"><span data-stu-id="e5da7-131">Read the contents of the file and create the entry point `Azure` object to start working with the API:</span></span>

```csharp
// pull in the location of the authentication properties file from the environment
var credentials = SdkContext.AzureCredentialsFactory
    .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```
