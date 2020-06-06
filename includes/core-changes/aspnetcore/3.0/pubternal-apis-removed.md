---
ms.openlocfilehash: b1fb9647091cecb80b9c2f04ec9b6bb156eb39ba
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2020
ms.locfileid: "84466808"
---
### <a name="pubternal-apis-removed"></a><span data-ttu-id="cb76f-101">Odebrána rozhraní API "Pubternal"</span><span class="sxs-lookup"><span data-stu-id="cb76f-101">"Pubternal" APIs removed</span></span>

<span data-ttu-id="cb76f-102">Aby se lépe zachovala veřejná plocha rozhraní API ASP.NET Core, většina typů v `*.Internal` oborech názvů (označovaných jako :::no-loc text="\"pubternal\""::: rozhraní API) se stane skutečně interní.</span><span class="sxs-lookup"><span data-stu-id="cb76f-102">To better maintain the public API surface of ASP.NET Core, most of the types in `*.Internal` namespaces (referred to as :::no-loc text="\"pubternal\""::: APIs) have become truly internal.</span></span> <span data-ttu-id="cb76f-103">U členů v těchto oborech názvů nikdy nechtěla být podporovaná jako veřejná rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="cb76f-103">Members in these namespaces were never meant to be supported as public-facing APIs.</span></span> <span data-ttu-id="cb76f-104">Rozhraní API se můžou v podverzích poškodit a často se jedná o.</span><span class="sxs-lookup"><span data-stu-id="cb76f-104">The APIs could break in minor releases and often did.</span></span> <span data-ttu-id="cb76f-105">Kód, který závisí na těchto rozhraních API, se při aktualizaci na ASP.NET Core 3,0 přeruší.</span><span class="sxs-lookup"><span data-stu-id="cb76f-105">Code that depends on these APIs breaks when updating to ASP.NET Core 3.0.</span></span>

