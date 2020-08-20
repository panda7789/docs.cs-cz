---
ms.openlocfilehash: d7a93cb539baee6a70f75d3afe52fd7546ac2399
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507073"
---
### <a name="extensions-package-reference-changes-affecting-some-nuget-packages"></a><span data-ttu-id="d62b7-101">Rozšíření: změny odkazů balíčku ovlivňují některé balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="d62b7-101">Extensions: Package reference changes affecting some NuGet packages</span></span>

<span data-ttu-id="d62b7-102">S migrací některých `Microsoft.Extensions.*` balíčků NuGet z úložiště [dotnet/Extensions](https://github.com/dotnet/extensions) do [dotnet/runtime](https://github.com/dotnet/runtime), jak je popsáno v tématu [ASPNET/oznámení # 411](https://github.com/aspnet/Announcements/issues/411), se změny balení aplikují na některé migrované balíčky.</span><span class="sxs-lookup"><span data-stu-id="d62b7-102">With the migration of some `Microsoft.Extensions.*` NuGet packages from the [dotnet/extensions](https://github.com/dotnet/extensions) repository to [dotnet/runtime](https://github.com/dotnet/runtime), as described in [aspnet/Announcements#411](https://github.com/aspnet/Announcements/issues/411), packaging changes are being applied to some of the migrated packages.</span></span> <span data-ttu-id="d62b7-103">Diskuzi o tomto problému najdete v tématu [dotnet/aspnetcore # 21033](https://github.com/dotnet/aspnetcore/issues/21033).</span><span class="sxs-lookup"><span data-stu-id="d62b7-103">For discussion on this issue, see [dotnet/aspnetcore#21033](https://github.com/dotnet/aspnetcore/issues/21033).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d62b7-104">Představená verze</span><span class="sxs-lookup"><span data-stu-id="d62b7-104">Version introduced</span></span>

<span data-ttu-id="d62b7-105">5,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="d62b7-105">5.0 Preview 4</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d62b7-106">Staré chování</span><span class="sxs-lookup"><span data-stu-id="d62b7-106">Old behavior</span></span>

<span data-ttu-id="d62b7-107">Některé `Microsoft.Extensions.*` balíčky zahrnovaly odkazy na balíčky pro rozhraní API, na kterých se vaše aplikace spoléhala.</span><span class="sxs-lookup"><span data-stu-id="d62b7-107">Some `Microsoft.Extensions.*` packages included package references for APIs on which your app relied.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d62b7-108">Nové chování</span><span class="sxs-lookup"><span data-stu-id="d62b7-108">New behavior</span></span>

<span data-ttu-id="d62b7-109">Vaše aplikace může muset přidat `Microsoft.Extensions.*` závislosti balíčků.</span><span class="sxs-lookup"><span data-stu-id="d62b7-109">Your app may have to add `Microsoft.Extensions.*` package dependencies.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d62b7-110">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="d62b7-110">Reason for change</span></span>

<span data-ttu-id="d62b7-111">Zásady balení byly aktualizovány pro lepší zarovnání s úložištěm *dotnet/runtime* .</span><span class="sxs-lookup"><span data-stu-id="d62b7-111">Packaging policies were updated to better align with the *dotnet/runtime* repository.</span></span> <span data-ttu-id="d62b7-112">V rámci nové zásady se nepoužité odkazy na balíčky během balení odeberou ze souborů *. nupkg* .</span><span class="sxs-lookup"><span data-stu-id="d62b7-112">Under the new policy, unused package references are removed from *.nupkg* files during packaging.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d62b7-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="d62b7-113">Recommended action</span></span>

<span data-ttu-id="d62b7-114">Uživatelé ovlivněných balíčků by měli přidat přímou závislost na odebrané závislosti balíčku ve svém projektu, pokud se používají rozhraní API ze odebrané závislosti balíčku.</span><span class="sxs-lookup"><span data-stu-id="d62b7-114">Consumers of the affected packages should add a direct dependency on the removed package dependency in their project if APIs from removed package dependency are used.</span></span> <span data-ttu-id="d62b7-115">V následující tabulce jsou uvedeny ovlivněné balíčky a příslušné změny.</span><span class="sxs-lookup"><span data-stu-id="d62b7-115">The following table lists the affected packages and the corresponding changes.</span></span>

|<span data-ttu-id="d62b7-116">Název balíčku</span><span class="sxs-lookup"><span data-stu-id="d62b7-116">Package name</span></span>|<span data-ttu-id="d62b7-117">Popis změny</span><span class="sxs-lookup"><span data-stu-id="d62b7-117">Change description</span></span>|
|------------|------------------|
|[<span data-ttu-id="d62b7-118">Microsoft.Extensions.Configuration. Vazba</span><span class="sxs-lookup"><span data-stu-id="d62b7-118">Microsoft.Extensions.Configuration.Binder</span></span>](https://nuget.org/packages/Microsoft.Extensions.Configuration.Binder)|<span data-ttu-id="d62b7-119">Odebraný odkaz na `Microsoft.Extensions.Configuration`</span><span class="sxs-lookup"><span data-stu-id="d62b7-119">Removed reference to `Microsoft.Extensions.Configuration`</span></span>|
|[<span data-ttu-id="d62b7-120">Microsoft.Extensions.Configuration.Jsna</span><span class="sxs-lookup"><span data-stu-id="d62b7-120">Microsoft.Extensions.Configuration.Json</span></span>](https://nuget.org/packages/Microsoft.Extensions.Configuration.Json)    |<span data-ttu-id="d62b7-121">Odebraný odkaz na `System.Threading.Tasks.Extensions`</span><span class="sxs-lookup"><span data-stu-id="d62b7-121">Removed reference to `System.Threading.Tasks.Extensions`</span></span>|
|[<span data-ttu-id="d62b7-122">Microsoft. Extensions. Hosting. abstrakce</span><span class="sxs-lookup"><span data-stu-id="d62b7-122">Microsoft.Extensions.Hosting.Abstractions</span></span>](https://nuget.org/packages/Microsoft.Extensions.Hosting.Abstractions)|<span data-ttu-id="d62b7-123">Odebraný odkaz na `Microsoft.Extensions.Logging.Abstractions`</span><span class="sxs-lookup"><span data-stu-id="d62b7-123">Removed reference to `Microsoft.Extensions.Logging.Abstractions`</span></span>|
|[<span data-ttu-id="d62b7-124">Microsoft. Extensions. Logging</span><span class="sxs-lookup"><span data-stu-id="d62b7-124">Microsoft.Extensions.Logging</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging)                          |<span data-ttu-id="d62b7-125">Odebraný odkaz na `Microsoft.Extensions.Configuration.Binder`</span><span class="sxs-lookup"><span data-stu-id="d62b7-125">Removed reference to `Microsoft.Extensions.Configuration.Binder`</span></span>|
|[<span data-ttu-id="d62b7-126">Microsoft. Extensions. Logging. Console</span><span class="sxs-lookup"><span data-stu-id="d62b7-126">Microsoft.Extensions.Logging.Console</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.Console)          |<span data-ttu-id="d62b7-127">Odebraný odkaz na `Microsoft.Extensions.Configuration.Abstractions`</span><span class="sxs-lookup"><span data-stu-id="d62b7-127">Removed reference to `Microsoft.Extensions.Configuration.Abstractions`</span></span>|
|[<span data-ttu-id="d62b7-128">Microsoft. Extensions. Logging. EventLog</span><span class="sxs-lookup"><span data-stu-id="d62b7-128">Microsoft.Extensions.Logging.EventLog</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.EventLog)        |<span data-ttu-id="d62b7-129">Odebral se odkaz na `System.Diagnostics.EventLog` pro zástupný název cílového rozhraní .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="d62b7-129">Removed reference to `System.Diagnostics.EventLog` for the .NET Framework 4.6.1 target framework moniker</span></span>|
|[<span data-ttu-id="d62b7-130">Microsoft. Extensions. Logging. EventSource</span><span class="sxs-lookup"><span data-stu-id="d62b7-130">Microsoft.Extensions.Logging.EventSource</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.EventSource)  |<span data-ttu-id="d62b7-131">Odebraný odkaz na `System.Threading.Tasks.Extensions`</span><span class="sxs-lookup"><span data-stu-id="d62b7-131">Removed reference to `System.Threading.Tasks.Extensions`</span></span>|
|[<span data-ttu-id="d62b7-132">Microsoft. Extensions. Options</span><span class="sxs-lookup"><span data-stu-id="d62b7-132">Microsoft.Extensions.Options</span></span>](https://nuget.org/packages/Microsoft.Extensions.Options)                          |<span data-ttu-id="d62b7-133">Odebraný odkaz na `System.ComponentModel.Annotations`</span><span class="sxs-lookup"><span data-stu-id="d62b7-133">Removed reference to `System.ComponentModel.Annotations`</span></span>|

<span data-ttu-id="d62b7-134">Například odkaz na balíček, který `Microsoft.Extensions.Configuration` byl odebrán z `Microsoft.Extensions.Configuration.Binder` .</span><span class="sxs-lookup"><span data-stu-id="d62b7-134">For example, the package reference to `Microsoft.Extensions.Configuration` was removed from `Microsoft.Extensions.Configuration.Binder`.</span></span> <span data-ttu-id="d62b7-135">V balíčku se nepoužilo žádné rozhraní API ze závislostí.</span><span class="sxs-lookup"><span data-stu-id="d62b7-135">No API from the dependency was used in the package.</span></span> <span data-ttu-id="d62b7-136">Uživatelé `Microsoft.Extensions.Configuration.Binder` , kteří závisejí na rozhraních API z, `Microsoft.Extensions.Configuration` by měli do svého projektu přidat přímý odkaz.</span><span class="sxs-lookup"><span data-stu-id="d62b7-136">Users of `Microsoft.Extensions.Configuration.Binder` who depend on APIs from `Microsoft.Extensions.Configuration` should add a direct reference to it in their project.</span></span>

#### <a name="category"></a><span data-ttu-id="d62b7-137">Kategorie</span><span class="sxs-lookup"><span data-stu-id="d62b7-137">Category</span></span>

<span data-ttu-id="d62b7-138">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d62b7-138">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d62b7-139">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="d62b7-139">Affected APIs</span></span>

<span data-ttu-id="d62b7-140">Žádné</span><span class="sxs-lookup"><span data-stu-id="d62b7-140">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
