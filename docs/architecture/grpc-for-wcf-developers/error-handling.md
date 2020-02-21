---
title: Zpracování chyb – gRPC pro vývojáře WCF
description: Témata týkající se zpracování chyb v gRPC. Obsahuje tabulku nejčastěji používaných stavových kódů.
ms.date: 09/02/2019
ms.openlocfilehash: c380c651f854adc97e8b2ead36d30c3b83662aac
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542790"
---
# <a name="error-handling"></a><span data-ttu-id="cc783-104">Zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="cc783-104">Error handling</span></span>

<span data-ttu-id="cc783-105">Windows Communication Foundation (WCF) používá <xref:System.ServiceModel.FaultException%601> a [FaultContract](xref:System.ServiceModel.FaultContractAttribute) k poskytování podrobných informací o chybách, včetně podpory standardu SOAP chyb.</span><span class="sxs-lookup"><span data-stu-id="cc783-105">Windows Communication Foundation (WCF) uses <xref:System.ServiceModel.FaultException%601> and [FaultContract](xref:System.ServiceModel.FaultContractAttribute) to provide detailed error information, including supporting the SOAP Fault standard.</span></span>

<span data-ttu-id="cc783-106">Aktuální verze gRPC bohužel neobsahuje sofistikovanější nalezené pomocí WCF a má pouze omezené integrované zpracování chyb na základě jednoduchých stavových kódů a metadat.</span><span class="sxs-lookup"><span data-stu-id="cc783-106">Unfortunately, the current version of gRPC lacks the sophistication found with WCF, and only has limited built-in error handling based on simple status codes and metadata.</span></span> <span data-ttu-id="cc783-107">V následující tabulce je Stručná příručka k nejčastěji používaným stavovým kódům:</span><span class="sxs-lookup"><span data-stu-id="cc783-107">The following table is a quick guide to the most commonly used status codes:</span></span>

| <span data-ttu-id="cc783-108">Kód stavu</span><span class="sxs-lookup"><span data-stu-id="cc783-108">Status code</span></span> | <span data-ttu-id="cc783-109">Problém</span><span class="sxs-lookup"><span data-stu-id="cc783-109">Problem</span></span> |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | <span data-ttu-id="cc783-110">Metoda nebyla zapsána.</span><span class="sxs-lookup"><span data-stu-id="cc783-110">Method hasn’t been written.</span></span> |
| `GRPC_STATUS_UNAVAILABLE` | <span data-ttu-id="cc783-111">Problém s celou službou.</span><span class="sxs-lookup"><span data-stu-id="cc783-111">Problem with the whole service.</span></span> |
| `GRPC_STATUS_UNKNOWN` | <span data-ttu-id="cc783-112">Neplatná odpověď.</span><span class="sxs-lookup"><span data-stu-id="cc783-112">Invalid response.</span></span> |
| `GRPC_STATUS_INTERNAL` | <span data-ttu-id="cc783-113">Problém s kódováním/dekódováním.</span><span class="sxs-lookup"><span data-stu-id="cc783-113">Problem with encoding/decoding.</span></span> |
| `GRPC_STATUS_UNAUTHENTICATED` | <span data-ttu-id="cc783-114">Ověřování se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="cc783-114">Authentication failed.</span></span> |
| `GRPC_STATUS_PERMISSION_DENIED` | <span data-ttu-id="cc783-115">Ověření se nepovedlo.</span><span class="sxs-lookup"><span data-stu-id="cc783-115">Authorization failed.</span></span> |
| `GRPC_STATUS_CANCELLED` | <span data-ttu-id="cc783-116">Volání bylo zrušeno, obvykle volající.</span><span class="sxs-lookup"><span data-stu-id="cc783-116">Call was canceled, usually by the caller.</span></span> |

## <a name="raise-errors-in-aspnet-core-grpc"></a><span data-ttu-id="cc783-117">Vyvolávání chyb v ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="cc783-117">Raise errors in ASP.NET Core gRPC</span></span>

