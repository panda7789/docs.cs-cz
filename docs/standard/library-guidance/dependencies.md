---
title: Závislosti a knihovny .NET
description: Doporučení osvědčených postupů pro správu závislostí NuGet v knihovnách .NET.
ms.date: 10/02/2018
ms.openlocfilehash: 6a260b54c45a0cd231059ab3bc6f2707ef7fb20e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "76731475"
---
# <a name="dependencies"></a><span data-ttu-id="305c7-103">Závislosti</span><span class="sxs-lookup"><span data-stu-id="305c7-103">Dependencies</span></span>

<span data-ttu-id="305c7-104">Primární způsob přidávání závislostí do knihovny .NET odkazuje na balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="305c7-104">The primary way of adding dependencies to a .NET library is referencing NuGet packages.</span></span> <span data-ttu-id="305c7-105">Odkazy na balíčky NuGet umožňují rychle znovu použít a využít již napsané funkce, ale jsou běžným zdrojem tření pro vývojáře rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="305c7-105">NuGet package references allow you to quickly reuse and leverage already written functionality, but they're a common source of friction for .NET developers.</span></span> <span data-ttu-id="305c7-106">Správná správa závislostí je důležitá, aby se zabránilo změnám v jiných knihovnách .NET v porušení knihovny .NET a naopak!</span><span class="sxs-lookup"><span data-stu-id="305c7-106">Correctly managing dependencies is important to prevent changes in other .NET libraries from breaking your .NET library, and vice versa!</span></span>

## <a name="diamond-dependencies"></a><span data-ttu-id="305c7-107">Diamantové závislosti</span><span class="sxs-lookup"><span data-stu-id="305c7-107">Diamond dependencies</span></span>

<span data-ttu-id="305c7-108">Je běžné situace pro projekt .NET mít více verzí balíčku ve svém stromu závislostí.</span><span class="sxs-lookup"><span data-stu-id="305c7-108">It's a common situation for a .NET project to have multiple versions of a package in its dependency tree.</span></span> <span data-ttu-id="305c7-109">Například aplikace závisí na dvou balíčcích NuGet, z nichž každý závisí na různých verzích stejného balíčku.</span><span class="sxs-lookup"><span data-stu-id="305c7-109">For example, an app depends on two NuGet packages, each of which depends on different versions of the same package.</span></span> <span data-ttu-id="305c7-110">V grafu závislostí aplikace nyní existuje závislost na kosočtverci.</span><span class="sxs-lookup"><span data-stu-id="305c7-110">A diamond dependency now exists in the app's dependency graph.</span></span>

<span data-ttu-id="305c7-111">![Závislost na kosočtverci](./media/dependencies/diamond-dependency.png "Závislost na kosočtverci")</span><span class="sxs-lookup"><span data-stu-id="305c7-111">![Diamond dependency](./media/dependencies/diamond-dependency.png "Diamond dependency")</span></span>

<span data-ttu-id="305c7-112">V době sestavení NuGet analyzuje všechny balíčky, které závisí na projektu, včetně závislostí závislostí.</span><span class="sxs-lookup"><span data-stu-id="305c7-112">At build time, NuGet analyzes all the packages that a project depends on, including the dependencies of dependencies.</span></span> <span data-ttu-id="305c7-113">Při zjištění více verzí balíčku jsou vyhodnocovány pravidla vybrat jeden.</span><span class="sxs-lookup"><span data-stu-id="305c7-113">When multiple versions of a package are detected, rules are evaluated to pick one.</span></span> <span data-ttu-id="305c7-114">Sjednocení balíčků je nezbytné, protože spuštění souběžných verzí sestavení ve stejné aplikaci je problematické v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="305c7-114">Unifying packages is necessary because running side-by-side versions of an assembly in the same application is problematic in .NET.</span></span>

<span data-ttu-id="305c7-115">Většina diamantové závislosti jsou snadno přeložit; mohou však za určitých okolností způsobit problémy:</span><span class="sxs-lookup"><span data-stu-id="305c7-115">Most diamond dependencies are easily resolved; however, they can create issues in certain circumstances:</span></span>

1. <span data-ttu-id="305c7-116">**Konfliktní odkazy na balíček NuGet** brání vyřešení verze během obnovení balíčku.</span><span class="sxs-lookup"><span data-stu-id="305c7-116">**Conflicting NuGet package references** prevent a version from being resolved during package restore.</span></span>
2. <span data-ttu-id="305c7-117">**Narušující změny mezi verzemi** způsobit chyby a výjimky za běhu.</span><span class="sxs-lookup"><span data-stu-id="305c7-117">**Breaking changes between the versions** cause bugs and exceptions at runtime.</span></span>
3. <span data-ttu-id="305c7-118">**Sestavení balíčku je silné s názvem**, verze sestavení změněna a aplikace je spuštěna v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="305c7-118">**The package assembly is strong named**, the assembly version changed, and the app is running on the .NET Framework.</span></span> <span data-ttu-id="305c7-119">Jsou vyžadována přesměrování vazby sestavení.</span><span class="sxs-lookup"><span data-stu-id="305c7-119">Assembly binding redirects are required.</span></span>

