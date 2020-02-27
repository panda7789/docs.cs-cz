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
# <a name="metadata"></a><span data-ttu-id="5bb2b-103">Metadata</span><span class="sxs-lookup"><span data-stu-id="5bb2b-103">Metadata</span></span>

<span data-ttu-id="5bb2b-104">*Metadata* odkazují na další data, která by mohla být užitečná při zpracování požadavků a odpovědí, ale která nejsou součástí skutečných aplikačních dat.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-104">*Metadata* refers to additional data that might be useful during the processing of requests and responses but that’s not part of the actual application data.</span></span> <span data-ttu-id="5bb2b-105">Metadata mohou zahrnovat ověřovací tokeny, vyžádat si identifikátory a značky pro účely monitorování a informace o datech, jako je počet záznamů v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-105">Metadata might include authentication tokens, request identifiers and tags for monitoring purposes, and information about the data, like the number of records in a dataset.</span></span>

<span data-ttu-id="5bb2b-106">Je možné přidat hlavičky obecných klíčů a hodnot do zpráv Windows Communication Foundation (WCF) pomocí <xref:System.ServiceModel.OperationContextScope> a vlastnosti <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> a zpracovávat je pomocí <xref:System.ServiceModel.Channels.MessageProperties>.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-106">It's possible to add generic key/value headers to Windows Communication Foundation (WCF) messages by using an <xref:System.ServiceModel.OperationContextScope> and the <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> property and handle them by using <xref:System.ServiceModel.Channels.MessageProperties>.</span></span>

<span data-ttu-id="5bb2b-107">volání a odpovědi gRPC můžou zahrnovat i metadata, která jsou podobná hlavičkám HTTP.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-107">gRPC calls and responses can also include metadata that's similar to HTTP headers.</span></span> <span data-ttu-id="5bb2b-108">Tato metadata jsou většinou neviditelná pro gRPC sebe sama a předávají se prostřednictvím kódu aplikace nebo middlewaru.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-108">This metadata is mostly invisible to gRPC itself and is passed through to be processed by your application code or middleware.</span></span> <span data-ttu-id="5bb2b-109">Metadata jsou reprezentována jako páry klíč/hodnota, kde klíč je řetězec a hodnota je buď řetězec, nebo binární data.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-109">Metadata is represented as key/value pairs, where the key is a string and the value is either a string or binary data.</span></span> <span data-ttu-id="5bb2b-110">V souboru `.proto` nemusíte zadávat metadata.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-110">You don’t need to specify metadata in the `.proto` file.</span></span>

<span data-ttu-id="5bb2b-111">Metadata jsou zpracována třídou `Metadata` balíčku NuGet [Grpc. Core. API](https://www.nuget.org/packages/Grpc.Core.Api/) .</span><span class="sxs-lookup"><span data-stu-id="5bb2b-111">Metadata is handled by the `Metadata` class of the [Grpc.Core.Api](https://www.nuget.org/packages/Grpc.Core.Api/) NuGet package.</span></span> <span data-ttu-id="5bb2b-112">Tato třída se dá použít se syntaxí inicializátoru kolekce.</span><span class="sxs-lookup"><span data-stu-id="5bb2b-112">This class can be used with collection initializer syntax.</span></span>

<span data-ttu-id="5bb2b-113">Tento příklad ukazuje, jak přidat metadata k volání z C# klienta:</span><span class="sxs-lookup"><span data-stu-id="5bb2b-113">This example shows how to add metadata to a call from a C# client:</span></span>

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

<span data-ttu-id="5bb2b-114">služby gRPC Services mají přístup k metadatům z vlastnosti `RequestHeaders` argumentu `ServerCallContext`:</span><span class="sxs-lookup"><span data-stu-id="5bb2b-114">gRPC services can access metadata from the `ServerCallContext` argument's `RequestHeaders` property:</span></span>

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

<span data-ttu-id="5bb2b-115">Služby mohou odesílat metadata klientům pomocí vlastnosti `ResponseTrailers` `ServerCallContext`:</span><span class="sxs-lookup"><span data-stu-id="5bb2b-115">Services can send metadata to clients by using the `ResponseTrailers` property of `ServerCallContext`:</span></span>

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    // ...
    context.ResponseTrailers.Add("Responder", _serverName);
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="5bb2b-116">[Předchozí](rpc-types.md)
>[Další](error-handling.md)</span><span class="sxs-lookup"><span data-stu-id="5bb2b-116">[Previous](rpc-types.md)
[Next](error-handling.md)</span></span>
