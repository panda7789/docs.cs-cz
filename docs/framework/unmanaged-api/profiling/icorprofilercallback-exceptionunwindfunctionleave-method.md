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
ms.openlocfilehash: 305c8c7abf778ea68efe06f3bdb57af001ea1b9a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227708"
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a><span data-ttu-id="b9c8a-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="b9c8a-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave Method</span></span>
<span data-ttu-id="b9c8a-103">Unwind fáze zpracování výjimek dokončení uvolnění funkce oznámí profileru.</span><span class="sxs-lookup"><span data-stu-id="b9c8a-103">Notifies the profiler that the unwind phase of exception handling has finished unwinding a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9c8a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9c8a-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="b9c8a-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b9c8a-105">Remarks</span></span>  
 <span data-ttu-id="b9c8a-106">Když `ExceptionUnwindFunctionLeave` metoda je volána, instance funkce a její zásobníku data se odeberou ze zásobníku.</span><span class="sxs-lookup"><span data-stu-id="b9c8a-106">When the `ExceptionUnwindFunctionLeave` method is called, the function instance and its stack data are removed from the stack.</span></span>  
  
 <span data-ttu-id="b9c8a-107">Profiler by neměl přerušováno během toto volání, protože zásobník nemusí být ve stavu, která umožňuje uvolňování paměti, a proto není možné preemptive uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b9c8a-107">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="b9c8a-108">Pokud se profiler bloky a uvolnění paměti dojde k pokusu o, modul runtime bude blokovat, dokud tento zpětného volání vrátí.</span><span class="sxs-lookup"><span data-stu-id="b9c8a-108">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="b9c8a-109">Během tohoto volání nesmí také profiler volat, do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="b9c8a-109">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9c8a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b9c8a-110">Requirements</span></span>  
 <span data-ttu-id="b9c8a-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9c8a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9c8a-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b9c8a-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b9c8a-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9c8a-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b9c8a-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b9c8a-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b9c8a-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b9c8a-115">See also</span></span>

- [<span data-ttu-id="b9c8a-116">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9c8a-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="b9c8a-117">ExceptionUnwindFunctionEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="b9c8a-117">ExceptionUnwindFunctionEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)