<span data-ttu-id="305c7-120">Není možné vědět, jaké balíčky budou použity vedle své vlastní.</span><span class="sxs-lookup"><span data-stu-id="305c7-120">It's not possible to know what packages will be used alongside your own.</span></span> <span data-ttu-id="305c7-121">Dobrým způsobem, jak snížit pravděpodobnost, že závislost na kosobru sdiamantové mincovní zařízení rozlomí vaši knihovnu, je minimalizovat počet balíčků, na kterých jste závislí.</span><span class="sxs-lookup"><span data-stu-id="305c7-121">A good way to reduce the likelihood of a diamond dependency breaking your library is to minimize the number of packages you depend on.</span></span>

<span data-ttu-id="305c7-122">✔️ do zkontrolujte knihovnu .NET pro zbytečné závislosti.</span><span class="sxs-lookup"><span data-stu-id="305c7-122">✔️ DO review your .NET library for unnecessary dependencies.</span></span>

## <a name="nuget-dependency-version-ranges"></a><span data-ttu-id="305c7-123">Rozsahy verzí závislostí NuGet</span><span class="sxs-lookup"><span data-stu-id="305c7-123">NuGet dependency version ranges</span></span>

<span data-ttu-id="305c7-124">Odkaz na balíček určuje rozsah platných balíčků, které umožňuje.</span><span class="sxs-lookup"><span data-stu-id="305c7-124">A package reference specifies the range of valid packages it allows.</span></span> <span data-ttu-id="305c7-125">Referenční verze balíčku v souboru projektu je obvykle minimální verze a neexistuje žádné maximum.</span><span class="sxs-lookup"><span data-stu-id="305c7-125">Typically, the package reference version in the project file is the minimum version and there's no maximum.</span></span>

```xml
<!-- Accepts any version 1.0 and above. -->
<PackageReference Include="ExamplePackage" Version="1.0" />
```

<span data-ttu-id="305c7-126">Pravidla, která NuGet používá při řešení závislostí jsou [složité](/nuget/consume-packages/dependency-resolution), ale NuGet vždy hledá nejnižší použitelnou verzi.</span><span class="sxs-lookup"><span data-stu-id="305c7-126">The rules that NuGet uses when resolving dependencies are [complex](/nuget/consume-packages/dependency-resolution), but NuGet always looks for the lowest applicable version.</span></span> <span data-ttu-id="305c7-127">NuGet upřednostňuje nejnižší použitelnou verzi před použitím nejvyšší dostupné, protože nejnižší bude mít nejmenší problémy s kompatibilitou.</span><span class="sxs-lookup"><span data-stu-id="305c7-127">NuGet prefers the lowest applicable version over using the highest available because the lowest will have the least compatibility issues.</span></span>

<span data-ttu-id="305c7-128">Z důvodu nuget nejnižší použitelné verze pravidlo, není nutné umístit horní verzi nebo přesný rozsah na odkazy na balíček, aby se zabránilo získání nejnovější verze.</span><span class="sxs-lookup"><span data-stu-id="305c7-128">Because of NuGet's lowest applicable version rule, it isn't necessary to place an upper version or exact range on package references to avoid getting the latest version.</span></span> <span data-ttu-id="305c7-129">NuGet se již snaží najít nejnižší, nejvíce kompatibilní verze pro vás.</span><span class="sxs-lookup"><span data-stu-id="305c7-129">NuGet already tries to find the lowest, most compatible version for you.</span></span>

```xml
<!-- Accepts 1.0 up to 1.x, but not 2.0 and higher. -->
<PackageReference Include="ExamplePackage" Version="[1.0,2.0)" />

<!-- Accepts exactly 1.0. -->
<PackageReference Include="ExamplePackage" Version="[1.0]" />
```

