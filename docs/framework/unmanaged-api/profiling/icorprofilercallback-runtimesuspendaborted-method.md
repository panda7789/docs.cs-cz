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
ms.openlocfilehash: a3fb5c398b8ccd7caba0b005bcf03e64ecef4ba5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503247"
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="77786-102">ICorProfilerCallback::RuntimeSuspendAborted – metoda</span><span class="sxs-lookup"><span data-stu-id="77786-102">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>
<span data-ttu-id="77786-103">Upozorní profileru, že modul runtime přerušil přerušení běhu, ke kterému došlo.</span><span class="sxs-lookup"><span data-stu-id="77786-103">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77786-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77786-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="77786-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="77786-105">Remarks</span></span>  
 <span data-ttu-id="77786-106">Pozastavení běhu může být přerušeno, pokud se dvě vlákna současně pokusí pozastavit modul runtime.</span><span class="sxs-lookup"><span data-stu-id="77786-106">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="77786-107">Zpětné volání [ICorProfilerCallback:: RuntimeSuspendFinished –](icorprofilercallback-runtimesuspendfinished-method.md) nebo `RuntimeSuspendAborted` zpětné volání bude provedeno v jednom vlákně po zpětném volání [ICorProfilerCallback:: runtimesuspendstarted –](icorprofilercallback-runtimesuspendstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="77786-107">Either the [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="77786-108">`RuntimeSuspendAborted`Ke zpětnému volání je zaručeno, že dojde ve stejném vlákně jako `RuntimeSuspendStarted` zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="77786-108">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77786-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="77786-109">Requirements</span></span>  
 <span data-ttu-id="77786-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77786-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77786-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="77786-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="77786-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="77786-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77786-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77786-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77786-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77786-114">See also</span></span>

- [<span data-ttu-id="77786-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="77786-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
