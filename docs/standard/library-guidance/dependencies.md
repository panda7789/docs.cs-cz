---
title: Závislosti a knihoven .NET
description: Doporučení osvědčených postupů pro správu závislostí NuGet knihoven .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 5566ab83040ce5dc23520401e3fc4bb619af4ec4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61909922"
---
# <a name="dependencies"></a><span data-ttu-id="5b4a7-103">Závislosti</span><span class="sxs-lookup"><span data-stu-id="5b4a7-103">Dependencies</span></span>

<span data-ttu-id="5b4a7-104">Primární způsob, jak přidat závislosti do knihovny .NET odkazuje na balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-104">The primary way of adding dependencies to a .NET library is referencing NuGet packages.</span></span> <span data-ttu-id="5b4a7-105">Odkazy na balíčky NuGet umožňují rychle opakovaně používat a využít už písemné funkce, ale jsou běžné příčiny případná problémová místa pro vývojáře na platformě .NET.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-105">NuGet package references allow you to quickly reuse and leverage already written functionality, but they're a common source of friction for .NET developers.</span></span> <span data-ttu-id="5b4a7-106">Správně Správa závislostí je důležité zabránit změnám v jiných knihovnách .NET z nejnovější knihovny .NET a naopak.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-106">Correctly managing dependencies is important to prevent changes in other .NET libraries from breaking your .NET library, and vice versa!</span></span>

## <a name="diamond-dependencies"></a><span data-ttu-id="5b4a7-107">Závislosti kosočtverec</span><span class="sxs-lookup"><span data-stu-id="5b4a7-107">Diamond dependencies</span></span>

<span data-ttu-id="5b4a7-108">Je běžné situace pro projekt .NET pro více verzí balíčku v jeho strom závislostí.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-108">It's a common situation for a .NET project to have multiple versions of a package in its dependency tree.</span></span> <span data-ttu-id="5b4a7-109">Například aplikace závisí na dva balíčky NuGet, z nichž každý závisí na různé verze stejného balíčku.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-109">For example, an app depends on two NuGet packages, each of which depends on different versions of the same package.</span></span> <span data-ttu-id="5b4a7-110">Závislost kosočtverce nyní existuje v grafu závislostí aplikace.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-110">A diamond dependency now exists in the app's dependency graph.</span></span>

<span data-ttu-id="5b4a7-111">![Diamond závislost](./media/dependencies/diamond-dependency.png "Diamond závislostí")</span><span class="sxs-lookup"><span data-stu-id="5b4a7-111">![Diamond dependency](./media/dependencies/diamond-dependency.png "Diamond dependency")</span></span>

<span data-ttu-id="5b4a7-112">V okamžiku sestavení NuGet analyzuje všech balíčků projektu, na kterých závisí, včetně závislostí závislosti.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-112">At build time, NuGet analyzes all the packages that a project depends on, including the dependencies of dependencies.</span></span> <span data-ttu-id="5b4a7-113">Když se zjistí více verzí balíčku, pravidla se vyhodnocují vybrat jednu.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-113">When multiple versions of a package are detected, rules are evaluated to pick one.</span></span> <span data-ttu-id="5b4a7-114">Sjednotit balíčků je nezbytné, protože spuštěná verze sestavení vedle sebe ve stejné aplikaci jen těžko v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-114">Unifying packages is necessary because running side-by-side versions of an assembly in the same application is problematic in .NET.</span></span>

<span data-ttu-id="5b4a7-115">Většina kosočtverce závislosti jsou snadno vyřešit; v některých případech však může vytvořit problémy:</span><span class="sxs-lookup"><span data-stu-id="5b4a7-115">Most diamond dependencies are easily resolved; however, they can create issues in certain circumstances:</span></span>

