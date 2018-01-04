---
title: "ICorProfilerCallback::RuntimeSuspendAborted – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeSuspendAborted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeSuspendAborted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted method [.NET Framework profiling]
- RuntimeSuspendAborted method [.NET Framework profiling]
ms.assetid: 5a8a4277-345b-448b-a028-fc8cff9998aa
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d62df6fc90a2601997aeb7ecbe410f1a35d7012
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="0ede3-102">ICorProfilerCallback::RuntimeSuspendAborted – metoda</span><span class="sxs-lookup"><span data-stu-id="0ede3-102">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>
<span data-ttu-id="0ede3-103">Aby modul runtime přerušil pozastavení runtime, který došlo ke upozorní profileru.</span><span class="sxs-lookup"><span data-stu-id="0ede3-103">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ede3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ede3-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="0ede3-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0ede3-105">Remarks</span></span>  
 <span data-ttu-id="0ede3-106">Pozastavení běhu může zrušit, pokud dva vláken současně pokusí pozastavit modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0ede3-106">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="0ede3-107">Buď [icorprofilercallback::runtimesuspendfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) zpětného volání nebo `RuntimeSuspendAborted` zpětného volání bude provedena v následující jedno vlákno [icorprofilercallback::runtimesuspendstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="0ede3-107">Either the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="0ede3-108">`RuntimeSuspendAborted` Zpětného volání záruku, že dojde k ve stejném vlákně, jako `RuntimeSuspendStarted` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="0ede3-108">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ede3-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0ede3-109">Requirements</span></span>  
 <span data-ttu-id="0ede3-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ede3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ede3-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0ede3-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0ede3-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ede3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ede3-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ede3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ede3-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ede3-114">See Also</span></span>  
 [<span data-ttu-id="0ede3-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ede3-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
