---
title: Omezení závislosti balíčku s project.json
description: Omezte závislosti balíčků, při vytváření knihovny project.json založené.
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.openlocfilehash: ae314800f789cee363728def8347b5e6990acb0b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44193605"
---
# <a name="reducing-package-dependencies-with-projectjson"></a><span data-ttu-id="65451-103">Omezení závislosti balíčku s project.json</span><span class="sxs-lookup"><span data-stu-id="65451-103">Reducing Package Dependencies with project.json</span></span>

<span data-ttu-id="65451-104">Tento článek popisuje, co potřebujete vědět o snižování závislosti balíčků při vytváření `project.json` knihovny.</span><span class="sxs-lookup"><span data-stu-id="65451-104">This article covers what you need to know about reducing your package dependencies when authoring `project.json` libraries.</span></span> <span data-ttu-id="65451-105">Na konci tohoto článku se dozvíte, jak sestavit knihovnu tak, aby používal jenom závislosti, které potřebuje.</span><span class="sxs-lookup"><span data-stu-id="65451-105">By the end of this article, you will learn how to compose your library such that it only uses the dependencies it needs.</span></span> 

## <a name="why-its-important"></a><span data-ttu-id="65451-106">Proč je důležité</span><span class="sxs-lookup"><span data-stu-id="65451-106">Why it's Important</span></span>

