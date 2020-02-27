---
title: Metadata – gRPC pro vývojáře WCF
description: Jak se v gRPC používají metadata k předání dalšího kontextu mezi klienty a servery.
ms.date: 09/02/2019
ms.openlocfilehash: 64fa94d1e63af480cbc7363631de161c5b8b8fb8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628576"
---
# <a name="metadata"></a>Metadata

*Metadata* odkazují na další data, která by mohla být užitečná při zpracování požadavků a odpovědí, ale která nejsou součástí skutečných aplikačních dat. Metadata mohou zahrnovat ověřovací tokeny, vyžádat si identifikátory a značky pro účely monitorování a informace o datech, jako je počet záznamů v datové sadě.

Je možné přidat hlavičky obecných klíčů a hodnot do zpráv Windows Communication Foundation (WCF) pomocí <xref:System.ServiceModel.OperationContextScope> a vlastnosti <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> a zpracovávat je pomocí <xref:System.ServiceModel.Channels.MessageProperties>.

volání a odpovědi gRPC můžou zahrnovat i metadata, která jsou podobná hlavičkám HTTP. Tato metadata jsou většinou neviditelná pro gRPC sebe sama a předávají se prostřednictvím kódu aplikace nebo middlewaru. Metadata jsou reprezentována jako páry klíč/hodnota, kde klíč je řetězec a hodnota je buď řetězec, nebo binární data. V souboru `.proto` nemusíte zadávat metadata.

Metadata jsou zpracována třídou `Metadata` balíčku NuGet [Grpc. Core. API](https://www.nuget.org/packages/Grpc.Core.Api/) . Tato třída se dá použít se syntaxí inicializátoru kolekce.

Tento příklad ukazuje, jak přidat metadata k volání z C# klienta:

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
