---
title: ICorProfilerCallback2::GarbageCollectionFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished
helpviewer_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished method [.NET Framework profiling]
- GarbageCollectionFinished method [.NET Framework profiling]
ms.assetid: 1a5758ea-2354-43c0-92a3-32c9909d64e1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f613842c12b50b8a58aac1b71bf2f3c53aaf961f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231094"
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="059c5-102">ICorProfilerCallback2::GarbageCollectionFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="059c5-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="059c5-103">Profiler upozorní, že uvolňování paměti byla dokončena a všechny zpětná volání kolekce uvolnění paměti byly vydány pro něj.</span><span class="sxs-lookup"><span data-stu-id="059c5-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="059c5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="059c5-104">Syntax</span></span>  
  
```  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="059c5-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="059c5-105">Remarks</span></span>  
 <span data-ttu-id="059c5-106">Je bezpečný pro profiler pro kontrolu objektů v jejich konečné umístění při `GarbageCollectionFinished` metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="059c5-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="059c5-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="059c5-107">Requirements</span></span>  
 <span data-ttu-id="059c5-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="059c5-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="059c5-109">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="059c5-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="059c5-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="059c5-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="059c5-111">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="059c5-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="059c5-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="059c5-112">See also</span></span>

- [<span data-ttu-id="059c5-113">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="059c5-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="059c5-114">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="059c5-114">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
