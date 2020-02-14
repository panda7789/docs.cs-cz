---
title: Nástroje pro přenos do .NET Core
description: Přečtěte si o některých nástrojích, které můžete použít k portům pro .NET Core.
author: cartermp
ms.date: 12/07/2018
ms.openlocfilehash: 3b71c31b4f26b278b2bd1088adc8e9f64d28ab7b
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215198"
---
# <a name="tools-to-help-with-porting-to-net-core"></a><span data-ttu-id="31895-103">Nástroje pro pomoc s přenosem aplikací do .NET Core</span><span class="sxs-lookup"><span data-stu-id="31895-103">Tools to help with porting to .NET Core</span></span>

<span data-ttu-id="31895-104">Můžete najít nástroje uvedené v tomto článku, které jsou užitečné při přenosu:</span><span class="sxs-lookup"><span data-stu-id="31895-104">You may find the tools listed in this article helpful when porting:</span></span>

- <span data-ttu-id="31895-105">[Analyzátor přenositelnosti .NET](../../standard/analyzers/portability-analyzer.md) – sada nástrojů, který může generovat sestavu způsobu, jakým je váš kód mezi .NET Framework a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="31895-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) - A toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core:</span></span>
  - <span data-ttu-id="31895-106">Jako [Nástroj příkazového řádku](https://github.com/Microsoft/dotnet-apiport/releases)</span><span class="sxs-lookup"><span data-stu-id="31895-106">As a [command-line tool](https://github.com/Microsoft/dotnet-apiport/releases)</span></span>
  - <span data-ttu-id="31895-107">Jako [rozšíření sady Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)</span><span class="sxs-lookup"><span data-stu-id="31895-107">As a [Visual Studio extension](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)</span></span>
- <span data-ttu-id="31895-108">[Rozhraní .NET API Analyzer](../../standard/analyzers/api-analyzer.md) – analyzátor Roslyn, který zjišťuje potenciální rizika kompatibility pro C# rozhraní API na různých platformách a detekuje volání zastaralých rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="31895-108">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - A Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span>

<span data-ttu-id="31895-109">Kromě toho se můžete pokusit přenést menší řešení nebo jednotlivé projekty do formátu souboru projektu .NET Core pomocí nástroje [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) Tool.</span><span class="sxs-lookup"><span data-stu-id="31895-109">Additionally, you can attempt to port smaller solutions or individual projects to the .NET Core project file format with the [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) tool.</span></span>

> [!WARNING] 
> <span data-ttu-id="31895-110">CsprojToVs2017 je nástroj třetí strany.</span><span class="sxs-lookup"><span data-stu-id="31895-110">CsprojToVs2017 is a third-party tool.</span></span> <span data-ttu-id="31895-111">Není zaručeno, že bude fungovat pro všechny vaše projekty a může způsobit drobné změny v chování, které jsou závislé na.</span><span class="sxs-lookup"><span data-stu-id="31895-111">There is no guarantee that it will work for all of your projects, and it may cause subtle changes in behavior that you depend on.</span></span> <span data-ttu-id="31895-112">CsprojToVs2017 by měla být použita jako _výchozí bod_ , který automatizuje základní věci, které lze automatizovat.</span><span class="sxs-lookup"><span data-stu-id="31895-112">CsprojToVs2017 should be used as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="31895-113">Není zaručené řešení pro migraci formátů souborů projektu.</span><span class="sxs-lookup"><span data-stu-id="31895-113">It is not a guaranteed solution to migrating project file formats.</span></span>
