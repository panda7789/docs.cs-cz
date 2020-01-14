---
ms.openlocfilehash: a8146db1fb54d63d4716b879ce793f7d817cef59
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937303"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a><span data-ttu-id="8a919-101">Shared framework: Assemblies removed from Microsoft.AspNetCore.App</span><span class="sxs-lookup"><span data-stu-id="8a919-101">Shared framework: Assemblies removed from Microsoft.AspNetCore.App</span></span>

<span data-ttu-id="8a919-102">Starting in ASP.NET Core 3.0, the ASP.NET Core shared framework (`Microsoft.AspNetCore.App`) only contains first-party assemblies that are fully developed, supported, and serviceable by Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8a919-102">Starting in ASP.NET Core 3.0, the ASP.NET Core shared framework (`Microsoft.AspNetCore.App`) only contains first-party assemblies that are fully developed, supported, and serviceable by Microsoft.</span></span>

#### <a name="change-description"></a><span data-ttu-id="8a919-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="8a919-103">Change description</span></span>

<span data-ttu-id="8a919-104">Think of the change as the redefining of boundaries for the ASP.NET Core "platform."</span><span class="sxs-lookup"><span data-stu-id="8a919-104">Think of the change as the redefining of boundaries for the ASP.NET Core "platform."</span></span> <span data-ttu-id="8a919-105">The shared framework will be [source-buildable by anybody via GitHub](https://github.com/dotnet/source-build) and will continue to offer the existing benefits of .NET Core shared frameworks to your apps.</span><span class="sxs-lookup"><span data-stu-id="8a919-105">The shared framework will be [source-buildable by anybody via GitHub](https://github.com/dotnet/source-build) and will continue to offer the existing benefits of .NET Core shared frameworks to your apps.</span></span> <span data-ttu-id="8a919-106">Some benefits include smaller deployment size, centralized patching, and faster startup time.</span><span class="sxs-lookup"><span data-stu-id="8a919-106">Some benefits include smaller deployment size, centralized patching, and faster startup time.</span></span>

<span data-ttu-id="8a919-107">As part of the change, some notable breaking changes are introduced in `Microsoft.AspNetCore.App`.</span><span class="sxs-lookup"><span data-stu-id="8a919-107">As part of the change, some notable breaking changes are introduced in `Microsoft.AspNetCore.App`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8a919-108">Version introduced</span><span class="sxs-lookup"><span data-stu-id="8a919-108">Version introduced</span></span>

<span data-ttu-id="8a919-109">3,0</span><span class="sxs-lookup"><span data-stu-id="8a919-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="8a919-110">Old behavior</span><span class="sxs-lookup"><span data-stu-id="8a919-110">Old behavior</span></span>

<span data-ttu-id="8a919-111">Projects referenced `Microsoft.AspNetCore.App` via a `<PackageReference>` element in the project file.</span><span class="sxs-lookup"><span data-stu-id="8a919-111">Projects referenced `Microsoft.AspNetCore.App` via a `<PackageReference>` element in the project file.</span></span>

<span data-ttu-id="8a919-112">Additionally, `Microsoft.AspNetCore.App` contained the following subcomponents:</span><span class="sxs-lookup"><span data-stu-id="8a919-112">Additionally, `Microsoft.AspNetCore.App` contained the following subcomponents:</span></span>

- <span data-ttu-id="8a919-113">Json.NET (`Newtonsoft.Json`)</span><span class="sxs-lookup"><span data-stu-id="8a919-113">Json.NET (`Newtonsoft.Json`)</span></span>
- <span data-ttu-id="8a919-114">Entity Framework Core (assemblies prefixed with `Microsoft.EntityFrameworkCore.`)</span><span class="sxs-lookup"><span data-stu-id="8a919-114">Entity Framework Core (assemblies prefixed with `Microsoft.EntityFrameworkCore.`)</span></span>
- <span data-ttu-id="8a919-115">Roslyn (`Microsoft.CodeAnalysis`)</span><span class="sxs-lookup"><span data-stu-id="8a919-115">Roslyn (`Microsoft.CodeAnalysis`)</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="8a919-116">New behavior</span><span class="sxs-lookup"><span data-stu-id="8a919-116">New behavior</span></span>

<span data-ttu-id="8a919-117">A reference to `Microsoft.AspNetCore.App` no longer requires a `<PackageReference>` element in the project file.</span><span class="sxs-lookup"><span data-stu-id="8a919-117">A reference to `Microsoft.AspNetCore.App` no longer requires a `<PackageReference>` element in the project file.</span></span> <span data-ttu-id="8a919-118">The .NET Core SDK supports a new element called `<FrameworkReference>`, which replaces the use of `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="8a919-118">The .NET Core SDK supports a new element called `<FrameworkReference>`, which replaces the use of `<PackageReference>`.</span></span>

<span data-ttu-id="8a919-119">For more information, see [dotnet/aspnetcore#3612](https://github.com/dotnet/aspnetcore/issues/3612).</span><span class="sxs-lookup"><span data-stu-id="8a919-119">For more information, see [dotnet/aspnetcore#3612](https://github.com/dotnet/aspnetcore/issues/3612).</span></span>

<span data-ttu-id="8a919-120">Entity Framework Core ships as NuGet packages.</span><span class="sxs-lookup"><span data-stu-id="8a919-120">Entity Framework Core ships as NuGet packages.</span></span> <span data-ttu-id="8a919-121">This change aligns the shipping model with all other data access libraries on .NET.</span><span class="sxs-lookup"><span data-stu-id="8a919-121">This change aligns the shipping model with all other data access libraries on .NET.</span></span> <span data-ttu-id="8a919-122">It provides Entity Framework Core the simplest path to continue innovating while supporting the various .NET platforms.</span><span class="sxs-lookup"><span data-stu-id="8a919-122">It provides Entity Framework Core the simplest path to continue innovating while supporting the various .NET platforms.</span></span> <span data-ttu-id="8a919-123">The move of Entity Framework Core out of the shared framework has no impact on its status as a Microsoft-developed, supported, and serviceable library.</span><span class="sxs-lookup"><span data-stu-id="8a919-123">The move of Entity Framework Core out of the shared framework has no impact on its status as a Microsoft-developed, supported, and serviceable library.</span></span> <span data-ttu-id="8a919-124">The [.NET Core support policy](https://www.microsoft.com/net/platform/support-policy) continues to cover it.</span><span class="sxs-lookup"><span data-stu-id="8a919-124">The [.NET Core support policy](https://www.microsoft.com/net/platform/support-policy) continues to cover it.</span></span>

<span data-ttu-id="8a919-125">Json.NET and Entity Framework Core continue to work with ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="8a919-125">Json.NET and Entity Framework Core continue to work with ASP.NET Core.</span></span> <span data-ttu-id="8a919-126">They won't, however, be included in the shared framework.</span><span class="sxs-lookup"><span data-stu-id="8a919-126">They won't, however, be included in the shared framework.</span></span>

<span data-ttu-id="8a919-127">For more information, see [The future of JSON in .NET Core 3.0](https://github.com/dotnet/announcements/issues/90).</span><span class="sxs-lookup"><span data-stu-id="8a919-127">For more information, see [The future of JSON in .NET Core 3.0](https://github.com/dotnet/announcements/issues/90).</span></span> <span data-ttu-id="8a919-128">Also see [the complete list of binaries](https://github.com/dotnet/aspnetcore/issues/3755) removed from the shared framework.</span><span class="sxs-lookup"><span data-stu-id="8a919-128">Also see [the complete list of binaries](https://github.com/dotnet/aspnetcore/issues/3755) removed from the shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="8a919-129">Reason for change</span><span class="sxs-lookup"><span data-stu-id="8a919-129">Reason for change</span></span>

<span data-ttu-id="8a919-130">This change simplifies the consumption of `Microsoft.AspNetCore.App` and reduces the duplication between NuGet packages and shared frameworks.</span><span class="sxs-lookup"><span data-stu-id="8a919-130">This change simplifies the consumption of `Microsoft.AspNetCore.App` and reduces the duplication between NuGet packages and shared frameworks.</span></span>

<span data-ttu-id="8a919-131">For more information on the motivation for this change, see [this blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="8a919-131">For more information on the motivation for this change, see [this blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8a919-132">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="8a919-132">Recommended action</span></span>

<span data-ttu-id="8a919-133">It won't be necessary for projects to consume assemblies in `Microsoft.AspNetCore.App` as NuGet packages.</span><span class="sxs-lookup"><span data-stu-id="8a919-133">It won't be necessary for projects to consume assemblies in `Microsoft.AspNetCore.App` as NuGet packages.</span></span> <span data-ttu-id="8a919-134">Aby se zjednodušilo cílení a použití ASP.NET Core sdílené architektury, mnoho balíčků NuGet dodaných od ASP.NET Core 1,0 se už nevyrábí.</span><span class="sxs-lookup"><span data-stu-id="8a919-134">To simplify the targeting and usage of the ASP.NET Core shared framework, many NuGet packages shipped since ASP.NET Core 1.0 are no longer produced.</span></span> <span data-ttu-id="8a919-135">Rozhraní API, která tyto balíčky poskytují, jsou stále k dispozici aplikacím pomocí `<FrameworkReference>` k `Microsoft.AspNetCore.App`.</span><span class="sxs-lookup"><span data-stu-id="8a919-135">The APIs those packages provide are still available to apps by using a `<FrameworkReference>` to `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="8a919-136">Mezi běžné příklady rozhraní API patří Kestrel, MVC a Razor.</span><span class="sxs-lookup"><span data-stu-id="8a919-136">Common API examples include Kestrel, MVC, and Razor.</span></span>

<span data-ttu-id="8a919-137">Tato změna se nevztahuje na všechny binární soubory, na které se odkazuje pomocí `Microsoft.AspNetCore.App` v ASP.NET Core 2. x.</span><span class="sxs-lookup"><span data-stu-id="8a919-137">This change doesn't apply to all binaries referenced via `Microsoft.AspNetCore.App` in ASP.NET Core 2.x.</span></span> <span data-ttu-id="8a919-138">Mezi významné výjimky patří:</span><span class="sxs-lookup"><span data-stu-id="8a919-138">Notable exceptions include:</span></span>

- <span data-ttu-id="8a919-139">`Microsoft.Extensions` knihovny, které pokračují v cíli .NET Standard, budou k dispozici jako balíčky NuGet (viz https://github.com/dotnet/extensions).</span><span class="sxs-lookup"><span data-stu-id="8a919-139">`Microsoft.Extensions` libraries that continue to target .NET Standard will be available as NuGet packages (see https://github.com/dotnet/extensions).</span></span>
- <span data-ttu-id="8a919-140">Rozhraní API vytvořená ASP.NET Core týmem, která nejsou součástí `Microsoft.AspNetCore.App`.</span><span class="sxs-lookup"><span data-stu-id="8a919-140">APIs produced by the ASP.NET Core team that aren't part of `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="8a919-141">Například následující komponenty jsou k dispozici jako balíčky NuGet:</span><span class="sxs-lookup"><span data-stu-id="8a919-141">For example, the following components are available as NuGet packages:</span></span>
  - <span data-ttu-id="8a919-142">Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="8a919-142">Entity Framework Core</span></span>
  - <span data-ttu-id="8a919-143">Rozhraní API, která poskytují integraci třetí strany</span><span class="sxs-lookup"><span data-stu-id="8a919-143">APIs that provide third-party integration</span></span>
  - <span data-ttu-id="8a919-144">Experimentální funkce</span><span class="sxs-lookup"><span data-stu-id="8a919-144">Experimental features</span></span>
  - <span data-ttu-id="8a919-145">Rozhraní API se závislostmi, které nemohly [splnit požadavky na sdílené rozhraní](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)</span><span class="sxs-lookup"><span data-stu-id="8a919-145">APIs with dependencies that couldn't [fulfill the requirements to be in the shared framework](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)</span></span>
- <span data-ttu-id="8a919-146">Rozšíření pro MVC, která udržují podporu pro Json.NET.</span><span class="sxs-lookup"><span data-stu-id="8a919-146">Extensions to MVC that maintain support for Json.NET.</span></span> <span data-ttu-id="8a919-147">Rozhraní API se poskytne jako balíček NuGet, který podporuje používání Json.NET a MVC.</span><span class="sxs-lookup"><span data-stu-id="8a919-147">An API will be provided as a NuGet package to support using Json.NET and MVC.</span></span>
- <span data-ttu-id="8a919-148">Klient rozhraní .NET pro signalizaci bude nadále podporovat .NET Standard a dodávat jako balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="8a919-148">The SignalR .NET client will continue to support .NET Standard and ship as a NuGet package.</span></span> <span data-ttu-id="8a919-149">Je určený pro použití v mnoha modulech runtime .NET, jako je například Xamarin nebo UWP.</span><span class="sxs-lookup"><span data-stu-id="8a919-149">It's intended for use on many .NET runtimes, such as Xamarin and UWP.</span></span>

<span data-ttu-id="8a919-150">Další informace naleznete v tématu [zastavení výroby balíčků pro sestavení sdílených rozhraní v 3,0](https://github.com/dotnet/aspnetcore/issues/3756).</span><span class="sxs-lookup"><span data-stu-id="8a919-150">For more information, see [Stop producing packages for shared framework assemblies in 3.0](https://github.com/dotnet/aspnetcore/issues/3756).</span></span> <span data-ttu-id="8a919-151">Diskuzi najdete v tématu [dotnet/aspnetcore # 3757](https://github.com/dotnet/aspnetcore/issues/3757).</span><span class="sxs-lookup"><span data-stu-id="8a919-151">For discussion, see [dotnet/aspnetcore#3757](https://github.com/dotnet/aspnetcore/issues/3757).</span></span>

#### <a name="category"></a><span data-ttu-id="8a919-152">Kategorie</span><span class="sxs-lookup"><span data-stu-id="8a919-152">Category</span></span>

<span data-ttu-id="8a919-153">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8a919-153">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8a919-154">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="8a919-154">Affected APIs</span></span>

- <xref:Microsoft.CodeAnalysis?displayProperty=nameWithType>
- <xref:Microsoft.EntityFrameworkCore?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.CodeAnalysis`
- `N:Microsoft.EntityFrameworkCore`

-->
