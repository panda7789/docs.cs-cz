---
ms.openlocfilehash: 2094da7ec94028c112d6683620ac1146a1544dab
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446966"
---
### <a name="localization-pubternal-apis-removed"></a><span data-ttu-id="5f838-101">Lokalizace: rozhraní API "Pubternal" byla odebrána</span><span class="sxs-lookup"><span data-stu-id="5f838-101">Localization: "Pubternal" APIs removed</span></span>

<span data-ttu-id="5f838-102">Aby se lépe zachovala veřejná plocha rozhraní API ASP.NET Core, :::no-loc text="\"pubternal\""::: odstranila se některá rozhraní API lokalizace.</span><span class="sxs-lookup"><span data-stu-id="5f838-102">To better maintain the public API surface of ASP.NET Core, some :::no-loc text="\"pubternal\""::: localization APIs were removed.</span></span> <span data-ttu-id="5f838-103">:::no-loc text="\"pubternal\"":::Rozhraní API má `public` modifikátor přístupu a je definováno v oboru názvů, který implikuje [vnitřní](/dotnet/csharp/language-reference/keywords/internal) záměr.</span><span class="sxs-lookup"><span data-stu-id="5f838-103">A :::no-loc text="\"pubternal\""::: API has a `public` access modifier and is defined in a namespace that implies an [internal](/dotnet/csharp/language-reference/keywords/internal) intent.</span></span>

<span data-ttu-id="5f838-104">Diskuzi najdete v tématu [dotnet/aspnetcore # 22291](https://github.com/dotnet/aspnetcore/issues/22291).</span><span class="sxs-lookup"><span data-stu-id="5f838-104">For discussion, see [dotnet/aspnetcore#22291](https://github.com/dotnet/aspnetcore/issues/22291).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5f838-105">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5f838-105">Version introduced</span></span>

<span data-ttu-id="5f838-106">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="5f838-106">5.0 Preview 6</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="5f838-107">Staré chování</span><span class="sxs-lookup"><span data-stu-id="5f838-107">Old behavior</span></span>

<span data-ttu-id="5f838-108">Následující rozhraní API `public` :</span><span class="sxs-lookup"><span data-stu-id="5f838-108">The following APIs were `public`:</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <span data-ttu-id="5f838-109">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` přetížení konstruktoru přijímají některý z následujících typů parametrů:</span><span class="sxs-lookup"><span data-stu-id="5f838-109">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

#### <a name="new-behavior"></a><span data-ttu-id="5f838-110">Nové chování</span><span class="sxs-lookup"><span data-stu-id="5f838-110">New behavior</span></span>

<span data-ttu-id="5f838-111">Následující seznam popisuje změny:</span><span class="sxs-lookup"><span data-stu-id="5f838-111">The following list outlines the changes:</span></span>

- <span data-ttu-id="5f838-112">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper` stalo `Microsoft.Extensions.Localization.AssemblyWrapper` a je nyní `internal` .</span><span class="sxs-lookup"><span data-stu-id="5f838-112">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper` became `Microsoft.Extensions.Localization.AssemblyWrapper` and is now `internal`.</span></span>
- <span data-ttu-id="5f838-113">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider` stalo `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` a je nyní `internal` .</span><span class="sxs-lookup"><span data-stu-id="5f838-113">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider` became `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` and is now `internal`.</span></span>
- <span data-ttu-id="5f838-114">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` přetížení konstruktoru, který přijímá některý z následujících typů parametrů, jsou nyní `internal` :</span><span class="sxs-lookup"><span data-stu-id="5f838-114">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types are now `internal`:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

#### <a name="reason-for-change"></a><span data-ttu-id="5f838-115">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="5f838-115">Reason for change</span></span>

<span data-ttu-id="5f838-116">Je vysvětleno podrobnější informace na [ASPNET/oznámeních # hodnoty 377](https://github.com/aspnet/Announcements/issues/377#issue-473651882), :::no-loc text="\"pubternal\""::: typy byly odebrány z `public` povrchu rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="5f838-116">Explained more thoroughly at [aspnet/Announcements#377](https://github.com/aspnet/Announcements/issues/377#issue-473651882), :::no-loc text="\"pubternal\""::: types were removed from the `public` API surface.</span></span> <span data-ttu-id="5f838-117">Tyto změny přizpůsobují více tříd k tomuto rozhodnutí o návrhu.</span><span class="sxs-lookup"><span data-stu-id="5f838-117">These changes adapt more classes to that design decision.</span></span> <span data-ttu-id="5f838-118">Příslušné třídy byly určeny jako body rozšíření pro interní testování týmu.</span><span class="sxs-lookup"><span data-stu-id="5f838-118">The classes in question were intended as extension points for the team's internal testing.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5f838-119">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="5f838-119">Recommended action</span></span>

<span data-ttu-id="5f838-120">I když je pravděpodobné, že některé aplikace můžou být úmyslně nebo náhodně závislé na :::no-loc text="\"pubternal\""::: typech.</span><span class="sxs-lookup"><span data-stu-id="5f838-120">Although it's unlikely, some apps may intentionally or accidentally depend upon the :::no-loc text="\"pubternal\""::: types.</span></span> <span data-ttu-id="5f838-121">Informace o tom, jak migrovat z typů, najdete v oddílech [nového chování](#new-behavior) .</span><span class="sxs-lookup"><span data-stu-id="5f838-121">See the [New behavior](#new-behavior) sections to determine how to migrate away from the types.</span></span>

<span data-ttu-id="5f838-122">Pokud jste identifikovali scénář, který povoluje veřejné rozhraní API před touto změnou, ale ne teď, zapište problém v [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span><span class="sxs-lookup"><span data-stu-id="5f838-122">If you've identified a scenario which the public API allowed before this change but doesn't now, file an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span>

#### <a name="category"></a><span data-ttu-id="5f838-123">Kategorie</span><span class="sxs-lookup"><span data-stu-id="5f838-123">Category</span></span>

<span data-ttu-id="5f838-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5f838-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5f838-125">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5f838-125">Affected APIs</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `T:Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.#ctor`

-->
