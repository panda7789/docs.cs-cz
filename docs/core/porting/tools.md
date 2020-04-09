---
title: Nástroje pro přenos do jádra .NET Core
description: Informace o některých nástrojích, které můžete použít k portu do rozhraní .NET Core
author: cartermp
ms.date: 12/07/2018
ms.openlocfilehash: 64bad7600d8e17ada83d4bd8bc56762fd1789f43
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989126"
---
# <a name="tools-to-help-with-porting-to-net-core"></a><span data-ttu-id="9b903-103">Nástroje pro pomoc s přenosem aplikací do .NET Core</span><span class="sxs-lookup"><span data-stu-id="9b903-103">Tools to help with porting to .NET Core</span></span>

<span data-ttu-id="9b903-104">Při přenosu můžete najít užitečné nástroje uvedené v tomto článku:</span><span class="sxs-lookup"><span data-stu-id="9b903-104">You may find the tools listed in this article helpful when porting:</span></span>

- <span data-ttu-id="9b903-105">[.NET Přenositelnost Analyzer](../../standard/analyzers/portability-analyzer.md) - toolchain, který může generovat zprávu o tom, jak přenosný kód je mezi rozhraním .NET Framework a .NET Core:</span><span class="sxs-lookup"><span data-stu-id="9b903-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) - A toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core:</span></span>
  - <span data-ttu-id="9b903-106">Jako [nástroj příkazového řádku](https://github.com/Microsoft/dotnet-apiport/releases)</span><span class="sxs-lookup"><span data-stu-id="9b903-106">As a [command-line tool](https://github.com/Microsoft/dotnet-apiport/releases)</span></span>
  - <span data-ttu-id="9b903-107">Jako [rozšíření sady Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)</span><span class="sxs-lookup"><span data-stu-id="9b903-107">As a [Visual Studio extension](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)</span></span>
- <span data-ttu-id="9b903-108">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - Analyzátor Roslyn, který zjišťuje potenciální rizika kompatibility pro rozhraní API jazyka C# na různých platformách a detekuje volání zastaralá rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="9b903-108">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - A Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span>

<span data-ttu-id="9b903-109">Kromě toho se můžete pokusit portovat menší řešení nebo jednotlivé projekty do formátu souboru projektu .NET Core pomocí nástroje [CsprojToVs2017.](https://github.com/hvanbakel/CsprojToVs2017)</span><span class="sxs-lookup"><span data-stu-id="9b903-109">Additionally, you can attempt to port smaller solutions or individual projects to the .NET Core project file format with the [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) tool.</span></span>

> [!WARNING]
> <span data-ttu-id="9b903-110">CsprojToVs2017 je nástroj třetí strany.</span><span class="sxs-lookup"><span data-stu-id="9b903-110">CsprojToVs2017 is a third-party tool.</span></span> <span data-ttu-id="9b903-111">Neexistuje žádná záruka, že bude fungovat pro všechny vaše projekty a může způsobit drobné změny v chování, které jste závislí na.</span><span class="sxs-lookup"><span data-stu-id="9b903-111">There is no guarantee that it will work for all of your projects, and it may cause subtle changes in behavior that you depend on.</span></span> <span data-ttu-id="9b903-112">CsprojToVs2017 by měl být použit jako _výchozí bod,_ který automatizuje základní věci, které lze automatizovat.</span><span class="sxs-lookup"><span data-stu-id="9b903-112">CsprojToVs2017 should be used as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="9b903-113">Není zaručeným řešením migrace formátů souborů projektu.</span><span class="sxs-lookup"><span data-stu-id="9b903-113">It is not a guaranteed solution to migrating project file formats.</span></span>
