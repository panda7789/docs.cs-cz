---
title: Port od .NET Framework do .NET Core
description: Pochopení procesu přenosu a zjišťování nástrojů, které můžete najít užitečné při přenosu .NET Framework projektu do .NET Core.
author: cartermp
ms.date: 10/22/2019
ms.custom: seodec18
ms.openlocfilehash: 89f00e5c6ce7f3cea7a3135c9b2856c54a70da40
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73038522"
---
# <a name="overview-of-the-porting-process-from-net-framework-to-net-core"></a><span data-ttu-id="d6d4e-103">Přehled procesu přenosu z .NET Framework do .NET Core</span><span class="sxs-lookup"><span data-stu-id="d6d4e-103">Overview of the porting process from .NET Framework to .NET Core</span></span>

<span data-ttu-id="d6d4e-104">Je možné, že máte kód, který se v současnosti spouští na .NET Framework, které vás zajímá o přenos do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6d4e-104">You might have code that currently runs on the .NET Framework that you're interested in porting to .NET Core.</span></span> <span data-ttu-id="d6d4e-105">Tento článek popisuje:</span><span class="sxs-lookup"><span data-stu-id="d6d4e-105">This article provides:</span></span>

* <span data-ttu-id="d6d4e-106">Přehled procesu přenosu.</span><span class="sxs-lookup"><span data-stu-id="d6d4e-106">An overview of the porting process.</span></span>
* <span data-ttu-id="d6d4e-107">Seznam nástrojů, které můžete najít užitečné při přenosu kódu do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6d4e-107">A list of the tools you may find helpful when you're porting your code to .NET Core.</span></span>

## <a name="overview-of-the-porting-process"></a><span data-ttu-id="d6d4e-108">Přehled procesu přenosu</span><span class="sxs-lookup"><span data-stu-id="d6d4e-108">Overview of the porting process</span></span>

<span data-ttu-id="d6d4e-109">Při přenosu projektu do .NET Core doporučujeme použít následující postup:</span><span class="sxs-lookup"><span data-stu-id="d6d4e-109">We recommend you to use the following process when porting your project to .NET Core:</span></span>

1. <span data-ttu-id="d6d4e-110">Přecílíte na všechny projekty, které chcete přenést, aby bylo možné cílit na .NET Framework 4.7.2 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="d6d4e-110">Retarget all projects you wish to port to target the .NET Framework 4.7.2 or higher.</span></span>

   <span data-ttu-id="d6d4e-111">Tento krok zajistí, že můžete použít alternativy rozhraní API pro cíle specifické pro .NET Framework, když .NET Core nepodporuje konkrétní rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="d6d4e-111">This step ensures that you can use API alternatives for .NET Framework-specific targets when .NET Core doesn't support a particular API.</span></span>

2. <span data-ttu-id="d6d4e-112">Pomocí [analyzátoru přenositelnosti .NET](../../standard/analyzers/portability-analyzer.md) můžete analyzovat vaše sestavení a zjistit, jestli jsou přenosné do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6d4e-112">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to analyze your assemblies and see if they're portable to .NET Core.</span></span>

   <span data-ttu-id="d6d4e-113">Nástroj Analyzátor přenositelnosti API analyzuje kompilovaná sestavení a generuje sestavu.</span><span class="sxs-lookup"><span data-stu-id="d6d4e-113">The API Portability Analyzer tool analyzes your compiled assemblies and generates a report.</span></span> <span data-ttu-id="d6d4e-114">Tato sestava zobrazuje souhrn přenositelnosti na vysoké úrovni a rozdělení každého rozhraní API, které používáte, není k dispozici v rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6d4e-114">This report shows a high-level portability summary and a breakdown of each API you're using that isn't available on NET Core.</span></span>

3. <span data-ttu-id="d6d4e-115">Nainstalujte [analyzátor rozhraní .NET API](../../standard/analyzers/api-analyzer.md) do svých projektů, abyste identifikovali vyvolané <xref:System.PlatformNotSupportedException> na některých platformách a nějaké jiné potenciální problémy s kompatibilitou.</span><span class="sxs-lookup"><span data-stu-id="d6d4e-115">Install the [.NET API analyzer](../../standard/analyzers/api-analyzer.md) into your projects to identify APIs throwing <xref:System.PlatformNotSupportedException> on some platforms and some other potential compatibility issues.</span></span>

   <span data-ttu-id="d6d4e-116">Tento nástroj je podobný analyzátoru přenositelnosti, ale místo analýzy toho, jestli se můžou věci vytvářet v .NET Core, se analyzuje, pokud používáte rozhraní API způsobem, který vyvolá <xref:System.PlatformNotSupportedException> za běhu.</span><span class="sxs-lookup"><span data-stu-id="d6d4e-116">This tool is similar to the portability analyzer, but instead of analyzing if things can build on .NET Core, it will analyze if you're using an API in a way that will throw the <xref:System.PlatformNotSupportedException> at runtime.</span></span> <span data-ttu-id="d6d4e-117">I když se nejedná o běžný postup, Pokud přesouváte z .NET Framework 4.7.2 nebo vyšší, je dobré ho kontrolovat.</span><span class="sxs-lookup"><span data-stu-id="d6d4e-117">Although this isn't common if you're moving from .NET Framework 4.7.2 or higher, it's good to check.</span></span>

