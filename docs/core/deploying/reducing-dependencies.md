---
title: Zmenšení závislostí balíčku pomocí Project. JSON
description: Zmenšení závislostí balíčku při vytváření knihoven založených na Project. JSON.
author: cartermp
ms.date: 06/20/2016
ms.openlocfilehash: 48ba3ef578388fd98fe7cb830df313512d359483
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740824"
---
# <a name="reducing-package-dependencies-with-projectjson"></a><span data-ttu-id="07157-103">Zmenšení závislostí balíčku pomocí Project. JSON</span><span class="sxs-lookup"><span data-stu-id="07157-103">Reducing Package Dependencies with project.json</span></span>

<span data-ttu-id="07157-104">Tento článek popisuje, co potřebujete znát o omezení závislostí balíčku při vytváření `project.json`ch knihoven.</span><span class="sxs-lookup"><span data-stu-id="07157-104">This article covers what you need to know about reducing your package dependencies when authoring `project.json` libraries.</span></span> <span data-ttu-id="07157-105">Na konci tohoto článku se naučíte, jak vytvořit knihovnu tak, aby používala pouze závislosti, které potřebuje.</span><span class="sxs-lookup"><span data-stu-id="07157-105">By the end of this article, you will learn how to compose your library such that it only uses the dependencies it needs.</span></span>

## <a name="why-its-important"></a><span data-ttu-id="07157-106">Proč je důležité</span><span class="sxs-lookup"><span data-stu-id="07157-106">Why it's Important</span></span>

