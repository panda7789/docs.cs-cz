---
ms.openlocfilehash: 8dc98b2d9c2c0b5f145ebce48cf8f5e054975c6e
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858419"
---
### <a name="corprfgcroothandles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="f1faa-101">COR_PRF_GC_ROOT_HANDLEs nejsou výčtu podle profilovací programy</span><span class="sxs-lookup"><span data-stu-id="f1faa-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f1faa-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="f1faa-102">Details</span></span>|<span data-ttu-id="f1faa-103">V rozhraní .NET Framework v4.5.1, rozhraní API profilování <code>RootReferences2()</code> nesprávně nikdy vrací <code>COR_PRF_GC_ROOT_HANDLE</code> (se vrátí jako <code>COR_PRF_GC_ROOT_OTHER</code> místo).</span><span class="sxs-lookup"><span data-stu-id="f1faa-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="f1faa-104">Tento problém vyřešen, počínaje .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="f1faa-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>|
|<span data-ttu-id="f1faa-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="f1faa-105">Suggestion</span></span>|<span data-ttu-id="f1faa-106">Tento problém jsme opravili v rozhraní .NET Framework 4.6 a může vyřešit upgradem na verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f1faa-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="f1faa-107">Scope</span><span class="sxs-lookup"><span data-stu-id="f1faa-107">Scope</span></span>|<span data-ttu-id="f1faa-108">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="f1faa-108">Minor</span></span>|
|<span data-ttu-id="f1faa-109">Version</span><span class="sxs-lookup"><span data-stu-id="f1faa-109">Version</span></span>|<span data-ttu-id="f1faa-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="f1faa-110">4.5.1</span></span>|
|<span data-ttu-id="f1faa-111">type</span><span class="sxs-lookup"><span data-stu-id="f1faa-111">Type</span></span>|<span data-ttu-id="f1faa-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="f1faa-112">Runtime</span></span>|