<span data-ttu-id="cb76f-106">Další informace naleznete v tématech [dotnet/aspnetcore # 4932](https://github.com/dotnet/aspnetcore/issues/4932) a [dotnet/aspnetcore # 11312](https://github.com/dotnet/aspnetcore/issues/11312).</span><span class="sxs-lookup"><span data-stu-id="cb76f-106">For more information, see [dotnet/aspnetcore#4932](https://github.com/dotnet/aspnetcore/issues/4932) and [dotnet/aspnetcore#11312](https://github.com/dotnet/aspnetcore/issues/11312).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="cb76f-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="cb76f-107">Version introduced</span></span>

<span data-ttu-id="cb76f-108">3.0</span><span class="sxs-lookup"><span data-stu-id="cb76f-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="cb76f-109">Staré chování</span><span class="sxs-lookup"><span data-stu-id="cb76f-109">Old behavior</span></span>

<span data-ttu-id="cb76f-110">Ovlivněná rozhraní API jsou označená `public` modifikátorem přístupu a existují v `*.Internal` oborech názvů.</span><span class="sxs-lookup"><span data-stu-id="cb76f-110">The affected APIs are marked with the `public` access modifier and exist in `*.Internal` namespaces.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="cb76f-111">Nové chování</span><span class="sxs-lookup"><span data-stu-id="cb76f-111">New behavior</span></span>

<span data-ttu-id="cb76f-112">Ovlivněná rozhraní API jsou označená modifikátorem [interního](/dotnet/csharp/language-reference/keywords/internal) přístupu a již nemohou být používána kódem mimo toto sestavení.</span><span class="sxs-lookup"><span data-stu-id="cb76f-112">The affected APIs are marked with the [internal](/dotnet/csharp/language-reference/keywords/internal) access modifier and can no longer be used by code outside that assembly.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="cb76f-113">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="cb76f-113">Reason for change</span></span>

<span data-ttu-id="cb76f-114">Pokyny pro tato :::no-loc text="\"pubternal\""::: rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="cb76f-114">The guidance for these :::no-loc text="\"pubternal\""::: APIs was that they:</span></span>

* <span data-ttu-id="cb76f-115">Může se změnit bez předchozího upozornění.</span><span class="sxs-lookup"><span data-stu-id="cb76f-115">Could change without notice.</span></span>
* <span data-ttu-id="cb76f-116">Nevedly se zásady rozhraní .NET, aby se zabránilo zásadním změnám.</span><span class="sxs-lookup"><span data-stu-id="cb76f-116">Weren't subject to .NET policies to prevent breaking changes.</span></span>

<span data-ttu-id="cb76f-117">Ukončení rozhraní API `public` (dokonce i v `*.Internal` oborech názvů) bylo matoucí pro zákazníky.</span><span class="sxs-lookup"><span data-stu-id="cb76f-117">Leaving the APIs `public` (even in the `*.Internal` namespaces) was confusing to customers.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cb76f-118">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="cb76f-118">Recommended action</span></span>

<span data-ttu-id="cb76f-119">Ukončete používání těchto :::no-loc text="\"pubternal\""::: rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="cb76f-119">Stop using these :::no-loc text="\"pubternal\""::: APIs.</span></span> <span data-ttu-id="cb76f-120">Pokud máte dotazy týkající se alternativních rozhraní API, otevřete problém v úložišti [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues) .</span><span class="sxs-lookup"><span data-stu-id="cb76f-120">If you have questions about alternate APIs, open an issue in the [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues) repository.</span></span>

<span data-ttu-id="cb76f-121">Zvažte například následující kód pro ukládání požadavků HTTP do vyrovnávací paměti v projektu ASP.NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="cb76f-121">For example, consider the following HTTP request buffering code in an ASP.NET Core 2.2 project.</span></span> <span data-ttu-id="cb76f-122">`EnableRewind`Metoda rozšíření existuje v `Microsoft.AspNetCore.Http.Internal` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cb76f-122">The `EnableRewind` extension method exists in the `Microsoft.AspNetCore.Http.Internal` namespace.</span></span>

```csharp
HttpContext.Request.EnableRewind();
```

<span data-ttu-id="cb76f-123">V projektu ASP.NET Core 3,0 nahraďte `EnableRewind` volání voláním `EnableBuffering` metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="cb76f-123">In an ASP.NET Core 3.0 project, replace the `EnableRewind` call with a call to the `EnableBuffering` extension method.</span></span> <span data-ttu-id="cb76f-124">Funkce ukládání požadavků do vyrovnávací paměti funguje stejně jako v minulosti.</span><span class="sxs-lookup"><span data-stu-id="cb76f-124">The request buffering feature works as it did in the past.</span></span> <span data-ttu-id="cb76f-125">`EnableBuffering`volá `internal` rozhraní API Now.</span><span class="sxs-lookup"><span data-stu-id="cb76f-125">`EnableBuffering` calls the now `internal` API.</span></span>

```csharp
HttpContext.Request.EnableBuffering();
```

#### <a name="category"></a><span data-ttu-id="cb76f-126">Kategorie</span><span class="sxs-lookup"><span data-stu-id="cb76f-126">Category</span></span>

<span data-ttu-id="cb76f-127">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="cb76f-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cb76f-128">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="cb76f-128">Affected APIs</span></span>

<span data-ttu-id="cb76f-129">Všechna rozhraní API v `Microsoft.AspNetCore.*` `Microsoft.Extensions.*` oborech názvů a, která mají `Internal` segment v názvu oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cb76f-129">All APIs in the `Microsoft.AspNetCore.*` and `Microsoft.Extensions.*` namespaces that have an `Internal` segment in the namespace name.</span></span> <span data-ttu-id="cb76f-130">Příklad:</span><span class="sxs-lookup"><span data-stu-id="cb76f-130">For example:</span></span>

- `Microsoft.AspNetCore.Authentication.Internal`
- `Microsoft.AspNetCore.Builder.Internal`
- `Microsoft.AspNetCore.DataProtection.Cng.Internal`
- `Microsoft.AspNetCore.DataProtection.Internal`
- `Microsoft.AspNetCore.Hosting.Internal`
- `Microsoft.AspNetCore.Http.Internal`
- `Microsoft.AspNetCore.Mvc.Core.Infrastructure`
- `Microsoft.AspNetCore.Mvc.Core.Internal`
- `Microsoft.AspNetCore.Mvc.Cors.Internal`
- `Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `Microsoft.AspNetCore.Mvc.Internal`
- `Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `Microsoft.AspNetCore.Mvc.Razor.Internal`
- `Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`
- `Microsoft.AspNetCore.Rewrite.Internal`
- `Microsoft.AspNetCore.Routing.Internal`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Http`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Infrastructure`
- `Microsoft.AspNetCore.Server.Kestrel.Https.Internal`

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Authentication.Internal`
- `N:Microsoft.AspNetCore.Builder.Internal`
- `N:Microsoft.AspNetCore.DataProtection.Cng.Internal`
- `N:Microsoft.AspNetCore.DataProtection.Internal`
- `N:Microsoft.AspNetCore.Hosting.Internal`
- `N:Microsoft.AspNetCore.Http.Internal`
- `N:Microsoft.AspNetCore.Mvc.Core.Infrastructure`
- `N:Microsoft.AspNetCore.Mvc.Core.Internal`
- `N:Microsoft.AspNetCore.Mvc.Cors.Internal`
- `N:Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `N:Microsoft.AspNetCore.Mvc.Internal`
- `N:Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `N:Microsoft.AspNetCore.Mvc.Razor.Internal`
- `N:Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `N:Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `N:Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`
- `N:Microsoft.AspNetCore.Rewrite.Internal`
- `N:Microsoft.AspNetCore.Routing.Internal`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Http`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Infrastructure`
- `N:Microsoft.AspNetCore.Server.Kestrel.Https.Internal`

-->
