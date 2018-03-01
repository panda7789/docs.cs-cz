---
title: "COR_PRF_GC_ROOT_KIND – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 537b39384d04e7a0080a22c6894cc2f6965b0bbc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corprfgcrootkind-enumeration"></a><span data-ttu-id="2f4c5-102">COR_PRF_GC_ROOT_KIND – výčet</span><span class="sxs-lookup"><span data-stu-id="2f4c5-102">COR_PRF_GC_ROOT_KIND Enumeration</span></span>
<span data-ttu-id="2f4c5-103">Určuje druh kořenové kolekce paměti, který je zveřejněný prostřednictvím [icorprofilercallback2::rootreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="2f4c5-103">Indicates the kind of garbage collection root that is exposed by the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f4c5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f4c5-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_ROOT_STACK = 1,  
    COR_PRF_GC_ROOT_FINALIZER = 2,  
    COR_PRF_GC_ROOT_HANDLE = 3,  
    COR_PRF_GC_ROOT_OTHER = 0  
} COR_PRF_GC_ROOT_KIND;  
```  
  
## <a name="members"></a><span data-ttu-id="2f4c5-105">Členové</span><span class="sxs-lookup"><span data-stu-id="2f4c5-105">Members</span></span>  
  
|<span data-ttu-id="2f4c5-106">Člen</span><span class="sxs-lookup"><span data-stu-id="2f4c5-106">Member</span></span>|<span data-ttu-id="2f4c5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2f4c5-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_STACK`|<span data-ttu-id="2f4c5-108">Kořenový adresář je proměnná v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="2f4c5-108">The root is a variable on the stack.</span></span>|  
|`COR_PRF_GC_ROOT_FINALIZER`|<span data-ttu-id="2f4c5-109">Kořenová je položku ve frontě finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="2f4c5-109">The root is an entry in the finalizer queue.</span></span>|  
|`COR_PRF_GC_ROOT_HANDLE`|<span data-ttu-id="2f4c5-110">Kořenový adresář je kolekce popisovač uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="2f4c5-110">The root is a garbage collection handle.</span></span>|  
|`COR_PRF_GC_ROOT_OTHER`|<span data-ttu-id="2f4c5-111">Druh kořenové není zadáno.</span><span class="sxs-lookup"><span data-stu-id="2f4c5-111">The kind of root is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2f4c5-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2f4c5-112">Requirements</span></span>  
 <span data-ttu-id="2f4c5-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f4c5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f4c5-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2f4c5-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2f4c5-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f4c5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f4c5-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f4c5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f4c5-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f4c5-117">See Also</span></span>  
 [<span data-ttu-id="2f4c5-118">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="2f4c5-118">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
