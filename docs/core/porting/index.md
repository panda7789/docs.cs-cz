---
title: Portování do .NET Core v rozhraní .NET Framework
description: Vysvětlení procesu přenosem a zjišťování nástroje, které vám můžou pomoct při přenášení do rozhraní .NET Framework projektu .NET Core.
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.openlocfilehash: d273b3abe46de59aa55b5b9a531d3c572a065124
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48835389"
---
# <a name="porting-to-net-core-from-net-framework"></a><span data-ttu-id="5641a-103">Portování do .NET Core v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5641a-103">Porting to .NET Core from .NET Framework</span></span>

<span data-ttu-id="5641a-104">Pokud máte kód spuštěný na rozhraní .NET Framework, může zajímat spouštění kódu v .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="5641a-104">If you've got code running on the .NET Framework, you may be interested in running your code on .NET Core 1.0.</span></span>  <span data-ttu-id="5641a-105">Tento článek obsahuje přehled procesu přenosem a seznam nástrojů, které vám můžou pomoct při přenášení do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5641a-105">This article covers an overview of the porting process and a list of the tools you may find helpful when porting to .NET Core.</span></span>

## <a name="overview-of-the-porting-process"></a><span data-ttu-id="5641a-106">Přehled procesu přenos</span><span class="sxs-lookup"><span data-stu-id="5641a-106">Overview of the Porting Process</span></span>

<span data-ttu-id="5641a-107">Doporučený postup pro přenesení následuje následující sérii kroků.</span><span class="sxs-lookup"><span data-stu-id="5641a-107">The recommended process for porting follows the following series of steps.</span></span>  <span data-ttu-id="5641a-108">Každá z těchto částí procesu se budeme věnovat jednotlivě podrobněji v dalších článcích.</span><span class="sxs-lookup"><span data-stu-id="5641a-108">Each of these parts of the process are covered in more detail in further articles.</span></span>

1. <span data-ttu-id="5641a-109">Identifikujte a účtu pro vašeho závislostí třetích stran.</span><span class="sxs-lookup"><span data-stu-id="5641a-109">Identify and account for your third-party dependencies.</span></span>

   <span data-ttu-id="5641a-110">To bude zahrnovat porozumění jaké závislostí třetích stran se, jak jsou závislé na nich, jak a zjistěte, jestli jsou také běží na .NET Core a kroky můžete provést v případě ne.</span><span class="sxs-lookup"><span data-stu-id="5641a-110">This will involve understanding what your third-party dependencies are, how you depend on them, how to see if they also run on .NET Core, and steps you can take if they don't.</span></span>
   
2. <span data-ttu-id="5641a-111">Přesměrovat všechny projekty, které chcete port pro cílové rozhraní .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="5641a-111">Retarget all projects you wish to port to target .NET Framework 4.6.2.</span></span>

   <span data-ttu-id="5641a-112">Tím se zajistí, že můžete použít alternativy rozhraní API pro .NET Framework specifické cíle v případech, kdy .NET Core nemůže zajišťovat podporu pro dané rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="5641a-112">This ensures that you can use API alternatives for .NET Framework-specific targets in the cases where .NET Core can't support a particular API.</span></span>
   
3. <span data-ttu-id="5641a-113">Použití [.NET Portability Analyzeru](../../standard/analyzers/portability-analyzer.md) analyzovat vaše sestavení a vývoj plánu na port na základě jejích výsledků.</span><span class="sxs-lookup"><span data-stu-id="5641a-113">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to analyze your assemblies and develop a plan to port based on its results.</span></span>

   <span data-ttu-id="5641a-114">Nástroj Analyzátor přenositelnosti rozhraní API analyzuje zkompilovaným sestavením a generovat sestavy, která zobrazuje souhrn vyšší úrovně přenositelnost a přehled každé rozhraní API používáte, není k dispozici v rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5641a-114">The API Portability Analyzer tool will analyze your compiled assemblies and generate a report which shows a high-level portability summary and a breakdown of each API you're using that isn't available on .NET Core.</span></span>  <span data-ttu-id="5641a-115">Můžete použít tuto sestavu spolu s analýzu vašeho základu kódu pro jak budete přeneste kód přes při vytváření plánu.</span><span class="sxs-lookup"><span data-stu-id="5641a-115">You can use this report alongside an analysis of your codebase to develop a plan for how you'll port your code over.</span></span>
   
