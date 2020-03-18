---
title: Snížení závislostí balíčků pomocí souboru project.json
description: Při vytváření knihoven založených na souboru project.json snižte závislosti na balíčcích.
author: cartermp
ms.date: 06/20/2016
ms.openlocfilehash: 48ba3ef578388fd98fe7cb830df313512d359483
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75740824"
---
# <a name="reducing-package-dependencies-with-projectjson"></a><span data-ttu-id="8ecab-103">Snížení závislostí balíčků pomocí souboru project.json</span><span class="sxs-lookup"><span data-stu-id="8ecab-103">Reducing Package Dependencies with project.json</span></span>

<span data-ttu-id="8ecab-104">Tento článek popisuje, co potřebujete vědět o snížení závislostí balíčků při `project.json` vytváření knihoven.</span><span class="sxs-lookup"><span data-stu-id="8ecab-104">This article covers what you need to know about reducing your package dependencies when authoring `project.json` libraries.</span></span> <span data-ttu-id="8ecab-105">Na konci tohoto článku se dozvíte, jak vytvořit knihovnu tak, aby používá pouze závislosti, které potřebuje.</span><span class="sxs-lookup"><span data-stu-id="8ecab-105">By the end of this article, you will learn how to compose your library such that it only uses the dependencies it needs.</span></span>

## <a name="why-its-important"></a><span data-ttu-id="8ecab-106">Proč je to důležité</span><span class="sxs-lookup"><span data-stu-id="8ecab-106">Why it's Important</span></span>

<span data-ttu-id="8ecab-107">.NET Core je produkt tvořený balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="8ecab-107">.NET Core is a product made up of NuGet packages.</span></span>  <span data-ttu-id="8ecab-108">Základním balíčkem je [. METAbalíček NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library), což je balíček NuGet složený z jiných balíčků.</span><span class="sxs-lookup"><span data-stu-id="8ecab-108">An essential package is the [.NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), which is a NuGet package composed of other packages.</span></span> <span data-ttu-id="8ecab-109">Poskytuje sadu balíčků, které mají zaručeně pracovat na více implementacích rozhraní .NET, jako je například rozhraní .NET Framework, .NET Core a Xamarin/Mono.</span><span class="sxs-lookup"><span data-stu-id="8ecab-109">It provides you with the set of packages that are guaranteed to work on multiple .NET implementations, such as .NET Framework, .NET Core, and Xamarin/Mono.</span></span>

<span data-ttu-id="8ecab-110">Existuje však velká šance, že vaše knihovna nebude používat každý balíček, který obsahuje.</span><span class="sxs-lookup"><span data-stu-id="8ecab-110">However, there's a good chance that your library won't use every single package it contains.</span></span>  <span data-ttu-id="8ecab-111">Při vytváření knihovny a distribuci přes NuGet, je osvědčeným postupem "trim" vaše závislosti až na pouze balíčky, které skutečně používáte.</span><span class="sxs-lookup"><span data-stu-id="8ecab-111">When authoring a library and distributing it over NuGet, it's a best practice to "trim" your dependencies down to only the packages you actually use.</span></span>  <span data-ttu-id="8ecab-112">To má za následek menší celkové nároky na půdu pro balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="8ecab-112">This results in a smaller overall footprint for NuGet packages.</span></span>

## <a name="how-to-do-it"></a><span data-ttu-id="8ecab-113">Jak na to</span><span class="sxs-lookup"><span data-stu-id="8ecab-113">How to do it</span></span>

<span data-ttu-id="8ecab-114">V současné době neexistuje `dotnet` žádný oficiální příkaz, který ořízne odkazy na balíček.</span><span class="sxs-lookup"><span data-stu-id="8ecab-114">Currently, there is no official `dotnet` command that trims package references.</span></span>  <span data-ttu-id="8ecab-115">Místo toho to budete muset udělat ručně.</span><span class="sxs-lookup"><span data-stu-id="8ecab-115">Instead, you'll have to do it manually.</span></span>  <span data-ttu-id="8ecab-116">Obecný proces vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="8ecab-116">The general process looks like the following:</span></span>

