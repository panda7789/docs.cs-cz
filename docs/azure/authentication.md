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
# <a name="authenticate-with-the-azure-sdk-for-net"></a>Ověřování pomocí sady Azure SDK pro .NET

## <a name="recommended-azureidentity"></a>Doporučené: Azure. identity

Nejnovější balíčky v sadě Azure SDK pro .NET používají pro ověření, že se používá společný ověřovací balíček `Azure.Identity` . Použití `Azure.Identity` se doporučuje u jiných ověřovacích mechanismů popsaných dále v tomto dokumentu. Balíčky podporující přihlašovací údaje, které poskytují, `Azure.Identity` mají identifikátory balíčků počínaje *Azure.* [Další informace najdete v tématu nejnovější verze sady Azure SDK pro .NET](https://azure.github.io/azure-sdk/releases/latest/index.html#net).

Podrobné pokyny k použití `Azure.Identity` v projektu najdete v dokumentaci ke [službě Azure identity Client pro .NET](/dotnet/api/overview/azure/identity-readme).

> [!TIP]
> Příklady použití identity Azure ke správě a přístupu k prostředkům Azure najdete v [ukázce Azure identity, Resource Management a Storage](/samples/dotnet/samples/azure-identity-resource-management-storage/) .

K ověřování pomocí knihoven, které nepodporují Azure. identity, se podívejte na zbývající část tohoto tématu.

## <a name="access-azure-resources"></a>Přístup k prostředkům Azure

K interakci s prostředky Azure, jako je například načítání tajného klíče z Key Vault nebo ukládání objektu blob do úložiště, mnoho knihoven služeb Azure vyžaduje připojovací řetězec nebo klíče pro ověřování. SQL Database například používá [standardní připojovací řetězec SQL](https://docs.microsoft.com/azure/azure-sql/database/connect-query-dotnet-core). Připojovací řetězce služby se používají v jiných službách Azure, jako je [CosmosDB](/azure/cosmos-db/), [Azure cache pro Redis](/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache)a [Service Bus](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues). Tyto řetězce můžete získat pomocí Azure Portal, CLI nebo PowerShellu. Můžete také použít knihovny pro správu Azure pro .NET k dotazování prostředků na vytváření připojovacích řetězců ve vašem kódu.

Metody pro použití připojovacího řetězce se liší podle produktu. [Informace najdete v dokumentaci k produktu Azure](/azure/?product=featured).

## <a name="manage-azure-resources"></a>Správa prostředků Azure

[!include[Create service principal](includes/create-sp.md)]

Nyní, když je objekt služby vytvořen, jsou k dispozici dvě možnosti pro ověření objektu služby pro vytváření a správu prostředků.

Pro obě možnosti budete muset do svého projektu přidat následující balíčky NuGet.

```powershell
Install-Package Microsoft.Azure.Management.Fluent
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="authenticate-with-token-credentials"></a>Ověřování pomocí přihlašovacích údajů tokenu

První metodou je vytvořit objekt přihlašovacích údajů tokenu v kódu. Přihlašovací údaje byste měli bezpečně ukládat do konfiguračního souboru, registru nebo úložiště klíčů Azure.

```csharp
var credentials = SdkContext.AzureCredentialsFactory
    .FromServicePrincipal(clientId,
        clientSecret,
        tenantId,
        AzureEnvironment.AzureGlobalCloud);
```

Při vytváření instančního objektu použijte hodnoty *ClientID*, *clientSecret*a *tenantId* z výstupu JSON.

Pak vytvořte objekt vstupního bodu `Azure` , abyste mohli začít pracovat s rozhraním API:

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

### <a name="file-based-authentication"></a><a name="mgmt-file"></a>Ověřování na základě souborů

Ověřování na základě souborů umožňuje umístit přihlašovací údaje instančního objektu do souboru prostého textu a zabezpečit ho v systému souborů.

[!include[File-based authentication](includes/file-based-auth.md)]

Přečtěte si obsah souboru a vytvořte objekt vstupního bodu `Azure` , abyste mohli začít pracovat s rozhraním API:

```csharp
// pull in the location of the authentication properties file from the environment
var credentials = SdkContext.AzureCredentialsFactory
    .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```
