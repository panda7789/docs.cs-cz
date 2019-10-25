---
title: Zpracování chyb – gRPC pro vývojáře WCF
description: BUDE URČENO K ZÁPISU
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 2ef1a0b38d9b63af7244c6e0428c9adbcb1d6527
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846663"
---
# <a name="error-handling"></a><span data-ttu-id="e3500-103">Zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="e3500-103">Error handling</span></span>

<span data-ttu-id="e3500-104">WCF používá `FaultException<T>` a `FaultContract` k poskytnutí podrobných informací o chybách, včetně podpory standardu SOAP chyb.</span><span class="sxs-lookup"><span data-stu-id="e3500-104">WCF uses `FaultException<T>` and `FaultContract` to provide detailed error information, including supporting the SOAP Fault standard.</span></span>

<span data-ttu-id="e3500-105">Aktuální verze gRPC bohužel neobsahuje sofistikovanější nalezené ve službě WCF a má pouze omezené integrované zpracování chyb na základě jednoduchých stavových kódů a metadat.</span><span class="sxs-lookup"><span data-stu-id="e3500-105">Unfortunately, the current version of gRPC lacks the sophistication found with WCF and only has limited built-in error handling based on simple status codes and metadata.</span></span> <span data-ttu-id="e3500-106">V následující tabulce je Stručná příručka k nejčastěji používaným stavovým kódům:</span><span class="sxs-lookup"><span data-stu-id="e3500-106">The following table is a quick guide to the most commonly used status codes:</span></span>

| <span data-ttu-id="e3500-107">Stavový kód</span><span class="sxs-lookup"><span data-stu-id="e3500-107">Status Code</span></span> | <span data-ttu-id="e3500-108">Problém</span><span class="sxs-lookup"><span data-stu-id="e3500-108">Problem</span></span> |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | <span data-ttu-id="e3500-109">Metoda nebyla zapsána.</span><span class="sxs-lookup"><span data-stu-id="e3500-109">Method hasn’t been written.</span></span> |
| `GRPC_STATUS_UNAVAILABLE` | <span data-ttu-id="e3500-110">Problém s celou službou.</span><span class="sxs-lookup"><span data-stu-id="e3500-110">Problem with the whole service.</span></span> |
| `GRPC_STATUS_UNKNOWN` | <span data-ttu-id="e3500-111">Neplatná odpověď.</span><span class="sxs-lookup"><span data-stu-id="e3500-111">Invalid response.</span></span> |
| `GRPC_STATUS_INTERNAL` | <span data-ttu-id="e3500-112">Problém s kódováním/dekódováním.</span><span class="sxs-lookup"><span data-stu-id="e3500-112">Problem with encoding/decoding.</span></span> |
| `GRPC_STATUS_UNAUTHENTICATED` | <span data-ttu-id="e3500-113">Ověřování se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="e3500-113">Authentication failed.</span></span> |
| `GRPC_STATUS_PERMISSION_DENIED` | <span data-ttu-id="e3500-114">Autorizace se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="e3500-114">Authorization failed.</span></span> |
| `GRPC_STATUS_CANCELLED` | <span data-ttu-id="e3500-115">Volání bylo zrušeno, obvykle volající.</span><span class="sxs-lookup"><span data-stu-id="e3500-115">Call was canceled, usually by the caller.</span></span> |

## <a name="raising-errors-in-aspnet-core-grpc"></a><span data-ttu-id="e3500-116">Vyvolávání chyb v ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="e3500-116">Raising errors in ASP.NET Core gRPC</span></span>

