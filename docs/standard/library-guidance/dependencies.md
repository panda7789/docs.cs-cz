---
title: Závislosti a knihovny .NET
description: Doporučení osvědčených postupů pro správu závislostí NuGet v knihovnách .NET.
ms.date: 10/02/2018
ms.openlocfilehash: b5742bf4724c4aff4beb4ca40a543bd096528a00
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706501"
---
# <a name="dependencies"></a><span data-ttu-id="81547-103">Závislosti</span><span class="sxs-lookup"><span data-stu-id="81547-103">Dependencies</span></span>

<span data-ttu-id="81547-104">Hlavním způsobem přidání závislostí do knihovny .NET je odkazování na balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="81547-104">The primary way of adding dependencies to a .NET library is referencing NuGet packages.</span></span> <span data-ttu-id="81547-105">Odkazy na balíček NuGet vám umožní rychle znovu využít a využívat už napsané funkce, ale jsou to společný zdroj tření pro vývojáře na platformě .NET.</span><span class="sxs-lookup"><span data-stu-id="81547-105">NuGet package references allow you to quickly reuse and leverage already written functionality, but they're a common source of friction for .NET developers.</span></span> <span data-ttu-id="81547-106">Správná Správa závislostí je důležité, aby nedošlo ke změnám v jiných knihovnách .NET proti narušení vaší knihovny .NET a naopak.</span><span class="sxs-lookup"><span data-stu-id="81547-106">Correctly managing dependencies is important to prevent changes in other .NET libraries from breaking your .NET library, and vice versa!</span></span>

## <a name="diamond-dependencies"></a><span data-ttu-id="81547-107">Kosočtvercové závislosti</span><span class="sxs-lookup"><span data-stu-id="81547-107">Diamond dependencies</span></span>

<span data-ttu-id="81547-108">V případě, že projekt .NET má ve stromu závislostí více verzí balíčku, je běžné situaci.</span><span class="sxs-lookup"><span data-stu-id="81547-108">It's a common situation for a .NET project to have multiple versions of a package in its dependency tree.</span></span> <span data-ttu-id="81547-109">Například aplikace závisí na dvou balíčcích NuGet, přičemž každý z nich závisí na různých verzích stejného balíčku.</span><span class="sxs-lookup"><span data-stu-id="81547-109">For example, an app depends on two NuGet packages, each of which depends on different versions of the same package.</span></span> <span data-ttu-id="81547-110">V grafu závislostí aplikace teď existuje závislost kosočtverce.</span><span class="sxs-lookup"><span data-stu-id="81547-110">A diamond dependency now exists in the app's dependency graph.</span></span>

<span data-ttu-id="81547-111">![Kosočtverec – závislost](./media/dependencies/diamond-dependency.png "Kosočtverec – závislost")</span><span class="sxs-lookup"><span data-stu-id="81547-111">![Diamond dependency](./media/dependencies/diamond-dependency.png "Diamond dependency")</span></span>

<span data-ttu-id="81547-112">V době sestavení NuGet analyzuje všechny balíčky, na kterých projekt závisí, včetně závislostí závislostí.</span><span class="sxs-lookup"><span data-stu-id="81547-112">At build time, NuGet analyzes all the packages that a project depends on, including the dependencies of dependencies.</span></span> <span data-ttu-id="81547-113">Při zjištění více verzí balíčku se pravidla vyhodnotí, aby se vybrala jedna.</span><span class="sxs-lookup"><span data-stu-id="81547-113">When multiple versions of a package are detected, rules are evaluated to pick one.</span></span> <span data-ttu-id="81547-114">Sjednocení balíčků je nezbytné, protože spuštěné souběžné verze sestavení ve stejné aplikaci jsou v rozhraní .NET problematické.</span><span class="sxs-lookup"><span data-stu-id="81547-114">Unifying packages is necessary because running side-by-side versions of an assembly in the same application is problematic in .NET.</span></span>

<span data-ttu-id="81547-115">Většinu diamantových závislostí lze snadno vyřešit. můžou se ale v určitých případech vytvářet problémy:</span><span class="sxs-lookup"><span data-stu-id="81547-115">Most diamond dependencies are easily resolved; however, they can create issues in certain circumstances:</span></span>

