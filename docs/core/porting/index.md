---
title: Portování do .NET Core z rozhraní .NET Framework
description: Princip přenosem a zjistit nástroje, které vás může být užitečná při portování rozhraní .NET Framework projektu na .NET Core.
keywords: Rozhraní .NET, .NET core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 00d00d38-99af-44f4-a75f-defcd9729dc5
ms.workload:
- dotnetcore
ms.openlocfilehash: 3413b73c2a0a3c3ebf49b0b3ec81d00c6558d9a8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="porting-to-net-core-from-net-framework"></a><span data-ttu-id="02171-104">Portování do .NET Core z rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="02171-104">Porting to .NET Core from .NET Framework</span></span>

<span data-ttu-id="02171-105">Pokud máte k dispozici kód spuštěný na rozhraní .NET Framework, může zajímat spuštěním kódu v .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="02171-105">If you've got code running on the .NET Framework, you may be interested in running your code on .NET Core 1.0.</span></span>  <span data-ttu-id="02171-106">Tento článek obsahuje přehled procesu přenosem a seznam nástroje, které vás může být užitečná při portování do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="02171-106">This article covers an overview of the porting process and a list of the tools you may find helpful when porting to .NET Core.</span></span>

## <a name="overview-of-the-porting-process"></a><span data-ttu-id="02171-107">Přehled procesu přenosem</span><span class="sxs-lookup"><span data-stu-id="02171-107">Overview of the Porting Process</span></span>

<span data-ttu-id="02171-108">Doporučený postup pro přenos zahrnuje následující sérii kroků.</span><span class="sxs-lookup"><span data-stu-id="02171-108">The recommended process for porting follows the following series of steps.</span></span>  <span data-ttu-id="02171-109">Každou z těchto součástí procesu jsou popsané v podrobněji další články.</span><span class="sxs-lookup"><span data-stu-id="02171-109">Each of these parts of the process are covered in more detail in further articles.</span></span>

1. <span data-ttu-id="02171-110">Identifikovat a účet pro svoje závislosti třetích stran.</span><span class="sxs-lookup"><span data-stu-id="02171-110">Identify and account for your third-party dependencies.</span></span>

   <span data-ttu-id="02171-111">To bude zahrnovat vysvětlení, co vaše třetích stran závislosti jsou, jak jsou závislé na je, jak a zjistěte, zda také běží na .NET Core a postup můžete provést v případě ne.</span><span class="sxs-lookup"><span data-stu-id="02171-111">This will involve understanding what your third-party dependencies are, how you depend on them, how to see if they also run on .NET Core, and steps you can take if they don't.</span></span>
   
2. <span data-ttu-id="02171-112">Změňte cíl všechny projekty, které chcete port na cílové rozhraní .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="02171-112">Retarget all projects you wish to port to target .NET Framework 4.6.2.</span></span>

   <span data-ttu-id="02171-113">Zajistíte, že můžete použít rozhraní API alternativy pro specifické pro rozhraní .NET Framework cíle v případech, kde .NET Core nepodporuje dané rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="02171-113">This ensures that you can use API alternatives for .NET Framework-specific targets in the cases where .NET Core can't support a particular API.</span></span>
   
