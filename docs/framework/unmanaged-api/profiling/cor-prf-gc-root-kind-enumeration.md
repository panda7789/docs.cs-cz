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
ms.openlocfilehash: 0ea584bfff4340e5e9635d6c31e177e88765b582
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500868"
---
# <a name="cor_prf_gc_root_kind-enumeration"></a><span data-ttu-id="091c0-102">COR_PRF_GC_ROOT_KIND – výčet</span><span class="sxs-lookup"><span data-stu-id="091c0-102">COR_PRF_GC_ROOT_KIND Enumeration</span></span>
<span data-ttu-id="091c0-103">Určuje druh kořene uvolňování paměti, který je vystavený zpětnému volání [ICorProfilerCallback2:: RootReferences2 –](icorprofilercallback2-rootreferences2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="091c0-103">Indicates the kind of garbage collection root that is exposed by the [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="091c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="091c0-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_STACK = 1,  
    COR_PRF_GC_ROOT_FINALIZER = 2,  
    COR_PRF_GC_ROOT_HANDLE = 3,  
    COR_PRF_GC_ROOT_OTHER = 0  
} COR_PRF_GC_ROOT_KIND;  
```  
  
## <a name="members"></a><span data-ttu-id="091c0-105">Členové</span><span class="sxs-lookup"><span data-stu-id="091c0-105">Members</span></span>  
  
|<span data-ttu-id="091c0-106">Člen</span><span class="sxs-lookup"><span data-stu-id="091c0-106">Member</span></span>|<span data-ttu-id="091c0-107">Description</span><span class="sxs-lookup"><span data-stu-id="091c0-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_STACK`|<span data-ttu-id="091c0-108">Kořen je proměnná v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="091c0-108">The root is a variable on the stack.</span></span>|  
|`COR_PRF_GC_ROOT_FINALIZER`|<span data-ttu-id="091c0-109">Kořen je položka ve frontě finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="091c0-109">The root is an entry in the finalizer queue.</span></span>|  
|`COR_PRF_GC_ROOT_HANDLE`|<span data-ttu-id="091c0-110">Kořen je popisovač uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="091c0-110">The root is a garbage collection handle.</span></span>|  
|`COR_PRF_GC_ROOT_OTHER`|<span data-ttu-id="091c0-111">Není zadán typ kořene.</span><span class="sxs-lookup"><span data-stu-id="091c0-111">The kind of root is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="091c0-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="091c0-112">Requirements</span></span>  
 <span data-ttu-id="091c0-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="091c0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="091c0-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="091c0-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="091c0-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="091c0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="091c0-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="091c0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="091c0-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="091c0-117">See also</span></span>

- [<span data-ttu-id="091c0-118">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="091c0-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
