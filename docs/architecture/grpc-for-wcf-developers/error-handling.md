---
title: Zpracování chyb - gRPC pro vývojáře WCF
description: Témata týkající se zpracování chyb v gRPC. Obsahuje tabulku nejčastěji používaných stavových kódů.
ms.date: 09/02/2019
ms.openlocfilehash: 64a2355a8bd608c074f9bc420312b23aba0c1fb2
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988944"
---
# <a name="error-handling"></a><span data-ttu-id="019b2-104">Zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="019b2-104">Error handling</span></span>

<span data-ttu-id="019b2-105">Windows Communication Foundation (WCF) používá <xref:System.ServiceModel.FaultException%601> a [FaultContract](xref:System.ServiceModel.FaultContractAttribute) poskytnout podrobné informace o chybě, včetně podpory standardu chyba SOAP.</span><span class="sxs-lookup"><span data-stu-id="019b2-105">Windows Communication Foundation (WCF) uses <xref:System.ServiceModel.FaultException%601> and [FaultContract](xref:System.ServiceModel.FaultContractAttribute) to provide detailed error information, including supporting the SOAP Fault standard.</span></span>

<span data-ttu-id="019b2-106">Bohužel, aktuální verze gRPC postrádá sofistikovanost nalezenou s WCF a má pouze omezené vestavěné zpracování chyb na základě jednoduchých stavových kódů a metadat.</span><span class="sxs-lookup"><span data-stu-id="019b2-106">Unfortunately, the current version of gRPC lacks the sophistication found with WCF, and only has limited built-in error handling based on simple status codes and metadata.</span></span> <span data-ttu-id="019b2-107">Následující tabulka obsahuje stručný průvodce nejčastěji používanými stavovými kódy:</span><span class="sxs-lookup"><span data-stu-id="019b2-107">The following table is a quick guide to the most commonly used status codes:</span></span>

| <span data-ttu-id="019b2-108">Kód stavu</span><span class="sxs-lookup"><span data-stu-id="019b2-108">Status code</span></span> | <span data-ttu-id="019b2-109">Problém</span><span class="sxs-lookup"><span data-stu-id="019b2-109">Problem</span></span> |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | <span data-ttu-id="019b2-110">Metoda nebyla napsána.</span><span class="sxs-lookup"><span data-stu-id="019b2-110">Method hasn't been written.</span></span> |
| `GRPC_STATUS_UNAVAILABLE` | <span data-ttu-id="019b2-111">Problém s celou službou.</span><span class="sxs-lookup"><span data-stu-id="019b2-111">Problem with the whole service.</span></span> |
| `GRPC_STATUS_UNKNOWN` | <span data-ttu-id="019b2-112">Neplatná odpověď.</span><span class="sxs-lookup"><span data-stu-id="019b2-112">Invalid response.</span></span> |
| `GRPC_STATUS_INTERNAL` | <span data-ttu-id="019b2-113">Problém s kódováním/dekódováním.</span><span class="sxs-lookup"><span data-stu-id="019b2-113">Problem with encoding/decoding.</span></span> |
| `GRPC_STATUS_UNAUTHENTICATED` | <span data-ttu-id="019b2-114">Ověření se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="019b2-114">Authentication failed.</span></span> |
| `GRPC_STATUS_PERMISSION_DENIED` | <span data-ttu-id="019b2-115">Autorizace se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="019b2-115">Authorization failed.</span></span> |
| `GRPC_STATUS_CANCELLED` | <span data-ttu-id="019b2-116">Hovor byl zrušen, obvykle volajícím.</span><span class="sxs-lookup"><span data-stu-id="019b2-116">Call was canceled, usually by the caller.</span></span> |

## <a name="raise-errors-in-aspnet-core-grpc"></a><span data-ttu-id="019b2-117">Zvýšení chyb v ASP.NET Core gRPC</span><span class="sxs-lookup"><span data-stu-id="019b2-117">Raise errors in ASP.NET Core gRPC</span></span>