<span data-ttu-id="305c7-130">Horní verze omezení způsobí NuGet nezdaří, pokud dojde ke konfliktu.</span><span class="sxs-lookup"><span data-stu-id="305c7-130">Upper version limits will cause NuGet to fail if there's a conflict.</span></span> <span data-ttu-id="305c7-131">Například jedna knihovna přijímá přesně 1.0, zatímco jiná knihovna vyžaduje 2.0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="305c7-131">For example, one library accepts exactly 1.0 while another library requires 2.0 or above.</span></span> <span data-ttu-id="305c7-132">Při porušení změny mohou být zavedeny ve verzi 2.0, přísné nebo horní limit verze závislost zaručuje chybu.</span><span class="sxs-lookup"><span data-stu-id="305c7-132">While breaking changes may have been introduced in version 2.0, a strict or upper limit version dependency guarantees an error.</span></span>

<span data-ttu-id="305c7-133">![Konflikt závislosti na diamantech](./media/dependencies/diamond-dependency-conflict.png "Konflikt závislosti na diamantech")</span><span class="sxs-lookup"><span data-stu-id="305c7-133">![Diamond dependency conflict](./media/dependencies/diamond-dependency-conflict.png "Diamond dependency conflict")</span></span>

<span data-ttu-id="305c7-134">❌Nemají Odkazy na balíček NuGet bez minimální verze.</span><span class="sxs-lookup"><span data-stu-id="305c7-134">❌ DO NOT have NuGet package references with no minimum version.</span></span>

<span data-ttu-id="305c7-135">❌VYHNĚTE se NuGet odkazy na balíček, které vyžadují přesnou verzi.</span><span class="sxs-lookup"><span data-stu-id="305c7-135">❌ AVOID NuGet package references that demand an exact version.</span></span>

<span data-ttu-id="305c7-136">❌VYHNĚTE se Odkazy na balíček NuGet s horním limitem verze.</span><span class="sxs-lookup"><span data-stu-id="305c7-136">❌ AVOID NuGet package references with a version upper limit.</span></span>

## <a name="nuget-shared-source-packages"></a><span data-ttu-id="305c7-137">Balíčky sdíleného zdroje NuGet</span><span class="sxs-lookup"><span data-stu-id="305c7-137">NuGet shared source packages</span></span>

