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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61914482"
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="677b4-102">ICorProfilerCallback2::GarbageCollectionFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="677b4-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="677b4-103">Profiler upozorní, že uvolňování paměti byla dokončena a všechny zpětná volání kolekce uvolnění paměti byly vydány pro něj.</span><span class="sxs-lookup"><span data-stu-id="677b4-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="677b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="677b4-104">Syntax</span></span>  
  
```  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="677b4-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="677b4-105">Remarks</span></span>  
 <span data-ttu-id="677b4-106">Je bezpečný pro profiler pro kontrolu objektů v jejich konečné umístění při `GarbageCollectionFinished` metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="677b4-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="677b4-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="677b4-107">Requirements</span></span>  
 <span data-ttu-id="677b4-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="677b4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="677b4-109">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="677b4-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="677b4-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="677b4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="677b4-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="677b4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="677b4-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="677b4-112">See also</span></span>

- [<span data-ttu-id="677b4-113">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="677b4-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="677b4-114">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="677b4-114">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
