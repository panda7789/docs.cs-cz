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
# <a name="metadata"></a><span data-ttu-id="c2626-103">Metadata</span><span class="sxs-lookup"><span data-stu-id="c2626-103">Metadata</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="c2626-104">"Metadata" odkazují na další data, která mohou být užitečná při zpracování požadavků a odpovědí, ale nejsou součástí skutečných aplikačních dat.</span><span class="sxs-lookup"><span data-stu-id="c2626-104">"Metadata" refers to additional data that may be useful while processing requests and responses but is not part of the actual application data.</span></span> <span data-ttu-id="c2626-105">Metadata mohou zahrnovat ověřovací tokeny, vyžádat si identifikátory a značky pro účely monitorování nebo informace o datech, jako je počet záznamů v datové sadě.</span><span class="sxs-lookup"><span data-stu-id="c2626-105">Metadata might include authentication tokens, request identifiers and tags for monitoring purposes, or information about the data like the number of records in a dataset.</span></span>

<span data-ttu-id="c2626-106">Je možné přidat záhlaví obecných klíčů a hodnot do zpráv WCF pomocí <xref:System.ServiceModel.OperationContextScope> <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> vlastnosti a a zpracovávat je pomocí <xref:System.ServiceModel.Channels.MessageProperties>.</span><span class="sxs-lookup"><span data-stu-id="c2626-106">It's possible to add generic key/value headers to WCF messages using an <xref:System.ServiceModel.OperationContextScope> and the <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders?displayProperty=nameWithType> property, and handle them using <xref:System.ServiceModel.Channels.MessageProperties>.</span></span>

<span data-ttu-id="c2626-107">volání a odpovědi gRPC můžou zahrnovat i metadata podobná hlavičkám HTTP.</span><span class="sxs-lookup"><span data-stu-id="c2626-107">gRPC calls and responses can also include metadata similar to HTTP headers.</span></span> <span data-ttu-id="c2626-108">Ty jsou většinou neviditelné, protože gRPC sebe sama a jsou předávány prostřednictvím kódu aplikace nebo middlewaru.</span><span class="sxs-lookup"><span data-stu-id="c2626-108">These are mostly invisible to gRPC itself and are passed through to be processed by your application code or middleware.</span></span> <span data-ttu-id="c2626-109">Metadata jsou reprezentována jako páry klíč/hodnota, kde klíč je řetězec a hodnota je buď řetězec, nebo binární data.</span><span class="sxs-lookup"><span data-stu-id="c2626-109">Metadata is represented as key/value pairs where the key is a string and the value is either a string or binary data.</span></span> <span data-ttu-id="c2626-110">V `.proto` souboru nemusíte zadávat metadata.</span><span class="sxs-lookup"><span data-stu-id="c2626-110">You don’t need to specify metadata in the `.proto` file.</span></span>

<span data-ttu-id="c2626-111">Metadata se zpracovávají pomocí `Metadata` třídy z balíčku NuGet [Grpc. Core](https://www.nuget.org/packages/Grpc.Core/) .</span><span class="sxs-lookup"><span data-stu-id="c2626-111">Metadata is handled using the `Metadata` class from the [Grpc.Core](https://www.nuget.org/packages/Grpc.Core/) NuGet package.</span></span> <span data-ttu-id="c2626-112">Tato třída se dá použít se syntaxí inicializátoru kolekce.</span><span class="sxs-lookup"><span data-stu-id="c2626-112">This class can be used with collection initializer syntax.</span></span>

<span data-ttu-id="c2626-113">Následující příklad ukazuje, jak přidat metadata k volání z C# klienta:</span><span class="sxs-lookup"><span data-stu-id="c2626-113">The following example shows how to add metadata to a call from a C# client:</span></span>

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

<span data-ttu-id="c2626-114">služby gRPC Services mají přístup k metadatům `ServerCallContext` z `RequestHeaders` vlastnosti argumentu:</span><span class="sxs-lookup"><span data-stu-id="c2626-114">gRPC services can access metadata from the `ServerCallContext` argument's `RequestHeaders` property:</span></span>

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

<span data-ttu-id="c2626-115">Služby mohou odesílat metadata klientům pomocí `ResponseTrailers` `ServerCallContext`vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="c2626-115">Services can send metadata to clients using the `ResponseTrailers` property of `ServerCallContext`:</span></span>

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    // ...
    context.ResponseTrailers.Add("Responder", _serverName);
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="c2626-116">[Předchozí](rpc-types.md)
>[Další](error-handling.md)</span><span class="sxs-lookup"><span data-stu-id="c2626-116">[Previous](rpc-types.md)
[Next](error-handling.md)</span></span>