1. <span data-ttu-id="81547-116">**Konfliktní odkazy na balíčky NuGet** brání v vyřešení verze během obnovování balíčku.</span><span class="sxs-lookup"><span data-stu-id="81547-116">**Conflicting NuGet package references** prevent a version from being resolved during package restore.</span></span>
2. <span data-ttu-id="81547-117">**Narušením změn mezi verzemi** dojde k chybám a výjimkám za běhu.</span><span class="sxs-lookup"><span data-stu-id="81547-117">**Breaking changes between the versions** cause bugs and exceptions at runtime.</span></span>
3. <span data-ttu-id="81547-118">**Sestavení balíčku má silný název**, verze sestavení se změnila a aplikace je spuštěná na .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="81547-118">**The package assembly is strong named**, the assembly version changed, and the app is running on the .NET Framework.</span></span> <span data-ttu-id="81547-119">Přesměrování vazby sestavení jsou povinná.</span><span class="sxs-lookup"><span data-stu-id="81547-119">Assembly binding redirects are required.</span></span>

<span data-ttu-id="81547-120">Není možné zjistit, jaké balíčky se budou používat společně s vašimi vlastními.</span><span class="sxs-lookup"><span data-stu-id="81547-120">It's not possible to know what packages will be used alongside your own.</span></span> <span data-ttu-id="81547-121">Dobrým způsobem, jak snížit pravděpodobnost přerušení vaší knihovny, je minimalizovat počet balíčků, na kterých jste závislí.</span><span class="sxs-lookup"><span data-stu-id="81547-121">A good way to reduce the likelihood of a diamond dependency breaking your library is to minimize the number of packages you depend on.</span></span>

<span data-ttu-id="81547-122">**✔️** Projděte si knihovnu .NET, abyste měli zbytečné závislosti.</span><span class="sxs-lookup"><span data-stu-id="81547-122">**✔️ DO** review your .NET library for unnecessary dependencies.</span></span>

## <a name="nuget-dependency-version-ranges"></a><span data-ttu-id="81547-123">Rozsahy verzí závislosti NuGet</span><span class="sxs-lookup"><span data-stu-id="81547-123">NuGet dependency version ranges</span></span>

<span data-ttu-id="81547-124">Odkaz na balíček určuje rozsah platných balíčků, které umožňuje.</span><span class="sxs-lookup"><span data-stu-id="81547-124">A package reference specifies the range of valid packages it allows.</span></span> <span data-ttu-id="81547-125">Obvykle je referenční verze balíčku v souboru projektu minimální verze a neexistuje žádná maximální hodnota.</span><span class="sxs-lookup"><span data-stu-id="81547-125">Typically, the package reference version in the project file is the minimum version and there's no maximum.</span></span>

```xml
<!-- Accepts any version 1.0 and above. -->
<PackageReference Include="ExamplePackage" Version="1.0" />
```

<span data-ttu-id="81547-126">Pravidla, která nástroj NuGet používá při řešení závislostí, jsou [složitá](/nuget/consume-packages/dependency-resolution), ale NuGet vždy vyhledává nejnižší platnou verzi.</span><span class="sxs-lookup"><span data-stu-id="81547-126">The rules that NuGet uses when resolving dependencies are [complex](/nuget/consume-packages/dependency-resolution), but NuGet always looks for the lowest applicable version.</span></span> <span data-ttu-id="81547-127">NuGet upřednostňuje nejnižší použitelnou verzi přes nejvyšší dostupný, protože nejnižší bude mít minimálně problémy s kompatibilitou.</span><span class="sxs-lookup"><span data-stu-id="81547-127">NuGet prefers the lowest applicable version over using the highest available because the lowest will have the least compatibility issues.</span></span>

<span data-ttu-id="81547-128">Vzhledem k tomu, že pravidlo pro nejnižší verzi NuGetu splňuje, není nutné při odkazech na balíček umístit horní nebo přesný rozsah, aby se předešlo získání nejnovější verze.</span><span class="sxs-lookup"><span data-stu-id="81547-128">Because of NuGet's lowest applicable version rule, it isn't necessary to place an upper version or exact range on package references to avoid getting the latest version.</span></span> <span data-ttu-id="81547-129">NuGet se už snaží najít nejnižší, nejvíce kompatibilní verzi.</span><span class="sxs-lookup"><span data-stu-id="81547-129">NuGet already tries to find the lowest, most compatible version for you.</span></span>

```xml
<!-- Accepts 1.0 up to 1.x, but not 2.0 and higher. -->
<PackageReference Include="ExamplePackage" Version="[1.0,2.0)" />

<!-- Accepts exactly 1.0. -->
<PackageReference Include="ExamplePackage" Version="[1.0]" />
```

