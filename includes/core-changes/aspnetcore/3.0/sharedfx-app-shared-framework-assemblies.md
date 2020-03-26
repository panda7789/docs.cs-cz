---
ms.openlocfilehash: 64e854b06895ca54a9ab9870b85868788a731c00
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2020
ms.locfileid: "79549609"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a><span data-ttu-id="0bc1e-101">Sdílený rámec: Sestavení odebraná z microsoft.aspNetCore.App</span><span class="sxs-lookup"><span data-stu-id="0bc1e-101">Shared framework: Assemblies removed from Microsoft.AspNetCore.App</span></span>

<span data-ttu-id="0bc1e-102">Počínaje ASP.NET jádrem 3.0 obsahuje sdílený`Microsoft.AspNetCore.App`rámec ASP.NET Core ( ) pouze sestavení první strany, která jsou plně vyvinutá, podporovaná a opravitelná společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0bc1e-102">Starting in ASP.NET Core 3.0, the ASP.NET Core shared framework (`Microsoft.AspNetCore.App`) only contains first-party assemblies that are fully developed, supported, and serviceable by Microsoft.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0bc1e-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="0bc1e-103">Change description</span></span>

<span data-ttu-id="0bc1e-104">Představte si změnu jako předefinování hranic pro ASP.NET "platformu Core".</span><span class="sxs-lookup"><span data-stu-id="0bc1e-104">Think of the change as the redefining of boundaries for the ASP.NET Core "platform."</span></span> <span data-ttu-id="0bc1e-105">Sdílený rámec bude [vytvářet kdokoli prostřednictvím GitHubu](https://github.com/dotnet/source-build) a bude i nadále nabízet existující výhody sdílených rozhraní .NET Core vašim aplikacím.</span><span class="sxs-lookup"><span data-stu-id="0bc1e-105">The shared framework will be [source-buildable by anybody via GitHub](https://github.com/dotnet/source-build) and will continue to offer the existing benefits of .NET Core shared frameworks to your apps.</span></span> <span data-ttu-id="0bc1e-106">Mezi výhody patří menší velikost nasazení, centralizované opravy a rychlejší spuštění.</span><span class="sxs-lookup"><span data-stu-id="0bc1e-106">Some benefits include smaller deployment size, centralized patching, and faster startup time.</span></span>

<span data-ttu-id="0bc1e-107">Jako součást změny, některé pozoruhodné lámání změny `Microsoft.AspNetCore.App`jsou zavedeny v .</span><span class="sxs-lookup"><span data-stu-id="0bc1e-107">As part of the change, some notable breaking changes are introduced in `Microsoft.AspNetCore.App`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0bc1e-108">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="0bc1e-108">Version introduced</span></span>

<span data-ttu-id="0bc1e-109">3.0</span><span class="sxs-lookup"><span data-stu-id="0bc1e-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0bc1e-110">Staré chování</span><span class="sxs-lookup"><span data-stu-id="0bc1e-110">Old behavior</span></span>

<span data-ttu-id="0bc1e-111">Projekty `Microsoft.AspNetCore.App` odkazované `<PackageReference>` prostřednictvím prvku v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="0bc1e-111">Projects referenced `Microsoft.AspNetCore.App` via a `<PackageReference>` element in the project file.</span></span>

<span data-ttu-id="0bc1e-112">Kromě toho `Microsoft.AspNetCore.App` obsahuje následující dílčí součásti:</span><span class="sxs-lookup"><span data-stu-id="0bc1e-112">Additionally, `Microsoft.AspNetCore.App` contained the following subcomponents:</span></span>

- <span data-ttu-id="0bc1e-113">Json.NET`Newtonsoft.Json`( )</span><span class="sxs-lookup"><span data-stu-id="0bc1e-113">Json.NET (`Newtonsoft.Json`)</span></span>
- <span data-ttu-id="0bc1e-114">Core frameworku entity (sestavy `Microsoft.EntityFrameworkCore.`s předponou )</span><span class="sxs-lookup"><span data-stu-id="0bc1e-114">Entity Framework Core (assemblies prefixed with `Microsoft.EntityFrameworkCore.`)</span></span>
- <span data-ttu-id="0bc1e-115">Roslyn`Microsoft.CodeAnalysis`( )</span><span class="sxs-lookup"><span data-stu-id="0bc1e-115">Roslyn (`Microsoft.CodeAnalysis`)</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="0bc1e-116">Nové chování</span><span class="sxs-lookup"><span data-stu-id="0bc1e-116">New behavior</span></span>

<span data-ttu-id="0bc1e-117">Odkaz na `Microsoft.AspNetCore.App` již nevyžaduje `<PackageReference>` prvek v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="0bc1e-117">A reference to `Microsoft.AspNetCore.App` no longer requires a `<PackageReference>` element in the project file.</span></span> <span data-ttu-id="0bc1e-118">Sada .NET Core SDK podporuje `<FrameworkReference>`nový prvek s `<PackageReference>`názvem , který nahrazuje použití .</span><span class="sxs-lookup"><span data-stu-id="0bc1e-118">The .NET Core SDK supports a new element called `<FrameworkReference>`, which replaces the use of `<PackageReference>`.</span></span>

<span data-ttu-id="0bc1e-119">Další informace naleznete [v tématu dotnet/aspnetcore#3612](https://github.com/dotnet/aspnetcore/issues/3612).</span><span class="sxs-lookup"><span data-stu-id="0bc1e-119">For more information, see [dotnet/aspnetcore#3612](https://github.com/dotnet/aspnetcore/issues/3612).</span></span>

<span data-ttu-id="0bc1e-120">Entity Framework Core dodává jako balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="0bc1e-120">Entity Framework Core ships as NuGet packages.</span></span> <span data-ttu-id="0bc1e-121">Tato změna zarovná model expedice se všemi ostatními knihovnami přístupu k datům v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="0bc1e-121">This change aligns the shipping model with all other data access libraries on .NET.</span></span> <span data-ttu-id="0bc1e-122">Poskytuje entity Framework Core nejjednodušší cestu k pokračování inovace při podpoře různých platforem .NET.</span><span class="sxs-lookup"><span data-stu-id="0bc1e-122">It provides Entity Framework Core the simplest path to continue innovating while supporting the various .NET platforms.</span></span> <span data-ttu-id="0bc1e-123">Přesunutí jádra entity frameworku ze sdíleného rozhraní nemá žádný vliv na jeho stav jako knihovny vyvinuté společností Microsoft, podporované a opravitelné.</span><span class="sxs-lookup"><span data-stu-id="0bc1e-123">The move of Entity Framework Core out of the shared framework has no impact on its status as a Microsoft-developed, supported, and serviceable library.</span></span> <span data-ttu-id="0bc1e-124">[Zásady podpory .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nadále pokrývají.</span><span class="sxs-lookup"><span data-stu-id="0bc1e-124">The [.NET Core support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) continues to cover it.</span></span>

<span data-ttu-id="0bc1e-125">Json.NET a Core entity nadále pracují s ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0bc1e-125">Json.NET and Entity Framework Core continue to work with ASP.NET Core.</span></span> <span data-ttu-id="0bc1e-126">Nebudou však zahrnuty do sdíleného rámce.</span><span class="sxs-lookup"><span data-stu-id="0bc1e-126">They won't, however, be included in the shared framework.</span></span>

<span data-ttu-id="0bc1e-127">Další informace naleznete [v tématu Budoucnost JSON v .NET Core 3.0](https://github.com/dotnet/announcements/issues/90).</span><span class="sxs-lookup"><span data-stu-id="0bc1e-127">For more information, see [The future of JSON in .NET Core 3.0](https://github.com/dotnet/announcements/issues/90).</span></span> <span data-ttu-id="0bc1e-128">Podívejte se také [na úplný seznam binárních souborů](https://github.com/dotnet/aspnetcore/issues/3755) odebraných ze sdíleného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0bc1e-128">Also see [the complete list of binaries](https://github.com/dotnet/aspnetcore/issues/3755) removed from the shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0bc1e-129">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="0bc1e-129">Reason for change</span></span>

<span data-ttu-id="0bc1e-130">Tato změna zjednodušuje `Microsoft.AspNetCore.App` spotřebu a snižuje duplicitu mezi balíčky NuGet a sdílené architektury.</span><span class="sxs-lookup"><span data-stu-id="0bc1e-130">This change simplifies the consumption of `Microsoft.AspNetCore.App` and reduces the duplication between NuGet packages and shared frameworks.</span></span>

<span data-ttu-id="0bc1e-131">Další informace o motivaci k této změně naleznete v [tomto příspěvku blogu](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="0bc1e-131">For more information on the motivation for this change, see [this blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0bc1e-132">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="0bc1e-132">Recommended action</span></span>

<span data-ttu-id="0bc1e-133">Nebude nutné pro projekty využívat sestavení `Microsoft.AspNetCore.App` jako balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="0bc1e-133">It won't be necessary for projects to consume assemblies in `Microsoft.AspNetCore.App` as NuGet packages.</span></span> <span data-ttu-id="0bc1e-134">Pro zjednodušení cílení a využití sdíleného rozhraní ASP.NET Core se již nevyrábí mnoho balíčků NuGet dodávaných od ASP.NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="0bc1e-134">To simplify the targeting and usage of the ASP.NET Core shared framework, many NuGet packages shipped since ASP.NET Core 1.0 are no longer produced.</span></span> <span data-ttu-id="0bc1e-135">Rozhraní API, která tyto balíčky poskytují, `<FrameworkReference>` `Microsoft.AspNetCore.App`jsou stále k dispozici aplikacím pomocí a to .</span><span class="sxs-lookup"><span data-stu-id="0bc1e-135">The APIs those packages provide are still available to apps by using a `<FrameworkReference>` to `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="0bc1e-136">Běžné příklady rozhraní API zahrnují Kestrel, MVC a Razor.</span><span class="sxs-lookup"><span data-stu-id="0bc1e-136">Common API examples include Kestrel, MVC, and Razor.</span></span>

<span data-ttu-id="0bc1e-137">Tato změna se nevztahuje na všechny `Microsoft.AspNetCore.App` binární soubory, na které odkazuje v ASP.NET Jádrem 2.x.</span><span class="sxs-lookup"><span data-stu-id="0bc1e-137">This change doesn't apply to all binaries referenced via `Microsoft.AspNetCore.App` in ASP.NET Core 2.x.</span></span> <span data-ttu-id="0bc1e-138">Mezi významné výjimky patří:</span><span class="sxs-lookup"><span data-stu-id="0bc1e-138">Notable exceptions include:</span></span>

- <span data-ttu-id="0bc1e-139">`Microsoft.Extensions`knihovny, které budou i nadále cílit na https://github.com/dotnet/extensions)standard .NET, budou k dispozici jako balíčky NuGet (viz .</span><span class="sxs-lookup"><span data-stu-id="0bc1e-139">`Microsoft.Extensions` libraries that continue to target .NET Standard will be available as NuGet packages (see https://github.com/dotnet/extensions).</span></span>
- <span data-ttu-id="0bc1e-140">API vytvořená týmem ASP.NET Core, která `Microsoft.AspNetCore.App`nejsou součástí aplikace .</span><span class="sxs-lookup"><span data-stu-id="0bc1e-140">APIs produced by the ASP.NET Core team that aren't part of `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="0bc1e-141">Například následující součásti jsou k dispozici jako balíčky NuGet:</span><span class="sxs-lookup"><span data-stu-id="0bc1e-141">For example, the following components are available as NuGet packages:</span></span>
  - <span data-ttu-id="0bc1e-142">Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="0bc1e-142">Entity Framework Core</span></span>
  - <span data-ttu-id="0bc1e-143">API, která poskytují integraci třetích stran</span><span class="sxs-lookup"><span data-stu-id="0bc1e-143">APIs that provide third-party integration</span></span>
  - <span data-ttu-id="0bc1e-144">Experimentální funkce</span><span class="sxs-lookup"><span data-stu-id="0bc1e-144">Experimental features</span></span>
  - <span data-ttu-id="0bc1e-145">Rozhraní API se závislostmi, které [nemohly splnit požadavky na být ve sdíleném rámci](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)</span><span class="sxs-lookup"><span data-stu-id="0bc1e-145">APIs with dependencies that couldn't [fulfill the requirements to be in the shared framework](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)</span></span>
- <span data-ttu-id="0bc1e-146">Rozšíření MVC, které udržují podporu pro Json.NET.</span><span class="sxs-lookup"><span data-stu-id="0bc1e-146">Extensions to MVC that maintain support for Json.NET.</span></span> <span data-ttu-id="0bc1e-147">Rozhraní API bude k dispozici jako balíček NuGet pro podporu pomocí Json.NET a MVC.</span><span class="sxs-lookup"><span data-stu-id="0bc1e-147">An API will be provided as a NuGet package to support using Json.NET and MVC.</span></span>
- <span data-ttu-id="0bc1e-148">Klient SignalR .NET bude nadále podporovat standard .NET a doručovat jako balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="0bc1e-148">The SignalR .NET client will continue to support .NET Standard and ship as a NuGet package.</span></span> <span data-ttu-id="0bc1e-149">Je určen pro použití v mnoha runčasech .NET, jako je Například Xamarin a UPW.</span><span class="sxs-lookup"><span data-stu-id="0bc1e-149">It's intended for use on many .NET runtimes, such as Xamarin and UWP.</span></span>

<span data-ttu-id="0bc1e-150">Další informace naleznete [v tématu Stop vyrábějící balíčky pro sestavení sdílené architektury v 3.0](https://github.com/dotnet/aspnetcore/issues/3756).</span><span class="sxs-lookup"><span data-stu-id="0bc1e-150">For more information, see [Stop producing packages for shared framework assemblies in 3.0](https://github.com/dotnet/aspnetcore/issues/3756).</span></span> <span data-ttu-id="0bc1e-151">Diskuse naleznete [v tématu dotnet/aspnetcore#3757](https://github.com/dotnet/aspnetcore/issues/3757).</span><span class="sxs-lookup"><span data-stu-id="0bc1e-151">For discussion, see [dotnet/aspnetcore#3757](https://github.com/dotnet/aspnetcore/issues/3757).</span></span>

#### <a name="category"></a><span data-ttu-id="0bc1e-152">Kategorie</span><span class="sxs-lookup"><span data-stu-id="0bc1e-152">Category</span></span>

<span data-ttu-id="0bc1e-153">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0bc1e-153">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0bc1e-154">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0bc1e-154">Affected APIs</span></span>

- <xref:Microsoft.CodeAnalysis?displayProperty=nameWithType>
- <xref:Microsoft.EntityFrameworkCore?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.CodeAnalysis`
- `N:Microsoft.EntityFrameworkCore`

-->
