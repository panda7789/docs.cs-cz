---
title: Správa verze závislosti balíčku pro .NET Core 1.0
description: Další informace o správě verze závislosti balíčku pro knihovny .NET Core a aplikace.
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.openlocfilehash: 96d154f045303e32de606475e77ab2e6b4f7bcda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33211335"
---
# <a name="how-to-manage-package-dependency-versions-for-net-core-10"></a><span data-ttu-id="5992a-103">Správa verze závislosti balíčku pro .NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="5992a-103">How to Manage Package Dependency Versions for .NET Core 1.0</span></span>

<span data-ttu-id="5992a-104">Tento článek popisuje, co potřebujete vědět o verze balíčku pro knihovny .NET Core a aplikace.</span><span class="sxs-lookup"><span data-stu-id="5992a-104">This article covers what you need to know about package versions for your .NET Core libraries and apps.</span></span>

## <a name="glossary"></a><span data-ttu-id="5992a-105">Slovníček</span><span class="sxs-lookup"><span data-stu-id="5992a-105">Glossary</span></span>

<span data-ttu-id="5992a-106">**Opravte** -opravě závislosti znamená používáte stejná "rodina" balíčků vydala NuGet pro rozhraní .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="5992a-106">**Fix** - Fixing dependencies means you are using the same "family" of packages released on NuGet for .NET Core 1.0.</span></span>

<span data-ttu-id="5992a-107">**Metapackage** -A NuGet balíček, který představuje sadu balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="5992a-107">**Metapackage** - A NuGet package that represents a set of NuGet packages.</span></span>

