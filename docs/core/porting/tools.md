---
title: Nástroje pro přenos do .NET Core
description: Další informace o některé nástroje, které můžete použít k portu až po .NET Core
author: cartermp
ms.author: mairaw
ms.date: 12/07/2018
ms.openlocfilehash: 88e3edb0442b3326a77323fe4b6396f3eb1ca767
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663112"
---
# <a name="tools-to-help-with-porting-to-net-core"></a><span data-ttu-id="bc72c-103">Nástroje, které pomáhají s přenos aplikací .NET Core</span><span class="sxs-lookup"><span data-stu-id="bc72c-103">Tools to help with porting to .NET Core</span></span>

<span data-ttu-id="bc72c-104">Může být pro vás nástroje uvedené v tomto článku, které jsou užitečné při přenosu:</span><span class="sxs-lookup"><span data-stu-id="bc72c-104">You may find the tools listed in this article helpful when porting:</span></span>

* <span data-ttu-id="bc72c-105">[.NET portability Analyzeru](../../standard/analyzers/portability-analyzer.md), sada nástrojů, které lze generovat sestavy je váš kód jak přenosné mezi rozhraní .NET Framework a .NET Core:  Jako [nástroj příkazového řádku](https://github.com/Microsoft/dotnet-apiport/releases) jako [rozšíření sady Visual Studio](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)</span><span class="sxs-lookup"><span data-stu-id="bc72c-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md), a toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core:  As a [command line tool](https://github.com/Microsoft/dotnet-apiport/releases) As a [Visual Studio Extension](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)</span></span>
* <span data-ttu-id="bc72c-106">[Analyzátor rozhraní .NET API](../../standard/analyzers/api-analyzer.md) -A Roslyn analyzátor, který zjišťuje potenciální problémy rizika pro C# rozhraní API na různých platformách a detekuje volání rozhraní API nepoužívané.</span><span class="sxs-lookup"><span data-stu-id="bc72c-106">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - A Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span>

<span data-ttu-id="bc72c-107">Kromě toho se můžete pokusit port menší řešení nebo na formát souboru projektu .NET Core s jednotlivými projekty [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) nástroj.</span><span class="sxs-lookup"><span data-stu-id="bc72c-107">Additionally, you can attempt to port smaller solutions or individual projects to the .NET Core project file format with the [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) tool.</span></span>

> [!WARNING] 
> <span data-ttu-id="bc72c-108">CsprojToVs2017 je nástroj třetí strany.</span><span class="sxs-lookup"><span data-stu-id="bc72c-108">CsprojToVs2017 is a third-party tool.</span></span> <span data-ttu-id="bc72c-109">Neexistuje žádná záruka, že bude fungovat pro všemi svými projekty a může to způsobit drobné změny v chování, které nejvíc potřebujete.</span><span class="sxs-lookup"><span data-stu-id="bc72c-109">There is no guarantee that it will work for all of your projects, and it may cause subtle changes in behavior that you depend on.</span></span> <span data-ttu-id="bc72c-110">CsprojToVs2017 by měla sloužit jako _počáteční bod_ , který automatizuje základní akce, které je možné automatizovat.</span><span class="sxs-lookup"><span data-stu-id="bc72c-110">CsprojToVs2017 should be used as a _starting point_ that automates the basic things that can be automated.</span></span> <span data-ttu-id="bc72c-111">Není zaručené řešení migrace formáty souborů projektu.</span><span class="sxs-lookup"><span data-stu-id="bc72c-111">It is not a guaranteed solution to migrating project file formats.</span></span>