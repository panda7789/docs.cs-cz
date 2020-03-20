---
ms.openlocfilehash: 8433899058c6f569e380999800557dbe8ed0a169
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858419"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="6bcff-101">COR_PRF_GC_ROOT_HANDLEs nejsou vyjmenovány profilovacími programy</span><span class="sxs-lookup"><span data-stu-id="6bcff-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

|   |   |
|---|---|
|<span data-ttu-id="6bcff-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="6bcff-102">Details</span></span>|<span data-ttu-id="6bcff-103">V rozhraní .NET Framework v4.5.1 <code>RootReferences2()</code> profilování rozhraní API <code>COR_PRF_GC_ROOT_HANDLE</code> je nesprávně <code>COR_PRF_GC_ROOT_OTHER</code> vrací (jsou vráceny jako místo).</span><span class="sxs-lookup"><span data-stu-id="6bcff-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="6bcff-104">Tento problém je vyřešen počínaje rozhraním .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="6bcff-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>|
|<span data-ttu-id="6bcff-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="6bcff-105">Suggestion</span></span>|<span data-ttu-id="6bcff-106">Tento problém byl vyřešen v rozhraní .NET Framework 4.6 a může být vyřešen upgradem na tuto verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6bcff-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="6bcff-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="6bcff-107">Scope</span></span>|<span data-ttu-id="6bcff-108">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="6bcff-108">Minor</span></span>|
|<span data-ttu-id="6bcff-109">Version</span><span class="sxs-lookup"><span data-stu-id="6bcff-109">Version</span></span>|<span data-ttu-id="6bcff-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="6bcff-110">4.5.1</span></span>|
|<span data-ttu-id="6bcff-111">Typ</span><span class="sxs-lookup"><span data-stu-id="6bcff-111">Type</span></span>|<span data-ttu-id="6bcff-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="6bcff-112">Runtime</span></span>|
