---
title: Metadata – gRPC pro vývojáře WCF
description: Jak se v gRPC používají metadata k předání dalšího kontextu mezi klienty a servery
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 1a2131fa3ee3112eaa3c3e7f7c97017fea6b1004
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184328"
---
# <a name="metadata"></a>Metadata

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

"Metadata" odkazují na další data, která mohou být užitečná při zpracování požadavků a odpovědí, ale nejsou součástí skutečných aplikačních dat. Metadata mohou zahrnovat ověřovací tokeny, vyžádat si identifikátory a značky pro účely monitorování nebo informace o datech, jako je počet záznamů v datové sadě.

Je možné přidat záhlaví obecných klíčů a hodnot do zpráv WCF pomocí <xref:System.ServiceModel.OperationContextScope> <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> vlastnosti a a zpracovávat je pomocí <xref:System.ServiceModel.Channels.MessageProperties>.

volání a odpovědi gRPC můžou zahrnovat i metadata podobná hlavičkám HTTP. Ty jsou většinou neviditelné, protože gRPC sebe sama a jsou předávány prostřednictvím kódu aplikace nebo middlewaru. Metadata jsou reprezentována jako páry klíč/hodnota, kde klíč je řetězec a hodnota je buď řetězec, nebo binární data. V `.proto` souboru nemusíte zadávat metadata.

Metadata se zpracovávají pomocí `Metadata` třídy z balíčku NuGet [Grpc. Core](https://www.nuget.org/packages/Grpc.Core/) . Tato třída se dá použít se syntaxí inicializátoru kolekce.

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

služby gRPC Services mají přístup k metadatům `ServerCallContext` z `RequestHeaders` vlastnosti argumentu:

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

Služby mohou odesílat metadata klientům pomocí `ResponseTrailers` `ServerCallContext`vlastnosti:

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
