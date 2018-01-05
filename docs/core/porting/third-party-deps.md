---
title: "Portování do .NET Core - analýza strany závislostmi třetích stran"
description: "Portování do .NET Core - analýza závislostmi třetích stran"
keywords: "Rozhraní .NET, .NET core"
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: b446e9e0-72f6-48f6-92c6-70ad0ce3f86a
ms.workload: dotnetcore
ms.openlocfilehash: 70b39c9762e4ee7450d0f59455bace0ac728844c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="porting-to-net-core---analyzing-your-third-party-party-dependencies"></a><span data-ttu-id="1efcc-104">Portování do .NET Core - analýza strany závislostmi třetích stran</span><span class="sxs-lookup"><span data-stu-id="1efcc-104">Porting to .NET Core - Analyzing your Third-Party Party Dependencies</span></span>

<span data-ttu-id="1efcc-105">Prvním krokem v procesu přenosem je pochopit závislostmi třetích stran.</span><span class="sxs-lookup"><span data-stu-id="1efcc-105">The first step in the porting process is to understand your third party dependencies.</span></span>  <span data-ttu-id="1efcc-106">Je třeba zjistit, kdo z nich, pokud existuje, není ještě spustit na .NET Core a vytvořte pohotovostní plán pro ty, které nechcete spustit na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1efcc-106">You need to figure out which of them, if any, don't yet run on .NET Core, and develop a contingency plan for those which don't run on .NET Core.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1efcc-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1efcc-107">Prerequisites</span></span>

<span data-ttu-id="1efcc-108">V tomto článku bude předpokládat, používáte Windows Server a Visual Studio, a že máte kód, který běží na rozhraní .NET Framework ještě dnes.</span><span class="sxs-lookup"><span data-stu-id="1efcc-108">This article will assume you are using Windows and Visual Studio, and that you have code which runs on the .NET Framework today.</span></span>

## <a name="analyzing-nuget-packages"></a><span data-ttu-id="1efcc-109">Analýza balíčků NuGet</span><span class="sxs-lookup"><span data-stu-id="1efcc-109">Analyzing NuGet Packages</span></span>

<span data-ttu-id="1efcc-110">Analýza balíčků NuGet pro přenositelnost je velmi snadné.</span><span class="sxs-lookup"><span data-stu-id="1efcc-110">Analyzing NuGet packages for portability is very easy.</span></span>  <span data-ttu-id="1efcc-111">Balíček NuGet je sám sadu složek, které obsahují sestavení specifické pro platformu, a proto všechny, které musíte udělat je zkontrolujte, zda je do složky, který obsahuje sestavení .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1efcc-111">Because a NuGet package is itself a set of folders which contain platform-specific assemblies, all you have to do is check to see if there is a folder which contains a .NET Core assembly.</span></span>

<span data-ttu-id="1efcc-112">Probíhá kontrola složky balíčku NuGet je nejjednodušší s [Explorer balíček NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) nástroj.</span><span class="sxs-lookup"><span data-stu-id="1efcc-112">Inspecting NuGet Package folders is easiest with the [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) tool.</span></span>  <span data-ttu-id="1efcc-113">Chcete-li to provést.</span><span class="sxs-lookup"><span data-stu-id="1efcc-113">Here's how to do it.</span></span>

1. <span data-ttu-id="1efcc-114">Stáhněte a otevřete Průzkumníka balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="1efcc-114">Download and open the NuGet Package Explorer.</span></span>
2. <span data-ttu-id="1efcc-115">Klikněte na tlačítko "Otevřete balíček z online kanálu".</span><span class="sxs-lookup"><span data-stu-id="1efcc-115">Click "Open package from online feed".</span></span>
3. <span data-ttu-id="1efcc-116">Vyhledejte název balíčku.</span><span class="sxs-lookup"><span data-stu-id="1efcc-116">Search for the name of the package.</span></span>
4. <span data-ttu-id="1efcc-117">Rozbalte složku "lib" na pravé straně a podívejte se na názvy složek.</span><span class="sxs-lookup"><span data-stu-id="1efcc-117">Expand the "lib" folder on the right-hand side and look at folder names.</span></span>