<span data-ttu-id="e3500-117">Služba ASP.NET Core gRPC může odeslat chybovou odpověď vyvoláním `RpcException`, kterou může klient zachytit, jako kdyby byl ve stejném procesu.</span><span class="sxs-lookup"><span data-stu-id="e3500-117">An ASP.NET Core gRPC service can send an error response by throwing an `RpcException`, which can be caught by the client as if it were in the same process.</span></span> <span data-ttu-id="e3500-118">`RpcException` musí zahrnovat stavový kód a popis a může volitelně zahrnovat metadata a delší zprávu o výjimce.</span><span class="sxs-lookup"><span data-stu-id="e3500-118">The `RpcException` must include a status code and description, and can optionally include metadata and a longer exception message.</span></span> <span data-ttu-id="e3500-119">Metadata lze použít k odesílání podpůrných dat, podobně jako `FaultContract` objekty mohou mít další data pro chyby WCF.</span><span class="sxs-lookup"><span data-stu-id="e3500-119">The metadata can be used to send supporting data, similar to how `FaultContract` objects could carry additional data for WCF errors.</span></span>

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    var user = context.GetHttpContext().User;
    if (!ValidateUser(user))
    {
        var metadata = new Metadata
        {
            { "User", user.Identity.Name }
        };
        throw new RpcException(new Status(StatusCode.PermissionDenied, "Permission denied"), metadata);
    }
}
```

## <a name="catching-errors-in-grpc-clients"></a><span data-ttu-id="e3500-120">Zachycení chyb v klientech gRPC</span><span class="sxs-lookup"><span data-stu-id="e3500-120">Catching errors in gRPC clients</span></span>

<span data-ttu-id="e3500-121">Stejně jako klienti WCF můžou zachytit chyby <xref:System.ServiceModel.FaultException%601>, klient gRPC může zachytit `RpcException` a zpracovávat chyby.</span><span class="sxs-lookup"><span data-stu-id="e3500-121">Just like WCF clients can catch <xref:System.ServiceModel.FaultException%601> errors, a gRPC client can catch an `RpcException` to handle errors.</span></span> <span data-ttu-id="e3500-122">Vzhledem k tomu, že `RpcException` není obecný typ, nemůžete zachytávání různých typů chyb v různých blocích C#, ale můžete použít funkci *filtrů výjimek* pro deklaraci samostatných`catch`ch bloků pro různé stavové kódy, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e3500-122">Since `RpcException` isn't a generic type, you can't catch different error types in different blocks, but you can use C#'s *exception filters* feature to declare separate `catch` blocks for different status codes, as shown in the following example:</span></span>

```csharp
try
{
    var portfolio = await client.GetPortfolioAsync(new GetPortfolioRequest { Id = id });
}
catch (RpcException ex) when (ex.StatusCode == StatusCode.PermissionDenied)
{
    var userEntry = ex.Trailers.FirstOrDefault(e => e.Key == "User");
    Console.WriteLine($"User '{userEntry.Value}' does not have permission to view this portfolio.");
}
catch (RpcException) 
{
    // Handle any other error type ...
}
```

> [!IMPORTANT]
> <span data-ttu-id="e3500-123">Když zadáte další metadata pro chyby, nezapomeňte zdokumentovat příslušné klíče a hodnoty v dokumentaci k rozhraní API nebo v komentářích v souboru `.proto`.</span><span class="sxs-lookup"><span data-stu-id="e3500-123">When you provide additional metadata for errors, be sure to document the relevant keys and values in your API documentation, or in comments in your `.proto` file.</span></span>

## <a name="grpc-richer-error-model"></a><span data-ttu-id="e3500-124">Model gRPC bohatých chyb</span><span class="sxs-lookup"><span data-stu-id="e3500-124">gRPC Richer Error Model</span></span>

<span data-ttu-id="e3500-125">Těšíme se na to, že Google vyvinul [model s](https://cloud.google.com/apis/design/errors#error_model) větším množstvím chyb, jako je například [FaultContract](xref:System.ServiceModel.FaultContractAttribute)WCF, ale C# ještě není podporován.</span><span class="sxs-lookup"><span data-stu-id="e3500-125">Looking ahead, Google has developed a [richer error model](https://cloud.google.com/apis/design/errors#error_model) that is more like WCF's [FaultContract](xref:System.ServiceModel.FaultContractAttribute), but isn't supported in C# yet.</span></span> <span data-ttu-id="e3500-126">V současné době je dostupná jenom pro jazyky for, Java, Python C++a, ale očekává C# se, že se bude příští rok přicházet k podpoře.</span><span class="sxs-lookup"><span data-stu-id="e3500-126">Currently, it's only available for Go, Java, Python and C++, but support for C# is expected to come next year.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e3500-127">[Předchozí](metadata.md)
>[Další](ws-protocols.md)</span><span class="sxs-lookup"><span data-stu-id="e3500-127">[Previous](metadata.md)
[Next](ws-protocols.md)</span></span>
