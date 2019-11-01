---
ms.openlocfilehash: c861d61cbbe8075db4b17a702e863336ea621f2b
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198399"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a><span data-ttu-id="0bd16-101">HTTP: synchronní v/v – zakázáno na všech serverech</span><span class="sxs-lookup"><span data-stu-id="0bd16-101">HTTP: Synchronous IO disabled in all servers</span></span>

<span data-ttu-id="0bd16-102">Počínaje ASP.NET Core 3,0 jsou synchronní operace serveru ve výchozím nastavení zakázané.</span><span class="sxs-lookup"><span data-stu-id="0bd16-102">Starting with ASP.NET Core 3.0, synchronous server operations are disabled by default.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0bd16-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="0bd16-103">Change description</span></span>

<span data-ttu-id="0bd16-104">`AllowSynchronousIO` je možnost na každém serveru, která povoluje nebo zakazuje synchronní rozhraní API pro vstupně-výstupní operace jako `HttpRequest.Body.Read`, `HttpResponse.Body.Write` a `Stream.Flush`.</span><span class="sxs-lookup"><span data-stu-id="0bd16-104">`AllowSynchronousIO` is an option in each server that enables or disables synchronous IO APIs like `HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush`.</span></span> <span data-ttu-id="0bd16-105">Tato rozhraní API jsou dlouhodobě zdrojem vláken vyčerpání a aplikace přestane reagovat.</span><span class="sxs-lookup"><span data-stu-id="0bd16-105">These APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="0bd16-106">Počínaje verzí ASP.NET Core 3,0 Preview 3 jsou tyto synchronní operace ve výchozím nastavení zakázány.</span><span class="sxs-lookup"><span data-stu-id="0bd16-106">Starting in ASP.NET Core 3.0 Preview 3, these synchronous operations are disabled by default.</span></span>

<span data-ttu-id="0bd16-107">Ovlivněné servery:</span><span class="sxs-lookup"><span data-stu-id="0bd16-107">Affected servers:</span></span>

- <span data-ttu-id="0bd16-108">Kestrel</span><span class="sxs-lookup"><span data-stu-id="0bd16-108">Kestrel</span></span>
- <span data-ttu-id="0bd16-109">HttpSys</span><span class="sxs-lookup"><span data-stu-id="0bd16-109">HttpSys</span></span>
- <span data-ttu-id="0bd16-110">Vnitroprocesové v rámci služby IIS</span><span class="sxs-lookup"><span data-stu-id="0bd16-110">IIS in-process</span></span>
- <span data-ttu-id="0bd16-111">TestServer</span><span class="sxs-lookup"><span data-stu-id="0bd16-111">TestServer</span></span>

<span data-ttu-id="0bd16-112">Očekávat chyby podobné:</span><span class="sxs-lookup"><span data-stu-id="0bd16-112">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

<span data-ttu-id="0bd16-113">Každý server má parametr `AllowSynchronousIO`, který řídí toto chování, přičemž výchozí hodnota pro všechny jsou nyní `false`.</span><span class="sxs-lookup"><span data-stu-id="0bd16-113">Each server has an `AllowSynchronousIO` option that controls this behavior and the default for all of them is now `false`.</span></span>

<span data-ttu-id="0bd16-114">Chování je také možné přepsat na základě jednotlivých požadavků jako dočasné zmírnění.</span><span class="sxs-lookup"><span data-stu-id="0bd16-114">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span> <span data-ttu-id="0bd16-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="0bd16-115">For example:</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

<span data-ttu-id="0bd16-116">Pokud máte potíže s `TextWriter` nebo jiným datovým proudem, který volá synchronní rozhraní API v `Dispose`, místo toho zavolejte nové rozhraní API `DisposeAsync`.</span><span class="sxs-lookup"><span data-stu-id="0bd16-116">If you have trouble with a `TextWriter` or another stream calling a synchronous API in `Dispose`, call the new `DisposeAsync` API instead.</span></span>

<span data-ttu-id="0bd16-117">Diskuzi najdete v tématu [ASPNET/AspNetCore # 7644](https://github.com/aspnet/AspNetCore/issues/7644).</span><span class="sxs-lookup"><span data-stu-id="0bd16-117">For discussion, see [aspnet/AspNetCore#7644](https://github.com/aspnet/AspNetCore/issues/7644).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0bd16-118">Představená verze</span><span class="sxs-lookup"><span data-stu-id="0bd16-118">Version introduced</span></span>

<span data-ttu-id="0bd16-119">3.0</span><span class="sxs-lookup"><span data-stu-id="0bd16-119">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0bd16-120">Staré chování</span><span class="sxs-lookup"><span data-stu-id="0bd16-120">Old behavior</span></span>

<span data-ttu-id="0bd16-121">ve výchozím nastavení byly povoleny `HttpRequest.Body.Read`, `HttpResponse.Body.Write` a `Stream.Flush`.</span><span class="sxs-lookup"><span data-stu-id="0bd16-121">`HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush` were allowed by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="0bd16-122">Nové chování</span><span class="sxs-lookup"><span data-stu-id="0bd16-122">New behavior</span></span>

<span data-ttu-id="0bd16-123">Ve výchozím nastavení nejsou povolena tato synchronní rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="0bd16-123">These synchronous APIs are disallowed by default:</span></span>

<span data-ttu-id="0bd16-124">Očekávat chyby podobné:</span><span class="sxs-lookup"><span data-stu-id="0bd16-124">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a><span data-ttu-id="0bd16-125">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="0bd16-125">Reason for change</span></span>

<span data-ttu-id="0bd16-126">Tato synchronní rozhraní API byla dlouhodobě zdrojem vláken vyčerpání a aplikace přestane reagovat.</span><span class="sxs-lookup"><span data-stu-id="0bd16-126">These synchronous APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="0bd16-127">Počínaje verzí ASP.NET Core 3,0 Preview 3 jsou synchronní operace ve výchozím nastavení zakázané.</span><span class="sxs-lookup"><span data-stu-id="0bd16-127">Starting in ASP.NET Core 3.0 Preview 3, the synchronous operations are disabled by default.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0bd16-128">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="0bd16-128">Recommended action</span></span>

<span data-ttu-id="0bd16-129">Použijte asynchronní verze metod.</span><span class="sxs-lookup"><span data-stu-id="0bd16-129">Use the asynchronous versions of the methods.</span></span> <span data-ttu-id="0bd16-130">Chování je také možné přepsat na základě jednotlivých požadavků jako dočasné zmírnění.</span><span class="sxs-lookup"><span data-stu-id="0bd16-130">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

#### <a name="category"></a><span data-ttu-id="0bd16-131">Kategorie</span><span class="sxs-lookup"><span data-stu-id="0bd16-131">Category</span></span>

<span data-ttu-id="0bd16-132">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0bd16-132">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0bd16-133">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0bd16-133">Affected APIs</span></span>

- <xref:System.IO.Stream.Flush%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.IO.Stream.Flush`
- `Overload:System.IO.Stream.Read`
- `Overload:System.IO.Stream.Write`

-->
