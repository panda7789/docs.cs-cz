---
title: ICorProfilerCallback::ExceptionUnwindFinallyLeave – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave method [.NET Framework profiling]
- ExceptionUnwindFinallyLeave method [.NET Framework profiling]
ms.assetid: 2350351e-f253-4c0c-a191-f952bc5700e6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce413ba184cfec731c6bac0d7f561c345bf53181
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452007"
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a><span data-ttu-id="e83fe-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="e83fe-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Method</span></span>
<span data-ttu-id="e83fe-103">Upozorní profileru, který fázi unwind výjimky zpracování opustil `finally` klauzule.</span><span class="sxs-lookup"><span data-stu-id="e83fe-103">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e83fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e83fe-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="e83fe-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e83fe-105">Remarks</span></span>  
 <span data-ttu-id="e83fe-106">Profileru by neměly blokovat během toto volání, protože zásobníku nemusí být ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit preemptivní uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="e83fe-106">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="e83fe-107">Pokud na profileru bloky a uvolnění paměti dojde k pokusu o, modul runtime zablokuje, dokud vrátí tuto zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="e83fe-107">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="e83fe-108">Navíc během tohoto hovoru profileru nesmějí provádět volání do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="e83fe-108">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e83fe-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e83fe-109">Requirements</span></span>  
 <span data-ttu-id="e83fe-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e83fe-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e83fe-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e83fe-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e83fe-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e83fe-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e83fe-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e83fe-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e83fe-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="e83fe-114">See Also</span></span>  
 [<span data-ttu-id="e83fe-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e83fe-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="e83fe-116">ExceptionUnwindFinallyEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="e83fe-116">ExceptionUnwindFinallyEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)
