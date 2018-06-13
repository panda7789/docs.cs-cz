---
title: Snižuje závislosti balíčků s project.json
description: Snížení závislosti balíčků, při vytváření obsahu na základě project.json knihovny.
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.openlocfilehash: ae314800f789cee363728def8347b5e6990acb0b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33211781"
---
# <a name="reducing-package-dependencies-with-projectjson"></a><span data-ttu-id="dc3d4-103">Snižuje závislosti balíčků s project.json</span><span class="sxs-lookup"><span data-stu-id="dc3d4-103">Reducing Package Dependencies with project.json</span></span>

<span data-ttu-id="dc3d4-104">Tento článek popisuje, co potřebujete vědět o snižuje vaše závislosti balíčků, při vytváření `project.json` knihovny.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-104">This article covers what you need to know about reducing your package dependencies when authoring `project.json` libraries.</span></span> <span data-ttu-id="dc3d4-105">Na konci tohoto článku se dozvíte, jak vytvořit knihovnu tak, že používá jenom závislosti, které potřebuje.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-105">By the end of this article, you will learn how to compose your library such that it only uses the dependencies it needs.</span></span> 

## <a name="why-its-important"></a><span data-ttu-id="dc3d4-106">Proč je důležité</span><span class="sxs-lookup"><span data-stu-id="dc3d4-106">Why it's Important</span></span>

<span data-ttu-id="dc3d4-107">.NET core je produkt skládá z balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-107">.NET Core is a product made up of NuGet packages.</span></span>  <span data-ttu-id="dc3d4-108">Je nezbytné balíček [. NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), které se balíček NuGet skládá z dalších balíčků.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-108">An essential package is the [.NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), which is a NuGet package composed of other packages.</span></span>  <span data-ttu-id="dc3d4-109">Poskytuje sadu balíčky, které zaručeně pracovat na více implementace rozhraní .NET, například rozhraní .NET Framework, .NET Core a Xamarin/Mono.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-109">It provides you with the set of packages that are guaranteed to work on multiple .NET implementations, such as .NET Framework, .NET Core and Xamarin/Mono.</span></span>

<span data-ttu-id="dc3d4-110">Je však dobré šance, že vaše knihovna nebude používat každý jeden balíček, které obsahuje.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-110">However, there's a good chance that your library won't use every single package it contains.</span></span>  <span data-ttu-id="dc3d4-111">Při vytváření knihovny a distribuci přes NuGet, je osvědčeným postupem "trim" závislostmi dolů jenom balíčky skutečně používáte.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-111">When authoring a library and distributing it over NuGet, it's a best practice to "trim" your dependencies down to only the packages you actually use.</span></span>  <span data-ttu-id="dc3d4-112">Výsledkem je menší celkové nároky na balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-112">This results in a smaller overall footprint for NuGet packages.</span></span>

## <a name="how-to-do-it"></a><span data-ttu-id="dc3d4-113">Jak to udělat</span><span class="sxs-lookup"><span data-stu-id="dc3d4-113">How to do it</span></span>

<span data-ttu-id="dc3d4-114">V současné době není žádná oficiální `dotnet` příkaz, který ořízne balíček odkazuje.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-114">Currently, there is no official `dotnet` command which trims package references.</span></span>  <span data-ttu-id="dc3d4-115">Místo toho budete muset provést ručně.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-115">Instead, you'll have to do it manually.</span></span>  <span data-ttu-id="dc3d4-116">Obecný postup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="dc3d4-116">The general process looks like the following:</span></span>

