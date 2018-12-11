---
title: Správa verzí závislosti balíčků pro .NET Core 1.0
description: Další informace o Správa verzí závislosti balíčků pro knihovny .NET Core a aplikace.
author: cartermp
ms.date: 06/20/2016
ms.custom: seodec18
ms.openlocfilehash: 7d7133ddb8717db1b830e531955454925c31a728
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168608"
---
# <a name="how-to-manage-package-dependency-versions-for-net-core-10"></a><span data-ttu-id="32624-103">Správa verzí závislosti balíčků pro .NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="32624-103">How to Manage Package Dependency Versions for .NET Core 1.0</span></span>

<span data-ttu-id="32624-104">Tento článek popisuje, co potřebujete vědět o verze balíčku pro knihovny .NET Core a aplikace.</span><span class="sxs-lookup"><span data-stu-id="32624-104">This article covers what you need to know about package versions for your .NET Core libraries and apps.</span></span>

## <a name="glossary"></a><span data-ttu-id="32624-105">Slovníček</span><span class="sxs-lookup"><span data-stu-id="32624-105">Glossary</span></span>

<span data-ttu-id="32624-106">**Oprava** – oprava závislostí znamená, že používáte stejné "řady" balíčků vydaných na webu NuGet pro .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="32624-106">**Fix** - Fixing dependencies means you are using the same "family" of packages released on NuGet for .NET Core 1.0.</span></span>

<span data-ttu-id="32624-107">**Microsoft.aspnetcore.all** -balíčku A NuGet, který představuje sadu balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="32624-107">**Metapackage** - A NuGet package that represents a set of NuGet packages.</span></span>

