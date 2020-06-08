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
ms.openlocfilehash: 8694a2d19c3b98487b86da4273eb0c68fb9d9ace
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500114"
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a><span data-ttu-id="0b863-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave – metoda</span><span class="sxs-lookup"><span data-stu-id="0b863-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave Method</span></span>
<span data-ttu-id="0b863-103">Upozorní profileru, že zpětná fáze zpracování výjimek dokončila odvinutí funkce.</span><span class="sxs-lookup"><span data-stu-id="0b863-103">Notifies the profiler that the unwind phase of exception handling has finished unwinding a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b863-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b863-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="0b863-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b863-105">Remarks</span></span>  
 <span data-ttu-id="0b863-106">Při `ExceptionUnwindFunctionLeave` volání metody je instance funkce a její data zásobníku z zásobníku odebrána.</span><span class="sxs-lookup"><span data-stu-id="0b863-106">When the `ExceptionUnwindFunctionLeave` method is called, the function instance and its stack data are removed from the stack.</span></span>  
  
 <span data-ttu-id="0b863-107">Profiler by neměl během tohoto volání blokovat, protože zásobník pravděpodobně není ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit bezkontaktní uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="0b863-107">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="0b863-108">Pokud profiler zablokuje a dojde k pokusu o uvolnění paměti, modul runtime zablokuje dokud toto zpětné volání nevrátí.</span><span class="sxs-lookup"><span data-stu-id="0b863-108">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="0b863-109">Během tohoto volání nesmí Profiler volat do spravovaného kódu nebo jakýmkoli způsobem způsobit přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="0b863-109">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b863-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0b863-110">Requirements</span></span>  
 <span data-ttu-id="0b863-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b863-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b863-112">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0b863-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0b863-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0b863-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b863-114">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b863-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b863-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b863-115">See also</span></span>

- [<span data-ttu-id="0b863-116">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0b863-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="0b863-117">ExceptionUnwindFunctionEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="0b863-117">ExceptionUnwindFunctionEnter Method</span></span>](icorprofilercallback-exceptionunwindfunctionenter-method.md)