3. <span data-ttu-id="02171-114">Použití [nástroj Analyzátor přenositelnost rozhraní API](https://github.com/Microsoft/dotnet-apiport/) analyzovat vaše sestavení a vytvořte plán na port, na základě jeho výsledků.</span><span class="sxs-lookup"><span data-stu-id="02171-114">Use the [API Portability Analyzer tool](https://github.com/Microsoft/dotnet-apiport/) to analyze your assemblies and develop a plan to port based on its results.</span></span>

   <span data-ttu-id="02171-115">Nástroj Analyzátor přenositelnost API analyzovat zkompilovaná sestavení a generovat sestavy, která se zobrazují souhrnné informace vysoké úrovně přenositelnost a rozpis každé rozhraní API používáte, není k dispozici na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="02171-115">The API Portability Analyzer tool will analyze your compiled assemblies and generate a report which shows a high-level portability summary and a breakdown of each API you're using that isn't available on .NET Core.</span></span>  <span data-ttu-id="02171-116">Můžete použít tuto sestavu spolu s analýzu vašeho základu kódu při vytváření plánu o tom, jak budete prostřednictvím portu vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="02171-116">You can use this report alongside an analysis of your codebase to develop a plan for how you'll port your code over.</span></span>
   
4. <span data-ttu-id="02171-117">Port testy kódu.</span><span class="sxs-lookup"><span data-stu-id="02171-117">Port your tests code.</span></span>

   <span data-ttu-id="02171-118">Portování do .NET Core je velkou změnu do vaší codebase, a proto se důrazně doporučujeme získat testy přesně tak, aby testy můžete spustit jako portu kód přes.</span><span class="sxs-lookup"><span data-stu-id="02171-118">Because porting to .NET Core is such a big change to your codebase, it's highly recommended to get your tests ported so that you can run tests as you port code over.</span></span>  <span data-ttu-id="02171-119">Mstestu, xUnit a NUnit podporovat dnes .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="02171-119">MSTest, xUnit, and NUnit all support .NET Core 1.0 today.</span></span>
   
6. <span data-ttu-id="02171-120">Spuštění plánu pro přenos!</span><span class="sxs-lookup"><span data-stu-id="02171-120">Execute your plan for porting!</span></span>

## <a name="tools-to-help"></a><span data-ttu-id="02171-121">Nástrojů, které pomůžou</span><span class="sxs-lookup"><span data-stu-id="02171-121">Tools to help</span></span>

<span data-ttu-id="02171-122">Tady je seznam krátké nástroje, které najdete užitečné:</span><span class="sxs-lookup"><span data-stu-id="02171-122">Here's a short list of the tools you'll find helpful:</span></span>

* <span data-ttu-id="02171-123">NuGet - [klienta Nuget](https://dist.nuget.org/index.html) nebo [Explorer balíček NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer), Správce balíčků společnosti Microsoft pro implementace rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="02171-123">NuGet - [Nuget Client](https://dist.nuget.org/index.html) or [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer), Microsoft's package manager for .NET implementations.</span></span>
* <span data-ttu-id="02171-124">Přenositelnost Analyzer API - [nástroj pro příkazový řádek](https://github.com/Microsoft/dotnet-apiport/releases) nebo [rozšíření sady Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b), nástrojů, který můžete vygenerovat sestavu, jak přenosné kódu je mezi rozhraní .NET Framework a .NET Core pomocí sestavení podle rozpis těchto problémů.</span><span class="sxs-lookup"><span data-stu-id="02171-124">Api Portability Analyzer - [command line tool](https://github.com/Microsoft/dotnet-apiport/releases) or [Visual Studio Extension](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b), a toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core, with an assembly-by-assembly breakdown of issues.</span></span>  <span data-ttu-id="02171-125">V tématu [nástrojů můžete v procesu](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/) Další informace.</span><span class="sxs-lookup"><span data-stu-id="02171-125">See [Tooling to help you on the process](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/) for more information.</span></span>
* <span data-ttu-id="02171-126">Reverse balíček vyhledávání - A [užitečné webové služby](https://packagesearch.azurewebsites.net) , které umožňuje hledat typ a vyhledejte balíčky, které obsahují typu.</span><span class="sxs-lookup"><span data-stu-id="02171-126">Reverse Package Search - A [useful web service](https://packagesearch.azurewebsites.net) that allows you to search for a type and find packages containing that type.</span></span>

## <a name="next-steps"></a><span data-ttu-id="02171-127">Další kroky</span><span class="sxs-lookup"><span data-stu-id="02171-127">Next steps</span></span>

[<span data-ttu-id="02171-128">Analýza závislostmi třetích stran.</span><span class="sxs-lookup"><span data-stu-id="02171-128">Analyzing your third-party dependencies.</span></span>](third-party-deps.md)
   