<span data-ttu-id="32624-108">**Ořezávání** – v rámci balíčky, které nezávisí na odebrání Microsoft.aspnetcore.all.</span><span class="sxs-lookup"><span data-stu-id="32624-108">**Trimming** - The act of removing the packages you do not depend on from a metapackage.</span></span>  <span data-ttu-id="32624-109">To je něco, které jsou relevantní pro autory balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="32624-109">This is something relevant for NuGet package authors.</span></span>  <span data-ttu-id="32624-110">Zobrazit [omezení závislosti balíčku s project.json](../deploying/reducing-dependencies.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="32624-110">See [Reducing Package Dependencies with project.json](../deploying/reducing-dependencies.md) for more information.</span></span> 

## <a name="fix-your-dependencies-to-net-core-10"></a><span data-ttu-id="32624-111">Oprava závislostí pro .NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="32624-111">Fix your dependencies to .NET Core 1.0</span></span>

<span data-ttu-id="32624-112">Spolehlivě obnovení balíčků a zápis spolehlivého kódu, je důležité, že oprava závislostí na verze balíčků přesouvání spolu s .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="32624-112">To reliably restore packages and write reliable code, it's important that you fix your dependencies to the versions of packages shipping alongside .NET Core 1.0.</span></span>  <span data-ttu-id="32624-113">To znamená, že každého balíčku by měl mít jednu verzi se žádné další kvalifikátory.</span><span class="sxs-lookup"><span data-stu-id="32624-113">This means every package should have a single version with no additional qualifiers.</span></span>

<span data-ttu-id="32624-114">**Příklady balíčků pevně 1.0**</span><span class="sxs-lookup"><span data-stu-id="32624-114">**Examples of packages fixed to 1.0**</span></span>

`"System.Collections":"4.0.11"`

`"NETStandard.Library":"1.6.0"`

`"Microsoft.NETCore.App":"1.0.0"`

<span data-ttu-id="32624-115">**Příklady balíčky, které jsou neopraveno 1.0**</span><span class="sxs-lookup"><span data-stu-id="32624-115">**Examples of packages that are NOT fixed to 1.0**</span></span>

`"Microsoft.NETCore.App":"1.0.0-rc4-00454-00"`

`"System.Net.Http":"4.1.0-*"`

`"System.Text.RegularExpressions":"4.0.10-rc3-24021-00"`

### <a name="why-does-this-matter"></a><span data-ttu-id="32624-116">Proč to důležité?</span><span class="sxs-lookup"><span data-stu-id="32624-116">Why does this matter?</span></span>

<span data-ttu-id="32624-117">Garantujeme, že pokud je oprava závislostí na co se dodává spolu s .NET Core 1.0, tyto balíčky budou všechny spolupracovat.</span><span class="sxs-lookup"><span data-stu-id="32624-117">We guarantee that if you fix your dependencies to what ships alongside .NET Core 1.0, those packages will all work together.</span></span> <span data-ttu-id="32624-118">Pokud používáte balíčky, které nejsou pevné tímto způsobem, není zaručeno takové.</span><span class="sxs-lookup"><span data-stu-id="32624-118">There is no such guarantee if you use packages which aren't fixed in this way.</span></span>

### <a name="scenarios"></a><span data-ttu-id="32624-119">Scénáře</span><span class="sxs-lookup"><span data-stu-id="32624-119">Scenarios</span></span>

<span data-ttu-id="32624-120">I když existuje velké objemy seznam všechny balíčky a jejich verzí vydané s .NET Core 1.0, pravděpodobně nemáte prohledávat, pokud váš kód v určitých situacích.</span><span class="sxs-lookup"><span data-stu-id="32624-120">Although there is a big list of all packages and their versions released with .NET Core 1.0, you may not have to look through it if your code falls under certain scenarios.</span></span>

<span data-ttu-id="32624-121">**Jste si v závislosti na pouze** `NETStandard.Library` **?**</span><span class="sxs-lookup"><span data-stu-id="32624-121">**Are you depending only on** `NETStandard.Library`**?**</span></span>

<span data-ttu-id="32624-122">Pokud ano, by měla vyřešit váš `NETStandard.Library` balíček verze `1.6`.</span><span class="sxs-lookup"><span data-stu-id="32624-122">If so, you should fix your `NETStandard.Library` package to version `1.6`.</span></span>  <span data-ttu-id="32624-123">Protože je to kurátorované Microsoft.aspnetcore.all, jeho uzavření balíčku je také pevně 1.0.</span><span class="sxs-lookup"><span data-stu-id="32624-123">Because this is a curated metapackage, its package closure is also fixed to 1.0.</span></span>

<span data-ttu-id="32624-124">**Jste si v závislosti na pouze** `Microsoft.NETCore.App` **?**</span><span class="sxs-lookup"><span data-stu-id="32624-124">**Are you depending only on** `Microsoft.NETCore.App`**?**</span></span>

<span data-ttu-id="32624-125">Pokud ano, by měla vyřešit váš `Microsoft.NETCore.App` balíček verze `1.0.0`.</span><span class="sxs-lookup"><span data-stu-id="32624-125">If so, you should fix your `Microsoft.NETCore.App` package to version `1.0.0`.</span></span>  <span data-ttu-id="32624-126">Protože je to kurátorované Microsoft.aspnetcore.all, jeho uzavření balíčku je také pevně 1.0.</span><span class="sxs-lookup"><span data-stu-id="32624-126">Because this is a curated metapackage, its package closure is also fixed to 1.0.</span></span>

<span data-ttu-id="32624-127">**Jste si [oříznutí](../deploying/reducing-dependencies.md) vaše** `NETStandard.Library` **nebo** `Microsoft.NETCore.App` **Microsoft.aspnetcore.all závislosti?**</span><span class="sxs-lookup"><span data-stu-id="32624-127">**Are you [trimming](../deploying/reducing-dependencies.md) your** `NETStandard.Library` **or** `Microsoft.NETCore.App` **metapackage dependencies?**</span></span>

<span data-ttu-id="32624-128">Pokud ano, měli byste zajistit, že je Microsoft.aspnetcore.all, které můžete začít s pevně 1.0.</span><span class="sxs-lookup"><span data-stu-id="32624-128">If so, you should ensure that the metapackage you start with is fixed to 1.0.</span></span>  <span data-ttu-id="32624-129">Jednotlivé balíčky, které závisí na po oříznutí odstraněny také 1.0.</span><span class="sxs-lookup"><span data-stu-id="32624-129">The individual packages you depend on after trimming are also fixed to 1.0.</span></span>

<span data-ttu-id="32624-130">**Jste si v závislosti na balíčky mimo** `NETStandard.Library` **nebo** `Microsoft.NETCore.App` **metabalíčky?**</span><span class="sxs-lookup"><span data-stu-id="32624-130">**Are you depending on packages outside the** `NETStandard.Library` **or** `Microsoft.NETCore.App` **metapackages?**</span></span>

<span data-ttu-id="32624-131">Pokud ano, budete muset opravit další závislosti 1.0.</span><span class="sxs-lookup"><span data-stu-id="32624-131">If so, you need to fix your other dependencies to 1.0.</span></span>  <span data-ttu-id="32624-132">Zobrazit verze správný balíček a sestaví čísel na konci tohoto článku.</span><span class="sxs-lookup"><span data-stu-id="32624-132">See the correct package versions and build numbers at the end of this article.</span></span>

### <a name="a-note-on-using-a-splat-string--when-versioning"></a><span data-ttu-id="32624-133">Poznámka týkající se použití splat řetězce (\*) při vytváření verzí</span><span class="sxs-lookup"><span data-stu-id="32624-133">A note on using a splat string (\*) when versioning</span></span>

<span data-ttu-id="32624-134">Přijali vzor správy verzí, který používá splat (\*) řetězce tímto způsobem: `"System.Collections":"4.0.11-*"`.</span><span class="sxs-lookup"><span data-stu-id="32624-134">You may have adopted a versioning pattern which uses a splat (\*) string like this: `"System.Collections":"4.0.11-*"`.</span></span>

<span data-ttu-id="32624-135">**Neměli byste**.</span><span class="sxs-lookup"><span data-stu-id="32624-135">**You should not do this**.</span></span>  <span data-ttu-id="32624-136">Pomocí řetězce splat by mohlo způsobit obnovují se balíčky z různých sestavení, z nichž některé mohou být dál než .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="32624-136">Using the splat string could result in restoring packages from different builds, some of which may be further along than .NET Core 1.0.</span></span>  <span data-ttu-id="32624-137">To může vést některých balíčků není kompatibilních.</span><span class="sxs-lookup"><span data-stu-id="32624-137">This could then result in some packages being incompatible.</span></span>

## <a name="packages-and-version-numbers-organized-by-metapackage"></a><span data-ttu-id="32624-138">Balíčky a čísel verzí uspořádané podle Microsoft.aspnetcore.all</span><span class="sxs-lookup"><span data-stu-id="32624-138">Packages and Version Numbers organized by Metapackage</span></span>

<span data-ttu-id="32624-139">[Seznam všech balíčků pro .NET Standard a jejich verze 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt).</span><span class="sxs-lookup"><span data-stu-id="32624-139">[List of all .NET Standard packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt).</span></span>

<span data-ttu-id="32624-140">[Seznam všech balíčků modulu runtime a jejich verze 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt).</span><span class="sxs-lookup"><span data-stu-id="32624-140">[List of all runtime packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt).</span></span>

<span data-ttu-id="32624-141">[Seznam všech balíčků aplikací .NET Core a jejich verze 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt).</span><span class="sxs-lookup"><span data-stu-id="32624-141">[List of all .NET Core application packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt).</span></span>
