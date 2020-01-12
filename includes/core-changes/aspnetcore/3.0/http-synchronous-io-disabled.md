---
ms.openlocfilehash: 53d2c989120c92f4e2d18f50ce4b364bd4c9b604
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901798"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a><span data-ttu-id="5228b-101">HTTP: synchronní v/v – zakázáno na všech serverech</span><span class="sxs-lookup"><span data-stu-id="5228b-101">HTTP: Synchronous IO disabled in all servers</span></span>

<span data-ttu-id="5228b-102">Počínaje ASP.NET Core 3,0 jsou synchronní operace serveru ve výchozím nastavení zakázané.</span><span class="sxs-lookup"><span data-stu-id="5228b-102">Starting with ASP.NET Core 3.0, synchronous server operations are disabled by default.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5228b-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="5228b-103">Change description</span></span>

<span data-ttu-id="5228b-104">`AllowSynchronousIO` je možnost na každém serveru, který povoluje nebo zakazuje synchronní rozhraní API pro vstupně-výstupní operace jako `HttpRequest.Body.Read`, `HttpResponse.Body.Write`a `Stream.Flush`.</span><span class="sxs-lookup"><span data-stu-id="5228b-104">`AllowSynchronousIO` is an option in each server that enables or disables synchronous IO APIs like `HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush`.</span></span> <span data-ttu-id="5228b-105">Tato rozhraní API jsou dlouhodobě zdrojem vláken vyčerpání a aplikace přestane reagovat.</span><span class="sxs-lookup"><span data-stu-id="5228b-105">These APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="5228b-106">Počínaje verzí ASP.NET Core 3,0 Preview 3 jsou tyto synchronní operace ve výchozím nastavení zakázány.</span><span class="sxs-lookup"><span data-stu-id="5228b-106">Starting in ASP.NET Core 3.0 Preview 3, these synchronous operations are disabled by default.</span></span>

<span data-ttu-id="5228b-107">Ovlivněné servery:</span><span class="sxs-lookup"><span data-stu-id="5228b-107">Affected servers:</span></span>

- <span data-ttu-id="5228b-108">Kestrel</span><span class="sxs-lookup"><span data-stu-id="5228b-108">Kestrel</span></span>
- <span data-ttu-id="5228b-109">HttpSys</span><span class="sxs-lookup"><span data-stu-id="5228b-109">HttpSys</span></span>
- <span data-ttu-id="5228b-110">Vnitroprocesové v rámci služby IIS</span><span class="sxs-lookup"><span data-stu-id="5228b-110">IIS in-process</span></span>
- <span data-ttu-id="5228b-111">TestServer</span><span class="sxs-lookup"><span data-stu-id="5228b-111">TestServer</span></span>

<span data-ttu-id="5228b-112">Očekávat chyby podobné:</span><span class="sxs-lookup"><span data-stu-id="5228b-112">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

<span data-ttu-id="5228b-113">Každý server má možnost `AllowSynchronousIO`, která řídí toto chování a výchozí hodnota pro všechny jsou nyní `false`.</span><span class="sxs-lookup"><span data-stu-id="5228b-113">Each server has an `AllowSynchronousIO` option that controls this behavior and the default for all of them is now `false`.</span></span>

<span data-ttu-id="5228b-114">Chování je také možné přepsat na základě jednotlivých požadavků jako dočasné zmírnění.</span><span class="sxs-lookup"><span data-stu-id="5228b-114">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span> <span data-ttu-id="5228b-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5228b-115">For example:</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

<span data-ttu-id="5228b-116">Pokud máte potíže s `TextWriter` nebo jiným datovým proudem, který volá synchronní rozhraní API v `Dispose`, zavolejte místo toho nové rozhraní API `DisposeAsync`.</span><span class="sxs-lookup"><span data-stu-id="5228b-116">If you have trouble with a `TextWriter` or another stream calling a synchronous API in `Dispose`, call the new `DisposeAsync` API instead.</span></span>

<span data-ttu-id="5228b-117">Diskuzi najdete v tématu [dotnet/aspnetcore # 7644](https://github.com/dotnet/aspnetcore/issues/7644).</span><span class="sxs-lookup"><span data-stu-id="5228b-117">For discussion, see [dotnet/aspnetcore#7644](https://github.com/dotnet/aspnetcore/issues/7644).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5228b-118">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5228b-118">Version introduced</span></span>

<span data-ttu-id="5228b-119">3,0</span><span class="sxs-lookup"><span data-stu-id="5228b-119">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="5228b-120">Staré chování</span><span class="sxs-lookup"><span data-stu-id="5228b-120">Old behavior</span></span>

<span data-ttu-id="5228b-121">ve výchozím nastavení jsou povolené `HttpRequest.Body.Read`, `HttpResponse.Body.Write`a `Stream.Flush`.</span><span class="sxs-lookup"><span data-stu-id="5228b-121">`HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush` were allowed by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="5228b-122">Nové chování</span><span class="sxs-lookup"><span data-stu-id="5228b-122">New behavior</span></span>

<span data-ttu-id="5228b-123">Ve výchozím nastavení nejsou povolena tato synchronní rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="5228b-123">These synchronous APIs are disallowed by default:</span></span>

<span data-ttu-id="5228b-124">Očekávat chyby podobné:</span><span class="sxs-lookup"><span data-stu-id="5228b-124">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a><span data-ttu-id="5228b-125">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="5228b-125">Reason for change</span></span>

<span data-ttu-id="5228b-126">Tato synchronní rozhraní API byla dlouhodobě zdrojem vláken vyčerpání a aplikace přestane reagovat.</span><span class="sxs-lookup"><span data-stu-id="5228b-126">These synchronous APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="5228b-127">Počínaje verzí ASP.NET Core 3,0 Preview 3 jsou synchronní operace ve výchozím nastavení zakázané.</span><span class="sxs-lookup"><span data-stu-id="5228b-127">Starting in ASP.NET Core 3.0 Preview 3, the synchronous operations are disabled by default.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5228b-128">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="5228b-128">Recommended action</span></span>

<span data-ttu-id="5228b-129">Použijte asynchronní verze metod.</span><span class="sxs-lookup"><span data-stu-id="5228b-129">Use the asynchronous versions of the methods.</span></span> <span data-ttu-id="5228b-130">Chování je také možné přepsat na základě jednotlivých požadavků jako dočasné zmírnění.</span><span class="sxs-lookup"><span data-stu-id="5228b-130">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

#### <a name="category"></a><span data-ttu-id="5228b-131">Kategorie</span><span class="sxs-lookup"><span data-stu-id="5228b-131">Category</span></span>

<span data-ttu-id="5228b-132">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5228b-132">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5228b-133">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5228b-133">Affected APIs</span></span>

- <xref:System.IO.Stream.Flush%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.IO.Stream.Flush`
- `Overload:System.IO.Stream.Read`
- `Overload:System.IO.Stream.Write`

-->