<span data-ttu-id="5992a-108">**Ořezávání** -operace odebrání balíčků není závislá na z metapackage.</span><span class="sxs-lookup"><span data-stu-id="5992a-108">**Trimming** - The act of removing the packages you do not depend on from a metapackage.</span></span>  <span data-ttu-id="5992a-109">Toto je něco relevantní pro autory balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="5992a-109">This is something relevant for NuGet package authors.</span></span>  <span data-ttu-id="5992a-110">V tématu [snižuje závislosti balíčků s project.json](../deploying/reducing-dependencies.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="5992a-110">See [Reducing Package Dependencies with project.json](../deploying/reducing-dependencies.md) for more information.</span></span> 

## <a name="fix-your-dependencies-to-net-core-10"></a><span data-ttu-id="5992a-111">Opravte svoje závislosti na .NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="5992a-111">Fix your dependencies to .NET Core 1.0</span></span>

<span data-ttu-id="5992a-112">Pokud chcete spolehlivě obnovení balíčků a zápis spolehlivého kódu, je důležité opravili závislostmi verzích balíčky přesouvání spolu s .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="5992a-112">To reliably restore packages and write reliable code, it's important that you fix your dependencies to the versions of packages shipping alongside .NET Core 1.0.</span></span>  <span data-ttu-id="5992a-113">To znamená, že každý balíček musí mít jednu verzi s žádné další kvalifikátory.</span><span class="sxs-lookup"><span data-stu-id="5992a-113">This means every package should have a single version with no additional qualifiers.</span></span>

<span data-ttu-id="5992a-114">**Příklady balíčků pevné hodnotě 1.0**</span><span class="sxs-lookup"><span data-stu-id="5992a-114">**Examples of packages fixed to 1.0**</span></span>

`"System.Collections":"4.0.11"`

`"NETStandard.Library":"1.6.0"`

`"Microsoft.NETCore.App":"1.0.0"`

<span data-ttu-id="5992a-115">**Příklady balíčky, které není nastaven na 1.0**</span><span class="sxs-lookup"><span data-stu-id="5992a-115">**Examples of packages that are NOT fixed to 1.0**</span></span>

`"Microsoft.NETCore.App":"1.0.0-rc4-00454-00"`

`"System.Net.Http":"4.1.0-*"`

`"System.Text.RegularExpressions":"4.0.10-rc3-24021-00"`

### <a name="why-does-this-matter"></a><span data-ttu-id="5992a-116">Proč této věci?</span><span class="sxs-lookup"><span data-stu-id="5992a-116">Why does this matter?</span></span>

<span data-ttu-id="5992a-117">Zaručujeme, že pokud neopravíte svoje závislosti na co se dodává spolu s .NET Core 1.0, tyto balíčky, budou všechny spolupracovat.</span><span class="sxs-lookup"><span data-stu-id="5992a-117">We guarantee that if you fix your dependencies to what ships alongside .NET Core 1.0, those packages will all work together.</span></span> <span data-ttu-id="5992a-118">Neexistuje žádná taková záruka, pokud používáte balíčky, které nejsou pevné tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="5992a-118">There is no such guarantee if you use packages which aren't fixed in this way.</span></span>

### <a name="scenarios"></a><span data-ttu-id="5992a-119">Scénáře</span><span class="sxs-lookup"><span data-stu-id="5992a-119">Scenarios</span></span>

<span data-ttu-id="5992a-120">I když je velký seznam všech balíčků a jejich verze vydané s .NET Core 1.0, nemusí mít si můžete prohlédnout, pokud kód klesne pod určité scénáře.</span><span class="sxs-lookup"><span data-stu-id="5992a-120">Although there is a big list of all packages and their versions released with .NET Core 1.0, you may not have to look through it if your code falls under certain scenarios.</span></span>

<span data-ttu-id="5992a-121">**Jste si v závislosti na pouze** `NETStandard.Library` **?**</span><span class="sxs-lookup"><span data-stu-id="5992a-121">**Are you depending only on** `NETStandard.Library`**?**</span></span>

<span data-ttu-id="5992a-122">Pokud ano, problém byste měli odstranit vaší `NETStandard.Library` balíček verze `1.6`.</span><span class="sxs-lookup"><span data-stu-id="5992a-122">If so, you should fix your `NETStandard.Library` package to version `1.6`.</span></span>  <span data-ttu-id="5992a-123">Protože je to kurátorované metapackage, jeho uzavření balíček také vyřešili 1.0.</span><span class="sxs-lookup"><span data-stu-id="5992a-123">Because this is a curated metapackage, its package closure is also fixed to 1.0.</span></span>

<span data-ttu-id="5992a-124">**Jste si v závislosti na pouze** `Microsoft.NETCore.App` **?**</span><span class="sxs-lookup"><span data-stu-id="5992a-124">**Are you depending only on** `Microsoft.NETCore.App`**?**</span></span>

<span data-ttu-id="5992a-125">Pokud ano, problém byste měli odstranit vaší `Microsoft.NETCore.App` balíček verze `1.0.0`.</span><span class="sxs-lookup"><span data-stu-id="5992a-125">If so, you should fix your `Microsoft.NETCore.App` package to version `1.0.0`.</span></span>  <span data-ttu-id="5992a-126">Protože je to kurátorované metapackage, jeho uzavření balíček také vyřešili 1.0.</span><span class="sxs-lookup"><span data-stu-id="5992a-126">Because this is a curated metapackage, its package closure is also fixed to 1.0.</span></span>

<span data-ttu-id="5992a-127">**Jste si [oříznutí](../deploying/reducing-dependencies.md) vaše** `NETStandard.Library` **nebo** `Microsoft.NETCore.App` **metapackage závislosti?**</span><span class="sxs-lookup"><span data-stu-id="5992a-127">**Are you [trimming](../deploying/reducing-dependencies.md) your** `NETStandard.Library` **or** `Microsoft.NETCore.App` **metapackage dependencies?**</span></span>

<span data-ttu-id="5992a-128">Pokud ano, měli byste zajistit, že metapackage se vyřešen 1.0.</span><span class="sxs-lookup"><span data-stu-id="5992a-128">If so, you should ensure that the metapackage you start with is fixed to 1.0.</span></span>  <span data-ttu-id="5992a-129">Jednotlivé balíčky, které závisí na po oříznutí odstraněny také 1.0.</span><span class="sxs-lookup"><span data-stu-id="5992a-129">The individual packages you depend on after trimming are also fixed to 1.0.</span></span>

<span data-ttu-id="5992a-130">**Jste si v závislosti na balíčky mimo** `NETStandard.Library` **nebo** `Microsoft.NETCore.App` **metapackages?**</span><span class="sxs-lookup"><span data-stu-id="5992a-130">**Are you depending on packages outside the** `NETStandard.Library` **or** `Microsoft.NETCore.App` **metapackages?**</span></span>

<span data-ttu-id="5992a-131">Pokud ano, budete muset vyřešit svoje závislosti do 1.0.</span><span class="sxs-lookup"><span data-stu-id="5992a-131">If so, you need to fix your other dependencies to 1.0.</span></span>  <span data-ttu-id="5992a-132">Zjistit verzi správný balíček a sestavte čísla na konci tohoto článku.</span><span class="sxs-lookup"><span data-stu-id="5992a-132">See the correct package versions and build numbers at the end of this article.</span></span>

### <a name="a-note-on-using-a-splat-string--when-versioning"></a><span data-ttu-id="5992a-133">Poznámka: na pomocí řetězce splat (\*) při Správa verzí</span><span class="sxs-lookup"><span data-stu-id="5992a-133">A note on using a splat string (\*) when versioning</span></span>

<span data-ttu-id="5992a-134">Přijaly vzor Správa verzí, která používá splat (\*) řetězec takto: `"System.Collections":"4.0.11-*"`.</span><span class="sxs-lookup"><span data-stu-id="5992a-134">You may have adopted a versioning pattern which uses a splat (\*) string like this: `"System.Collections":"4.0.11-*"`.</span></span>

<span data-ttu-id="5992a-135">**Neměli byste**.</span><span class="sxs-lookup"><span data-stu-id="5992a-135">**You should not do this**.</span></span>  <span data-ttu-id="5992a-136">Pomocí řetězce splat, může mít za následek obnovují se balíčky z různých sestavení pro některé z nich může být, že se vám dál než .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="5992a-136">Using the splat string could result in restoring packages from different builds, some of which may be further along than .NET Core 1.0.</span></span>  <span data-ttu-id="5992a-137">Výsledkem by mohlo pak některé balíčky se nekompatibilní.</span><span class="sxs-lookup"><span data-stu-id="5992a-137">This could then result in some packages being incompatible.</span></span>

## <a name="packages-and-version-numbers-organized-by-metapackage"></a><span data-ttu-id="5992a-138">Balíčky a uspořádané podle Metapackage čísla verzí</span><span class="sxs-lookup"><span data-stu-id="5992a-138">Packages and Version Numbers organized by Metapackage</span></span>

<span data-ttu-id="5992a-139">[Seznam všech balíčků .NET Standard a jejich verze 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt).</span><span class="sxs-lookup"><span data-stu-id="5992a-139">[List of all .NET Standard packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt).</span></span>

<span data-ttu-id="5992a-140">[Seznam všech balíčků runtime a jejich verze 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt).</span><span class="sxs-lookup"><span data-stu-id="5992a-140">[List of all runtime packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt).</span></span>

<span data-ttu-id="5992a-141">[Seznam všech balíčků aplikací .NET Core a jejich verze 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt).</span><span class="sxs-lookup"><span data-stu-id="5992a-141">[List of all .NET Core application packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt).</span></span>