<span data-ttu-id="1efcc-118">Můžete také zjistit, co balíček podporuje na [nuget.org](https://www.nuget.org/) pod **závislosti** části stránky pro tento balíček.</span><span class="sxs-lookup"><span data-stu-id="1efcc-118">You can also see what a package supports on [nuget.org](https://www.nuget.org/) under the **Dependencies** section of the page for that package.</span></span>

<span data-ttu-id="1efcc-119">V obou případech budete muset najít složku nebo položku na [nuget.org](https://www.nuget.org/) s žádným z následujících názvů:</span><span class="sxs-lookup"><span data-stu-id="1efcc-119">In either case, you'll need to look for a folder or entry on [nuget.org](https://www.nuget.org/) with any of the following names:</span></span>

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netcoreapp1.0
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

<span data-ttu-id="1efcc-120">Jedná se o Monikery Framework cíl (TFM) které mapování na verzích [.NET Standard](../../standard/net-standard.md) a tradiční profily přenosných třída knihovny PCL (), které jsou slučitelné s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1efcc-120">These are the Target Framework Monikers (TFM) which map to versions of the [.NET Standard](../../standard/net-standard.md) and traditional Portable Class Library (PCL) profiles which are compatible with .NET Core.</span></span>  <span data-ttu-id="1efcc-121">Všimněte si, že `netcoreapp1.0`, při kompatibilní, je pro aplikace a není knihovny.</span><span class="sxs-lookup"><span data-stu-id="1efcc-121">Note that `netcoreapp1.0`, while compatible, is for applications and not libraries.</span></span>  <span data-ttu-id="1efcc-122">I když není nic nesprávný s použitím knihovny, která je `netcoreapp1.0`– na základě, že knihovna nemusí být žádoucí pro všechno, co *jiných* než jiné spotřeba `netcoreapp1.0` aplikace.</span><span class="sxs-lookup"><span data-stu-id="1efcc-122">Although there's nothing wrong with using a library which is `netcoreapp1.0`-based, that library may not be intended for anything *other* than consumption by other `netcoreapp1.0` applications.</span></span>

<span data-ttu-id="1efcc-123">Existují také některé starší verze TFMs v předběžné verze jádra rozhraní .NET, která je také možné kompatibilní:</span><span class="sxs-lookup"><span data-stu-id="1efcc-123">There are also some legacy TFMs used in pre-release versions of .NET Core that may also be compatible:</span></span>

```
dnxcore50
dotnet5.0
dotnet5.1
dotnet5.2
dotnet5.3
dotnet5.4
dotnet5.5
```

<span data-ttu-id="1efcc-124">**Když to bude pravděpodobně pracovat s kódu, neexistuje žádná záruka kompatibility**.</span><span class="sxs-lookup"><span data-stu-id="1efcc-124">**While these will likely work with your code, there is no guarantee of compatibility**.</span></span>  <span data-ttu-id="1efcc-125">Balíčky s tyto TFMs nebyly vytvořené s balíčky předběžné verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1efcc-125">Packages with these TFMs were built with pre-release .NET Core packages.</span></span>  <span data-ttu-id="1efcc-126">Poznamenejte si při (nebo pokud) balíčky takto jsou aktualizovány být `netstandard`– na základě.</span><span class="sxs-lookup"><span data-stu-id="1efcc-126">Take note of when (or if) packages like this are updated to be `netstandard`-based.</span></span>

> [!NOTE]
> <span data-ttu-id="1efcc-127">Chcete-li použít balíček cílení tradiční PCL nebo předběžné verze .NET Core cíl, musíte použít `imports` direktivy v vaší `project.json` souboru.</span><span class="sxs-lookup"><span data-stu-id="1efcc-127">To use a package targeting a traditional PCL or pre-release .NET Core target, you must use the `imports` directive in your `project.json` file.</span></span>

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a><span data-ttu-id="1efcc-128">Co dělat, když vaše závislost balíčku NuGet nefunguje v .NET Core</span><span class="sxs-lookup"><span data-stu-id="1efcc-128">What to do when your NuGet package dependency doesn't run on .NET Core</span></span>

<span data-ttu-id="1efcc-129">Existuje několik věcí, které můžete provést, pokud balíček NuGet, které závisí na se nespustí na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1efcc-129">There are a few things you can do if a NuGet package you depend on won't run on .NET Core.</span></span>

1. <span data-ttu-id="1efcc-130">Pokud projekt je open source a je hostovaná někde jako GitHub, můžete použít developer(s) přímo.</span><span class="sxs-lookup"><span data-stu-id="1efcc-130">If the project is open source and hosted somewhere like GitHub, you can engage the developer(s) directly.</span></span>
2. <span data-ttu-id="1efcc-131">Obraťte se na autora přímo na [nuget.org](https://www.nuget.org/) vyhledávání pro balíček a kliknutím na možnost "Obraťte se na vlastníky" na levé straně stránky daného balíčku.</span><span class="sxs-lookup"><span data-stu-id="1efcc-131">You can contact the author directly on [nuget.org](https://www.nuget.org/) by searching for the package and clicking "Contact Owners" on the left hand side of the package's page.</span></span>
3. <span data-ttu-id="1efcc-132">Můžete vyhledat jiný balíček, který běží na .NET Core, která má jako balíčku, který jste používali pro stejnou úlohu.</span><span class="sxs-lookup"><span data-stu-id="1efcc-132">You can look for another package that runs on .NET Core which accomplishes the same task as the package you were using.</span></span>
4. <span data-ttu-id="1efcc-133">Můžete se pokusit napsat kód, že balíček dělal sami.</span><span class="sxs-lookup"><span data-stu-id="1efcc-133">You can attempt to write the code the package was doing yourself.</span></span>
5. <span data-ttu-id="1efcc-134">Závislost na balíček může eliminovat alespoň změnou funkce aplikace, dokud nebude k dispozici kompatibilní verzi balíčku.</span><span class="sxs-lookup"><span data-stu-id="1efcc-134">You could eliminate the dependency on the package by changing the functionality of your app, at least until a compatible version of the package becomes available.</span></span>

<span data-ttu-id="1efcc-135">Prosím pamatujte, že údržby opensourcový projekt programu a vydavatelé balíček NuGet jsou často kteří přispívat, protože zajímají pro danou doménu, provést zdarma a často mají různé denní úlohy.</span><span class="sxs-lookup"><span data-stu-id="1efcc-135">Please remember that open source project maintainers and NuGet package publishers are often volunteers who contribute because they care about a given domain, do it for free, and often have a different daytime job.</span></span> <span data-ttu-id="1efcc-136">Pokud oslovení, můžete začít s kladné prohlášení o knihovně před výzvou týkající se podpory .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1efcc-136">If you do reach out, you might start with a positive statement about the library before asking about .NET Core support.</span></span>

<span data-ttu-id="1efcc-137">Pokud nemůžete vyřešit problém s žádným z výše, budete muset port na .NET Core později.</span><span class="sxs-lookup"><span data-stu-id="1efcc-137">If you're unable to resolve your issue with any of the above, you may have to port to .NET Core at a later date.</span></span>

<span data-ttu-id="1efcc-138">Tým služby .NET chcete vědět, které knihovny jsou nejdůležitější pro další podporu s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1efcc-138">The .NET Team would like to know which libraries are the most important to support next with .NET Core.</span></span> <span data-ttu-id="1efcc-139">Můžete také nám poslat poštu na dotnet@microsoft.com o knihovny, které chcete použít.</span><span class="sxs-lookup"><span data-stu-id="1efcc-139">You can also send us mail at dotnet@microsoft.com about the libraries you'd like to use.</span></span>

## <a name="analyzing-dependencies-which-arent-nuget-packages"></a><span data-ttu-id="1efcc-140">Analýza závislosti, které nejsou balíčků NuGet</span><span class="sxs-lookup"><span data-stu-id="1efcc-140">Analyzing Dependencies which aren't NuGet Packages</span></span>

<span data-ttu-id="1efcc-141">Můžete mít závislost, která není balíčku NuGet, jako je například knihovny DLL v systému souborů.</span><span class="sxs-lookup"><span data-stu-id="1efcc-141">You may have a dependency that isn't a NuGet package, such as a DLL in the filesystem.</span></span>  <span data-ttu-id="1efcc-142">Jediný způsob, jak určit přenositelnost této závislosti se ke spuštění [ApiPort nástroj](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/).</span><span class="sxs-lookup"><span data-stu-id="1efcc-142">The only way to determine the portability of that dependency is to run the [ApiPort tool](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="1efcc-143">Další kroky</span><span class="sxs-lookup"><span data-stu-id="1efcc-143">Next steps</span></span>

<span data-ttu-id="1efcc-144">Pokud jste portování knihovnu, podívejte se na [portování knihovnách](libraries.md).</span><span class="sxs-lookup"><span data-stu-id="1efcc-144">If you're porting a library, check out [Porting your Libraries](libraries.md).</span></span>
