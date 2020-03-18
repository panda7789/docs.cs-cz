---
ms.openlocfilehash: a8146db1fb54d63d4716b879ce793f7d817cef59
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937303"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a><span data-ttu-id="3a7e6-101">Sdílený rámec: Sestavení odebraná z microsoft.aspNetCore.App</span><span class="sxs-lookup"><span data-stu-id="3a7e6-101">Shared framework: Assemblies removed from Microsoft.AspNetCore.App</span></span>

<span data-ttu-id="3a7e6-102">Počínaje ASP.NET jádrem 3.0 obsahuje sdílený`Microsoft.AspNetCore.App`rámec ASP.NET Core ( ) pouze sestavení první strany, která jsou plně vyvinutá, podporovaná a opravitelná společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3a7e6-102">Starting in ASP.NET Core 3.0, the ASP.NET Core shared framework (`Microsoft.AspNetCore.App`) only contains first-party assemblies that are fully developed, supported, and serviceable by Microsoft.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3a7e6-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="3a7e6-103">Change description</span></span>

<span data-ttu-id="3a7e6-104">Představte si změnu jako předefinování hranic pro ASP.NET "platformu Core".</span><span class="sxs-lookup"><span data-stu-id="3a7e6-104">Think of the change as the redefining of boundaries for the ASP.NET Core "platform."</span></span> <span data-ttu-id="3a7e6-105">Sdílený rámec bude [vytvářet kdokoli prostřednictvím GitHubu](https://github.com/dotnet/source-build) a bude i nadále nabízet existující výhody sdílených rozhraní .NET Core vašim aplikacím.</span><span class="sxs-lookup"><span data-stu-id="3a7e6-105">The shared framework will be [source-buildable by anybody via GitHub](https://github.com/dotnet/source-build) and will continue to offer the existing benefits of .NET Core shared frameworks to your apps.</span></span> <span data-ttu-id="3a7e6-106">Mezi výhody patří menší velikost nasazení, centralizované opravy a rychlejší spuštění.</span><span class="sxs-lookup"><span data-stu-id="3a7e6-106">Some benefits include smaller deployment size, centralized patching, and faster startup time.</span></span>

<span data-ttu-id="3a7e6-107">Jako součást změny, některé pozoruhodné lámání změny `Microsoft.AspNetCore.App`jsou zavedeny v .</span><span class="sxs-lookup"><span data-stu-id="3a7e6-107">As part of the change, some notable breaking changes are introduced in `Microsoft.AspNetCore.App`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3a7e6-108">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="3a7e6-108">Version introduced</span></span>

<span data-ttu-id="3a7e6-109">3.0</span><span class="sxs-lookup"><span data-stu-id="3a7e6-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="3a7e6-110">Staré chování</span><span class="sxs-lookup"><span data-stu-id="3a7e6-110">Old behavior</span></span>

<span data-ttu-id="3a7e6-111">Projekty `Microsoft.AspNetCore.App` odkazované `<PackageReference>` prostřednictvím prvku v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="3a7e6-111">Projects referenced `Microsoft.AspNetCore.App` via a `<PackageReference>` element in the project file.</span></span>

<span data-ttu-id="3a7e6-112">Kromě toho `Microsoft.AspNetCore.App` obsahuje následující dílčí součásti:</span><span class="sxs-lookup"><span data-stu-id="3a7e6-112">Additionally, `Microsoft.AspNetCore.App` contained the following subcomponents:</span></span>

- <span data-ttu-id="3a7e6-113">Json.NET`Newtonsoft.Json`( )</span><span class="sxs-lookup"><span data-stu-id="3a7e6-113">Json.NET (`Newtonsoft.Json`)</span></span>
- <span data-ttu-id="3a7e6-114">Core frameworku entity (sestavy `Microsoft.EntityFrameworkCore.`s předponou )</span><span class="sxs-lookup"><span data-stu-id="3a7e6-114">Entity Framework Core (assemblies prefixed with `Microsoft.EntityFrameworkCore.`)</span></span>
- <span data-ttu-id="3a7e6-115">Roslyn`Microsoft.CodeAnalysis`( )</span><span class="sxs-lookup"><span data-stu-id="3a7e6-115">Roslyn (`Microsoft.CodeAnalysis`)</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="3a7e6-116">Nové chování</span><span class="sxs-lookup"><span data-stu-id="3a7e6-116">New behavior</span></span>

<span data-ttu-id="3a7e6-117">Odkaz na `Microsoft.AspNetCore.App` již nevyžaduje `<PackageReference>` prvek v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="3a7e6-117">A reference to `Microsoft.AspNetCore.App` no longer requires a `<PackageReference>` element in the project file.</span></span> <span data-ttu-id="3a7e6-118">Sada .NET Core SDK podporuje `<FrameworkReference>`nový prvek s `<PackageReference>`názvem , který nahrazuje použití .</span><span class="sxs-lookup"><span data-stu-id="3a7e6-118">The .NET Core SDK supports a new element called `<FrameworkReference>`, which replaces the use of `<PackageReference>`.</span></span>

<span data-ttu-id="3a7e6-119">Další informace naleznete [v tématu dotnet/aspnetcore#3612](https://github.com/dotnet/aspnetcore/issues/3612).</span><span class="sxs-lookup"><span data-stu-id="3a7e6-119">For more information, see [dotnet/aspnetcore#3612](https://github.com/dotnet/aspnetcore/issues/3612).</span></span>

<span data-ttu-id="3a7e6-120">Entity Framework Core dodává jako balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="3a7e6-120">Entity Framework Core ships as NuGet packages.</span></span> <span data-ttu-id="3a7e6-121">Tato změna zarovná model expedice se všemi ostatními knihovnami přístupu k datům v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="3a7e6-121">This change aligns the shipping model with all other data access libraries on .NET.</span></span> <span data-ttu-id="3a7e6-122">Poskytuje entity Framework Core nejjednodušší cestu k pokračování inovace při podpoře různých platforem .NET.</span><span class="sxs-lookup"><span data-stu-id="3a7e6-122">It provides Entity Framework Core the simplest path to continue innovating while supporting the various .NET platforms.</span></span> <span data-ttu-id="3a7e6-123">Přesunutí jádra entity frameworku ze sdíleného rozhraní nemá žádný vliv na jeho stav jako knihovny vyvinuté společností Microsoft, podporované a opravitelné.</span><span class="sxs-lookup"><span data-stu-id="3a7e6-123">The move of Entity Framework Core out of the shared framework has no impact on its status as a Microsoft-developed, supported, and serviceable library.</span></span> <span data-ttu-id="3a7e6-124">[Zásady podpory .NET Core](https://www.microsoft.com/net/platform/support-policy) nadále pokrývají.</span><span class="sxs-lookup"><span data-stu-id="3a7e6-124">The [.NET Core support policy](https://www.microsoft.com/net/platform/support-policy) continues to cover it.</span></span>

<span data-ttu-id="3a7e6-125">Json.NET a Core entity nadále pracují s ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="3a7e6-125">Json.NET and Entity Framework Core continue to work with ASP.NET Core.</span></span> <span data-ttu-id="3a7e6-126">Nebudou však zahrnuty do sdíleného rámce.</span><span class="sxs-lookup"><span data-stu-id="3a7e6-126">They won't, however, be included in the shared framework.</span></span>

<span data-ttu-id="3a7e6-127">Další informace naleznete [v tématu Budoucnost JSON v .NET Core 3.0](https://github.com/dotnet/announcements/issues/90).</span><span class="sxs-lookup"><span data-stu-id="3a7e6-127">For more information, see [The future of JSON in .NET Core 3.0](https://github.com/dotnet/announcements/issues/90).</span></span> <span data-ttu-id="3a7e6-128">Podívejte se také [na úplný seznam binárních souborů](https://github.com/dotnet/aspnetcore/issues/3755) odebraných ze sdíleného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3a7e6-128">Also see [the complete list of binaries](https://github.com/dotnet/aspnetcore/issues/3755) removed from the shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3a7e6-129">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="3a7e6-129">Reason for change</span></span>

<span data-ttu-id="3a7e6-130">Tato změna zjednodušuje `Microsoft.AspNetCore.App` spotřebu a snižuje duplicitu mezi balíčky NuGet a sdílené architektury.</span><span class="sxs-lookup"><span data-stu-id="3a7e6-130">This change simplifies the consumption of `Microsoft.AspNetCore.App` and reduces the duplication between NuGet packages and shared frameworks.</span></span>

<span data-ttu-id="3a7e6-131">Další informace o motivaci k této změně naleznete v [tomto příspěvku blogu](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="3a7e6-131">For more information on the motivation for this change, see [this blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3a7e6-132">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="3a7e6-132">Recommended action</span></span>

<span data-ttu-id="3a7e6-133">Nebude nutné pro projekty využívat sestavení `Microsoft.AspNetCore.App` jako balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="3a7e6-133">It won't be necessary for projects to consume assemblies in `Microsoft.AspNetCore.App` as NuGet packages.</span></span> <span data-ttu-id="3a7e6-134">Pro zjednodušení cílení a využití sdíleného rozhraní ASP.NET Core se již nevyrábí mnoho balíčků NuGet dodávaných od ASP.NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="3a7e6-134">To simplify the targeting and usage of the ASP.NET Core shared framework, many NuGet packages shipped since ASP.NET Core 1.0 are no longer produced.</span></span> <span data-ttu-id="3a7e6-135">Rozhraní API, která tyto balíčky poskytují, `<FrameworkReference>` `Microsoft.AspNetCore.App`jsou stále k dispozici aplikacím pomocí a to .</span><span class="sxs-lookup"><span data-stu-id="3a7e6-135">The APIs those packages provide are still available to apps by using a `<FrameworkReference>` to `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="3a7e6-136">Běžné příklady rozhraní API zahrnují Kestrel, MVC a Razor.</span><span class="sxs-lookup"><span data-stu-id="3a7e6-136">Common API examples include Kestrel, MVC, and Razor.</span></span>

<span data-ttu-id="3a7e6-137">Tato změna se nevztahuje na všechny `Microsoft.AspNetCore.App` binární soubory, na které odkazuje v ASP.NET Jádrem 2.x.</span><span class="sxs-lookup"><span data-stu-id="3a7e6-137">This change doesn't apply to all binaries referenced via `Microsoft.AspNetCore.App` in ASP.NET Core 2.x.</span></span> <span data-ttu-id="3a7e6-138">Mezi významné výjimky patří:</span><span class="sxs-lookup"><span data-stu-id="3a7e6-138">Notable exceptions include:</span></span>

- <span data-ttu-id="3a7e6-139">`Microsoft.Extensions`knihovny, které budou i nadále cílit na https://github.com/dotnet/extensions)standard .NET, budou k dispozici jako balíčky NuGet (viz .</span><span class="sxs-lookup"><span data-stu-id="3a7e6-139">`Microsoft.Extensions` libraries that continue to target .NET Standard will be available as NuGet packages (see https://github.com/dotnet/extensions).</span></span>
- <span data-ttu-id="3a7e6-140">API vytvořená týmem ASP.NET Core, která `Microsoft.AspNetCore.App`nejsou součástí aplikace .</span><span class="sxs-lookup"><span data-stu-id="3a7e6-140">APIs produced by the ASP.NET Core team that aren't part of `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="3a7e6-141">Například následující součásti jsou k dispozici jako balíčky NuGet:</span><span class="sxs-lookup"><span data-stu-id="3a7e6-141">For example, the following components are available as NuGet packages:</span></span>
  - <span data-ttu-id="3a7e6-142">Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="3a7e6-142">Entity Framework Core</span></span>
  - <span data-ttu-id="3a7e6-143">API, která poskytují integraci třetích stran</span><span class="sxs-lookup"><span data-stu-id="3a7e6-143">APIs that provide third-party integration</span></span>
  - <span data-ttu-id="3a7e6-144">Experimentální funkce</span><span class="sxs-lookup"><span data-stu-id="3a7e6-144">Experimental features</span></span>
  - <span data-ttu-id="3a7e6-145">Rozhraní API se závislostmi, které [nemohly splnit požadavky na být ve sdíleném rámci](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)</span><span class="sxs-lookup"><span data-stu-id="3a7e6-145">APIs with dependencies that couldn't [fulfill the requirements to be in the shared framework](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)</span></span>
- <span data-ttu-id="3a7e6-146">Rozšíření MVC, které udržují podporu pro Json.NET.</span><span class="sxs-lookup"><span data-stu-id="3a7e6-146">Extensions to MVC that maintain support for Json.NET.</span></span> <span data-ttu-id="3a7e6-147">Rozhraní API bude k dispozici jako balíček NuGet pro podporu pomocí Json.NET a MVC.</span><span class="sxs-lookup"><span data-stu-id="3a7e6-147">An API will be provided as a NuGet package to support using Json.NET and MVC.</span></span>
- <span data-ttu-id="3a7e6-148">Klient SignalR .NET bude nadále podporovat standard .NET a doručovat jako balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="3a7e6-148">The SignalR .NET client will continue to support .NET Standard and ship as a NuGet package.</span></span> <span data-ttu-id="3a7e6-149">Je určen pro použití v mnoha runčasech .NET, jako je Například Xamarin a UPW.</span><span class="sxs-lookup"><span data-stu-id="3a7e6-149">It's intended for use on many .NET runtimes, such as Xamarin and UWP.</span></span>

<span data-ttu-id="3a7e6-150">Další informace naleznete [v tématu Stop vyrábějící balíčky pro sestavení sdílené architektury v 3.0](https://github.com/dotnet/aspnetcore/issues/3756).</span><span class="sxs-lookup"><span data-stu-id="3a7e6-150">For more information, see [Stop producing packages for shared framework assemblies in 3.0](https://github.com/dotnet/aspnetcore/issues/3756).</span></span> <span data-ttu-id="3a7e6-151">Diskuse naleznete [v tématu dotnet/aspnetcore#3757](https://github.com/dotnet/aspnetcore/issues/3757).</span><span class="sxs-lookup"><span data-stu-id="3a7e6-151">For discussion, see [dotnet/aspnetcore#3757](https://github.com/dotnet/aspnetcore/issues/3757).</span></span>

#### <a name="category"></a><span data-ttu-id="3a7e6-152">Kategorie</span><span class="sxs-lookup"><span data-stu-id="3a7e6-152">Category</span></span>

<span data-ttu-id="3a7e6-153">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="3a7e6-153">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3a7e6-154">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="3a7e6-154">Affected APIs</span></span>

- <xref:Microsoft.CodeAnalysis?displayProperty=nameWithType>
- <xref:Microsoft.EntityFrameworkCore?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.CodeAnalysis`
- `N:Microsoft.EntityFrameworkCore`

-->
