---
ms.openlocfilehash: 439a4976482639cd2e4e17315ec1a53ca54aa477
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235271"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="2413a-101">Profilace aplikací ASP.Net MVC4 může vést k závažné chybě</span><span class="sxs-lookup"><span data-stu-id="2413a-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

|   |   |
|---|---|
|<span data-ttu-id="2413a-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="2413a-102">Details</span></span>|<span data-ttu-id="2413a-103">Profilovací programy pomocí sestavení NGEN/Profile dojít k chybě profilovaných aplikací technologie ASP.NET MVC4 při spuštění s "závažnou spuštění modulu výjimku.</span><span class="sxs-lookup"><span data-stu-id="2413a-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>|
|<span data-ttu-id="2413a-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="2413a-104">Suggestion</span></span>|<span data-ttu-id="2413a-105">Tento problém je vyřešen v rozhraní .NET Framework 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="2413a-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="2413a-106">Alternativně může profiler vyhnout tomuto problému zadáním <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> v jeho masky události.</span><span class="sxs-lookup"><span data-stu-id="2413a-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>|
|<span data-ttu-id="2413a-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="2413a-107">Scope</span></span>|<span data-ttu-id="2413a-108">Edge</span><span class="sxs-lookup"><span data-stu-id="2413a-108">Edge</span></span>|
|<span data-ttu-id="2413a-109">Version</span><span class="sxs-lookup"><span data-stu-id="2413a-109">Version</span></span>|<span data-ttu-id="2413a-110">4.5</span><span class="sxs-lookup"><span data-stu-id="2413a-110">4.5</span></span>|
|<span data-ttu-id="2413a-111">Type</span><span class="sxs-lookup"><span data-stu-id="2413a-111">Type</span></span>|<span data-ttu-id="2413a-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="2413a-112">Runtime</span></span>|