1. <span data-ttu-id="5b4a7-116">**Konfliktní odkazy na balíčky NuGet** zabránit se přeloží během obnovení balíčku verze.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-116">**Conflicting NuGet package references** prevent a version from being resolved during package restore.</span></span>
2. <span data-ttu-id="5b4a7-117">**Rozbíjející změny mezi verzí** způsobovat chyby a výjimky za běhu.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-117">**Breaking changes between the versions** cause bugs and exceptions at runtime.</span></span>
3. <span data-ttu-id="5b4a7-118">**Balíček sestavení silně pojmenováno**změně verze sestavení a spuštění aplikace v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-118">**The package assembly is strong named**, the assembly version changed, and the app is running on the .NET Framework.</span></span> <span data-ttu-id="5b4a7-119">Přesměrování vazby sestavení jsou povinné.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-119">Assembly binding redirects are required.</span></span>

<span data-ttu-id="5b4a7-120">Není možné zjistit, jaké balíčky budou používat souběžně s vlastními.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-120">It's not possible to know what packages will be used alongside your own.</span></span> <span data-ttu-id="5b4a7-121">Dobrým způsobem, jak snížit pravděpodobnost, že kosočtverce závislosti zásadní knihovny je minimalizovat počet balíčků, které nejvíc potřebujete.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-121">A good way to reduce the likelihood of a diamond dependency breaking your library is to minimize the number of packages you depend on.</span></span>

<span data-ttu-id="5b4a7-122">**PROVEĎTE ✔️** zkontrolujte vaše knihovna .NET pro nepotřebné závislosti.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-122">**✔️ DO** review your .NET library for unnecessary dependencies.</span></span>

## <a name="nuget-dependency-version-ranges"></a><span data-ttu-id="5b4a7-123">Rozsahů verzí závislostí NuGet</span><span class="sxs-lookup"><span data-stu-id="5b4a7-123">NuGet dependency version ranges</span></span>

<span data-ttu-id="5b4a7-124">Odkaz na balíček určuje rozsah platný balíčky, které umožňuje.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-124">A package reference specifies the range of valid packages it allows.</span></span> <span data-ttu-id="5b4a7-125">Obvykle referenční verze balíčku v souboru projektu je minimální verze a neexistuje žádná maximální.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-125">Typically, the package reference version in the project file is the minimum version and there's no maximum.</span></span>

```xml
<!-- Accepts any version 1.0 and above. -->
<PackageReference Include="ExamplePackage" Version="1.0" />
```

<span data-ttu-id="5b4a7-126">Jsou pravidla, která používá NuGet při řešení závislostí [komplexní](/nuget/consume-packages/dependency-resolution), ale NuGet vždycky hledá na nejnižší příslušné verzi.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-126">The rules that NuGet uses when resolving dependencies are [complex](/nuget/consume-packages/dependency-resolution), but NuGet always looks for the lowest applicable version.</span></span> <span data-ttu-id="5b4a7-127">NuGet upřednostňuje nejnižší použitelná verze oproti použití nejvyšší dostupná, protože nejnižší bude mít nejnižší problémy s kompatibilitou.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-127">NuGet prefers the lowest applicable version over using the highest available because the lowest will have the least compatibility issues.</span></span>

<span data-ttu-id="5b4a7-128">Z důvodu nejnižší pravidlo použít verze NuGet není potřeba umístit horní verzi nebo přesně rozsah na odkazy na balíček, aby se zabránilo načtení nejnovější verze.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-128">Because of NuGet's lowest applicable version rule, it isn't necessary to place an upper version or exact range on package references to avoid getting the latest version.</span></span> <span data-ttu-id="5b4a7-129">NuGet již pokusí najít verzi nejnižší, nejkompatibilnější za vás.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-129">NuGet already tries to find the lowest, most compatible version for you.</span></span>

```xml
<!-- Accepts 1.0 up to 1.x, but not 2.0 and higher. -->
<PackageReference Include="ExamplePackage" Version="[1.0,2.0)" />

<!-- Accepts exactly 1.0. -->
<PackageReference Include="ExamplePackage" Version="[1.0]" />
```