1. <span data-ttu-id="dc3d4-117">Referenční dokumentace `NETStandard.Library` verze `1.6.0` v `dependencies` část vaší `project.json`.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-117">Reference `NETStandard.Library` version `1.6.0` in a `dependencies` section of your `project.json`.</span></span>
2. <span data-ttu-id="dc3d4-118">Obnovení balíčků s `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-118">Restore packages with `dotnet restore` ([see note](#dotnet-restore-note)) from the command line.</span></span>
3. <span data-ttu-id="dc3d4-119">Zkontrolujte `project.lock.json` souboru a najděte `NETSTandard.Library` části.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-119">Inspect the `project.lock.json` file and find the `NETSTandard.Library` section.</span></span>  <span data-ttu-id="dc3d4-120">Je na začátku souboru.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-120">It's near the beginning of the file.</span></span>
4. <span data-ttu-id="dc3d4-121">Zkopírujte všechny balíčky uvedené v části `dependencies`.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-121">Copy all of the listed packages under `dependencies`.</span></span>
5. <span data-ttu-id="dc3d4-122">Odeberte `.NETStandard.Library` odkazovat a nahraďte ji metodou zkopírovaný balíčky.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-122">Remove the `.NETStandard.Library` reference and replace it with the copied packages.</span></span>
6. <span data-ttu-id="dc3d4-123">Odeberte odkazy na balíčky, které nepotřebujete.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-123">Remove references to packages you don't need.</span></span>


<span data-ttu-id="dc3d4-124">Můžete zjistit balíčky, které nepotřebujete pomocí jedné z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="dc3d4-124">You can find out which packages you don't need by one of the following ways:</span></span>

1. <span data-ttu-id="dc3d4-125">Zkušební verze a došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-125">Trial and error.</span></span>  <span data-ttu-id="dc3d4-126">To zahrnuje odstranění balíčku, obnovení, zobrazuje, pokud vaše knihovna stále zkompiluje a opakováním tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-126">This involves removing a package, restoring, seeing if your library still compiles, and repeating this process.</span></span>
2. <span data-ttu-id="dc3d4-127">Pomocí některého nástroje, jako třeba [ILSpy](http://ilspy.net) nebo [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) k zobrazení náhledu odkazy na zjistit, co váš kód ve skutečnosti používá.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-127">Using a tool such as [ILSpy](http://ilspy.net) or [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) to peek at references to see what your code is actually using.</span></span>  <span data-ttu-id="dc3d4-128">Potom můžete odebrat balíčky, které si odpovídají typy, které používáte.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-128">You can then remove packages which don't correspond to types you're using.</span></span>

## <a name="example"></a><span data-ttu-id="dc3d4-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="dc3d4-129">Example</span></span> 

<span data-ttu-id="dc3d4-130">Představte si, že jste napsali jste knihovnu, která poskytuje další funkce pro obecné typy kolekcí.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-130">Imagine that you wrote a library which provided additional functionality to generic collection types.</span></span>  <span data-ttu-id="dc3d4-131">Tuto knihovnu by bylo potřeba závisí na balíčky, jako `System.Collections`, ale vůbec záviset na balíčky, jako `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-131">Such a library would need to depend on packages such as `System.Collections`, but may not at all depend on packages such as `System.Net.Http`.</span></span>  <span data-ttu-id="dc3d4-132">Jako takový bylo by dobré oříznout závislosti balíčků dolů co tato knihovna je požadován, pouze!</span><span class="sxs-lookup"><span data-stu-id="dc3d4-132">As such, it would be good to trim package dependencies down to only what this library required!</span></span>

<span data-ttu-id="dc3d4-133">Abyste mohli trim této knihovny, spusťte s `project.json` souboru a přidejte odkaz na `NETStandard.Library` verze `1.6.0`.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-133">To trim this library, you start with the `project.json` file and add a reference to `NETStandard.Library` version `1.6.0`.</span></span>

```json
{
    "version":"1.0.0",
    "dependencies":{
        "NETStandard.Library":"1.6.0"
    },
    "frameworks": {
        "netstandard1.0": {}
     }
}
```

<span data-ttu-id="dc3d4-134">V dalším kroku obnovení balíčků s `dotnet restore` ([viz Poznámka](#dotnet-restore-note)), zkontrolujte `project.lock.json` souboru a najít všechny balíčky obnovit pro `NETSTandard.Library`.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-134">Next, you restore packages with `dotnet restore` ([see note](#dotnet-restore-note)), inspect the `project.lock.json` file, and find all the packages restored for `NETSTandard.Library`.</span></span>

<span data-ttu-id="dc3d4-135">Zde je v jaké v příslušné části `project.lock.json` soubor vypadá jako při cílení na `netstandard1.0`:</span><span class="sxs-lookup"><span data-stu-id="dc3d4-135">Here's what the relevant section in the `project.lock.json` file looks like when targeting `netstandard1.0`:</span></span>

```json
"NETStandard.Library/1.6.0":{
    "type": "package",
    "dependencies": {
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    }
}
```

<span data-ttu-id="dc3d4-136">Zkopírujte přes odkazy na balíček do `dependencies` části knihovně `project.json` souboru, nahraďte `NETStandard.Library` odkaz:</span><span class="sxs-lookup"><span data-stu-id="dc3d4-136">Next, copy over the package references into the `dependencies` section of the library's `project.json` file, replacing the `NETStandard.Library` reference:</span></span>

```json
{
    "version":"1.0.0",
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
    }
}
```

<span data-ttu-id="dc3d4-137">To je velmi velký balíčky, řadu které který určitě nejsou potřebné pro rozšíření typy kolekcí.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-137">That's quite a lot of packages, many of which which certainly aren't necessary for extending collection types.</span></span>  <span data-ttu-id="dc3d4-138">Můžete odebrat balíčky ručně nebo pomocí nástroje, jako například [ILSpy](http://ilspy.net) nebo [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) používá k identifikaci, který ve skutečnosti balíčků kódu.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-138">You can either remove packages manually or use a tool such as [ILSpy](http://ilspy.net) or [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) to identify which packages your code actually uses.</span></span>

<span data-ttu-id="dc3d4-139">Zde je, jak může vypadat oříznutý balíčku:</span><span class="sxs-lookup"><span data-stu-id="dc3d4-139">Here's what a trimmed package could look like:</span></span>

```json
{
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Linq": "4.1.0",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Runtime.Handles": "4.0.1",
        "System.Runtime.InteropServices": "4.1.0",
        "System.Runtime.InteropServices.RuntimeInformation": "4.0.0",
        "System.Threading.Tasks": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
     }
}
```

<span data-ttu-id="dc3d4-140">Teď má menší nároky než pokud měl závisí na `NETStandard.Library` metapackage.</span><span class="sxs-lookup"><span data-stu-id="dc3d4-140">Now, it has a smaller footprint than if it had depended on the `NETStandard.Library` metapackage.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]