4. <span data-ttu-id="d6d4e-118">Převeďte všechny své `packages.config` závislosti na formát [PackageReference](/nuget/consume-packages/package-references-in-project-files) pomocí nástroje pro [převod v aplikaci Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).</span><span class="sxs-lookup"><span data-stu-id="d6d4e-118">Convert all of your `packages.config` dependencies to the [PackageReference](/nuget/consume-packages/package-references-in-project-files) format with the [conversion tool in Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).</span></span>

   <span data-ttu-id="d6d4e-119">Tento krok zahrnuje převod závislostí ze staršího formátu `packages.config`.</span><span class="sxs-lookup"><span data-stu-id="d6d4e-119">This step involves converting your dependencies from the legacy `packages.config` format.</span></span> <span data-ttu-id="d6d4e-120">`packages.config` nefunguje v rozhraní .NET Core, proto je tento převod nutný, pokud máte závislosti balíčku.</span><span class="sxs-lookup"><span data-stu-id="d6d4e-120">`packages.config` doesn't work on .NET Core, so this conversion is required if you have package dependencies.</span></span>

5. <span data-ttu-id="d6d4e-121">Vytvořte nové projekty pro .NET Core a zkopírujte přes zdrojové soubory nebo se pokuste převést existující soubor projektu pomocí nástroje.</span><span class="sxs-lookup"><span data-stu-id="d6d4e-121">Create new projects for .NET Core and copy over source files, or attempt to convert your existing project file with a tool.</span></span>

   <span data-ttu-id="d6d4e-122">.NET Core používá zjednodušený (a odlišný) [Formát souboru projektu](../tools/csproj.md) než .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d6d4e-122">.NET Core uses a simplified (and different) [project file format](../tools/csproj.md) than .NET Framework.</span></span> <span data-ttu-id="d6d4e-123">Aby bylo možné pokračovat, budete muset soubory projektu převést do tohoto formátu.</span><span class="sxs-lookup"><span data-stu-id="d6d4e-123">You'll need to convert your project files into this format to continue.</span></span>

6. <span data-ttu-id="d6d4e-124">Port vašeho testovacího kódu.</span><span class="sxs-lookup"><span data-stu-id="d6d4e-124">Port your test code.</span></span>

   <span data-ttu-id="d6d4e-125">Vzhledem k tomu, že přenos do .NET Core je podstatnou změnou základu kódu, důrazně doporučujeme, abyste si nadostali své testy, abyste mohli spouštět testy během přenosu kódu.</span><span class="sxs-lookup"><span data-stu-id="d6d4e-125">Because porting to .NET Core is such a significant change to your codebase, it's highly recommended to get your tests ported, so that you can run tests as you port your code over.</span></span> <span data-ttu-id="d6d4e-126">MSTest, xUnit a NUnit všechny fungují na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6d4e-126">MSTest, xUnit, and NUnit all work on .NET Core.</span></span>

<span data-ttu-id="d6d4e-127">Kromě toho se můžete pokusit přenést menší řešení nebo jednotlivé projekty do formátu souboru projektu .NET Core pomocí nástroje [dotnet try-Convert](https://github.com/dotnet/try-convert) v jedné operaci.</span><span class="sxs-lookup"><span data-stu-id="d6d4e-127">Additionally, you can attempt to port smaller solutions or individual projects to the .NET Core project file format with the [dotnet try-convert](https://github.com/dotnet/try-convert) tool in one operation.</span></span> <span data-ttu-id="d6d4e-128">`dotnet try-convert` není zaručená práce pro všechny vaše projekty a může způsobit drobné změny v chování, které byste zjistili, na kterých jste se zapracovali.</span><span class="sxs-lookup"><span data-stu-id="d6d4e-128">`dotnet try-convert` is not guaranteed to work for all your projects, and it may cause subtle changes in behavior that you may find that you depended on.</span></span> <span data-ttu-id="d6d4e-129">Měl by se použít jako _výchozí bod_ , který automatizuje základní věci, které je možné automatizovat.</span><span class="sxs-lookup"><span data-stu-id="d6d4e-129">It should be used as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="d6d4e-130">Není zaručené řešení pro migraci projektu.</span><span class="sxs-lookup"><span data-stu-id="d6d4e-130">It isn't a guaranteed solution to migrating a project.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="d6d4e-131">Next</span><span class="sxs-lookup"><span data-stu-id="d6d4e-131">Next</span></span>](net-framework-tech-unavailable.md)
