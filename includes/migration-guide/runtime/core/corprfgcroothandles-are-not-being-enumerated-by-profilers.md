---
ms.openlocfilehash: 8433899058c6f569e380999800557dbe8ed0a169
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649091"
---
### <a name="corprfgcroothandles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="5bc17-101">COR_PRF_GC_ROOT_HANDLEs nejsou výčtu podle profilovací programy</span><span class="sxs-lookup"><span data-stu-id="5bc17-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

|   |   |
|---|---|
|<span data-ttu-id="5bc17-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="5bc17-102">Details</span></span>|<span data-ttu-id="5bc17-103">V rozhraní .NET Framework v4.5.1, rozhraní API profilování <code>RootReferences2()</code> nesprávně nikdy vrací <code>COR_PRF_GC_ROOT_HANDLE</code> (se vrátí jako <code>COR_PRF_GC_ROOT_OTHER</code> místo).</span><span class="sxs-lookup"><span data-stu-id="5bc17-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="5bc17-104">Tento problém vyřešen, počínaje .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="5bc17-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>|
|<span data-ttu-id="5bc17-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="5bc17-105">Suggestion</span></span>|<span data-ttu-id="5bc17-106">Tento problém jsme opravili v rozhraní .NET Framework 4.6 a může vyřešit upgradem na verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5bc17-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="5bc17-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="5bc17-107">Scope</span></span>|<span data-ttu-id="5bc17-108">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="5bc17-108">Minor</span></span>|
|<span data-ttu-id="5bc17-109">Version</span><span class="sxs-lookup"><span data-stu-id="5bc17-109">Version</span></span>|<span data-ttu-id="5bc17-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="5bc17-110">4.5.1</span></span>|
|<span data-ttu-id="5bc17-111">Type</span><span class="sxs-lookup"><span data-stu-id="5bc17-111">Type</span></span>|<span data-ttu-id="5bc17-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="5bc17-112">Runtime</span></span>|
