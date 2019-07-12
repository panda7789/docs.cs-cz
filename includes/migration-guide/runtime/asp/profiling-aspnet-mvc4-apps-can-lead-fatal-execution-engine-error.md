---
ms.openlocfilehash: 107b34c7bd26e1396e8a6638d6929c15de92b8e4
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803202"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="c8080-101">Profilace aplikací ASP.Net MVC4 může vést k závažné chybě</span><span class="sxs-lookup"><span data-stu-id="c8080-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c8080-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="c8080-102">Details</span></span>|<span data-ttu-id="c8080-103">Profilovací programy pomocí sestavení NGEN/Profile dojít k chybě profilovaných aplikací technologie ASP.NET MVC4 při spuštění s "závažnou spuštění modulu výjimku.</span><span class="sxs-lookup"><span data-stu-id="c8080-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>|
|<span data-ttu-id="c8080-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="c8080-104">Suggestion</span></span>|<span data-ttu-id="c8080-105">Tento problém je vyřešen v rozhraní .NET Framework 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="c8080-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="c8080-106">Alternativně může profiler vyhnout tomuto problému zadáním <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> v jeho masky události.</span><span class="sxs-lookup"><span data-stu-id="c8080-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>|
|<span data-ttu-id="c8080-107">Scope</span><span class="sxs-lookup"><span data-stu-id="c8080-107">Scope</span></span>|<span data-ttu-id="c8080-108">Edge</span><span class="sxs-lookup"><span data-stu-id="c8080-108">Edge</span></span>|
|<span data-ttu-id="c8080-109">Version</span><span class="sxs-lookup"><span data-stu-id="c8080-109">Version</span></span>|<span data-ttu-id="c8080-110">4.5</span><span class="sxs-lookup"><span data-stu-id="c8080-110">4.5</span></span>|
|<span data-ttu-id="c8080-111">type</span><span class="sxs-lookup"><span data-stu-id="c8080-111">Type</span></span>|<span data-ttu-id="c8080-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="c8080-112">Runtime</span></span>|