<span data-ttu-id="cc783-118">Služba ASP.NET Core gRPC může odeslat chybovou odpověď vyvoláním `RpcException`, kterou může klient zachytit, jako kdyby byl ve stejném procesu.</span><span class="sxs-lookup"><span data-stu-id="cc783-118">An ASP.NET Core gRPC service can send an error response by throwing an `RpcException`, which can be caught by the client as if it were in the same process.</span></span> <span data-ttu-id="cc783-119">`RpcException` musí zahrnovat stavový kód a popis a může volitelně zahrnovat metadata a delší zprávu o výjimce.</span><span class="sxs-lookup"><span data-stu-id="cc783-119">The `RpcException` must include a status code and description, and can optionally include metadata and a longer exception message.</span></span> <span data-ttu-id="cc783-120">Metadata lze použít k odesílání podpůrných dat, podobně jako `FaultContract` objekty mohou pro chyby WCF přenášet další data.</span><span class="sxs-lookup"><span data-stu-id="cc783-120">The metadata can be used to send supporting data, similar to how `FaultContract` objects can carry additional data for WCF errors.</span></span>

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

## <a name="catch-errors-in-grpc-clients"></a><span data-ttu-id="cc783-121">Zachycení chyb v klientech gRPC</span><span class="sxs-lookup"><span data-stu-id="cc783-121">Catch errors in gRPC clients</span></span>

<span data-ttu-id="cc783-122">Stejně jako klienti WCF můžou zachytit chyby <xref:System.ServiceModel.FaultException%601>, klient gRPC může zachytit `RpcException` a zpracovávat chyby.</span><span class="sxs-lookup"><span data-stu-id="cc783-122">Just like WCF clients can catch <xref:System.ServiceModel.FaultException%601> errors, a gRPC client can catch an `RpcException` to handle errors.</span></span> <span data-ttu-id="cc783-123">Vzhledem k tomu, že `RpcException` není obecný typ, nemůžete zachytávání různých typů chyb v různých blocích.</span><span class="sxs-lookup"><span data-stu-id="cc783-123">Because `RpcException` isn't a generic type, you can't catch different error types in different blocks.</span></span> <span data-ttu-id="cc783-124">Můžete ale použít C#funkci *filtry výjimek* pro deklaraci samostatných `catch`ch bloků pro různé stavové kódy, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="cc783-124">But you can use C#'s *exception filters* feature to declare separate `catch` blocks for different status codes, as shown in the following example:</span></span>

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
> <span data-ttu-id="cc783-125">Když zadáte další metadata pro chyby, nezapomeňte zdokumentovat příslušné klíče a hodnoty v dokumentaci k rozhraní API nebo v komentářích v souboru `.proto`.</span><span class="sxs-lookup"><span data-stu-id="cc783-125">When you provide additional metadata for errors, be sure to document the relevant keys and values in your API documentation, or in comments in your `.proto` file.</span></span>

## <a name="grpc-richer-error-model"></a><span data-ttu-id="cc783-126">model gRPC bohatých chyb</span><span class="sxs-lookup"><span data-stu-id="cc783-126">gRPC richer error model</span></span>

<span data-ttu-id="cc783-127">Google vyvinul [model rozsáhlejších chyb](https://cloud.google.com/apis/design/errors#error_model) , který je více podobný jako [FaultContract](xref:System.ServiceModel.FaultContractAttribute)WCF, ale tento model C# ještě není podporovaný.</span><span class="sxs-lookup"><span data-stu-id="cc783-127">Google has developed a [richer error model](https://cloud.google.com/apis/design/errors#error_model) that's more like WCF's [FaultContract](xref:System.ServiceModel.FaultContractAttribute), but this model isn't supported in C# yet.</span></span> <span data-ttu-id="cc783-128">V současné době je dostupná jenom pro jazyky přejít, Java, Python a C++.</span><span class="sxs-lookup"><span data-stu-id="cc783-128">Currently, it's only available for Go, Java, Python, and C++.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="cc783-129">[Předchozí](metadata.md)
>[Další](ws-protocols.md)</span><span class="sxs-lookup"><span data-stu-id="cc783-129">[Previous](metadata.md)
[Next](ws-protocols.md)</span></span>
