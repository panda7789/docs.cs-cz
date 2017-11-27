---
title: "ICorProfilerCallback2::GarbageCollectionFinished – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2.GarbageCollectionFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2::GarbageCollectionFinished
helpviewer_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished method [.NET Framework profiling]
- GarbageCollectionFinished method [.NET Framework profiling]
ms.assetid: 1a5758ea-2354-43c0-92a3-32c9909d64e1
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 287c33a80144b9b04fd7e0797071d40e46a52454
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="520db-102">ICorProfilerCallback2::GarbageCollectionFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="520db-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="520db-103">Profileru upozorní, že uvolňování paměti bylo dokončeno a všechny zpětná volání kolekce paměti byl vydán pro ho.</span><span class="sxs-lookup"><span data-stu-id="520db-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="520db-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="520db-104">Syntax</span></span>  
  
```  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="520db-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="520db-105">Remarks</span></span>  
 <span data-ttu-id="520db-106">Je bezpečné pro přístup z profileru ke kontrole objekty v jejich poslední umístění při `GarbageCollectionFinished` metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="520db-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="520db-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="520db-107">Requirements</span></span>  
 <span data-ttu-id="520db-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="520db-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="520db-109">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="520db-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="520db-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="520db-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="520db-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="520db-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="520db-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="520db-112">See Also</span></span>  
 [<span data-ttu-id="520db-113">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="520db-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="520db-114">Icorprofilercallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="520db-114">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
