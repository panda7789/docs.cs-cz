---
ms.openlocfilehash: 439a4976482639cd2e4e17315ec1a53ca54aa477
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803202"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="47552-101">Profilování ASP.Net aplikací MVC4 může vést k závažné chybě spuštění motoru</span><span class="sxs-lookup"><span data-stu-id="47552-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

|   |   |
|---|---|
|<span data-ttu-id="47552-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="47552-102">Details</span></span>|<span data-ttu-id="47552-103">Profilovací programy používající sestavení NGEN /Profile mohou při spuštění s chybně závažnou výjimkou modulu provádění dojít k chybě ASP.NET aplikacích MVC4.</span><span class="sxs-lookup"><span data-stu-id="47552-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>|
|<span data-ttu-id="47552-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="47552-104">Suggestion</span></span>|<span data-ttu-id="47552-105">Tento problém je vyřešen v rozhraní .NET Framework 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="47552-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="47552-106">Případně profiler může zabránit tomuto problému <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> zadáním v jeho maska události.</span><span class="sxs-lookup"><span data-stu-id="47552-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>|
|<span data-ttu-id="47552-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="47552-107">Scope</span></span>|<span data-ttu-id="47552-108">Edge</span><span class="sxs-lookup"><span data-stu-id="47552-108">Edge</span></span>|
|<span data-ttu-id="47552-109">Version</span><span class="sxs-lookup"><span data-stu-id="47552-109">Version</span></span>|<span data-ttu-id="47552-110">4.5</span><span class="sxs-lookup"><span data-stu-id="47552-110">4.5</span></span>|
|<span data-ttu-id="47552-111">Typ</span><span class="sxs-lookup"><span data-stu-id="47552-111">Type</span></span>|<span data-ttu-id="47552-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="47552-112">Runtime</span></span>|
