---
title: Roslyn na základě analyzátorů - rozhraní .NET
description: Další informace o Roslyn na základě analyzátory, které najít problémy a navrhněte opravy těchto problémů.
keywords: Rozhraní .NET, .NET core
author: billwagner
ms.author: billwagner
ms.date: 01/24/2018
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.openlocfilehash: 8c6524716ba403bc426df8dc33e64b8b2934d3d7
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2018
---
# <a name="the-roslyn-based-analyzers"></a><span data-ttu-id="386a4-104">Roslyn na základě analyzátory</span><span class="sxs-lookup"><span data-stu-id="386a4-104">The Roslyn based Analyzers</span></span>

<span data-ttu-id="386a4-105">Na základě Roslyn analyzátorů používat sadu .NET SDK kompilátoru (Roslyn rozhraní API) k analýze vašeho projektu zdrojového kódu k vyhledání problémů a opravy zobrazovat.</span><span class="sxs-lookup"><span data-stu-id="386a4-105">Roslyn-based analyzers use the .NET Compiler SDK (Roslyn APIs) to analyze your project's source code to find issues and suggest corrections.</span></span> <span data-ttu-id="386a4-106">Různé analyzátory vyhledejte různé třídy problémy, od postupů, které mohou způsobit chyby k zabezpečení se k rozhraní API kompatibility.</span><span class="sxs-lookup"><span data-stu-id="386a4-106">Different analyzers look for different classes of issues, ranging from practices that are likely to cause bugs to security concerns to API compatibility.</span></span>

<span data-ttu-id="386a4-107">Na základě Roslyn analyzátorů fungovat i interaktivně a během sestavení.</span><span class="sxs-lookup"><span data-stu-id="386a4-107">Roslyn-based analyzers work both interactively and during builds.</span></span> <span data-ttu-id="386a4-108">Nástroje analyzer obsahuje různé pokyny, když v sadě Visual Studio nebo v sestavení příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="386a4-108">The analyzer provides different guidance when in Visual Studio or in command-line builds.</span></span>

<span data-ttu-id="386a4-109">Během úprav kódu v sadě Visual Studio spusťte analyzátory při provádění změn, jakmile vytvoříte kód, který aktivuje obavy zachytávání možných problémů.</span><span class="sxs-lookup"><span data-stu-id="386a4-109">While you edit code in Visual Studio, the analyzers run as you make changes, catching possible issues as soon as you create code that trigger concerns.</span></span> <span data-ttu-id="386a4-110">Všechny problémy se zvýrazněnou s podtržení vlnovkou pod jakýkoli problém.</span><span class="sxs-lookup"><span data-stu-id="386a4-110">Any issues are highlighted with squiggles under any issue.</span></span> <span data-ttu-id="386a4-111">Visual Studio zobrazí žárovky, a když na ni kliknete analyzátor navrhovat možné opravy pro daný problém.</span><span class="sxs-lookup"><span data-stu-id="386a4-111">Visual Studio displays a light bulb, and when you click on it the analyzer will suggest possible fixes for that issue.</span></span> <span data-ttu-id="386a4-112">Při sestavování projektu v sadě Visual Studio nebo z příkazového řádku zdrojového kódu se analyzují a nástroje analyzer poskytuje úplný seznam potenciální problémy.</span><span class="sxs-lookup"><span data-stu-id="386a4-112">When you build the project, either in Visual Studio or from the command line, all the source code is analyzed and the analyzer provides a full list of potential issues.</span></span> <span data-ttu-id="386a4-113">Následující obrázek znázorňuje jedním z příkladů.</span><span class="sxs-lookup"><span data-stu-id="386a4-113">The following figure shows one example.</span></span>

![problémy hlášené analyzátor framework](./media/framework-analyzers-2.png)

<span data-ttu-id="386a4-115">Na základě Roslyn analyzátorů sestavy potenciální problémy jako chyby, upozornění a informace na základě jejich závažnosti problému.</span><span class="sxs-lookup"><span data-stu-id="386a4-115">Roslyn-based analyzers report potential issues as errors, warnings, or information based on the severity of the issue.</span></span>

<span data-ttu-id="386a4-116">Nainstalujete na základě Roslyn analyzátorů jako balíčky NuGet ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="386a4-116">You install Roslyn-based analyzers as NuGet packages in your project.</span></span> <span data-ttu-id="386a4-117">Nakonfigurované analyzátory a všechna nastavení pro každou analyzátor jsou obnovit a spustit na počítači pro všechny vývojáře pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="386a4-117">The configured analyzers and any settings for each analyzer are restored and run on any developer's machine for that project.</span></span>

> [!NOTE]
> <span data-ttu-id="386a4-118">Uživatelské prostředí na základě Roslyn analyzátorů je jiné než u knihovny analýz kód jako starší verze FxCop a nástrojů pro analýzu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="386a4-118">The user experience for Roslyn-based analyzers is different than that of the Code Analysis libraries like the older versions of FxCop and the security analysis tools.</span></span>  <span data-ttu-id="386a4-119">Nemusíte explicitně spustit na základě Roslyn analyzátorů.</span><span class="sxs-lookup"><span data-stu-id="386a4-119">You don't need to explicitly run the Roslyn-based analyzers.</span></span> <span data-ttu-id="386a4-120">Není nutné používat položky nabídky "analýza kódu spustit" v sadě Visual Studio v nabídce "Analyzovat".</span><span class="sxs-lookup"><span data-stu-id="386a4-120">There's no need to use the "Run Code Analysis" menu items on the "Analyze" menu in Visual Studio.</span></span> <span data-ttu-id="386a4-121">Na základě Roslyn analyzátorů spustit asychronously při práci.</span><span class="sxs-lookup"><span data-stu-id="386a4-121">Roslyn-based analyzers run asychronously as you work.</span></span> 

## <a name="more-information-on-specific-analyzers"></a><span data-ttu-id="386a4-122">Další informace o konkrétní analyzátory</span><span class="sxs-lookup"><span data-stu-id="386a4-122">More information on specific analyzers</span></span>

<span data-ttu-id="386a4-123">Následující analyzátorů jsou popsané v této části:</span><span class="sxs-lookup"><span data-stu-id="386a4-123">The following analyzers are covered in this section:</span></span>

<span data-ttu-id="386a4-124">[Rozhraní API analyzátor](api-analyzer.md): Tento analyzátor prozkoumá kódu pro potenciální rizika kompatibility nebo používá zastaralá rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="386a4-124">[API Analyzer](api-analyzer.md): This analyzer examines your code for potential compatibility risks or uses of deprecated APIs.</span></span>    
<span data-ttu-id="386a4-125">[Analyzátor Framework](framework-analyzer.md): Tento analyzátor prozkoumá kódu zajistit postupuje podle pokynů pro aplikace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="386a4-125">[Framework Analyzer](framework-analyzer.md): This analyzer examines your code to ensure it follows the guidelines for .NET Framework applications.</span></span> <span data-ttu-id="386a4-126">Mezi tato pravidla patří několik doporučení na základě zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="386a4-126">These rules include several security-based recommendations.</span></span>
