---
title: Nástroje pro přenos do jádra .NET Core
description: Informace o některých nástrojích, které můžete použít k portu do rozhraní .NET Core
author: cartermp
ms.date: 12/07/2018
ms.openlocfilehash: 98b3a29f2287414b2cd323f1cbf2225905592b26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157515"
---
# <a name="tools-to-help-with-porting-to-net-core"></a><span data-ttu-id="25243-103">Nástroje pro pomoc s přenosem aplikací do .NET Core</span><span class="sxs-lookup"><span data-stu-id="25243-103">Tools to help with porting to .NET Core</span></span>

<span data-ttu-id="25243-104">Při přenosu můžete najít užitečné nástroje uvedené v tomto článku:</span><span class="sxs-lookup"><span data-stu-id="25243-104">You may find the tools listed in this article helpful when porting:</span></span>

- <span data-ttu-id="25243-105">[.NET Přenositelnost Analyzer](../../standard/analyzers/portability-analyzer.md) - toolchain, který může generovat zprávu o tom, jak přenosný kód je mezi rozhraním .NET Framework a .NET Core:</span><span class="sxs-lookup"><span data-stu-id="25243-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) - A toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core:</span></span>
  - <span data-ttu-id="25243-106">Jako [nástroj příkazového řádku](https://github.com/Microsoft/dotnet-apiport/releases)</span><span class="sxs-lookup"><span data-stu-id="25243-106">As a [command-line tool](https://github.com/Microsoft/dotnet-apiport/releases)</span></span>
  - <span data-ttu-id="25243-107">Jako [rozšíření sady Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)</span><span class="sxs-lookup"><span data-stu-id="25243-107">As a [Visual Studio extension](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)</span></span>
- <span data-ttu-id="25243-108">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - Analyzátor Roslyn, který zjišťuje potenciální rizika kompatibility pro rozhraní API jazyka C# na různých platformách a detekuje volání zastaralá rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="25243-108">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - A Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span>

<span data-ttu-id="25243-109">Kromě toho se můžete pokusit portovat menší řešení nebo jednotlivé projekty do formátu souboru projektu .NET Core pomocí nástroje [CsprojToVs2017.](https://github.com/hvanbakel/CsprojToVs2017)</span><span class="sxs-lookup"><span data-stu-id="25243-109">Additionally, you can attempt to port smaller solutions or individual projects to the .NET Core project file format with the [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) tool.</span></span>

> [!WARNING]
> <span data-ttu-id="25243-110">CsprojToVs2017 je nástroj třetí strany.</span><span class="sxs-lookup"><span data-stu-id="25243-110">CsprojToVs2017 is a third-party tool.</span></span> <span data-ttu-id="25243-111">Neexistuje žádná záruka, že bude fungovat pro všechny vaše projekty a může způsobit drobné změny v chování, které jste závislí na.</span><span class="sxs-lookup"><span data-stu-id="25243-111">There is no guarantee that it will work for all of your projects, and it may cause subtle changes in behavior that you depend on.</span></span> <span data-ttu-id="25243-112">CsprojToVs2017 by měl být použit jako _výchozí bod,_ který automatizuje základní věci, které lze automatizovat.</span><span class="sxs-lookup"><span data-stu-id="25243-112">CsprojToVs2017 should be used as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="25243-113">Není zaručeným řešením migrace formátů souborů projektu.</span><span class="sxs-lookup"><span data-stu-id="25243-113">It is not a guaranteed solution to migrating project file formats.</span></span>
