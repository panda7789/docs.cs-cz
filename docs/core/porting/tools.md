---
title: Nástroje pro přenos do .NET Core
description: Přečtěte si o některých nástrojích, které můžete použít k portům pro .NET Core.
author: cartermp
ms.date: 05/03/2020
ms.openlocfilehash: d0cf0abf206950beb34556ca3ba7243d8cad241e
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795583"
---
# <a name="tools-to-help-with-porting-to-net-core"></a><span data-ttu-id="ded5f-103">Nástroje pro pomoc s přenosem aplikací do .NET Core</span><span class="sxs-lookup"><span data-stu-id="ded5f-103">Tools to help with porting to .NET Core</span></span>

<span data-ttu-id="ded5f-104">Můžete najít nástroje uvedené v tomto článku, které jsou užitečné při přenosu:</span><span class="sxs-lookup"><span data-stu-id="ded5f-104">You may find the tools listed in this article helpful when porting:</span></span>

- <span data-ttu-id="ded5f-105">[Analyzátor přenositelnosti .NET](../../standard/analyzers/portability-analyzer.md) – sada nástrojů, který může generovat sestavu způsobu, jakým je váš kód mezi .NET Framework a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ded5f-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) - A toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core:</span></span>
  - <span data-ttu-id="ded5f-106">Jako [Nástroj příkazového řádku](https://github.com/Microsoft/dotnet-apiport/releases)</span><span class="sxs-lookup"><span data-stu-id="ded5f-106">As a [command-line tool](https://github.com/Microsoft/dotnet-apiport/releases)</span></span>
  - <span data-ttu-id="ded5f-107">Jako [rozšíření sady Visual Studio](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)</span><span class="sxs-lookup"><span data-stu-id="ded5f-107">As a [Visual Studio extension](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)</span></span>
- <span data-ttu-id="ded5f-108">[Rozhraní .NET API Analyzer](../../standard/analyzers/api-analyzer.md) – analyzátor Roslyn, který zjišťuje potenciální rizika kompatibility pro rozhraní API jazyka C# na různých platformách a detekuje volání zastaralých rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="ded5f-108">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - A Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span>
- <span data-ttu-id="ded5f-109">[Try-Convert](https://www.nuget.org/packages/try-convert/) -globální nástroj .NET Core, který může převést projekt nebo celé řešení na sadu .NET SDK, včetně přesunu desktopových aplikací do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ded5f-109">[try-convert](https://www.nuget.org/packages/try-convert/) - A .NET Core global tool that can convert a project or entire solution to the .NET SDK, including moving desktop apps to .NET Core.</span></span> <span data-ttu-id="ded5f-110">Nedoporučuje se, pokud máte navázánější sestavení (například vlastní úkoly, cíle nebo importy) a odmítáte mnoho typů projektů, které nejsou kompatibilní s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ded5f-110">It is not recommended if you have a more complicated build established (such as custom tasks, targets, or imports), and it rejects many project types that are incompatible with .NET Core.</span></span>