<span data-ttu-id="65451-107">.NET core je produkt tvořené balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="65451-107">.NET Core is a product made up of NuGet packages.</span></span>  <span data-ttu-id="65451-108">Základní balíček je [. NETStandard.Library Microsoft.aspnetcore.all](https://www.nuget.org/packages/NETStandard.Library), který se balíček NuGet skládá z dalších balíčků.</span><span class="sxs-lookup"><span data-stu-id="65451-108">An essential package is the [.NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), which is a NuGet package composed of other packages.</span></span>  <span data-ttu-id="65451-109">To vám poskytuje sadu balíčků, které jsou zaručeny pracovat na více implementací rozhraní .NET, jako je například rozhraní .NET Framework, .NET Core a Xamarin/Mono.</span><span class="sxs-lookup"><span data-stu-id="65451-109">It provides you with the set of packages that are guaranteed to work on multiple .NET implementations, such as .NET Framework, .NET Core and Xamarin/Mono.</span></span>

<span data-ttu-id="65451-110">Je však vhodné šance, že vaše knihovna nebudeme používat každý jeden balíček, který obsahuje.</span><span class="sxs-lookup"><span data-stu-id="65451-110">However, there's a good chance that your library won't use every single package it contains.</span></span>  <span data-ttu-id="65451-111">Při vytváření knihovny a jejich distribuci přes NuGet, je osvědčeným postupem "trim" závislostí dolů pouze balíčky skutečně využíváte.</span><span class="sxs-lookup"><span data-stu-id="65451-111">When authoring a library and distributing it over NuGet, it's a best practice to "trim" your dependencies down to only the packages you actually use.</span></span>  <span data-ttu-id="65451-112">Výsledkem je menší celkové nároky na místo pro balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="65451-112">This results in a smaller overall footprint for NuGet packages.</span></span>

## <a name="how-to-do-it"></a><span data-ttu-id="65451-113">Jak na to</span><span class="sxs-lookup"><span data-stu-id="65451-113">How to do it</span></span>

<span data-ttu-id="65451-114">V současné době neexistuje žádné oficiální `dotnet` příkazu, který ořízne odkazy na balíček.</span><span class="sxs-lookup"><span data-stu-id="65451-114">Currently, there is no official `dotnet` command which trims package references.</span></span>  <span data-ttu-id="65451-115">Místo toho budete muset provést ručně.</span><span class="sxs-lookup"><span data-stu-id="65451-115">Instead, you'll have to do it manually.</span></span>  <span data-ttu-id="65451-116">Obecný postup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="65451-116">The general process looks like the following:</span></span>

1. <span data-ttu-id="65451-117">Referenční dokumentace `NETStandard.Library` verze `1.6.0` v `dependencies` část vaší `project.json`.</span><span class="sxs-lookup"><span data-stu-id="65451-117">Reference `NETStandard.Library` version `1.6.0` in a `dependencies` section of your `project.json`.</span></span>
2. <span data-ttu-id="65451-118">Obnovení balíčků s `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="65451-118">Restore packages with `dotnet restore` ([see note](#dotnet-restore-note)) from the command line.</span></span>
3. <span data-ttu-id="65451-119">Zkontrolujte `project.lock.json` souborů a vyhledejte `NETSTandard.Library` oddílu.</span><span class="sxs-lookup"><span data-stu-id="65451-119">Inspect the `project.lock.json` file and find the `NETSTandard.Library` section.</span></span>  <span data-ttu-id="65451-120">Je na začátku souboru.</span><span class="sxs-lookup"><span data-stu-id="65451-120">It's near the beginning of the file.</span></span>
4. <span data-ttu-id="65451-121">Zkopírujte všechny balíčky uvedené v části `dependencies`.</span><span class="sxs-lookup"><span data-stu-id="65451-121">Copy all of the listed packages under `dependencies`.</span></span>
5. <span data-ttu-id="65451-122">Odeberte `.NETStandard.Library` odkazovat a nahraďte ji metodou zkopírovaný balíčky.</span><span class="sxs-lookup"><span data-stu-id="65451-122">Remove the `.NETStandard.Library` reference and replace it with the copied packages.</span></span>
6. <span data-ttu-id="65451-123">Odeberte odkazy na balíčky, které nepotřebujete.</span><span class="sxs-lookup"><span data-stu-id="65451-123">Remove references to packages you don't need.</span></span>


<span data-ttu-id="65451-124">Můžete zjistit, které balíčky, není nutné pomocí jedné z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="65451-124">You can find out which packages you don't need by one of the following ways:</span></span>

1. <span data-ttu-id="65451-125">Došlo k chybě a zkušební verze.</span><span class="sxs-lookup"><span data-stu-id="65451-125">Trial and error.</span></span>  <span data-ttu-id="65451-126">To zahrnuje odebrání balíčku, obnovení, zobrazuje, pokud se stále zkompiluje knihovnu a opakováním tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="65451-126">This involves removing a package, restoring, seeing if your library still compiles, and repeating this process.</span></span>
2. <span data-ttu-id="65451-127">Pomocí nástroje, jako například [ILSpy](http://ilspy.net) nebo [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) a prohlédněte si odkazy, které chcete zjistit, co váš kód skutečně.</span><span class="sxs-lookup"><span data-stu-id="65451-127">Using a tool such as [ILSpy](http://ilspy.net) or [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) to peek at references to see what your code is actually using.</span></span>  <span data-ttu-id="65451-128">Následně můžete odebrat balíčky, které neodpovídají na typy, které používáte.</span><span class="sxs-lookup"><span data-stu-id="65451-128">You can then remove packages which don't correspond to types you're using.</span></span>

## <a name="example"></a><span data-ttu-id="65451-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="65451-129">Example</span></span> 

<span data-ttu-id="65451-130">Představte si, že jste napsali knihovnu, která poskytuje další funkce do obecných typů kolekce.</span><span class="sxs-lookup"><span data-stu-id="65451-130">Imagine that you wrote a library which provided additional functionality to generic collection types.</span></span>  <span data-ttu-id="65451-131">Tyto knihovny by bylo potřeba závisí na balíčky, jako `System.Collections`, ale vůbec záviset na balíčky, jako `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="65451-131">Such a library would need to depend on packages such as `System.Collections`, but may not at all depend on packages such as `System.Net.Http`.</span></span>  <span data-ttu-id="65451-132">V důsledku toho by bylo dobré mají být odebrány závislosti balíčků dolů pouze co tuto knihovnu požadovanou!</span><span class="sxs-lookup"><span data-stu-id="65451-132">As such, it would be good to trim package dependencies down to only what this library required!</span></span>

<span data-ttu-id="65451-133">Oříznout této knihovny, začínat `project.json` a přidejte odkaz na `NETStandard.Library` verze `1.6.0`.</span><span class="sxs-lookup"><span data-stu-id="65451-133">To trim this library, you start with the `project.json` file and add a reference to `NETStandard.Library` version `1.6.0`.</span></span>

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

<span data-ttu-id="65451-134">V dalším kroku obnovit balíčky s `dotnet restore` ([viz Poznámka](#dotnet-restore-note)), zkontrolujte `project.lock.json` souboru a vyhledání všech balíčků byl obnoven pro `NETSTandard.Library`.</span><span class="sxs-lookup"><span data-stu-id="65451-134">Next, you restore packages with `dotnet restore` ([see note](#dotnet-restore-note)), inspect the `project.lock.json` file, and find all the packages restored for `NETSTandard.Library`.</span></span>

<span data-ttu-id="65451-135">Zde je co příslušné části v `project.lock.json` souboru vypadá podobně jako při cílení na `netstandard1.0`:</span><span class="sxs-lookup"><span data-stu-id="65451-135">Here's what the relevant section in the `project.lock.json` file looks like when targeting `netstandard1.0`:</span></span>

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

<span data-ttu-id="65451-136">V dalším kroku zkopírujte odkazy na balíčky do `dependencies` části knihovny `project.json` souboru, nahradí `NETStandard.Library` odkaz:</span><span class="sxs-lookup"><span data-stu-id="65451-136">Next, copy over the package references into the `dependencies` section of the library's `project.json` file, replacing the `NETStandard.Library` reference:</span></span>

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

<span data-ttu-id="65451-137">To je poměrně velké balíčky, mnoho kterému jistě nejsou potřebné pro rozšíření typy kolekcí.</span><span class="sxs-lookup"><span data-stu-id="65451-137">That's quite a lot of packages, many of which which certainly aren't necessary for extending collection types.</span></span>  <span data-ttu-id="65451-138">Můžete odebrat balíčky, které ručně nebo pomocí nástroje, jako [ILSpy](http://ilspy.net) nebo [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) používá k identifikaci, který ve skutečnosti balíčky kódu.</span><span class="sxs-lookup"><span data-stu-id="65451-138">You can either remove packages manually or use a tool such as [ILSpy](http://ilspy.net) or [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) to identify which packages your code actually uses.</span></span>

<span data-ttu-id="65451-139">Tady je oříznutý balíčku by mohla vypadat:</span><span class="sxs-lookup"><span data-stu-id="65451-139">Here's what a trimmed package could look like:</span></span>

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

<span data-ttu-id="65451-140">Teď má menší nároky na místo než pokud měl závisí na `NETStandard.Library` Microsoft.aspnetcore.all.</span><span class="sxs-lookup"><span data-stu-id="65451-140">Now, it has a smaller footprint than if it had depended on the `NETStandard.Library` metapackage.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]