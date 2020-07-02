---
ms.openlocfilehash: 2e13268d4983af5d2fdd6d12b4d9e67d61d07f3d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622029"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="c99e3-101">Profilace aplikací ASP.Net MVC4 může vést k závažné chybě spouštěcího modulu.</span><span class="sxs-lookup"><span data-stu-id="c99e3-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

#### <a name="details"></a><span data-ttu-id="c99e3-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="c99e3-102">Details</span></span>

<span data-ttu-id="c99e3-103">Profilery používající sestavení NGEN/Profile můžou při spuštění selhat ASP.NET MVC4 aplikací s závažnou výjimkou modulu provádění.</span><span class="sxs-lookup"><span data-stu-id="c99e3-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c99e3-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="c99e3-104">Suggestion</span></span>

<span data-ttu-id="c99e3-105">Tento problém je opravený v .NET Framework 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="c99e3-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="c99e3-106">Případně se může Profiler vyhnout tomuto problému zadáním <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> v jeho masce události.</span><span class="sxs-lookup"><span data-stu-id="c99e3-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>

| <span data-ttu-id="c99e3-107">Name</span><span class="sxs-lookup"><span data-stu-id="c99e3-107">Name</span></span>    | <span data-ttu-id="c99e3-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c99e3-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c99e3-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="c99e3-109">Scope</span></span>   |<span data-ttu-id="c99e3-110">Edge</span><span class="sxs-lookup"><span data-stu-id="c99e3-110">Edge</span></span>|
|<span data-ttu-id="c99e3-111">Verze</span><span class="sxs-lookup"><span data-stu-id="c99e3-111">Version</span></span>|<span data-ttu-id="c99e3-112">4.5</span><span class="sxs-lookup"><span data-stu-id="c99e3-112">4.5</span></span>|
|<span data-ttu-id="c99e3-113">Typ</span><span class="sxs-lookup"><span data-stu-id="c99e3-113">Type</span></span>|<span data-ttu-id="c99e3-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="c99e3-114">Runtime</span></span>|
