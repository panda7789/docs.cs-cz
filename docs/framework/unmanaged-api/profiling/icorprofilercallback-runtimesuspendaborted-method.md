---
title: ICorProfilerCallback::RuntimeSuspendAborted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendAborted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted method [.NET Framework profiling]
- RuntimeSuspendAborted method [.NET Framework profiling]
ms.assetid: 5a8a4277-345b-448b-a028-fc8cff9998aa
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e9aaf7325b8e7e65aa98904513cc7efe94e35087
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041805"
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="58cbe-102">ICorProfilerCallback::RuntimeSuspendAborted – metoda</span><span class="sxs-lookup"><span data-stu-id="58cbe-102">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>
<span data-ttu-id="58cbe-103">Oznámí profileru, že modul runtime byla přerušena pozastavení modulu runtime, které se vyskytují.</span><span class="sxs-lookup"><span data-stu-id="58cbe-103">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58cbe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58cbe-104">Syntax</span></span>  
  
```  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="58cbe-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="58cbe-105">Remarks</span></span>  
 <span data-ttu-id="58cbe-106">Pozastavení běhu může být přerušeno dvěma vlákny současně pokusu o pozastavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="58cbe-106">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="58cbe-107">Buď [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) zpětného volání nebo `RuntimeSuspendAborted` zpětného volání dojde u následujících jedno vlákno [icorprofilercallback::runtimesuspendstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="58cbe-107">Either the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="58cbe-108">`RuntimeSuspendAborted` Zpětného volání je zaručeno, ke kterým dochází ve stejném vlákně jako `RuntimeSuspendStarted` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="58cbe-108">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58cbe-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="58cbe-109">Requirements</span></span>  
 <span data-ttu-id="58cbe-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58cbe-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58cbe-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="58cbe-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="58cbe-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58cbe-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58cbe-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58cbe-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58cbe-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58cbe-114">See also</span></span>

- [<span data-ttu-id="58cbe-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="58cbe-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
