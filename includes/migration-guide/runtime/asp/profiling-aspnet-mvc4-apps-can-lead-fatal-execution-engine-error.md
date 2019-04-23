---
ms.openlocfilehash: 439a4976482639cd2e4e17315ec1a53ca54aa477
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803717"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="79a64-101">Profilace aplikací ASP.Net MVC4 může vést k závažné chybě</span><span class="sxs-lookup"><span data-stu-id="79a64-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

|   |   |
|---|---|
|<span data-ttu-id="79a64-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="79a64-102">Details</span></span>|<span data-ttu-id="79a64-103">Profilovací programy pomocí sestavení NGEN/Profile dojít k chybě profilovaných aplikací technologie ASP.NET MVC4 při spuštění s "závažnou spuštění modulu výjimku.</span><span class="sxs-lookup"><span data-stu-id="79a64-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>|
|<span data-ttu-id="79a64-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="79a64-104">Suggestion</span></span>|<span data-ttu-id="79a64-105">Tento problém je vyřešen v rozhraní .NET Framework 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="79a64-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="79a64-106">Alternativně může profiler vyhnout tomuto problému zadáním <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> v jeho masky události.</span><span class="sxs-lookup"><span data-stu-id="79a64-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>|
|<span data-ttu-id="79a64-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="79a64-107">Scope</span></span>|<span data-ttu-id="79a64-108">Edge</span><span class="sxs-lookup"><span data-stu-id="79a64-108">Edge</span></span>|
|<span data-ttu-id="79a64-109">Version</span><span class="sxs-lookup"><span data-stu-id="79a64-109">Version</span></span>|<span data-ttu-id="79a64-110">4.5</span><span class="sxs-lookup"><span data-stu-id="79a64-110">4.5</span></span>|
|<span data-ttu-id="79a64-111">Type</span><span class="sxs-lookup"><span data-stu-id="79a64-111">Type</span></span>|<span data-ttu-id="79a64-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="79a64-112">Runtime</span></span>|
