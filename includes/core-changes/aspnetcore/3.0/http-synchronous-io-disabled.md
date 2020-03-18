---
ms.openlocfilehash: 53d2c989120c92f4e2d18f50ce4b364bd4c9b604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901798"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a><span data-ttu-id="67b5a-101">HTTP: Synchronní vi zakázáno na všech serverech</span><span class="sxs-lookup"><span data-stu-id="67b5a-101">HTTP: Synchronous IO disabled in all servers</span></span>

<span data-ttu-id="67b5a-102">Počínaje ASP.NET jádrem 3.0 jsou synchronní operace serveru ve výchozím nastavení zakázány.</span><span class="sxs-lookup"><span data-stu-id="67b5a-102">Starting with ASP.NET Core 3.0, synchronous server operations are disabled by default.</span></span>

#### <a name="change-description"></a><span data-ttu-id="67b5a-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="67b5a-103">Change description</span></span>

<span data-ttu-id="67b5a-104">`AllowSynchronousIO`je možnost na každém serveru, která povoluje nebo `HttpRequest.Body.Read` `HttpResponse.Body.Write`zakazuje `Stream.Flush`synchronní vypovězení vi, jako je , a .</span><span class="sxs-lookup"><span data-stu-id="67b5a-104">`AllowSynchronousIO` is an option in each server that enables or disables synchronous IO APIs like `HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush`.</span></span> <span data-ttu-id="67b5a-105">Tato rozhraní API jsou již dlouho zdrojem hladovění podprocesu a přestane reagovat aplikace.</span><span class="sxs-lookup"><span data-stu-id="67b5a-105">These APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="67b5a-106">Počínaje ASP.NET Core 3.0 Preview 3, tyto synchronní operace jsou ve výchozím nastavení zakázány.</span><span class="sxs-lookup"><span data-stu-id="67b5a-106">Starting in ASP.NET Core 3.0 Preview 3, these synchronous operations are disabled by default.</span></span>

<span data-ttu-id="67b5a-107">Ohrožené servery:</span><span class="sxs-lookup"><span data-stu-id="67b5a-107">Affected servers:</span></span>

- <span data-ttu-id="67b5a-108">Kestrel</span><span class="sxs-lookup"><span data-stu-id="67b5a-108">Kestrel</span></span>
- <span data-ttu-id="67b5a-109">HttpSys</span><span class="sxs-lookup"><span data-stu-id="67b5a-109">HttpSys</span></span>
- <span data-ttu-id="67b5a-110">IIS v průběhu</span><span class="sxs-lookup"><span data-stu-id="67b5a-110">IIS in-process</span></span>
- <span data-ttu-id="67b5a-111">Testovací server</span><span class="sxs-lookup"><span data-stu-id="67b5a-111">TestServer</span></span>

<span data-ttu-id="67b5a-112">Očekávejte chyby podobné:</span><span class="sxs-lookup"><span data-stu-id="67b5a-112">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

<span data-ttu-id="67b5a-113">Každý server `AllowSynchronousIO` má možnost, která řídí toto chování `false`a výchozí pro všechny z nich je nyní .</span><span class="sxs-lookup"><span data-stu-id="67b5a-113">Each server has an `AllowSynchronousIO` option that controls this behavior and the default for all of them is now `false`.</span></span>

<span data-ttu-id="67b5a-114">Chování může být také přepsána na základě požadavku jako dočasné zmírnění.</span><span class="sxs-lookup"><span data-stu-id="67b5a-114">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span> <span data-ttu-id="67b5a-115">Například:</span><span class="sxs-lookup"><span data-stu-id="67b5a-115">For example:</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

<span data-ttu-id="67b5a-116">Pokud máte potíže `TextWriter` s nebo jiný datový proud `Dispose`volání synchronní `DisposeAsync` rozhraní API v , volání nové rozhraní API místo.</span><span class="sxs-lookup"><span data-stu-id="67b5a-116">If you have trouble with a `TextWriter` or another stream calling a synchronous API in `Dispose`, call the new `DisposeAsync` API instead.</span></span>

<span data-ttu-id="67b5a-117">Diskuse naleznete [v tématu dotnet/aspnetcore#7644](https://github.com/dotnet/aspnetcore/issues/7644).</span><span class="sxs-lookup"><span data-stu-id="67b5a-117">For discussion, see [dotnet/aspnetcore#7644](https://github.com/dotnet/aspnetcore/issues/7644).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="67b5a-118">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="67b5a-118">Version introduced</span></span>

<span data-ttu-id="67b5a-119">3.0</span><span class="sxs-lookup"><span data-stu-id="67b5a-119">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="67b5a-120">Staré chování</span><span class="sxs-lookup"><span data-stu-id="67b5a-120">Old behavior</span></span>

<span data-ttu-id="67b5a-121">`HttpRequest.Body.Read`, `HttpResponse.Body.Write`a `Stream.Flush` byly ve výchozím nastavení povoleny.</span><span class="sxs-lookup"><span data-stu-id="67b5a-121">`HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush` were allowed by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="67b5a-122">Nové chování</span><span class="sxs-lookup"><span data-stu-id="67b5a-122">New behavior</span></span>

<span data-ttu-id="67b5a-123">Tato synchronní prostředí API jsou ve výchozím nastavení zakázána:</span><span class="sxs-lookup"><span data-stu-id="67b5a-123">These synchronous APIs are disallowed by default:</span></span>

<span data-ttu-id="67b5a-124">Očekávejte chyby podobné:</span><span class="sxs-lookup"><span data-stu-id="67b5a-124">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a><span data-ttu-id="67b5a-125">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="67b5a-125">Reason for change</span></span>

<span data-ttu-id="67b5a-126">Tato synchronní rozhraní API jsou již dlouho zdrojem hladovění podprocesu a přestane reagovat.</span><span class="sxs-lookup"><span data-stu-id="67b5a-126">These synchronous APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="67b5a-127">Počínaje ASP.NET Core 3.0 Preview 3 jsou synchronní operace ve výchozím nastavení zakázány.</span><span class="sxs-lookup"><span data-stu-id="67b5a-127">Starting in ASP.NET Core 3.0 Preview 3, the synchronous operations are disabled by default.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="67b5a-128">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="67b5a-128">Recommended action</span></span>

<span data-ttu-id="67b5a-129">Použijte asynchronní verze metod.</span><span class="sxs-lookup"><span data-stu-id="67b5a-129">Use the asynchronous versions of the methods.</span></span> <span data-ttu-id="67b5a-130">Chování může být také přepsána na základě požadavku jako dočasné zmírnění.</span><span class="sxs-lookup"><span data-stu-id="67b5a-130">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

#### <a name="category"></a><span data-ttu-id="67b5a-131">Kategorie</span><span class="sxs-lookup"><span data-stu-id="67b5a-131">Category</span></span>

<span data-ttu-id="67b5a-132">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="67b5a-132">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="67b5a-133">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="67b5a-133">Affected APIs</span></span>

- <xref:System.IO.Stream.Flush%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.IO.Stream.Flush`
- `Overload:System.IO.Stream.Read`
- `Overload:System.IO.Stream.Write`

-->