<span data-ttu-id="5b4a7-130">Verze horní omezení způsobí, že správci balíčků NuGet selhat, pokud dojde ke konfliktu.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-130">Upper version limits will cause NuGet to fail if there's a conflict.</span></span> <span data-ttu-id="5b4a7-131">Například jedna knihovna přijímá přesně 1,0, zatímco jiné knihovny vyžaduje 2.0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-131">For example, one library accepts exactly 1.0 while another library requires 2.0 or above.</span></span> <span data-ttu-id="5b4a7-132">Zatímco rozbíjející změny v může zavedly ve verzi 2.0, závislost verze strict nebo horní mez zaručuje chybu.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-132">While breaking changes may have been introduced in version 2.0, a strict or upper limit version dependency guarantees an error.</span></span>

<span data-ttu-id="5b4a7-133">![Diamond závislost konflikt](./media/dependencies/diamond-dependency-conflict.png "Diamond konflikt závislostí")</span><span class="sxs-lookup"><span data-stu-id="5b4a7-133">![Diamond dependency conflict](./media/dependencies/diamond-dependency-conflict.png "Diamond dependency conflict")</span></span>

<span data-ttu-id="5b4a7-134">**❌ NEPODPORUJÍ** mají odkazy na balíčky NuGet se žádná minimální verze.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-134">**❌ DO NOT** have NuGet package references with no minimum version.</span></span>

<span data-ttu-id="5b4a7-135">**❌ Nepoužívejte** odkazy na balíčky NuGet, které vyžadují přesnou verzi.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-135">**❌ AVOID** NuGet package references that demand an exact version.</span></span>

<span data-ttu-id="5b4a7-136">**❌ Nepoužívejte** odkazy na balíček NuGet s verzí horní mez.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-136">**❌ AVOID** NuGet package references with a version upper limit.</span></span>

## <a name="nuget-shared-source-packages"></a><span data-ttu-id="5b4a7-137">Balíčky NuGet, které jsou sdílené zdroje</span><span class="sxs-lookup"><span data-stu-id="5b4a7-137">NuGet shared source packages</span></span>

