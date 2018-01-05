---
title: "ICorProfilerCallback::ThreadAssignedToOSThread – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ThreadAssignedToOSThread
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ThreadAssignedToOSThread
helpviewer_keywords:
- ThreadAssignedToOSThread method [.NET Framework profiling]
- ICorProfilerCallback::ThreadAssignedToOSThread method [.NET Framework profiling]
ms.assetid: f9671e5a-7b14-4f5b-8404-58136422c8b2
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 42c23a8190ea611d0333ebd96a31428574191b23
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a><span data-ttu-id="215d2-102">ICorProfilerCallback::ThreadAssignedToOSThread – metoda</span><span class="sxs-lookup"><span data-stu-id="215d2-102">ICorProfilerCallback::ThreadAssignedToOSThread Method</span></span>
<span data-ttu-id="215d2-103">Upozorní profileru, že spravované vlákno se implementuje pomocí vlákno konkrétní operační systém.</span><span class="sxs-lookup"><span data-stu-id="215d2-103">Notifies the profiler that a managed thread is being implemented using a particular operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="215d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="215d2-104">Syntax</span></span>  
  
```  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="215d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="215d2-105">Parameters</span></span>  
 `managedThreadId`  
 <span data-ttu-id="215d2-106">[v] Identifikátor spravovaných vláken.</span><span class="sxs-lookup"><span data-stu-id="215d2-106">[in] The identifier of the managed thread.</span></span>  
  
 `osThreadId`  
 <span data-ttu-id="215d2-107">[v] Identifikátor vláknu operačního systému.</span><span class="sxs-lookup"><span data-stu-id="215d2-107">[in] The identifier of the operating system thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="215d2-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="215d2-108">Remarks</span></span>  
 <span data-ttu-id="215d2-109">`ThreadAssignedToOSThread` Zpětného volání existuje tak, aby profileru můžete udržovat přesné mapování mezi jsou vlákna vláken operačního systému na spravovaná vlákna.</span><span class="sxs-lookup"><span data-stu-id="215d2-109">The `ThreadAssignedToOSThread` callback exists so that the profiler can maintain an accurate mapping across fibers of operating system threads to managed threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="215d2-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="215d2-110">Requirements</span></span>  
 <span data-ttu-id="215d2-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="215d2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="215d2-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="215d2-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="215d2-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="215d2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="215d2-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="215d2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="215d2-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="215d2-115">See Also</span></span>  
 [<span data-ttu-id="215d2-116">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="215d2-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
