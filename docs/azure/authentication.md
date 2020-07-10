---
title: Principy ověřování v knihovnách Azure pro .NET
description: Vysvětluje různé způsoby ověřování pomocí sady Azure SDK pro .NET.
ms.date: 06/19/2020
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: 5ed29d5485dc7f59bcc757c8903116edf6bd5d7d
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174946"
---
# <a name="authenticate-with-the-azure-sdk-for-net"></a><span data-ttu-id="2e498-103">Ověřování pomocí sady Azure SDK pro .NET</span><span class="sxs-lookup"><span data-stu-id="2e498-103">Authenticate with the Azure SDK for .NET</span></span>

## <a name="recommended-azureidentity"></a><span data-ttu-id="2e498-104">Doporučené: Azure. identity</span><span class="sxs-lookup"><span data-stu-id="2e498-104">Recommended: Azure.Identity</span></span>

<span data-ttu-id="2e498-105">Nejnovější balíčky v sadě Azure SDK pro .NET používají pro ověření, že se používá společný ověřovací balíček `Azure.Identity` .</span><span class="sxs-lookup"><span data-stu-id="2e498-105">The latest packages in the Azure SDK for .NET use a common authentication package to authenticate, `Azure.Identity`.</span></span> <span data-ttu-id="2e498-106">Použití `Azure.Identity` se doporučuje u jiných ověřovacích mechanismů popsaných dále v tomto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="2e498-106">Using `Azure.Identity` is recommended over other authentication mechanisms described later in this document.</span></span> <span data-ttu-id="2e498-107">Balíčky podporující přihlašovací údaje, které poskytují, `Azure.Identity` mají identifikátory balíčků počínaje *Azure.*</span><span class="sxs-lookup"><span data-stu-id="2e498-107">Packages supporting the credentials provided by `Azure.Identity` have package identifiers starting with *Azure.*</span></span> <span data-ttu-id="2e498-108">[Další informace najdete v tématu nejnovější verze sady Azure SDK pro .NET](https://azure.github.io/azure-sdk/releases/latest/index.html#net).</span><span class="sxs-lookup"><span data-stu-id="2e498-108">[For more information, see the latest releases in the Azure SDK for .NET](https://azure.github.io/azure-sdk/releases/latest/index.html#net).</span></span>

<span data-ttu-id="2e498-109">Podrobné pokyny k použití `Azure.Identity` v projektu najdete v dokumentaci ke [službě Azure identity Client pro .NET](/dotnet/api/overview/azure/identity-readme).</span><span class="sxs-lookup"><span data-stu-id="2e498-109">For complete instructions on using `Azure.Identity` in your project, see the documentation for [Azure Identity client for .NET](/dotnet/api/overview/azure/identity-readme).</span></span>

> [!TIP]
> <span data-ttu-id="2e498-110">Příklady použití identity Azure ke správě a přístupu k prostředkům Azure najdete v [ukázce Azure identity, Resource Management a Storage](/samples/dotnet/samples/azure-identity-resource-management-storage/) .</span><span class="sxs-lookup"><span data-stu-id="2e498-110">See the [Azure Identity, Resource Management, and Storage sample](/samples/dotnet/samples/azure-identity-resource-management-storage/) for examples of using Azure Identity to manage and access Azure resources.</span></span>

<span data-ttu-id="2e498-111">K ověřování pomocí knihoven, které nepodporují Azure. identity, se podívejte na zbývající část tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="2e498-111">To authenticate with libraries that don't support Azure.Identity, see the rest of this topic.</span></span>

## <a name="access-azure-resources"></a><span data-ttu-id="2e498-112">Přístup k prostředkům Azure</span><span class="sxs-lookup"><span data-stu-id="2e498-112">Access Azure resources</span></span>

<span data-ttu-id="2e498-113">K interakci s prostředky Azure, jako je například načítání tajného klíče z Key Vault nebo ukládání objektu blob do úložiště, mnoho knihoven služeb Azure vyžaduje připojovací řetězec nebo klíče pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="2e498-113">To interact with Azure resources, such as retrieving a secret from Key Vault or storing a blob in Storage, many Azure service libraries require a connection string or keys for authentication.</span></span> <span data-ttu-id="2e498-114">SQL Database například používá [standardní připojovací řetězec SQL](https://docs.microsoft.com/azure/azure-sql/database/connect-query-dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="2e498-114">For example, SQL Database uses a [standard SQL connection string](https://docs.microsoft.com/azure/azure-sql/database/connect-query-dotnet-core).</span></span> <span data-ttu-id="2e498-115">Připojovací řetězce služby se používají v jiných službách Azure, jako je [CosmosDB](/azure/cosmos-db/), [Azure cache pro Redis](/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache)a [Service Bus](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues).</span><span class="sxs-lookup"><span data-stu-id="2e498-115">Service connection strings are used in other Azure services like [CosmosDB](/azure/cosmos-db/), [Azure Cache for Redis](/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache), and [Service Bus](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues).</span></span> <span data-ttu-id="2e498-116">Tyto řetězce můžete získat pomocí Azure Portal, CLI nebo PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="2e498-116">You can get those strings using the Azure portal, CLI, or PowerShell.</span></span> <span data-ttu-id="2e498-117">Můžete také použít knihovny pro správu Azure pro .NET k dotazování prostředků na vytváření připojovacích řetězců ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="2e498-117">You can also use the Azure management libraries for .NET to query resources to build connection strings in your code.</span></span>

<span data-ttu-id="2e498-118">Metody pro použití připojovacího řetězce se liší podle produktu.</span><span class="sxs-lookup"><span data-stu-id="2e498-118">The methods for using a connection string vary by product.</span></span> <span data-ttu-id="2e498-119">[Informace najdete v dokumentaci k produktu Azure](/azure/?product=featured).</span><span class="sxs-lookup"><span data-stu-id="2e498-119">[Refer to the documentation for your Azure product](/azure/?product=featured).</span></span>

## <a name="manage-azure-resources"></a><span data-ttu-id="2e498-120">Správa prostředků Azure</span><span class="sxs-lookup"><span data-stu-id="2e498-120">Manage Azure resources</span></span>

[!include[Create service principal](includes/create-sp.md)]

<span data-ttu-id="2e498-121">Nyní, když je objekt služby vytvořen, jsou k dispozici dvě možnosti pro ověření objektu služby pro vytváření a správu prostředků.</span><span class="sxs-lookup"><span data-stu-id="2e498-121">Now that the service principal is created, two options are available to authenticate to the service principal to create and manage resources.</span></span>

<span data-ttu-id="2e498-122">Pro obě možnosti budete muset do svého projektu přidat následující balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="2e498-122">For both options you will need to add the following NuGet packages to your project.</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Fluent
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="authenticate-with-token-credentials"></a><span data-ttu-id="2e498-123">Ověřování pomocí přihlašovacích údajů tokenu</span><span class="sxs-lookup"><span data-stu-id="2e498-123">Authenticate with token credentials</span></span>

<span data-ttu-id="2e498-124">První metodou je vytvořit objekt přihlašovacích údajů tokenu v kódu.</span><span class="sxs-lookup"><span data-stu-id="2e498-124">The first method is to build the token credential object in code.</span></span> <span data-ttu-id="2e498-125">Přihlašovací údaje byste měli bezpečně ukládat do konfiguračního souboru, registru nebo úložiště klíčů Azure.</span><span class="sxs-lookup"><span data-stu-id="2e498-125">You should store the credentials securely in a configuration file, the registry, or Azure KeyVault.</span></span>

```csharp
var credentials = SdkContext.AzureCredentialsFactory
    .FromServicePrincipal(clientId,
        clientSecret,
        tenantId,
        AzureEnvironment.AzureGlobalCloud);
```

<span data-ttu-id="2e498-126">Při vytváření instančního objektu použijte hodnoty *ClientID*, *clientSecret*a *tenantId* z výstupu JSON.</span><span class="sxs-lookup"><span data-stu-id="2e498-126">Use the *clientId*, *clientSecret*, and *tenantId* values from the JSON output when you created the service principal.</span></span>

<span data-ttu-id="2e498-127">Pak vytvořte objekt vstupního bodu `Azure` , abyste mohli začít pracovat s rozhraním API:</span><span class="sxs-lookup"><span data-stu-id="2e498-127">Then create the entry point `Azure` object to start working with the API:</span></span>

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

### <a name="file-based-authentication"></a><a name="mgmt-file"></a><span data-ttu-id="2e498-128">Ověřování na základě souborů</span><span class="sxs-lookup"><span data-stu-id="2e498-128">File-based authentication</span></span>

<span data-ttu-id="2e498-129">Ověřování na základě souborů umožňuje umístit přihlašovací údaje instančního objektu do souboru prostého textu a zabezpečit ho v systému souborů.</span><span class="sxs-lookup"><span data-stu-id="2e498-129">File-based authentication allows you to put the service principal credentials in a plain text file and secure it within the file system.</span></span>

[!include[File-based authentication](includes/file-based-auth.md)]

<span data-ttu-id="2e498-130">Přečtěte si obsah souboru a vytvořte objekt vstupního bodu `Azure` , abyste mohli začít pracovat s rozhraním API:</span><span class="sxs-lookup"><span data-stu-id="2e498-130">Read the contents of the file and create the entry point `Azure` object to start working with the API:</span></span>

```csharp
// pull in the location of the authentication properties file from the environment
var credentials = SdkContext.AzureCredentialsFactory
    .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```
