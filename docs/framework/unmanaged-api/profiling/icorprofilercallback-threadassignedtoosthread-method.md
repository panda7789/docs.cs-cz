---
title: ICorProfilerCallback::ThreadAssignedToOSThread – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadAssignedToOSThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadAssignedToOSThread
helpviewer_keywords:
- ThreadAssignedToOSThread method [.NET Framework profiling]
- ICorProfilerCallback::ThreadAssignedToOSThread method [.NET Framework profiling]
ms.assetid: f9671e5a-7b14-4f5b-8404-58136422c8b2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eefcd4436a28fdf52cbe55da5d4bb7eea4449463
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158454"
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a><span data-ttu-id="9febe-102">ICorProfilerCallback::ThreadAssignedToOSThread – metoda</span><span class="sxs-lookup"><span data-stu-id="9febe-102">ICorProfilerCallback::ThreadAssignedToOSThread Method</span></span>
<span data-ttu-id="9febe-103">Oznámí profileru, že spravovaným vláknem se implementuje pomocí vlákno konkrétní operační systém.</span><span class="sxs-lookup"><span data-stu-id="9febe-103">Notifies the profiler that a managed thread is being implemented using a particular operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9febe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9febe-104">Syntax</span></span>  
  
```  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9febe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9febe-105">Parameters</span></span>  
 `managedThreadId`  
 <span data-ttu-id="9febe-106">[in] Identifikátor spravované vlákno.</span><span class="sxs-lookup"><span data-stu-id="9febe-106">[in] The identifier of the managed thread.</span></span>  
  
 `osThreadId`  
 <span data-ttu-id="9febe-107">[in] Identifikátor vlákna operačního systému.</span><span class="sxs-lookup"><span data-stu-id="9febe-107">[in] The identifier of the operating system thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9febe-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9febe-108">Remarks</span></span>  
 <span data-ttu-id="9febe-109">`ThreadAssignedToOSThread` Zpětného volání existuje tak, že profiler může udržovat přesné mapování mezi vlákna vlákna operačního systému na spravovaná vlákna.</span><span class="sxs-lookup"><span data-stu-id="9febe-109">The `ThreadAssignedToOSThread` callback exists so that the profiler can maintain an accurate mapping across fibers of operating system threads to managed threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9febe-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9febe-110">Requirements</span></span>  
 <span data-ttu-id="9febe-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9febe-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9febe-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9febe-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9febe-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9febe-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="9febe-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9febe-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9febe-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9febe-115">See also</span></span>

- [<span data-ttu-id="9febe-116">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9febe-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
