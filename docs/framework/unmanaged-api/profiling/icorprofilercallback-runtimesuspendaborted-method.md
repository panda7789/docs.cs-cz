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
ms.openlocfilehash: 62682ca19b9f987370ca11d2bda63fba27f28474
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782991"
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="bf6b1-102">ICorProfilerCallback::RuntimeSuspendAborted – metoda</span><span class="sxs-lookup"><span data-stu-id="bf6b1-102">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>
<span data-ttu-id="bf6b1-103">Oznámí profileru, že modul runtime byla přerušena pozastavení modulu runtime, které se vyskytují.</span><span class="sxs-lookup"><span data-stu-id="bf6b1-103">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf6b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf6b1-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="bf6b1-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bf6b1-105">Remarks</span></span>  
 <span data-ttu-id="bf6b1-106">Pozastavení běhu může být přerušeno dvěma vlákny současně pokusu o pozastavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="bf6b1-106">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="bf6b1-107">Buď [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) zpětného volání nebo `RuntimeSuspendAborted` zpětného volání dojde u následujících jedno vlákno [icorprofilercallback::runtimesuspendstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="bf6b1-107">Either the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="bf6b1-108">`RuntimeSuspendAborted` Zpětného volání je zaručeno, ke kterým dochází ve stejném vlákně jako `RuntimeSuspendStarted` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="bf6b1-108">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf6b1-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bf6b1-109">Requirements</span></span>  
 <span data-ttu-id="bf6b1-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf6b1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf6b1-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bf6b1-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bf6b1-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf6b1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf6b1-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf6b1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf6b1-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf6b1-114">See also</span></span>

- [<span data-ttu-id="bf6b1-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf6b1-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
