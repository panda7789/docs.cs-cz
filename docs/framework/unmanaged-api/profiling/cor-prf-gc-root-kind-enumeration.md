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
ms.openlocfilehash: bff45e6f6f57b95d07ac5073cb70020818cce000
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867162"
---
# <a name="cor_prf_gc_root_kind-enumeration"></a><span data-ttu-id="b45b7-102">COR_PRF_GC_ROOT_KIND – výčet</span><span class="sxs-lookup"><span data-stu-id="b45b7-102">COR_PRF_GC_ROOT_KIND Enumeration</span></span>
<span data-ttu-id="b45b7-103">Určuje druh kořene uvolňování paměti, který je vystavený zpětnému volání [ICorProfilerCallback2:: RootReferences2 –](icorprofilercallback2-rootreferences2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b45b7-103">Indicates the kind of garbage collection root that is exposed by the [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b45b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b45b7-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_STACK = 1,  
    COR_PRF_GC_ROOT_FINALIZER = 2,  
    COR_PRF_GC_ROOT_HANDLE = 3,  
    COR_PRF_GC_ROOT_OTHER = 0  
} COR_PRF_GC_ROOT_KIND;  
```  
  
## <a name="members"></a><span data-ttu-id="b45b7-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b45b7-105">Members</span></span>  
  
|<span data-ttu-id="b45b7-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b45b7-106">Member</span></span>|<span data-ttu-id="b45b7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b45b7-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_STACK`|<span data-ttu-id="b45b7-108">Kořen je proměnná v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="b45b7-108">The root is a variable on the stack.</span></span>|  
|`COR_PRF_GC_ROOT_FINALIZER`|<span data-ttu-id="b45b7-109">Kořen je položka ve frontě finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="b45b7-109">The root is an entry in the finalizer queue.</span></span>|  
|`COR_PRF_GC_ROOT_HANDLE`|<span data-ttu-id="b45b7-110">Kořen je popisovač uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b45b7-110">The root is a garbage collection handle.</span></span>|  
|`COR_PRF_GC_ROOT_OTHER`|<span data-ttu-id="b45b7-111">Není zadán typ kořene.</span><span class="sxs-lookup"><span data-stu-id="b45b7-111">The kind of root is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b45b7-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b45b7-112">Requirements</span></span>  
 <span data-ttu-id="b45b7-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b45b7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b45b7-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b45b7-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b45b7-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b45b7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b45b7-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b45b7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b45b7-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b45b7-117">See also</span></span>

- [<span data-ttu-id="b45b7-118">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="b45b7-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
