---
title: Metadata – gRPC pro vývojáře WCF
description: Jak se v gRPC používají metadata k předání dalšího kontextu mezi klienty a servery
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 32559b3404b12f366fc1624299d04cff9faad9d6
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846616"
---
# <a name="metadata"></a>Metadata

"Metadata" odkazují na další data, která mohou být užitečná při zpracování požadavků a odpovědí, ale nejsou součástí skutečných aplikačních dat. Metadata mohou zahrnovat ověřovací tokeny, vyžádat si identifikátory a značky pro účely monitorování nebo informace o datech, jako je počet záznamů v datové sadě.

Je možné přidat do zpráv WCF záhlaví obecných klíčů a hodnot pomocí <xref:System.ServiceModel.OperationContextScope> a vlastnost <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> a pomocí <xref:System.ServiceModel.Channels.MessageProperties> je zpracovat.

volání a odpovědi gRPC můžou zahrnovat i metadata podobná hlavičkám HTTP. Ty jsou většinou neviditelné, protože gRPC sebe sama a jsou předávány prostřednictvím kódu aplikace nebo middlewaru. Metadata jsou reprezentována jako páry klíč/hodnota, kde klíč je řetězec a hodnota je buď řetězec, nebo binární data. V souboru `.proto` nemusíte zadávat metadata.

Metadata se zpracovávají pomocí `Metadata` třídy z balíčku NuGet pro [Grpc. Core. API](https://www.nuget.org/packages/Grpc.Core.Api/) . Tato třída se dá použít se syntaxí inicializátoru kolekce.

Následující příklad ukazuje, jak přidat metadata k volání z C# klienta:

```csharp
var metadata = new Metadata
{
    { "Requester", _clientName }
};

var request = new GetPortfolioRequest
{
    Id = portfolioId
};

var response = await client.GetPortfolioAsync(request, metadata);
```

služby gRPC Services mají přístup k metadatům z vlastnosti `RequestHeaders` argumentu `ServerCallContext`:

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    var requesterHeader = context.RequestHeaders.FirstOrDefault(e => e.Key == "Requester");
    if (requesterHeader != null)
    {
        _logger.LogInformation($"Request from {requesterHeader.Value}");
    }
    // ...
}
```

Služby mohou odesílat metadata klientům pomocí vlastnosti `ResponseTrailers` `ServerCallContext`:

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    // ...
    context.ResponseTrailers.Add("Responder", _serverName);
    // ...
}
```

>[!div class="step-by-step"]
>[Předchozí](rpc-types.md)
>[Další](error-handling.md)
