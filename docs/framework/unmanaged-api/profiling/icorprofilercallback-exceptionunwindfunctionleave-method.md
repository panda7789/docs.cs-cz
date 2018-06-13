---
title: ICorProfilerCallback::ExceptionUnwindFunctionLeave – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave method [.NET Framework profiling]
- ExceptionUnwindFunctionLeave method [.NET Framework profiling]
ms.assetid: ebaad1d5-ee0a-4cb0-96bc-8ba5d371b747
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a79a9c925392b0ab5e50269479b2f693f1a9b58d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451237"
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a><span data-ttu-id="68f23-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="68f23-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave Method</span></span>
<span data-ttu-id="68f23-103">Upozorní profileru, že byla dokončena fázi unwind výjimek unwinding funkce.</span><span class="sxs-lookup"><span data-stu-id="68f23-103">Notifies the profiler that the unwind phase of exception handling has finished unwinding a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68f23-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68f23-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="68f23-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="68f23-105">Remarks</span></span>  
 <span data-ttu-id="68f23-106">Když `ExceptionUnwindFunctionLeave` metoda je volána, instance funkce a jeho zásobníku data se odeberou ze zásobníku.</span><span class="sxs-lookup"><span data-stu-id="68f23-106">When the `ExceptionUnwindFunctionLeave` method is called, the function instance and its stack data are removed from the stack.</span></span>  
  
 <span data-ttu-id="68f23-107">Profileru by neměly blokovat během toto volání, protože zásobníku nemusí být ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit preemptivní uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="68f23-107">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="68f23-108">Pokud na profileru bloky a uvolnění paměti dojde k pokusu o, modul runtime zablokuje, dokud vrátí tuto zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="68f23-108">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="68f23-109">Navíc během tohoto hovoru profileru nesmějí provádět volání do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="68f23-109">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68f23-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="68f23-110">Requirements</span></span>  
 <span data-ttu-id="68f23-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68f23-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68f23-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="68f23-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="68f23-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68f23-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68f23-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68f23-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68f23-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="68f23-115">See Also</span></span>  
 [<span data-ttu-id="68f23-116">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68f23-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="68f23-117">ExceptionUnwindFunctionEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="68f23-117">ExceptionUnwindFunctionEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)