<span data-ttu-id="5b4a7-138">Jedním ze způsobů ke snížení externí závislosti balíčků NuGet je odkazují na sdílené zdroje balíčků.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-138">One way to reduce external NuGet package dependencies is to reference shared source packages.</span></span> <span data-ttu-id="5b4a7-139">Sdílený zdrojový balíček obsahuje [souborů zdrojového kódu](/nuget/reference/nuspec#including-content-files) , které jsou součástí projektu při odkazování.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-139">A shared source package contains [source code files](/nuget/reference/nuspec#including-content-files) that are included in a project when referenced.</span></span> <span data-ttu-id="5b4a7-140">Protože jste právě včetně soubory zdrojového kódu, které jsou kompilovány s využitím zbytku projektu, neexistuje žádné externí závislosti a pravděpodobnost konfliktu.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-140">Because you're just including source code files that are compiled with the rest of your project, there's no external dependency and chance of conflict.</span></span>

<span data-ttu-id="5b4a7-141">Sdílený zdroj, které balíčky se skvěle hodí k včetně malé funkce.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-141">Shared source packages are great for including small pieces of functionality.</span></span> <span data-ttu-id="5b4a7-142">Například sdílené zdroje balíčku z metody helper pro volání HTTP.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-142">For example, a shared source package of helper methods for making HTTP calls.</span></span>

<span data-ttu-id="5b4a7-143">![Sdílený zdroj balíčku](./media/dependencies/shared-source-package.png "sdílené zdroje balíčku")</span><span class="sxs-lookup"><span data-stu-id="5b4a7-143">![Shared source package](./media/dependencies/shared-source-package.png "Shared source package")</span></span>

```xml
<PackageReference Include="Microsoft.Extensions.Buffers.Testing.Sources" PrivateAssets="All" Version="1.0" />
```

<span data-ttu-id="5b4a7-144">![Sdílený zdroj projektu](./media/dependencies/shared-source-project.png "sdílený zdrojový projekt")</span><span class="sxs-lookup"><span data-stu-id="5b4a7-144">![Shared source project](./media/dependencies/shared-source-project.png "Shared source project")</span></span>

<span data-ttu-id="5b4a7-145">Sdílený zdroj balíčků mají určitá omezení.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-145">Shared source packages have some limitations.</span></span> <span data-ttu-id="5b4a7-146">Se může odkazovat jen `PackageReference`, tak starší `packages.config` projekty jsou vyloučeny.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-146">They can only be referenced by `PackageReference`, so older `packages.config` projects are excluded.</span></span> <span data-ttu-id="5b4a7-147">Sdílený zdroj balíčků jsou také pouze použitelný pro projekty se stejným typem jazyka.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-147">Also shared source packages are only usable by projects with the same language type.</span></span> <span data-ttu-id="5b4a7-148">Z důvodu tato omezení jsou nejvhodnější sdílené zdroje balíčků ke sdílení funkcí v rámci projektu aplikace open source.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-148">Because of these limitations shared source packages are best used to share functionality within an open-source project.</span></span>

<span data-ttu-id="5b4a7-149">**✔️ ZVAŽTE** odkazování na sdílené zdroje balíčků pro malé a interní funkční součásti.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-149">**✔️ CONSIDER** referencing shared source packages for small, internal pieces of functionality.</span></span>

<span data-ttu-id="5b4a7-150">**✔️ ZVAŽTE** provádění vašeho balíčku sdílené zdroje balíčku pokud poskytuje malé, interní funkční součásti.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-150">**✔️ CONSIDER** making your package a shared source package if it provides small, internal pieces of functionality.</span></span>

<span data-ttu-id="5b4a7-151">**PROVEĎTE ✔️** odkazují na sdílené zdroje balíčků s `PrivateAssets="All"`.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-151">**✔️ DO** reference shared source packages with `PrivateAssets="All"`.</span></span>

> <span data-ttu-id="5b4a7-152">Toto nastavení určuje balíček NuGet je pouze pro použití při vývoji a by neměly být vystaveny jako veřejné závislost.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-152">This setting tells NuGet the package is only to be used at development time and shouldn't be exposed as a public dependency.</span></span>

<span data-ttu-id="5b4a7-153">**❌ NEPODPORUJÍ** být sdílených typů zdroje balíčku ve veřejném rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-153">**❌ DO NOT** have shared source package types in your public API.</span></span>

> <span data-ttu-id="5b4a7-154">Sdílený zdroj typy jsou kompilovány do odkazující sestavení a nemůže se vyměňují přes hranice sestavení.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-154">Shared source types are compiled into the referencing assembly and can't be exchanged across assembly boundaries.</span></span> <span data-ttu-id="5b4a7-155">Například sdílené zdroje `IRepository` typ v jednom projektu je samostatný typ ze stejného sdíleného zdroje `IRepository` v jiném projektu.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-155">For example, a shared-source `IRepository` type in one project is a separate type from the same shared-source `IRepository` in another project.</span></span> <span data-ttu-id="5b4a7-156">Typy v balíčcích sdílené zdroje by měly mít `internal` viditelnost.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-156">Types in shared source packages should have an `internal` visibility.</span></span>

<span data-ttu-id="5b4a7-157">**❌ NEPODPORUJÍ** publikování sdílené zdroje balíčků na NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-157">**❌ DO NOT** publish shared source packages to NuGet.org.</span></span>

> <span data-ttu-id="5b4a7-158">Sdílený zdroj balíčky obsahují zdrojový kód a jde použít jenom projekty se stejným typem jazyka.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-158">Shared source packages contain source code and can only be used by projects with the same language type.</span></span> <span data-ttu-id="5b4a7-159">Například C# sdílené zdroje balíčku nelze použít pro F# aplikace.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-159">For example, a C# shared source package cannot be used by an F# application.</span></span>
>
> <span data-ttu-id="5b4a7-160">Publikovat balíčky sdílené zdroje, které mají [místní informační kanál či MyGet](./publish-nuget-package.md) využívat interně v rámci svého projektu.</span><span class="sxs-lookup"><span data-stu-id="5b4a7-160">Publish shared source packages to a [local feed or MyGet](./publish-nuget-package.md) to consume them internally within your project.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5b4a7-161">[Předchozí](nuget.md)
>[další](sourcelink.md)</span><span class="sxs-lookup"><span data-stu-id="5b4a7-161">[Previous](nuget.md)
[Next](sourcelink.md)</span></span>