<span data-ttu-id="305c7-138">Jedním ze způsobů, jak snížit externí NuGet balíček závislostí je odkazovat na sdílené zdrojové balíčky.</span><span class="sxs-lookup"><span data-stu-id="305c7-138">One way to reduce external NuGet package dependencies is to reference shared source packages.</span></span> <span data-ttu-id="305c7-139">Sdílený zdrojový balíček obsahuje [soubory zdrojového kódu,](/nuget/reference/nuspec#including-content-files) které jsou zahrnuty v projektu při odkazování.</span><span class="sxs-lookup"><span data-stu-id="305c7-139">A shared source package contains [source code files](/nuget/reference/nuspec#including-content-files) that are included in a project when referenced.</span></span> <span data-ttu-id="305c7-140">Vzhledem k tomu, že jste právě včetně souborů zdrojového kódu, které jsou kompilovány se zbytkem projektu, neexistuje žádná externí závislost a šance na konflikt.</span><span class="sxs-lookup"><span data-stu-id="305c7-140">Because you're just including source code files that are compiled with the rest of your project, there's no external dependency and chance of conflict.</span></span>

<span data-ttu-id="305c7-141">Sdílené zdrojové balíčky jsou skvělé pro zahrnutí malých částí funkcí.</span><span class="sxs-lookup"><span data-stu-id="305c7-141">Shared source packages are great for including small pieces of functionality.</span></span> <span data-ttu-id="305c7-142">Například sdílený zdrojový balíček pomocných metod pro volání HTTP.</span><span class="sxs-lookup"><span data-stu-id="305c7-142">For example, a shared source package of helper methods for making HTTP calls.</span></span>

<span data-ttu-id="305c7-143">![Sdílený zdrojový balíček](./media/dependencies/shared-source-package.png "Sdílený zdrojový balíček")</span><span class="sxs-lookup"><span data-stu-id="305c7-143">![Shared source package](./media/dependencies/shared-source-package.png "Shared source package")</span></span>

```xml
<PackageReference Include="Microsoft.Extensions.Buffers.Testing.Sources" PrivateAssets="All" Version="1.0" />
```

<span data-ttu-id="305c7-144">![Projekt sdíleného zdroje](./media/dependencies/shared-source-project.png "Projekt sdíleného zdroje")</span><span class="sxs-lookup"><span data-stu-id="305c7-144">![Shared source project](./media/dependencies/shared-source-project.png "Shared source project")</span></span>

<span data-ttu-id="305c7-145">Sdílené zdrojové balíčky mají určitá omezení.</span><span class="sxs-lookup"><span data-stu-id="305c7-145">Shared source packages have some limitations.</span></span> <span data-ttu-id="305c7-146">Mohou být odkazovány `PackageReference`pouze na `packages.config` , takže starší projekty jsou vyloučeny.</span><span class="sxs-lookup"><span data-stu-id="305c7-146">They can only be referenced by `PackageReference`, so older `packages.config` projects are excluded.</span></span> <span data-ttu-id="305c7-147">Sdílené zdrojové balíčky jsou použitelné pouze pro projekty se stejným typem jazyka.</span><span class="sxs-lookup"><span data-stu-id="305c7-147">Also shared source packages are only usable by projects with the same language type.</span></span> <span data-ttu-id="305c7-148">Z důvodu těchto omezení sdílené zdrojové balíčky se nejlépe používají ke sdílení funkcí v rámci projektu s otevřeným zdrojovým kódem.</span><span class="sxs-lookup"><span data-stu-id="305c7-148">Because of these limitations shared source packages are best used to share functionality within an open-source project.</span></span>

<span data-ttu-id="305c7-149">✔️ zvažte odkazování na sdílené zdrojové balíčky pro malé, interní části funkcí.</span><span class="sxs-lookup"><span data-stu-id="305c7-149">✔️ CONSIDER referencing shared source packages for small, internal pieces of functionality.</span></span>

<span data-ttu-id="305c7-150">✔️ zvažte vytvoření balíčku sdílený zdrojový balíček, pokud poskytuje malé, vnitřní části funkcí.</span><span class="sxs-lookup"><span data-stu-id="305c7-150">✔️ CONSIDER making your package a shared source package if it provides small, internal pieces of functionality.</span></span>

<span data-ttu-id="305c7-151">✔️ do odkaz sdílené `PrivateAssets="All"`zdrojové balíčky s .</span><span class="sxs-lookup"><span data-stu-id="305c7-151">✔️ DO reference shared source packages with `PrivateAssets="All"`.</span></span>

> <span data-ttu-id="305c7-152">Toto nastavení říká NuGet balíček je pouze pro použití v době vývoje a by neměly být vystaveny jako veřejné závislosti.</span><span class="sxs-lookup"><span data-stu-id="305c7-152">This setting tells NuGet the package is only to be used at development time and shouldn't be exposed as a public dependency.</span></span>

<span data-ttu-id="305c7-153">❌Nemáte sdílené typy zdrojových balíčků ve veřejném rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="305c7-153">❌ DO NOT have shared source package types in your public API.</span></span>

> <span data-ttu-id="305c7-154">Sdílené typy zdrojů jsou kompilovány do referenčního sestavení a nelze je vyměňovat přes hranice sestavení.</span><span class="sxs-lookup"><span data-stu-id="305c7-154">Shared source types are compiled into the referencing assembly and can't be exchanged across assembly boundaries.</span></span> <span data-ttu-id="305c7-155">Například typ sdíleného `IRepository` zdroje v jednom projektu je samostatný typ `IRepository` ze stejného sdíleného zdroje v jiném projektu.</span><span class="sxs-lookup"><span data-stu-id="305c7-155">For example, a shared-source `IRepository` type in one project is a separate type from the same shared-source `IRepository` in another project.</span></span> <span data-ttu-id="305c7-156">Typy ve sdílených zdrojových balíčcích by měly mít `internal` viditelnost.</span><span class="sxs-lookup"><span data-stu-id="305c7-156">Types in shared source packages should have an `internal` visibility.</span></span>

<span data-ttu-id="305c7-157">❌NEPublikujte sdílené zdrojové balíčky, které mají NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="305c7-157">❌ DO NOT publish shared source packages to NuGet.org.</span></span>

> <span data-ttu-id="305c7-158">Sdílené zdrojové balíčky obsahují zdrojový kód a mohou být používány pouze projekty se stejným typem jazyka.</span><span class="sxs-lookup"><span data-stu-id="305c7-158">Shared source packages contain source code and can only be used by projects with the same language type.</span></span> <span data-ttu-id="305c7-159">Například balíček sdíleného zdroje Jazyka C# nelze použít aplikací F#.</span><span class="sxs-lookup"><span data-stu-id="305c7-159">For example, a C# shared source package cannot be used by an F# application.</span></span>
>
> <span data-ttu-id="305c7-160">Publikovat sdílené zdrojové balíčky do [místního informačního kanálu nebo MyGet](./publish-nuget-package.md) využívat interně v rámci projektu.</span><span class="sxs-lookup"><span data-stu-id="305c7-160">Publish shared source packages to a [local feed or MyGet](./publish-nuget-package.md) to consume them internally within your project.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="305c7-161">[Předchozí](nuget.md)
>[další](sourcelink.md)</span><span class="sxs-lookup"><span data-stu-id="305c7-161">[Previous](nuget.md)
[Next](sourcelink.md)</span></span>