4. <span data-ttu-id="5641a-116">Přeneste kód testy.</span><span class="sxs-lookup"><span data-stu-id="5641a-116">Port your tests code.</span></span>

   <span data-ttu-id="5641a-117">Přenos aplikací .NET Core je velkou změnu do vašeho základu kódu, se důrazně doporučujeme zobrazíte testy přenáší tak, aby jako port kód prostřednictvím je možné spustit testy.</span><span class="sxs-lookup"><span data-stu-id="5641a-117">Because porting to .NET Core is such a big change to your codebase, it's highly recommended to get your tests ported so that you can run tests as you port code over.</span></span>  <span data-ttu-id="5641a-118">MSTest, xUnit a NUnit podpora .NET Core 1.0 ještě dnes.</span><span class="sxs-lookup"><span data-stu-id="5641a-118">MSTest, xUnit, and NUnit all support .NET Core 1.0 today.</span></span>
   
6. <span data-ttu-id="5641a-119">Spuštění vašeho plánu pro přenos!</span><span class="sxs-lookup"><span data-stu-id="5641a-119">Execute your plan for porting!</span></span>

## <a name="tools-to-help"></a><span data-ttu-id="5641a-120">Nástroje, které pomáhají</span><span class="sxs-lookup"><span data-stu-id="5641a-120">Tools to help</span></span>

<span data-ttu-id="5641a-121">Tady je krátký seznam nástrojů, které najdete užitečné:</span><span class="sxs-lookup"><span data-stu-id="5641a-121">Here's a short list of the tools you'll find helpful:</span></span>

* <span data-ttu-id="5641a-122">NuGet – [pro klienta Nuget](https://dist.nuget.org/index.html) nebo [NuGet – Průzkumník balíčků](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer), Správce balíčků od Microsoftu pro implementace .NET.</span><span class="sxs-lookup"><span data-stu-id="5641a-122">NuGet - [Nuget Client](https://dist.nuget.org/index.html) or [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer), Microsoft's package manager for .NET implementations.</span></span>
* <span data-ttu-id="5641a-123">Rozhraní API Portability Analyzeru - [nástroj příkazového řádku](https://github.com/Microsoft/dotnet-apiport/releases) nebo [rozšíření sady Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b), sada nástrojů, který může vygenerovat sestavu jak přenosného kódu je mezi rozhraní .NET Framework a .NET Core s Rozpis sestavení podle problémů.</span><span class="sxs-lookup"><span data-stu-id="5641a-123">Api Portability Analyzer - [command line tool](https://github.com/Microsoft/dotnet-apiport/releases) or [Visual Studio Extension](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b), a toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core, with an assembly-by-assembly breakdown of issues.</span></span>  <span data-ttu-id="5641a-124">Zobrazit [nástroje, které vám pomohou v procesu](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/) Další informace.</span><span class="sxs-lookup"><span data-stu-id="5641a-124">See [Tooling to help you on the process](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/) for more information.</span></span>
* <span data-ttu-id="5641a-125">Reverzního vyhledávání balíčků – A [užitečné webová služba](https://packagesearch.azurewebsites.net) , který umožňuje hledat typ a vyhledat balíčky obsahující tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="5641a-125">Reverse Package Search - A [useful web service](https://packagesearch.azurewebsites.net) that allows you to search for a type and find packages containing that type.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5641a-126">Další kroky</span><span class="sxs-lookup"><span data-stu-id="5641a-126">Next steps</span></span>

[<span data-ttu-id="5641a-127">Analýza závislostí třetích stran.</span><span class="sxs-lookup"><span data-stu-id="5641a-127">Analyzing your third-party dependencies.</span></span>](third-party-deps.md)
   