<span data-ttu-id="81547-130">Omezení horní verze způsobí selhání NuGet v případě konfliktu.</span><span class="sxs-lookup"><span data-stu-id="81547-130">Upper version limits will cause NuGet to fail if there's a conflict.</span></span> <span data-ttu-id="81547-131">Například jedna knihovna akceptuje přesně 1,0, zatímco jiná knihovna vyžaduje 2,0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="81547-131">For example, one library accepts exactly 1.0 while another library requires 2.0 or above.</span></span> <span data-ttu-id="81547-132">I když mohou být zásadní změny představené ve verzi 2,0, je zaručena chybná závislost verze striktní nebo horní limit.</span><span class="sxs-lookup"><span data-stu-id="81547-132">While breaking changes may have been introduced in version 2.0, a strict or upper limit version dependency guarantees an error.</span></span>

<span data-ttu-id="81547-133">![Konflikt závislosti v kosočtverec](./media/dependencies/diamond-dependency-conflict.png "Konflikt závislosti v kosočtverec")</span><span class="sxs-lookup"><span data-stu-id="81547-133">![Diamond dependency conflict](./media/dependencies/diamond-dependency-conflict.png "Diamond dependency conflict")</span></span>

<span data-ttu-id="81547-134">**❌** nemáte odkazy na balíček NuGet bez minimální verze.</span><span class="sxs-lookup"><span data-stu-id="81547-134">**❌ DO NOT** have NuGet package references with no minimum version.</span></span>

<span data-ttu-id="81547-135">**❌ se vyhnout** Balíček NuGet odkazuje na přesnou verzi.</span><span class="sxs-lookup"><span data-stu-id="81547-135">**❌ AVOID** NuGet package references that demand an exact version.</span></span>

<span data-ttu-id="81547-136">**❌ se vyhnout** Balíček NuGet odkazuje na horní limit verze.</span><span class="sxs-lookup"><span data-stu-id="81547-136">**❌ AVOID** NuGet package references with a version upper limit.</span></span>

## <a name="nuget-shared-source-packages"></a><span data-ttu-id="81547-137">Sdílené zdrojové balíčky NuGet</span><span class="sxs-lookup"><span data-stu-id="81547-137">NuGet shared source packages</span></span>

