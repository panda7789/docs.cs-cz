---
ms.openlocfilehash: 4f52535e54607cc824500f9c6a14964a1dec9d32
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619957"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="66bd0-101">COR_PRF_GC_ROOT_HANDLEs nejsou vytvářeny pomocí profilovacích programů</span><span class="sxs-lookup"><span data-stu-id="66bd0-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

#### <a name="details"></a><span data-ttu-id="66bd0-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="66bd0-102">Details</span></span>

<span data-ttu-id="66bd0-103">V .NET Framework v 4.5.1 se rozhraní API profilování <code>RootReferences2()</code> nevrátí správně <code>COR_PRF_GC_ROOT_HANDLE</code> (vrátí se jako <code>COR_PRF_GC_ROOT_OTHER</code> místo).</span><span class="sxs-lookup"><span data-stu-id="66bd0-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="66bd0-104">Tento problém je vyřešen od .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="66bd0-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="66bd0-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="66bd0-105">Suggestion</span></span>

<span data-ttu-id="66bd0-106">Tento problém byl opravený v .NET Framework 4,6 a může se řešit upgradem na verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="66bd0-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="66bd0-107">Name</span><span class="sxs-lookup"><span data-stu-id="66bd0-107">Name</span></span>    | <span data-ttu-id="66bd0-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="66bd0-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="66bd0-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="66bd0-109">Scope</span></span>   |<span data-ttu-id="66bd0-110">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="66bd0-110">Minor</span></span>|
|<span data-ttu-id="66bd0-111">Verze</span><span class="sxs-lookup"><span data-stu-id="66bd0-111">Version</span></span>|<span data-ttu-id="66bd0-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="66bd0-112">4.5.1</span></span>|
|<span data-ttu-id="66bd0-113">Typ</span><span class="sxs-lookup"><span data-stu-id="66bd0-113">Type</span></span>|<span data-ttu-id="66bd0-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="66bd0-114">Runtime</span></span>|
