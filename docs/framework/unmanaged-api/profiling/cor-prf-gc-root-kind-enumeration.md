---
title: COR_PRF_GC_ROOT_KIND – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_KIND
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_KIND
helpviewer_keywords:
- COR_PRF_GC_ROOT_KIND enumeration [.NET Framework profiling]
ms.assetid: b9fb1c03-417f-41d4-aed4-02cb4ade8def
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7dfbba3cef8afadfc6e12e53ea328c4fc7165ca0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599346"
---
# <a name="corprfgcrootkind-enumeration"></a><span data-ttu-id="5156a-102">COR_PRF_GC_ROOT_KIND – výčet</span><span class="sxs-lookup"><span data-stu-id="5156a-102">COR_PRF_GC_ROOT_KIND Enumeration</span></span>
<span data-ttu-id="5156a-103">Označuje druh kořenové kolekce uvolňování paměti, který je zveřejněný prostřednictvím [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="5156a-103">Indicates the kind of garbage collection root that is exposed by the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5156a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5156a-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_ROOT_STACK = 1,  
    COR_PRF_GC_ROOT_FINALIZER = 2,  
    COR_PRF_GC_ROOT_HANDLE = 3,  
    COR_PRF_GC_ROOT_OTHER = 0  
} COR_PRF_GC_ROOT_KIND;  
```  
  
## <a name="members"></a><span data-ttu-id="5156a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="5156a-105">Members</span></span>  
  
|<span data-ttu-id="5156a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="5156a-106">Member</span></span>|<span data-ttu-id="5156a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5156a-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_STACK`|<span data-ttu-id="5156a-108">Kořenový adresář je proměnná v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="5156a-108">The root is a variable on the stack.</span></span>|  
|`COR_PRF_GC_ROOT_FINALIZER`|<span data-ttu-id="5156a-109">Kořenový adresář je položka ve frontě finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="5156a-109">The root is an entry in the finalizer queue.</span></span>|  
|`COR_PRF_GC_ROOT_HANDLE`|<span data-ttu-id="5156a-110">Kořenový adresář je popisovač kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="5156a-110">The root is a garbage collection handle.</span></span>|  
|`COR_PRF_GC_ROOT_OTHER`|<span data-ttu-id="5156a-111">Druh root není zadána.</span><span class="sxs-lookup"><span data-stu-id="5156a-111">The kind of root is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5156a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5156a-112">Requirements</span></span>  
 <span data-ttu-id="5156a-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5156a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5156a-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5156a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5156a-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5156a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5156a-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5156a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5156a-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5156a-117">See also</span></span>

- [<span data-ttu-id="5156a-118">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="5156a-118">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