<span data-ttu-id="81547-138">Jedním ze způsobů, jak omezit externí závislosti balíčků NuGet, je odkazování na sdílené zdrojové balíčky.</span><span class="sxs-lookup"><span data-stu-id="81547-138">One way to reduce external NuGet package dependencies is to reference shared source packages.</span></span> <span data-ttu-id="81547-139">Sdílený zdrojový balíček obsahuje [soubory zdrojového kódu](/nuget/reference/nuspec#including-content-files) , které jsou zahrnuty v projektu, pokud se na něj odkazuje.</span><span class="sxs-lookup"><span data-stu-id="81547-139">A shared source package contains [source code files](/nuget/reference/nuspec#including-content-files) that are included in a project when referenced.</span></span> <span data-ttu-id="81547-140">Vzhledem k tomu, že právě jste zadali soubory zdrojového kódu, které jsou kompilovány se zbytkem projektu, neexistuje žádná externí závislost a šance na konflikt.</span><span class="sxs-lookup"><span data-stu-id="81547-140">Because you're just including source code files that are compiled with the rest of your project, there's no external dependency and chance of conflict.</span></span>

<span data-ttu-id="81547-141">Sdílené zdrojové balíčky jsou skvělé pro zahrnutí malých kousků funkcí.</span><span class="sxs-lookup"><span data-stu-id="81547-141">Shared source packages are great for including small pieces of functionality.</span></span> <span data-ttu-id="81547-142">Například sdílený zdrojový balíček pomocných metod pro vytváření volání HTTP.</span><span class="sxs-lookup"><span data-stu-id="81547-142">For example, a shared source package of helper methods for making HTTP calls.</span></span>

<span data-ttu-id="81547-143">![Sdílený zdrojový balíček](./media/dependencies/shared-source-package.png "Sdílený zdrojový balíček")</span><span class="sxs-lookup"><span data-stu-id="81547-143">![Shared source package](./media/dependencies/shared-source-package.png "Shared source package")</span></span>

```xml
<PackageReference Include="Microsoft.Extensions.Buffers.Testing.Sources" PrivateAssets="All" Version="1.0" />
```

<span data-ttu-id="81547-144">![Sdílený zdrojový projekt](./media/dependencies/shared-source-project.png "Sdílený zdrojový projekt")</span><span class="sxs-lookup"><span data-stu-id="81547-144">![Shared source project](./media/dependencies/shared-source-project.png "Shared source project")</span></span>

<span data-ttu-id="81547-145">Sdílené zdrojové balíčky mají určitá omezení.</span><span class="sxs-lookup"><span data-stu-id="81547-145">Shared source packages have some limitations.</span></span> <span data-ttu-id="81547-146">Můžou na ně odkazovat jenom `PackageReference`, aby se vyloučily starší `packages.config` projekty.</span><span class="sxs-lookup"><span data-stu-id="81547-146">They can only be referenced by `PackageReference`, so older `packages.config` projects are excluded.</span></span> <span data-ttu-id="81547-147">Sdílené zdrojové balíčky jsou také použitelné pouze v projektech se stejným typem jazyka.</span><span class="sxs-lookup"><span data-stu-id="81547-147">Also shared source packages are only usable by projects with the same language type.</span></span> <span data-ttu-id="81547-148">Z důvodu těchto omezení jsou sdílené zdrojové balíčky nejlépe používány pro sdílení funkcí v rámci open source projektu.</span><span class="sxs-lookup"><span data-stu-id="81547-148">Because of these limitations shared source packages are best used to share functionality within an open-source project.</span></span>

<span data-ttu-id="81547-149">**✔️ zvažte** odkazování na sdílené zdrojové balíčky pro malé, interní funkce.</span><span class="sxs-lookup"><span data-stu-id="81547-149">**✔️ CONSIDER** referencing shared source packages for small, internal pieces of functionality.</span></span>

<span data-ttu-id="81547-150">**✔️ zvažte** vytvoření balíčku sdíleného zdrojového kódu, pokud poskytuje malé, interní funkce.</span><span class="sxs-lookup"><span data-stu-id="81547-150">**✔️ CONSIDER** making your package a shared source package if it provides small, internal pieces of functionality.</span></span>

<span data-ttu-id="81547-151">**✔️** odkazují na sdílené zdrojové balíčky pomocí `PrivateAssets="All"`.</span><span class="sxs-lookup"><span data-stu-id="81547-151">**✔️ DO** reference shared source packages with `PrivateAssets="All"`.</span></span>

> <span data-ttu-id="81547-152">Toto nastavení říká NuGet, že balíček se má použít jenom v době vývoje a neměl by být vystavený jako veřejná závislost.</span><span class="sxs-lookup"><span data-stu-id="81547-152">This setting tells NuGet the package is only to be used at development time and shouldn't be exposed as a public dependency.</span></span>

<span data-ttu-id="81547-153">ve veřejném rozhraní API **není❌** sdílené zdrojové typy balíčků.</span><span class="sxs-lookup"><span data-stu-id="81547-153">**❌ DO NOT** have shared source package types in your public API.</span></span>

> <span data-ttu-id="81547-154">Sdílené zdrojové typy jsou kompilovány do odkazujícího sestavení a nelze je vyměňovat přes hranice sestavení.</span><span class="sxs-lookup"><span data-stu-id="81547-154">Shared source types are compiled into the referencing assembly and can't be exchanged across assembly boundaries.</span></span> <span data-ttu-id="81547-155">Například typ Shared-Source `IRepository` v jednom projektu je samostatný typ ze stejného `IRepository` Shared Source v jiném projektu.</span><span class="sxs-lookup"><span data-stu-id="81547-155">For example, a shared-source `IRepository` type in one project is a separate type from the same shared-source `IRepository` in another project.</span></span> <span data-ttu-id="81547-156">Typy ve sdílených zdrojových balíčcích by měly mít `internal` viditelnost.</span><span class="sxs-lookup"><span data-stu-id="81547-156">Types in shared source packages should have an `internal` visibility.</span></span>

<span data-ttu-id="81547-157">**❌** nepublikujte sdílené zdrojové balíčky do NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="81547-157">**❌ DO NOT** publish shared source packages to NuGet.org.</span></span>

> <span data-ttu-id="81547-158">Sdílené zdrojové balíčky obsahují zdrojový kód a mohou být použity pouze v projektech se stejným typem jazyka.</span><span class="sxs-lookup"><span data-stu-id="81547-158">Shared source packages contain source code and can only be used by projects with the same language type.</span></span> <span data-ttu-id="81547-159">Například C# sdílený zdrojový balíček nemůže používat F# aplikace.</span><span class="sxs-lookup"><span data-stu-id="81547-159">For example, a C# shared source package cannot be used by an F# application.</span></span>
>
> <span data-ttu-id="81547-160">Publikujte sdílené zdrojové balíčky do [místního kanálu nebo MyGet](./publish-nuget-package.md) , aby je bylo možné interně spotřebovat ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="81547-160">Publish shared source packages to a [local feed or MyGet](./publish-nuget-package.md) to consume them internally within your project.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="81547-161">[Předchozí](nuget.md)
>[Další](sourcelink.md)</span><span class="sxs-lookup"><span data-stu-id="81547-161">[Previous](nuget.md)
[Next](sourcelink.md)</span></span>