<span data-ttu-id="07157-107">.NET Core je produkt vytvořený z balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="07157-107">.NET Core is a product made up of NuGet packages.</span></span>  <span data-ttu-id="07157-108">Základní balíček je [. NETStandard. Library Metapackage](https://www.nuget.org/packages/NETStandard.Library), což je balíček NuGet tvořený jinými balíčky.</span><span class="sxs-lookup"><span data-stu-id="07157-108">An essential package is the [.NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), which is a NuGet package composed of other packages.</span></span> <span data-ttu-id="07157-109">Poskytuje sadu balíčků, u kterých je zaručena práce s více implementacemi .NET, například .NET Framework, .NET Core a Xamarin/mono.</span><span class="sxs-lookup"><span data-stu-id="07157-109">It provides you with the set of packages that are guaranteed to work on multiple .NET implementations, such as .NET Framework, .NET Core, and Xamarin/Mono.</span></span>

<span data-ttu-id="07157-110">Existuje však velmi pravděpodobné, že vaše knihovna nebude používat každý balíček, který obsahuje.</span><span class="sxs-lookup"><span data-stu-id="07157-110">However, there's a good chance that your library won't use every single package it contains.</span></span>  <span data-ttu-id="07157-111">Když vytváříte knihovnu a distribuujete ji přes NuGet, je osvědčeným postupem, jak vyčistit závislosti až na balíčky, které skutečně používáte.</span><span class="sxs-lookup"><span data-stu-id="07157-111">When authoring a library and distributing it over NuGet, it's a best practice to "trim" your dependencies down to only the packages you actually use.</span></span>  <span data-ttu-id="07157-112">Výsledkem je menší celkové nároky na balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="07157-112">This results in a smaller overall footprint for NuGet packages.</span></span>

## <a name="how-to-do-it"></a><span data-ttu-id="07157-113">Jak na to</span><span class="sxs-lookup"><span data-stu-id="07157-113">How to do it</span></span>

<span data-ttu-id="07157-114">V současné době není k dispozici žádný oficiální `dotnet` příkaz, který ořízne odkazy na balíčky.</span><span class="sxs-lookup"><span data-stu-id="07157-114">Currently, there is no official `dotnet` command that trims package references.</span></span>  <span data-ttu-id="07157-115">Místo toho ho budete muset provést ručně.</span><span class="sxs-lookup"><span data-stu-id="07157-115">Instead, you'll have to do it manually.</span></span>  <span data-ttu-id="07157-116">Obecný proces vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="07157-116">The general process looks like the following:</span></span>

1. <span data-ttu-id="07157-117">Referenční `NETStandard.Library` verze `1.6.0` v části `dependencies` `project.json`.</span><span class="sxs-lookup"><span data-stu-id="07157-117">Reference `NETStandard.Library` version `1.6.0` in a `dependencies` section of your `project.json`.</span></span>
2. <span data-ttu-id="07157-118">Obnovte balíčky pomocí `dotnet restore` ([Viz poznámku](#dotnet-restore-note)) z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="07157-118">Restore packages with `dotnet restore` ([see note](#dotnet-restore-note)) from the command line.</span></span>
3. <span data-ttu-id="07157-119">Zkontrolujte soubor `project.lock.json` a najděte oddíl `NETStandard.Library`.</span><span class="sxs-lookup"><span data-stu-id="07157-119">Inspect the `project.lock.json` file and find the `NETStandard.Library` section.</span></span>  <span data-ttu-id="07157-120">Je poblíž začátku souboru.</span><span class="sxs-lookup"><span data-stu-id="07157-120">It's near the beginning of the file.</span></span>
4. <span data-ttu-id="07157-121">Zkopírujte všechny uvedené balíčky pod `dependencies`.</span><span class="sxs-lookup"><span data-stu-id="07157-121">Copy all of the listed packages under `dependencies`.</span></span>
5. <span data-ttu-id="07157-122">Odeberte odkaz na `.NETStandard.Library` a nahraďte ho zkopírovanými balíčky.</span><span class="sxs-lookup"><span data-stu-id="07157-122">Remove the `.NETStandard.Library` reference and replace it with the copied packages.</span></span>
6. <span data-ttu-id="07157-123">Odeberte odkazy na balíčky, které nepotřebujete.</span><span class="sxs-lookup"><span data-stu-id="07157-123">Remove references to packages you don't need.</span></span>

<span data-ttu-id="07157-124">Balíčky, které nepotřebujete, můžete zjistit jedním z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="07157-124">You can find out which packages you don't need by one of the following ways:</span></span>

1. <span data-ttu-id="07157-125">Zkušební verze a chyba.</span><span class="sxs-lookup"><span data-stu-id="07157-125">Trial and error.</span></span> <span data-ttu-id="07157-126">To zahrnuje odebrání balíčku, obnovení a zjištění, zda je vaše knihovna stále zkompilována, a zopakování tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="07157-126">This involves removing a package, restoring, seeing if your library still compiles, and repeating this process.</span></span>
2. <span data-ttu-id="07157-127">Použití nástroje, jako je [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) nebo [reflektor .NET](https://www.red-gate.com/products/dotnet-development/reflector) , k prohlížení odkazů k zobrazení, co váš kód skutečně používá.</span><span class="sxs-lookup"><span data-stu-id="07157-127">Using a tool such as [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) or [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector) to peek at references to see what your code is actually using.</span></span> <span data-ttu-id="07157-128">Pak můžete odebrat balíčky, které neodpovídají typům, které používáte.</span><span class="sxs-lookup"><span data-stu-id="07157-128">You can then remove packages that don't correspond to types you're using.</span></span>

## <a name="example"></a><span data-ttu-id="07157-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="07157-129">Example</span></span>

<span data-ttu-id="07157-130">Představte si, že jste napsali knihovnu, která poskytuje další funkce pro obecné typy kolekcí.</span><span class="sxs-lookup"><span data-stu-id="07157-130">Imagine that you wrote a library that provided additional functionality to generic collection types.</span></span> <span data-ttu-id="07157-131">Taková knihovna by musela záviset na balíčcích, jako je `System.Collections`, ale nemusí být vůbec závislé na balíčcích, jako je `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="07157-131">Such a library would need to depend on packages such as `System.Collections`, but may not at all depend on packages such as `System.Net.Http`.</span></span> <span data-ttu-id="07157-132">V takovém případě by bylo vhodné oříznout závislosti balíčků a snížit tak pouze to, co tato knihovna vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="07157-132">As such, it would be good to trim package dependencies down to only what this library required!</span></span>

<span data-ttu-id="07157-133">Chcete-li tuto knihovnu oříznout, začněte se souborem `project.json` a přidejte odkaz na verzi `NETStandard.Library` `1.6.0`.</span><span class="sxs-lookup"><span data-stu-id="07157-133">To trim this library, you start with the `project.json` file and add a reference to `NETStandard.Library` version `1.6.0`.</span></span>

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

<span data-ttu-id="07157-134">V dalším kroku obnovíte balíčky pomocí `dotnet restore` ([Viz poznámku](#dotnet-restore-note)), zkontrolujete soubor `project.lock.json` a vyhledáte všechny balíčky obnovené pro `NETStandard.Library`.</span><span class="sxs-lookup"><span data-stu-id="07157-134">Next, you restore packages with `dotnet restore` ([see note](#dotnet-restore-note)), inspect the `project.lock.json` file, and find all the packages restored for `NETStandard.Library`.</span></span>

<span data-ttu-id="07157-135">V takovém případě se v souboru `project.lock.json` zdá, že při cílení `netstandard1.0`vypadá nějak takto:</span><span class="sxs-lookup"><span data-stu-id="07157-135">Here's what the relevant section in the `project.lock.json` file looks like when targeting `netstandard1.0`:</span></span>

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

<span data-ttu-id="07157-136">V dalším kroku zkopírujte odkazy na balíček do oddílu `dependencies` `project.json` souboru knihovny a nahraďte `NETStandard.Library` odkaz:</span><span class="sxs-lookup"><span data-stu-id="07157-136">Next, copy over the package references into the `dependencies` section of the library's `project.json` file, replacing the `NETStandard.Library` reference:</span></span>

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

<span data-ttu-id="07157-137">To je poměrně velké množství balíčků, z nichž mnoho není nezbytné pro rozšíření typů kolekcí.</span><span class="sxs-lookup"><span data-stu-id="07157-137">That's quite a lot of packages, many of which certainly aren't necessary for extending collection types.</span></span>  <span data-ttu-id="07157-138">Můžete buď odebrat balíčky ručně, nebo použít nástroj, jako je [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) nebo [reflektor .NET](https://www.red-gate.com/products/dotnet-development/reflector/) , k určení balíčků, které váš kód skutečně používá.</span><span class="sxs-lookup"><span data-stu-id="07157-138">You can either remove packages manually or use a tool such as [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) or [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector/) to identify which packages your code actually uses.</span></span>

<span data-ttu-id="07157-139">V tomto příkladu může být oříznutý balíček vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="07157-139">Here's what a trimmed package could look like:</span></span>

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

<span data-ttu-id="07157-140">Teď má menší nároky, než kdyby byla závislá na `NETStandard.Library` Metapackage.</span><span class="sxs-lookup"><span data-stu-id="07157-140">Now, it has a smaller footprint than if it had depended on the `NETStandard.Library` metapackage.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