1. <span data-ttu-id="8ecab-117">Referenční `NETStandard.Library` `1.6.0` verze `dependencies` v části `project.json`vašeho .</span><span class="sxs-lookup"><span data-stu-id="8ecab-117">Reference `NETStandard.Library` version `1.6.0` in a `dependencies` section of your `project.json`.</span></span>
2. <span data-ttu-id="8ecab-118">Obnovte `dotnet restore` balíčky pomocí příkazového řádku ([viz poznámka).](#dotnet-restore-note)</span><span class="sxs-lookup"><span data-stu-id="8ecab-118">Restore packages with `dotnet restore` ([see note](#dotnet-restore-note)) from the command line.</span></span>
3. <span data-ttu-id="8ecab-119">Zkontrolujte `project.lock.json` soubor a `NETStandard.Library` vyhledejte oddíl.</span><span class="sxs-lookup"><span data-stu-id="8ecab-119">Inspect the `project.lock.json` file and find the `NETStandard.Library` section.</span></span>  <span data-ttu-id="8ecab-120">Je to blízko začátku složky.</span><span class="sxs-lookup"><span data-stu-id="8ecab-120">It's near the beginning of the file.</span></span>
4. <span data-ttu-id="8ecab-121">Zkopírujte všechny uvedené `dependencies`balíčky v části .</span><span class="sxs-lookup"><span data-stu-id="8ecab-121">Copy all of the listed packages under `dependencies`.</span></span>
5. <span data-ttu-id="8ecab-122">Odeberte `.NETStandard.Library` odkaz a nahraďte jej zkopírovanými balíčky.</span><span class="sxs-lookup"><span data-stu-id="8ecab-122">Remove the `.NETStandard.Library` reference and replace it with the copied packages.</span></span>
6. <span data-ttu-id="8ecab-123">Odeberte odkazy na balíčky, které nepotřebujete.</span><span class="sxs-lookup"><span data-stu-id="8ecab-123">Remove references to packages you don't need.</span></span>

<span data-ttu-id="8ecab-124">Které balíčky nepotřebujete, můžete zjistit jedním z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="8ecab-124">You can find out which packages you don't need by one of the following ways:</span></span>

1. <span data-ttu-id="8ecab-125">Pokus a omyl.</span><span class="sxs-lookup"><span data-stu-id="8ecab-125">Trial and error.</span></span> <span data-ttu-id="8ecab-126">To zahrnuje odebrání balíčku, obnovení, zjištění, zda vaše knihovna stále kompiluje, a opakování tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="8ecab-126">This involves removing a package, restoring, seeing if your library still compiles, and repeating this process.</span></span>
2. <span data-ttu-id="8ecab-127">Pomocí nástroje, jako je [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) nebo [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector) nahlédnout na odkazy vidět, co váš kód je skutečně používá.</span><span class="sxs-lookup"><span data-stu-id="8ecab-127">Using a tool such as [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) or [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector) to peek at references to see what your code is actually using.</span></span> <span data-ttu-id="8ecab-128">Potom můžete odebrat balíčky, které neodpovídají typům, které používáte.</span><span class="sxs-lookup"><span data-stu-id="8ecab-128">You can then remove packages that don't correspond to types you're using.</span></span>

## <a name="example"></a><span data-ttu-id="8ecab-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="8ecab-129">Example</span></span>

<span data-ttu-id="8ecab-130">Představte si, že jste napsali knihovnu, která poskytuje další funkce pro obecné typy kolekcí.</span><span class="sxs-lookup"><span data-stu-id="8ecab-130">Imagine that you wrote a library that provided additional functionality to generic collection types.</span></span> <span data-ttu-id="8ecab-131">Taková knihovna by musela záviset `System.Collections`na balíčcích, jako je `System.Net.Http`například , ale nemusí záviset na balíčcích, jako je .</span><span class="sxs-lookup"><span data-stu-id="8ecab-131">Such a library would need to depend on packages such as `System.Collections`, but may not at all depend on packages such as `System.Net.Http`.</span></span> <span data-ttu-id="8ecab-132">Jako takový, bylo by dobré zkrátit balíček závislosti pouze na to, co tato knihovna vyžaduje!</span><span class="sxs-lookup"><span data-stu-id="8ecab-132">As such, it would be good to trim package dependencies down to only what this library required!</span></span>

<span data-ttu-id="8ecab-133">Chcete-li tuto knihovnu `project.json` oříznout, začněte `NETStandard.Library` `1.6.0`se souborem a přidejte odkaz na verzi .</span><span class="sxs-lookup"><span data-stu-id="8ecab-133">To trim this library, you start with the `project.json` file and add a reference to `NETStandard.Library` version `1.6.0`.</span></span>

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

<span data-ttu-id="8ecab-134">Dále `dotnet restore` obnovíte balíčky s ( viz[poznámka](#dotnet-restore-note)), zkontrolujte `project.lock.json` soubor `NETStandard.Library`a vyhledejte všechny balíčky obnovené pro .</span><span class="sxs-lookup"><span data-stu-id="8ecab-134">Next, you restore packages with `dotnet restore` ([see note](#dotnet-restore-note)), inspect the `project.lock.json` file, and find all the packages restored for `NETStandard.Library`.</span></span>

<span data-ttu-id="8ecab-135">Tady je, jak vypadá `project.lock.json` příslušná část `netstandard1.0`v souboru při cílení :</span><span class="sxs-lookup"><span data-stu-id="8ecab-135">Here's what the relevant section in the `project.lock.json` file looks like when targeting `netstandard1.0`:</span></span>

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

<span data-ttu-id="8ecab-136">Dále zkopírujte odkazy na balíček do `dependencies` části `project.json` souboru knihovny `NETStandard.Library` a nahrazte odkaz:</span><span class="sxs-lookup"><span data-stu-id="8ecab-136">Next, copy over the package references into the `dependencies` section of the library's `project.json` file, replacing the `NETStandard.Library` reference:</span></span>

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

<span data-ttu-id="8ecab-137">To je docela dost balíčků, z nichž mnohé rozhodně nejsou nezbytné pro rozšíření typů sběru.</span><span class="sxs-lookup"><span data-stu-id="8ecab-137">That's quite a lot of packages, many of which certainly aren't necessary for extending collection types.</span></span>  <span data-ttu-id="8ecab-138">Můžete buď odebrat balíčky ručně, nebo použít nástroj, jako je [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) nebo [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector/) k identifikaci, které balíčky váš kód skutečně používá.</span><span class="sxs-lookup"><span data-stu-id="8ecab-138">You can either remove packages manually or use a tool such as [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) or [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector/) to identify which packages your code actually uses.</span></span>

<span data-ttu-id="8ecab-139">Zde je to, co zdobené balíček by mohl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="8ecab-139">Here's what a trimmed package could look like:</span></span>

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

<span data-ttu-id="8ecab-140">Nyní má menší půdorys, než kdyby `NETStandard.Library` závisel na metabalíčku.</span><span class="sxs-lookup"><span data-stu-id="8ecab-140">Now, it has a smaller footprint than if it had depended on the `NETStandard.Library` metapackage.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