<span data-ttu-id="019b2-118">Služba ASP.NET Core gRPC může odeslat odpověď `RpcException`na chybu vyvoláním , který může být zachycen klientem, jako by byl ve stejném procesu.</span><span class="sxs-lookup"><span data-stu-id="019b2-118">An ASP.NET Core gRPC service can send an error response by throwing an `RpcException`, which can be caught by the client as if it were in the same process.</span></span> <span data-ttu-id="019b2-119">Musí `RpcException` obsahovat stavový kód a popis a volitelně může obsahovat metadata a delší zprávu o výjimce.</span><span class="sxs-lookup"><span data-stu-id="019b2-119">The `RpcException` must include a status code and description, and can optionally include metadata and a longer exception message.</span></span> <span data-ttu-id="019b2-120">Metadata lze použít k odeslání podpůrných dat, podobně jako `FaultContract` objekty mohou přenášet další data pro chyby WCF.</span><span class="sxs-lookup"><span data-stu-id="019b2-120">The metadata can be used to send supporting data, similar to how `FaultContract` objects can carry additional data for WCF errors.</span></span>

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

## <a name="catch-errors-in-grpc-clients"></a><span data-ttu-id="019b2-121">Zachytávat chyby v klientech gRPC</span><span class="sxs-lookup"><span data-stu-id="019b2-121">Catch errors in gRPC clients</span></span>

<span data-ttu-id="019b2-122">Stejně jako WCF <xref:System.ServiceModel.FaultException%601> klienti mohou zachytit chyby, `RpcException` gRPC klient může zachytit zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="019b2-122">Just like WCF clients can catch <xref:System.ServiceModel.FaultException%601> errors, a gRPC client can catch an `RpcException` to handle errors.</span></span> <span data-ttu-id="019b2-123">Protože `RpcException` není obecný typ, nelze zachytit různé typy chyb v různých blocích.</span><span class="sxs-lookup"><span data-stu-id="019b2-123">Because `RpcException` isn't a generic type, you can't catch different error types in different blocks.</span></span> <span data-ttu-id="019b2-124">Ale můžete použít C# *filtry výjimek* funkce deklarovat samostatné `catch` bloky pro různé stavové kódy, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="019b2-124">But you can use C#'s *exception filters* feature to declare separate `catch` blocks for different status codes, as shown in the following example:</span></span>

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
> <span data-ttu-id="019b2-125">Pokud zadáte další metadata pro chyby, nezapomeňte zdokumentovat příslušné klíče a hodnoty `.proto` v dokumentaci k rozhraní API nebo v komentářích v souboru.</span><span class="sxs-lookup"><span data-stu-id="019b2-125">When you provide additional metadata for errors, be sure to document the relevant keys and values in your API documentation, or in comments in your `.proto` file.</span></span>

## <a name="grpc-richer-error-model"></a><span data-ttu-id="019b2-126">gRPC bohatší chybový model</span><span class="sxs-lookup"><span data-stu-id="019b2-126">gRPC richer error model</span></span>

<span data-ttu-id="019b2-127">Google vyvinul [bohatší chybový model,](https://cloud.google.com/apis/design/errors#error_model) který je spíše jako [WCF FaultContract](xref:System.ServiceModel.FaultContractAttribute), ale tento model není podporován v C# dosud.</span><span class="sxs-lookup"><span data-stu-id="019b2-127">Google has developed a [richer error model](https://cloud.google.com/apis/design/errors#error_model) that's more like WCF's [FaultContract](xref:System.ServiceModel.FaultContractAttribute), but this model isn't supported in C# yet.</span></span> <span data-ttu-id="019b2-128">V současné době je k dispozici pouze pro Go, Java, Python a C++.</span><span class="sxs-lookup"><span data-stu-id="019b2-128">Currently, it's only available for Go, Java, Python, and C++.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="019b2-129">[Předchozí](metadata.md)
>[další](ws-protocols.md)</span><span class="sxs-lookup"><span data-stu-id="019b2-129">[Previous](metadata.md)
[Next](ws-protocols.md)</span></span>
